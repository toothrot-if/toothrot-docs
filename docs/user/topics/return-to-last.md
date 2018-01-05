
/---- previous
[Next Node](next-node.md)
----/

# Returning to the Last Node

A node can specify that its *next* node is the last node that was shown before the
current node. This is as easy as writing this on a new line at the end of your node:

```toothrot
(<)
```

You can also return to the last node with a certain [tag](node-tags.md). For example, if you want to
return to the last visited node that is tagged "room", you can write:

```toothrot
(<) room
```

In the game, the return is made visible by the *return [indicator](indicators.md)*,
a left-facing triangle:

![Return indicator](../../images/return-indicator.png)

## Returning from anonymous nodes

When a return is written in a chain of anonymous nodes
(see [shorthand notation for next nodes](next-node.md#shorthand-notation)), the return
target is **not** the previous anonymous node, nor is it the named node which the chain of
anonymous nodes belongs to; instead, the return target is the node that was displayed
*before* the named node that contains the chain of anonymous nodes.


/---- next
[Option Menus](option-menus.md)
----/
