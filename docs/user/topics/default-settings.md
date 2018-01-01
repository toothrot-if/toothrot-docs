
/---- previous
[Auto Next](auto-next.md)
----/

# Default Settings

The default behavior of your story can be modified with a special JSON code block in the
head section of the main story file, `story.trot.md`:

````toothrot
# My Story

```json @settings
{
    "textSpeed": 100,
    "soundVolume": 80,
    "musicVolume": 50,
    "ambienceVolume": 100,
    "skipMainMenu": true,
    "continueOnStart": true
}
```
````

The `@settings` block must be in the head section of your story, that is between the story
title and the first section. The block must contain a JSON object.

## Available Settings

|Property Name      | Values                       | Description                                   |
|:------------------|:-----------------------------|:----------------------------------------------|
| textSpeed         | `1` to `100`                 | Speed of reveal effect; `100`: instantly      |
| soundVolume       | `0` to `100`                 | Volume of sound effects in percent            |
| musicVolume       | `0` to `100`                 | Volume of music in percent                    |
| ambienceVolume    | `0` to `100`                 | Volume of ambience track in percent           |
| skipMainMenu*     | `true` or `false`            | If `true` story starts directly (no menu)     |
| continueOnStart*  | `true` or `false`            | If `true` story starts directly at last node  |

The properties marked with an `*` cannot be set using the default settings screen included in
Toothrot.

### Skipping the main menu

The `skipMainMenu` setting allows you to skip the main menu. This means that when your players
start your game, they don't see a menu and the story starts directly at the `start` node.
This setting only affects the main menu though -- the pause menu will still be shown when the
player clicks the menu button during play or when he presses the `ESC` key.

### Continue at last visited node

When the `continueOnStart` setting is set to `true` and the player had previously started the game,
then the main menu will not be displayed when the player returns to your game; instead, the story
will continue where the player last left off.
