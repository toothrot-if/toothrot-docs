
/---- previous
[The Story Format](story-format.md)
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

In this example, we have a named node `boring_story` and a bunch of connected nodes
defined by `***`.

/---- next
[Return to the Last Node](return-to-last.md)
----/
