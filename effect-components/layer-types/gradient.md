# gradient

**Layer type**
<br>`gradient`

**Description**
<br>The gradient layer type applies a static or moving color gradient to the source text.

## Syntax
```yaml
- type: gradient
  colors:
   - TEXT
   - TEXT
  pattern: TEXT
  wavelength: NUMBER
  offset: NUMBER
  motion:
    direction: TEXT
    cycles: NUMBER
```

### colors
```yaml
colors:
 - TEXT
 - TEXT
```
Sets the colors used to generate the gradient.
<br>At least two valid colors must be configured. The same MiniMessage and Minecraft color formats supported by SMC-Core can be used.

### pattern
```yaml
pattern: TEXT
```
> *Supported values:* `linear`, `repeat`, `wave`  
> *Default value:* `linear`

Sets how the configured colors are distributed across the source text.

| Pattern | Description |
|---|---|
| `linear` | Stretches the configured colors once across the complete text. |
| `repeat` | Repeats the configured color sequence across the text. |
| `wave` | Moves through the configured colors forward and backward to create a mirrored pattern. |

### wavelength
```yaml
wavelength: NUMBER
```
Sets the number of visible character positions occupied by one complete `repeat` or `wave` pattern.
<br>The value must be greater than zero and is required when using either of these patterns. This option is not used by the `linear` pattern.

### offset
```yaml
offset: NUMBER
```
> *Default value:* `0`

Sets the starting position within the configured gradient pattern.

### motion
```yaml
motion:
  direction: TEXT
  cycles: NUMBER
```
Sets how the gradient moves during the active timeline stage.
<br>If omitted, the gradient remains static.

#### direction
```yaml
direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`  
> *Default value:* `left-to-right`

Sets the direction in which the gradient moves.

#### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of complete gradient movements performed during the active duration.

## Examples

### Apply a static gold gradient
```yaml
layers:
 - type: gradient
   colors:
    - "&#FF8A00"
    - "&#FFE66D"
   pattern: linear
```

### Move a repeating wave across the text
```yaml
timeline:
 - duration: 2.8s
   layers:
    - type: gradient
      colors:
       - "&#FFA620"
       - "&#FFEB3C"
      pattern: wave
      wavelength: 14
      offset: 6
      motion:
        direction: left-to-right
        cycles: 1
```
