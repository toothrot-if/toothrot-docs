
/---- previous
[Auto Next](auto-next.md)
----/

# Backgrounds

You can set a background for your story using either a node or section property called
`background`:

```toothrot
## section

(#) background: "url(images/my-section-image.png) center/cover"

### first

This is the first node.

(>) second

### second

(#) background: "url(images/my-node-image.png) center/cover"

This is the second node.

(>) first
```

When you would run the above example, the following backgrounds would be shown:

| Node name | Background             | Reason                                    |
|:----------|:-----------------------|:------------------------------------------|
| `first`   | `my-section-image.png` | Node inherits background from section     |
| `second`  | `my-node-image.png`    | Node property overwrites section property |

The `background` property expects as its value a string containing a valid
[CSS background](https://developer.mozilla.org/en-US/docs/Web/CSS/background) value.
This means you have full control over the background: it can be a single color, a
gradient or, as shown in the example above, an image.

When a background change occurs, a cross-fade effect is used to switch between the backgrounds.

/---- info
If you set a background in a node and its section doesn't define a background, the
background will be shown in the following nodes as well, as long as these do not define
backgrounds of their own. In that sense, you could say that backgrounds are *sticky*.
----/

/---- next
[Audio](audio.md)
----/
