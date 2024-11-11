---
description: Audio alerts for raised hands, chat messages and if somebody joins the room
---

# \&notify

Sender-Side Option / Director Option! ([`&push`](push.md), [`&director`](../viewers-settings/director.md))

## Aliases

* `&beep`
* `&tone`

## Details

Add this to a guest's/director's URL and you get audio alerts for raised-hands, chat messages and if somebody joins the room.

{% hint style="warning" %}
If you can't hear a sound, click any button in the room. Then the sounds will be activated.
{% endhint %}

## Advanced configurations

Enable audio notifications for specified events.

* Values: Comma-separated list of: `join`, `leave`, `test`
* Example: `?beep=join,leave` enables just the join and leave sounds
* Example: `?notify=join` enables only join sounds
* Note: Using the parameter without values (e.g., `?beep`) will enable all sound types.

### Custom Sound Settings

#### `customjoin=<url>`

Custom sound for join notifications.

* Value: URL to audio file
* Example: `?customjoin=https://example.com/join.mp3`
* Default if not specified: `./media/join.mp3`

#### `customleave=<url>`

Custom sound for leave notifications.

* Value: URL to audio file
* Example: `?customleave=https://example.com/leave.mp3`
* Default if not specified: `./media/leave.mp3`

#### `custombeep=<url>`

Sets a custom sound for the test tone.

* Value: URL to audio file
* Example: `?custombeep=https://example.com/beep.mp3`
* Supported formats: mp3, wav, ogg, aac, m4a, opus, flac, webm

#### `r2d2`

Replaces the test tone with a robot sound.

* Usage: `?r2d2`
* Effect: Sets test tone to `./media/robot.mp3`

### Volume Control

#### `beepvolume=<number>`

Sets volume for all notification sounds.

* Value: Number between 0-100 for normal volume, >100 for amplified volume
* Example: `?beepvolume=50` for 50% volume
* Example: `?beepvolume=500` for 500% volume using Web Audio API amplification
  * volume values are linear, yet the human ear hears loudness logarithmically, so 500 isn't that much louder.
* Default: 100 (100% volume)

#### Important Volume Limitations

When using `beepvolume` values greater than 100:

* Audio files must be hosted on a server that allows CORS access
* External audio files (like those from myinstants.com) may fail due to CORS restrictions
* If CORS fails, the audio will fallback to normal volume (100% max)
* For best results with amplified volume, host audio files on your own domain
* Volume boost requires Web Audio API support in the browser

### Examples

Basic notification setup:

```url
?beep=join,leave&beepvolume=75
```

Custom sounds with normal volume:

```url
urlCopy?beep=join,leave&customjoin=custom.mp3&customleave=custom2.mp3&beepvolume=100
```

Custom test tone:

```url
?custombeep=https://example.com/tone.mp3
```

R2D2 sounds with custom volume:

```url
?r2d2&beepvolume=80&beep=join,leave
```

### Best Practices

1. When using custom sounds:
   * Host audio files on your own domain to avoid CORS issues
   * Use short, small audio files for better performance
   * Test with both normal and amplified volume settings
2. When using amplified volume:
   * Test with your specific audio files first
   * Have a fallback plan if CORS restrictions prevent volume boost
   * Consider users with different audio setups

### Sound clip resources and hosting

There are sound effects available at [https://www.myinstants.com/](https://www.myinstants.com/), however it's generally not considered polite to directly link to their MP3 audio files. Instead, it is better to download any and host them yourself, perhaps on GitHub or a proper webserver.

As noted, if using `&beepvolume`, and you set it higher than 100, then direct linking to audio files will fail with some sites, such as with myinstants.com.&#x20;

## Related

{% content-ref url="r2d2.md" %}
[r2d2.md](r2d2.md)
{% endcontent-ref %}

{% content-ref url="and-hands.md" %}
[and-hands.md](and-hands.md)
{% endcontent-ref %}
