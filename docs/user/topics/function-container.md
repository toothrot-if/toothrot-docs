
# The Function Container: _

The next way to interact with the engine from a JavaScript snippet is the
*environment* `_`. It contains a bunch of functions to alter the game's state
in some way or help you write your scripts.


## _.skipTo(nodeId)

The `skipTo(nodeId)` function skips the current node immediately before showing
any text or effects or playing any audio. The following will skip the node where
it is written and continue with the node `foo` instead:

    _.skipTo("foo")


## _.link(label, target)

Creates a direct link to another node:

````toothrot
### my_node

```js @link
_.link("go to the other room", "other_room")
```

You can `@link`.

### other_room

Another room.

(<)
````

## _.addOption(label, target[, value])

Adds an option to the node's option menu. The first parameter is the text that's displayed on
the button. The second parameter, `target`, is the target node that will be executed if the user
clicks on the option. The third parameter, `value`, is optional and can be used to specify the
options string value (see section about special variable `$._choice`).


## _.node([nodeName])

Returns the current node when used without an argument:

    _.node()

Returns a node given its name:

    _.node("other_room")

Details about the object returned here can be found in [the Node API documentation](node-api.md).


## _.self()

Returns the node that contains the currently executed script. This can sometimes be a different
node than the one returned by `_.node()`.

````toothrot
### the_room

(#) contains: ["item"]

```js @current
_.node().id
```

```js @self
_.self().id
```

In the_room: `@self`, `@current`


### item

```js @brief
"In item@brief: " + _.self().id + ", " + _.node().id
```
````

This will result in the following output when visiting node `the_room`:

    In the_room: the_room, the_room
    
    In item@brief: item, the_room


## _.oneOf(a1, a2, ..., aN)

Returns one of its arguments randomly:

    ```js @entry
    $.hairColor = _.oneOf("blond", "brown", "black", "red", "white", "gray");
    ```

## _.event(textOrObject)


## _.last([tag])

Returns the name of the last node, or if tag is given, the last node with the tag.


## _.save(savegameId[, then])

Saves the current state of the game under savegameId.


## _.load(savegameId[, then])

Loads a savegame.


## _.notify(text[, type[, duration]])

Displays a notification.
