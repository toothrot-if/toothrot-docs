# The Story Format

Toothrot Engine comes with its own story format. It looks similar to
[markdown](https://de.wikipedia.org/wiki/Markdown) and has some special parts
to structure your story.

A basic story file looks like this:

```toothrot
# My Story

## default_section


### start

This is some text with **markdown** formatting.

And [this is a link to another node](#another_node). Click it.


### another_node

This is the text of another node.

(<)
```

A toothrot story file is divided into sections (starting with `##`) and nodes
(starting with `###`).

Nodes are pieces of text that are displayed one after the other. The first node is always
the `start` node.

/---- next
[Next Nodes](next-node.md)
----/
