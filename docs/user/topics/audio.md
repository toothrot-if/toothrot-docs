
/---- previous
[Backgrounds](backgrounds.md)
----/

# Audio

You can use audio in Toothrot to make the experience more immersive for the player.
There are three types of audio in Toothrot, and each one has its own volume level.

* The `ambience` channel can be used for ambience/environment sounds
* The `music` channel can be used to play music tracks
* The `sound` channel can be used to play sounds, for example creaking doors

Both the `ambience` and the `music` channel play their tracks in a loop. The `sound`
channel, on the other hand, plays a sound effect only once.

## Audio properties

Audio can be started and stopped using either node or section properties. The value
of such a property must either be a **string** containing the path to the audio file
(relative to the `index.html` file of the game) or an **array** of strings.

If an **array** is used, then the first string in the array is the file path without any file
extension (relative to `index.html`), and all of the other items in the array are available
file extensions for the audio track.

For example, in the following code, either `audio/file.ogg` or `audio/file.mp3` is played,
depending on what the preferred format is for the browser that the player uses:

```toothrot
### play_audio

(#) ambience: ["audio/file", "ogg", "mp3"]

You should hear an ambience track right now!
```

For most use cases, it's a good idea to have at least an OGG and an MP3 version of your
audio tracks.

| Audio channel     | Property name     | Possible values        | Loops? |
|:------------------|:------------------|------------------------|:-------|
| Ambience          | `ambience`        | string, array, `false` | Yes    |
| Music             | `music`           | string, array, `false` | Yes    |
| Sound             | `sound`           | string, array, `false` | No     |
| ALL               | `audio`           | `false`                | N/A    |

/---- info
Similar to the [background property](backgrounds.md), the audio properties behave *sticky*
as well. This means that once you start an ambience or music track, it will be played
until either a new track is played on the same channel or until the channel is explicitly stopped.
----/

## Stopping the audio

Audio channels can be stopped by setting their respective property to `false`:

```toothrot
### stop_tracks

(#) music: false
(#) ambience: false
(#) sound: false

Ahhh... silence! Finally!

(<)
```

To stop *all* channels at once, the `audio` property can be set to `false`:

```toothrot
### stop_tracks

(#) audio: false

Ahhh... silence! Finally!

(<)
```

/---- next
[Default Settings](default-settings.md)
----/
