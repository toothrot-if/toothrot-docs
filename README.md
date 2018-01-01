# Toothrot Engine Documentation

[Come chat with us on Discord!](https://discord.gg/DJ8SAr5)

This is the documentation for both Toothrot Engine and the Toothrot IDE application.

## Building the docs

The documentation is written in Markdown files. These files are converted into a functioning
website using [allthedocs](https://github.com/allthedocs/allthedocs).

#### Node JavaScript API

Much of a node's behavior can be controlled using the node JavaScript API.

## Variables

Variables can be inserted into a node's text by using this notation:

    The variable `foo` contains: `$foo`

Variables can be set in script blocks like this:

    ```js @entry
    $.foo = "bar";
    ```


## JavaScript

A node can contain blocks of JavaScript. The JavaScript inside a node gets executed right
before the node is shown. JavaScript can be written in the node's text between
`(!` and `!)`. The last value of the JavaScript snippet will be inserted into
the text.

### The variable container: $

Inside the JavaScript snippets, there are two main ways in which you can interact
with the engine. The first is `$`. It's an object containing all of the game's
current variables.

For example, the following snippets produce the same output:

    Foo is: `$foo`

    Foo is: (! $.foo !)

#### Special variable: $._choice

The `$._choice` variable contains the value of the last clicked option.

### The function container: _

The next way to interact with the engine from a JavaScript snippet is the
*environment* `_`. It contains a bunch of functions to alter the game's state
in some way or help you write your scripts.

#### _.skipTo(nodeId)

The `skipTo(nodeId)` function skips the current node immediately before showing
any text or effects or playing any audio. The following will skip the node where
it is written and continue with the node `foo` instead:

    _.skipTo("foo")

#### _.link(label, target)

Creates a direct link to another node:

    You can (! _.link("go to the other room", "other_room") !).

#### _.addOption(label, target[, value])

Adds an option to the node's option menu. The first parameter is the text that's displayed on
the button. The second parameter, `target`, is the target node that will be executed if the user
clicks on the option. The third parameter, `value`, is optional and can be used to specify the
options string value (see section about special variable `$._choice`).

#### _.node()

Returns the current node. 

#### _.oneOf(a1, a2, ..., aN)

Returns one of its arguments randomly:

    ```js @entry
    $.hairColor = _.oneOf("blond", "brown", "black", "red", "white", "gray");
    ```

## Node and section properties

Both nodes and sections can be augmented with properties. To add a property
to a node or section, add the following on an empty line somewhere in the
node's or section's text:

    (#) theKey: "theValue"

In this example, a property `theKey` is defined with a string value of `"theValue"`.
The value of a property can be any JSON value like `string`, `number`, `boolean`,
`array`, `object` or `null`.

If a property is defined for a section, it will affect all the nodes contained
within that section. If a property is defined for a node, it will only belong
to the node itself.

If both a node and its section define the same property, then the node's property
is used.

### Property: timeout [number]

You can specify a timeout for a node:

    (#) timeout: 2000

This means that after 2 seconds (2000 milliseconds), a choice will be made for the user:
If the node contains options but no default option is specified, the first option will
be chosen. If a default option has been specified for the node, this option will be chosen.
Finally, if the node doesn't have options but has a next node or a node to return to, the game
will go to this node instead.

### Property: defaultOption [number]

If this property is specified and the node has a timeout, the option specified here will be
chosen after the timeout instead of the first option. This property's value is the zero-based
index of the option.

    (#) defaultOption: 2

This will choose the third option.

    (#) defaultOption: 0

This will choose the first option.


## Audio

You can play audio files with Toothrot. There are three different kinds of audio,
and each has its own "channel" (meaning its own volume):

 * sound: Sounds that are played once when something happens, e.g. glass breaking, door shutting.
 * music: Looping background music.
 * ambience: Looping ambience (noise) tracks, e.g. ocean waves or restaurant chatter.

You can use node properties to play audio. To play a sound, at a `sound` property to your node:

    (#) sound: "doorShutting.ogg"

To start a background music track (or change the one currently playing), use:

    (#) music: "mainTheme.ogg"

And for playing or changing the ambience track:

    (#) ambience: "restaurant.ogg"

You can stop whatever is playing on a channel by setting it to `false`:

    (#) music: false

And if you want to stop all audio at once, use this:

    (#) audio: false

The paths to your audio files is relative to the `index.html` file of your built project.
So if you write this:

    (#) sound: "beep.ogg"

It plays the file `my_project/files/beep.ogg`. And if you write:

    (#) sound: "sounds/beep.ogg"

Then it plays `my_project/files/sounds/beep.ogg`.

If you build your project for the use in browsers, you might need to supply different formats of
the same audio file. You can specify alternatives like this:

    (#) sound: ["sounds/beep", "ogg", "mp3"]

The browser will choose the format it supports automatically, so it will either play
`my_project/files/sounds/beep.ogg` or `my_project/files/sounds/beep.mp3`.


## Customizing screens and the game UI

You will need basic HTML skills to customize your screens. You can customize your game's screens
by simply changing a screen's template. The screen templates can be found in the
`resources/screens/` folder. Likewise, you can customize the UI by editing the templates found
in `resources/templates/`.

The following default templates are available:

 * `resources/templates/confirm.html` for the confirm dialog
 * `resources/templates/notification.html` for notifications
 * `resources/templates/ui.html` for the in-game UI

### Linking from one screen to another

You can add a clickable element that will open another screen when clicked by specifying
these two attributes:

    data-type="menu-item"
    data-target="my_screen"

If the user clicks on a link or button that has these attributes, the screen defined in the
file `resources/screens/my_screen.html` will be shown.

### Making links or buttons work with keyboard navigation

To make an element in a screen navigatable, you must add the following attribute:

    data-focus-mode="screen"

To make the element also reachable by using the `tab` button (important for screen readers!),
you can add these attributes:

    tabindex="0"
    role="button"

### Showing or hiding elements depending on the platform's features

Some of the engine's features are only available if you export your game as a desktop application,
like switching to fullscreen mode or exiting the application. To ensure that screen or UI parts
referencing such features are only shown when the feature is available, you can use the
`data-feature` attribute:

    data-feature="exit"

Currently these two platform-dependent features are available: "exit" and "fullscreen".

Here's how to make a screen element quit the game when clicked:

    data-type="menu-item"
    data-target="exit"
    data-feature="exit"

And for toggling between fullscreen and window mode, you can use:

    data-type="button"
    data-action="toggleFullscreen"
    data-feature="fullscreen"


### The keyboard focus mode

There are different focus modes for the keyboard navigation. These are:

 * "screen" for elements in screens
 * "node" when a node's text is displayed
 * "action" when an object link's actions are displayed
 * "messagebox" for elements when a messagebox (like a confirm dialog) is displayed

For each clickable UI element in your screens or templates, you need to specify the keyboard focus
mode for keyboard navigation to work correctly:

    data-focus-mode="screen"

