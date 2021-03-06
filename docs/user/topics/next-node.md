
/---- previous
[Linking to Other Nodes](links.md)
----/

# Next Node

A node can have a *next node*. The next node can be reached by clicking somewhere on the screen
or by pressing either the `SPACE` or `RIGHT` key. You can specify the next node by writing
`(>) name_of_next_node` on a new line.

For example, if you want the next node of the node `my_node` to be `another_node`,
you can write it like this:

```toothrot
### my_node

Some text.

(>) another_node
```

The fact that a node has a next node is made visible in the game by a right-facing triangle,
the *next [indicator](indicators.md)*:

![Next indicator](../../images/next-indicator.png)


## Shorthand notation

Sometimes you might want to create many connected nodes that don't need to be accessible from
somewhere else. There's a shorthand notation for nodes like that:

```toothrot
### boring_story

Once upon a time, there was a man.
***
He married a woman from another village.
***
They had a lot of children.
***
The man and the woman grew older and older.
***
Then they died.
```

In this example, we have a named node `boring_story` and a bunch of connected
nodes defined by `***`. Nodes connected in this way are called *anonymous nodes* because
they don't have a name of its own.

/---- info
**Please note:** Anonymous nodes behave a little differently when it comes to returning
to the last node. See the next page for details.
----/

/---- next
[Return to the Last Node](return-to-last.md)
----/
