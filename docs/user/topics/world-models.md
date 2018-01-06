
# World Model(s)

The world model of Toothrot games is both simple and very flexible. But if you're not
familiar with parser-based interactive fiction engines like Inform, you might be wondering
what a world model is and why you would ever need one.

In a "pure" choice-based game (similar to some of the early Choose Your Own Adventure books) or
a "pure" hypertext fiction, each text node always contains the same text, no matter how the
player might have reached it. The experience of the player is unique for each set of choices
she makes, but the game (or the world of the story) itself never actually changes.

This is fine for a broad range of interactive fiction, but if you want to write a game
where the world of the story actually reacts to the actions of the player, you need some kind
of model of how the world of the game behaves to the player's input.

The world model in toothrot is not nearly as sophisticated as the world model of traditional
parser-based interactive fiction engines like Inform. Instead, it gives you a few simple
building blocks that you can use to define your own world model.

## Giving meaning to nodes

Text nodes (passages) in Toothrot are more than just pieces of text.

Nodes can be labeled using *[tags](node-tags.md)*.
With tags, you can define a node to be a room or an item,
or you can label it something else completely. The engine doesn't actually know what
a "room" or an "item" is, but it allows you to treat one kind of node differently from
another kind.

Each node can have an unlimited number of tags. Tags can be put into a
[hierarchy](tag-hierarchy.md). This way you can define, for example, that a container is
an item and that both a person and an animal are beings.

A node's internal state can be changed using so-called *[flags](node-flags.md)*.
A flag doesn't have a value itself, it just defines that a fact is true or not true for
a node. Options (you can think about them as actions the player can do) can be shown
or hidden depending on these flags. For example, a node that acts as a container can have
or not have a `closed` flag set and then display either a `Close` or `Open` option
depending on whether or not the flag is set.

/---- next
[Node Tags](node-tags.md)
----/
