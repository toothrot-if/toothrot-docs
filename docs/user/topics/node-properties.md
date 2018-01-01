
/---- previous
[Option Menus](options-menus.md)
----/

# Node Properties

Nodes can be given properties using the `(#)` syntax:

```toothrot
### my_node

(#) key: "value"

The node's text.
```

A line starting with `(#)` sets a property of the node. The first part after `(#)` and
before `:` is the *property name*. Everything after `:` until the end of the line is the
*property value*. Values must be valid [JSON](http://json.org) values
(strings, numbers, arrays, objects).

Node properties can be changed at runtime of the game using scripts. Property values are
automatically saved when a savegame is created and will be restored when the savegame is
loaded.

/---- next
[Timeout](timeout.md)
----/
