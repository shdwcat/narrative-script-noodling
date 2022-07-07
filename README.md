# Getting Started

Install this extension for vscode in order to support Wikilink syntax in Markdown files:
https://marketplace.visualstudio.com/items?itemName=shdwcat.markdown-wiki-links-preview-extended

# Notes

[Test.Yarn](Content/Test.yarn) is a very literal port of the [Chatterbox Test.Yarn](https://github.com/JujuAdams/Chatterbox/blob/master/datafiles/Test.yarn) script converted to 'Narrative Markdown', in the following way:

1. Node titles are declared with Markdown headers
1. Command syntax (`<<command stuff>>`) uses Markdown-style backticks (`) instead
1. Markdown list syntax (using `+` `-` or `*`) replaces Yarn Option syntax (`-> Option`)
1. `<<jump Node>>` syntax is replaced by wikilinks preceded by `=>` e.g. `=> [[#Node1]]` (see examples in Test.yarn)
    - Note that `#Heading` links are used to link between nodes in the same file. You can link to other files via `[[File]]`, and nodes within other files via `[[File#Heading]]`.

# Future Thoughts

## Dedicated if/else syntax using `?` lists?
For example, replace this:
```
`if $variable2 is 1`
    You chose Choice 1!
`endif`
`if $variable2 is 2`
    You chose Choice 2!
`endif`
`if $variable2 is 0`
    We failed to set the variable!
`endif`
```
With this:
```
? `if $variable2 is 1`
	You chose Choice 1!
? `if $variable2 is 2`
    You chose Choice 2!
? `if $variable2 is 0`
    We failed to set the variable!
```
Note: this would benefit from (and basically require) a vscode extension specifically for this custom markdown format

# ink-style choice limiting

[Ink](https://github.com/inkle/ink/) has a concept called [Sticky Choices](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md#sticky-choices), where the different choice symbols mean different things:
* `*` is a choice that will only be shown once
* `+` is a choice that will be shown no matter how many times you choose it

Since Markdown already supports using those symbols for list items, it wouldn't be hard to support something similar in an implementation

The one issue I can think of is that the markdown spec says that if you mix the list item symbol then the items are considered parts of separate lists, rather than different types of items within the same list. Solvable, but a bit icky, perhaps.