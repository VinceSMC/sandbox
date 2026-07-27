# highlight

**Layer type**
<br>`highlight`

**Description**
<br>The highlight layer type moves a color sweep across the source text while preserving the colors outside the highlighted area.

## Syntax
```yaml
- type: highlight
  color: TEXT
  width: NUMBER
  softness: NUMBER
  include-spaces: BOOLEAN
  motion:
    mode: TEXT
    direction: TEXT
    cycles: NUMBER
```

### color
```yaml
color: TEXT
```
Sets the color used at the center of the highlight.
<br>The same MiniMessage and Minecraft color formats supported by SMC-Core can be used.

### width
```yaml
width: NUMBER
```
> *Supported values:* `1` or greater  
> *Default value:* `1`

Sets the number of adjacent visible characters that receive the complete highlight color.
<br>For example, a width of `2` allows two complete characters to be highlighted at the same time.

### softness
```yaml
softness: NUMBER
```
> *Supported values:* `0` or greater  
> *Default value:* `0`

Sets the number of additional character positions on each side of the highlight that fade between their existing color and the configured highlight color.
<br>Each character still uses one solid color. This option creates a color falloff between neighboring characters and does not blur or partially color a character.
<br>A value of `0` creates a hard edge around the highlighted characters.

### include spaces
```yaml
include-spaces: BOOLEAN
```
> *Default value:* `false`

Sets whether spaces consume positions while the highlight moves across the text.
<br>Spaces cannot visibly display the highlight color. When enabled, the highlight still spends part of its movement crossing them. When disabled, spaces are skipped.

### motion
```yaml
motion:
  mode: TEXT
  direction: TEXT
  cycles: NUMBER
```
Sets how the highlight moves during the active timeline stage.

#### mode
```yaml
mode: TEXT
```
> *Supported values:* `smooth`, `stepped`  
> *Default value:* `smooth`

Sets how the highlight advances between visible character positions.

| Mode | Description |
|---|---|
| `smooth` | Moves a virtual highlight position continuously across the text. Complete characters gradually change color based on their distance from that position. This is most visible when `softness` is greater than `0`. |
| `stepped` | Holds the highlight on one visible character position before advancing to the next. This produces clearly separated character states. |

> [!NOTE]
> Both modes still render complete characters only. The visible smoothness also depends on the configured frame rate and how frequently the location displaying the placeholder is updated.

#### direction
```yaml
direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`  
> *Default value:* `left-to-right`

Sets the direction in which the highlight moves.

#### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of complete passes performed during the active duration.

## Examples

### Move a white highlight across each character
```yaml
timeline:
 - duration: 3s
   layers:
    - type: highlight
      color: "&f"
      width: 1
      softness: 0
      include-spaces: false
      motion:
        mode: stepped
        direction: left-to-right
        cycles: 1
```

### Create a character-based shine
```yaml
timeline:
 - duration: 1.2s
   layers:
    - type: highlight
      color: "&f"
      width: 2
      softness: 2
      include-spaces: false
      motion:
        mode: smooth
        direction: left-to-right
        cycles: 1
```
