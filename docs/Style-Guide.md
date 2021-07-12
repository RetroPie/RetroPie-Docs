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

### Comments

This is a comment:
```
[I CAN WRITE WHATEVER I WANT HERE!]: #
```
