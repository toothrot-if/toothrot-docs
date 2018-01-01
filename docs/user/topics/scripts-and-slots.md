
# Scripts and Slots

Simple choices or links don't cut it for your game? Then you can use JavaScript to further
customize the behavior of your game.

## Defining and using scripts

Each node can contain named blocks of JavaScript:

````toothrot
### my_node

```js @my_script
"And here's some more text."
```

Here's some text. `@my_script`
````

The above defines a script named `my_script` for the node `my_node`. This script will be executed
only if it is referenced in the node's text. Scripts can be referenced by using the slot syntax.
The `` `@my_script` `` part written in the text of the node tells the engine
to execute the script `my_script` and replace the `` `@my_script` `` with
whatever the result of the script was.

If you would run the above example, the text that would be displayed is:

    Here's some text. And here's some more text.

/---- warning
The character used here is the **backtick**, not a single quotation mark!
----/

## Return value of scripts

The last value computed by a script is automatically treated as the resulting value of the script. 
This value is what is inserted into a slot when its corresponding script is executed.

/---- next
[Special Scripts](special-scripts.md)
----/
