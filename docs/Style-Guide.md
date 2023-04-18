# RetroPie documentation style guide

RetroPie documentation pages uses [Markdown](https://daringfireball.net/projects/markdown/) for formatting and [MkDocs](https://github.com/mkdocs/mkdocs) to  the documentation pages. The sources are hosted as a Github project at [RetroPie-Docs](https://github.com/retropie/retropie-docs/).

You'll want to use [Commonmark](http://commonmark.org/help/) Markdown and the reason for this is MkDocs' Python parsers handle Markdown flavours differently and it will choke on certain aspects of Github (or other) flavoured Markdown.

To modify or add a new page, a Github account is required.   
An existing page can be edited by:   

- editing the page from the Docs project repository directly, picking the page from one of pages in the [repository](https://github.com/RetroPie/RetroPie-Docs/tree/master/docs)
- clicking on the _Edit_ link at the top of the page, from the documentation site

After editing is complete, a Github pull request (PR) should be submitted to the RetroPie-Docs Github repository. Github will do that automatically if you used the web interface to edit the page.

When adding a new page that should present in the navigation menu (TOC) of the documentation, the `mkdocs.yml` file should be also modified and the new page added under the `nav` setting.

The following are some notes on proper syntax.

### Headings

The headings (defined by `#`) should follow a natural progression of the hierarchy of the page contents. You cannot have two title headings otherwise they won't show up on the table of contents on the right side of the page

E.G.
```
# Title
## Main heading one
### Sub Heading one
### Sub heading two
## Main heading two
```
etc.

### Links

Links should follow this syntax

```
[Link](http://link)
```
If it is a link to another documentation page, it should be the name of the page:
```
[Installation](Installation)
```

You can link to a specific section of a document page by adding an anchor (`#`) to that particular section:
```
[NeoGeo BIOS talk](Neogeo#BIOS_Talk)
```

Bare URLs can be formatted automatically as links by enclosing them with angle brackets (`<` , `>`):
```
<https://retropie.org.uk/forum>
```

### Code Blocks

Code blocks should be created with backticks: 1 set for inline code highlighting and 3 for code blocks

* Inline code highlights:

`` `inline` ``

will render as:
`inline` 

* Code blocks:


` ``` `

`code block`

` ``` ` 

will render as:
```
code block
```

Code blocks can have syntax highlighting applied, by specifying the type of code/text file contained in the block. The list of supported lexers is available on the [Pygments site](https://pygments.org/languages/).

Example highlighting for a shell script
````
``` sh
function printMsgs() {
    local type="$1"
    shift
    if [[ "$__nodialog" == "1" && "$type" == "dialog" ]]; then
        type="console"
    fi
    for msg in "$@"; do
        [[ "$type" == "dialog" ]] && dialog --backtitle "$__backtitle" --cr-wrap --no-collapse --msgbox "$msg" 20 60 >/dev/tty
        [[ "$type" == "console" ]] && echo -e "$msg"
        [[ "$type" == "heading" ]] && echo -e "\n= = = = = = = = = = = = = = = = = = = = =\n$msg\n= = = = = = = = = = = = = = = = = = = = =\n"
    done
    return 0
}
```
````

Optionally, a title attribute can be added to the code block, which will appear on top of the formatted block.
````
``` ini title="SNES Controller Configuration"
input_device = "USB gamepad           "
input_driver = "udev"
input_r_btn = "5"
input_save_state_btn = "5"
input_start_btn = "9"
input_exit_emulator_btn = "9"
input_l_btn = "4"
input_load_state_btn = "4"
input_up_axis = "-1"
input_a_btn = "1"
input_b_btn = "2"
input_reset_btn = "2"
input_down_axis = "+1"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "0"
input_menu_toggle_btn = "0"
input_select_btn = "8"
input_enable_hotkey_btn = "8"
input_y_btn = "3"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
```
````


### Nesting lists

If you are doing sub-nests on un-ordered lists, use 2 spaces to indent each list level.

```
- 1st list level
  - 2nd level
    -  a 3rd level
  - 2nd level again
```

It should render like this:

- 1st list level
  - 2nd level
    -  a 3rd level
  - 2nd level again

A line break in a list should be created by using 4 spaces:
```
- a list item
    continued here on the 2nd paragraph
- 2nd list item

```

Will render as:

- a list item   
    continued here on the 2nd paragraph
- 2nd list item


### Numbering

Numbers will only order properly if in a listed sequence. If that sequence is broken by paragraphs then the numbering will restart.

Numbered lists are formatted as follows:
```
1. item 1
2. item 2
3. item 3
4. item 4
```
If they are not in a listed sequence then you can just label the numbers manually with:

```
Step 1.
Step 2.
Step 3.
```
etc. or you can just use un-ordered lists if numbers really aren't that important.

### Symbols/Emojis

Emojis are not supported with Python markdown and should be avoided. Rather important text should be bolded or italicised.

The following in Github:
```
:exclamation:
```
renders to :exclamation:

but in the generated docs it will show
```
:exclamation:
```

### Images

Images can be added using the standard Markdown syntax:

``` md
![Image Title](path/url/to/image)
```

To add a caption to the image, the `figure markdown` tag can be used:

``` md
<figure markdown>
  ![Image Title](path)
  <figcaption>Image caption</figcaption>
</figure>
```

The `figcaption` tag accepts the usual Markdown text styling options, so the caption text can be bolded/emphasized/underlined/etc.
### Comments

This is a comment:
```
[I CAN WRITE WHATEVER I WANT HERE!]: #
```
