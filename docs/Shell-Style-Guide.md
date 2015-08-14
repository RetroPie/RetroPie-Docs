# RetroPie-Setup Script Code Style Guide Snippets

<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [Features and Bugs](#features-and-bugs)
    - [Command Substitution](#command-substitution)
    - [Test and Square Braces](#test-and-square-braces)
    - [Testing Strings](#testing-strings)
- [Naming Conventions](#naming-conventions)
    - [Function Names](#function-names)
    - [Variable Names](#variable-names)
    - [Constants and Environment Variable Names](#constants-and-environment-variable-names)
    - [Read-only variables](#read-only-variables)
    - [Use Local Variables](#use-local-variables)
- [Comments](#comments)
- [Function Comments](#function-comments)
    - [Implementation Comments](#implementation-comments)
- [Formatting](#formatting)
    - [Indentation](#indentation)
    - [Pipelines](#pipelines)
    - [Braces](#braces)
- [Conclusion](#conclusion)

<!-- /MarkdownTOC -->


## Introduction

This document describes the style guide that has to be used used for the devlopment of the RetroPie-Setup Script sources. This guide is adapted from the [Google Shell Style Guide](https://google-styleguide.googlecode.com/svn/trunk/shell.xml?showone=Indentation#Indentation).

## Features and Bugs

### Command Substitution

Use $(command) instead of backticks.

Nested backticks require escaping the inner ones with \. The $(command) format doesn't change when nested and is easier to read.

Example:

``` bash
# This is preferred:
var="$(command "$(command1)")"

# This is not:
var="`command \`command1\``"
```

### Test and Square Braces

\[\[ ... \]\] is preferred over \[, test and /usr/bin/\[.
\[\[ ... \]\] reduces errors as no pathname expansion or word splitting takes place between \[\[ and \]\] and \[\[ ... \]\] allows for regular expression matching where \[ ... \] does not.

``` bash
# This ensures the string on the left is made up of characters in the
# alnum character class followed by the string name.
# Note that the RHS should not be quoted here.
# For the gory details, see
# E14 at http://tiswww.case.edu/php/chet/bash/FAQ
if [[ "filename" =~ ^[[:alnum:]]+name ]]; then
echo "Match"
fi

# This matches the exact pattern "f*" (Does not match in this case)
if [[ "filename" == "f*" ]]; then
echo "Match"
fi

# This gives a "too many arguments" error as f* is expanded to the
# contents of the current directory
if [ "filename" == f* ]; then
echo "Match"
fi
```

### Testing Strings

Use quotes rather than filler characters where possible.
Bash is smart enough to deal with an empty string in a test. So, given that the code is much easier to read, use tests for empty/non-empty strings or empty strings rather than filler characters.

``` bash
# Do this:
if [[ "${my_var}" == "some_string" ]]; then
do_something
fi

# -z (string length is zero) and -n (string length is not zero) are
# preferred over testing for an empty string
if [[ -z "${my_var}" ]]; then
do_something
fi

# This is OK (ensure quotes on the empty side), but not preferred:
if [[ "${my_var}" == "" ]]; then
do_something
fi

# Not this:
if [[ "${my_var}X" == "some_stringX" ]]; then
do_something
fi
```

To avoid confusion about what you're testing for, explicitly use -z or -n.

``` bash
# Use this
if [[ -n "${my_var}" ]]; then
do_something
fi

# Instead of this as errors can occur if ${my_var} expands to a test
# flag
if [[ "${my_var}" ]]; then
do_something
fi
```

## Naming Conventions

### Function Names

Functions should start with a non-capital letter and have a capital letter for each new word. No underscores. Parentheses are required after the function name.

The only exception to this rule is when defining interface functions for the RetroPie-Setup Script modules.


For example:

``` bash
function depends_retroarch() {  % OK, module interface function
...
}

function sources_retroarch() {  % OK, module interface function
...
}

function build_retroarch() {  % OK, module interface function
...
}

function install_retroarch() {  % OK, module interface function
...
}

function ensureSystemretroconfig {  % OK
...
}

function ensure_another_Systemretroconfig {  % NOT OK, no module interface function
...
}

function configure_retroarch() {  % OK, module interface function
...
}
```


### Variable Names

The names of variables are generally all lowercase and can use underscores if needed.


### Constants and Environment Variable Names

All caps, separated with underscores, declared at the top of the file.
Constants and anything exported to the environment should be capitalized.

``` bash
# Constant
readonly PATH_TO_FILES='/some/path'

# Both constant and environment
declare -xr ORACLE_SID='PROD'
Some things become constant at their first setting (for example, via getopts). Thus, it's OK to set a constant in getopts or based on a condition, but it should be made readonly immediately afterwards. Note that declare doesn't operate on global variables within functions, so readonly or export is recommended instead.

VERBOSE='false'
while getopts 'v' flag; do
case "${flag}" in
v) VERBOSE='true' ;;
esac
done
readonly VERBOSE
```

### Read-only variables

Use readonly or declare -r to ensure they're read only.
As globals are widely used in shell, it's important to catch errors when working with them. When you declare a variable that is meant to be read-only, make this explicit.

``` bash
zip_version="$(dpkg --status zip | grep Version: | cut -d ' ' -f 2)"
if [[ -z "${zip_version}" ]]; then
    error_message
else
    readonly zip_version
fi
```

### Use Local Variables

Declare function-specific variables with local. Declaration and assignment should be on different lines.
Ensure that local variables are only seen inside a function and its children by using local when declaring them. This avoids polluting the global name space and inadvertently setting variables that may have significance outside the function.

Declaration and assignment must be separate statements when the assignment value is provided by a command substitution; as the 'local' builtin does not propagate the exit code from the command substitution.

``` bash
my_func2() {
    local name="$1"

    # Separate lines for declaration and assignment:
    local my_var
    my_var="$(my_func)" || return

    # DO NOT do this: $? contains the exit code of 'local', not my_func
    local my_var="$(my_func)"
    [[ $? -eq 0 ]] || return

    ...
}
```

## Comments

## Function Comments

Any function that is not both obvious and short must be commented. Any function in a library must be commented regardless of length or complexity.
It should be possible for someone else to learn how to use your program or to use a function in your library by reading the comments (and self-help, if provided) without reading the code.

All function comments should contain:

Description of the function
Global variables used and modified
Arguments taken
Returned values other than the default exit status of the last command run
Example:

``` bash
#!/bin/bash
#
# Perform hot backups of Oracle databases.

export PATH='/usr/xpg4/bin:/usr/bin:/opt/csw/bin:/opt/goog/bin'

#######################################
# Cleanup files from the backup dir
# Globals:
#   BACKUP_DIR
#   ORACLE_SID
# Arguments:
#   None
# Returns:
#   None
#######################################
cleanup() {
    ...
}
```

### Implementation Comments

Comment tricky, non-obvious, interesting or important parts of your code.


## Formatting

### Indentation

Indent 4 spaces. No tabs.

Use blank lines between blocks to improve readability. Indentation is two spaces. Whatever you do, don't use tabs. For existing files, stay faithful to the existing indentation.


### Pipelines

Pipelines should be split one per line if they don't all fit on one line.
If a pipeline all fits on one line, it should be on one line.

If not, it should be split at one pipe segment per line with the pipe on the newline and a 2 space indent for the next section of the pipe. This applies to a chain of commands combined using '|' as well as to logical compounds using '||' and '&&'.

Example:
``` bash
# All fits on one line
command1 | command2

# Long commands
command1 \
| command2 \
| command3 \
| command4
```

### Braces

The open parenthesis is always on the same line as the function name. The closing parenthesis is always on a separate line.

For example:

``` bash
function ensureSystemretroconfig {  % OK
...
}

function ensureSystemretroconfig
{  % NOT OK
...
}
```

## Conclusion

Use common sense and BE CONSISTENT.
