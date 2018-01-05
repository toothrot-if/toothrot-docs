# The Story Format

Toothrot Engine comes with its own story format, which is what you use to write the actual
content of your story. The format looks similar to
[markdown](https://en.wikipedia.org/wiki/Markdown) and has some special parts
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

A Toothrot story file is divided into sections (starting with `##`) and nodes
(starting with `###`).

<table>
    <thead>
        <tr>
            <th>Code from example</th>
            <th>What is it?</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <pre><code class="lang-toothrot"># My Story</code></pre>
            </td>
            <td>
                <p>
                    The story title. It can be freely chosen. The part directly after the
                    story title is the <i>head</i> of the story. It can contain some code blocks
                    for overall settings of the story. Any text written in the <i>head</i>
                    will not be displayed.
                </p>
                <p>
                    The story title will be displayed as the title of the tab or browser window.
                </p>
            </tr>
        </tr>
        <tr>
            <td>
                <pre><code class="lang-toothrot">## default_section</code></pre>
            </td>
            <td>
                A section called <code>default_section</code>.
                The name of a section can contain letters, numbers and underscores, and it
                will not be displayed to the player.
            </tr>
        </tr>
        <tr>
            <td>
                <pre><code class="lang-toothrot">### start</code></pre>
            </td>
            <td>
                <p>A text node called <code>start</code>. The name of a node, similarly to
                a section name, can contain letters, numbers and underscores, and it will not
                be displayed to the player.</p>
                <p>Text nodes (also called passages) contain the text that is actually
                displayed to the player.</p>
            </tr>
        </tr>
    </tbody>
</table>

/---- info
**Please note:** The name of a node must be unique amongst all nodes, and the name of
a section must be unqiue amongst all sections.
----/

## Story files

A Toothrot project must have at least a `story.trot.md` file. This is the main story file, and
it cannot be deleted or renamed. Apart from the main story file, any number of extension files
(file names ending in `trot.ext.md`) can be used.

Each extension file should contain at least one section, and each section can only be defined
once. This means that if you want to write a section in a separate file, all the nodes
belonging to this section should be in this file, not in any other file.

## Nodes

Nodes are pieces of text that are displayed one after the other. The first node is always
the `start` node.

Nodes can contain both text and various special kinds of formatting to define the behavior
of the node. This is explained in more detail in the following pages of this documentation.

Node text itself can be formatted using both [markdown](https://en.wikipedia.org/wiki/Markdown)
and [HTML](https://en.wikipedia.org/wiki/HTML).

## Sections

Sections group text nodes together and allow defining some behavior that applies to
all the nodes contained in the section. For example, you can set a background for a section
and then all its nodes will be displayed with this background (except
for those nodes that define a separate background themselves).

/---- next
[Linking to Other Nodes](links.md)
----/
