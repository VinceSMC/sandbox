# playback

**Effect component**
<br>`playback`

**Description**
<br>The playback component controls how an effect timeline is played, rendered, and synchronized between viewers.

## Syntax
```yaml
playback:
  mode: TEXT
  frame-rate: NUMBER
  synchronization: TEXT
```

### mode
```yaml
mode: TEXT
```
> *Supported values:* `loop`, `once`, `ping-pong`, `static`  
> *Default value:* `loop`

Sets how the effect timeline is played.

| Mode | Description |
|---|---|
| `loop` | Repeats the timeline continuously. |
| `once` | Plays the timeline once and keeps its final rendered state. |
| `ping-pong` | Plays the timeline forward and then in reverse. |
| `static` | Renders one fixed state using only the root style and root layers. A timeline is not required. |

### frame rate
```yaml
frame-rate: NUMBER
```
> *Supported values:* `1` to `20`  
> *Default value:* `20`

Sets the maximum number of rendered states generated per second.
<br>The frame rate controls the smoothness of an effect, but does not change how long its timeline stages last.

| Frame rate | Time per rendered state |
|---|---|
| `5` | `200ms` |
| `10` | `100ms` |
| `20` | `50ms` |

> [!NOTE]
> The visible frame rate can be limited by how often the location displaying the placeholder is updated.

### synchronization
```yaml
synchronization: TEXT
```
> *Supported values:* `global`, `player`  
> *Default value:* `global`

Sets whether viewers share the same timeline position.

| Synchronization | Description |
|---|---|
| `global` | All viewers see the same rendered state of the effect. The timeline begins when the effect is loaded or reloaded. |
| `player` | Each player receives an independent timeline that begins when the effect is first requested for them. |

`global` synchronization is recommended for shared branding, scoreboards, player lists, and menu text.
<br>Use `player` synchronization when the effect should begin separately for each viewer.

## Examples

### Loop a globally synchronized effect at 20 frames per second
```yaml
playback:
  mode: loop
  frame-rate: 20
  synchronization: global
```

### Play an effect once for each player
```yaml
playback:
  mode: once
  frame-rate: 10
  synchronization: player
```
