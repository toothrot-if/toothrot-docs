
/---- previous
[Linking to Other Nodes](links.md)
----/

# Option Menus

Each text node can have an option menu. Options are displayed as buttons below the text of the node.
If you want to write a quiz game or a choice game or have dialogs like in point and click
adventures, options are probably the right thing to use.

To add an option to a text node, just write it at the end of the node's text like this:

```toothrot
(@) Click me? => option_clicked
```

This will display a button with the text `Click me?` and, when clicked, it will go to the node
named `option_clicked`.

You can also specify a value for an option:

```toothrot
(@) Click me? => option_clicked | This is the value
```

When a user clicks on an option with a value, the chosen value will be saved in the special
variable `$._choice`. In the example above, if the user clicks the option, the `$._choice` variable
will contain the string `"This is the value"`.

Options can be shown or hidden depending on a node's flags (see the section about flags for more
info). For example, the following will show the `Open` option only when the node has a flag
`closed` set, and it will only show the `Close` option if that flag is not set on the node.

```toothrot
(@) closed  ??? Open => open_container
(@) !closed ??? Closed => close_container
```

/---- next
[Node Properties](node-properties.md)
----/
