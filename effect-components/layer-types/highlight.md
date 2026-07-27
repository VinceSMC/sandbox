# highlight

**Layer type**
<br>`highlight`

**Description**
<br>The highlight layer type moves a colored highlight across the source text while preserving the existing colors outside the highlighted area.

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
Sets the center color of the highlight.
<br>Supports legacy and hexadecimal color codes.

### width
```yaml
width: NUMBER
```
> *Supported values:* `1` or greater  
> *Default value:* `1`

Sets the number of fully highlighted visible characters.

### softness
```yaml
softness: NUMBER
```
> *Supported values:* `0` or greater  
> *Default value:* `0`

Sets the number of surrounding characters blended toward the highlight color.
<br>A value of `0` creates a hard edge around the highlight.

### include spaces
```yaml
include-spaces: BOOLEAN
```
> *Default value:* `false`

Sets whether spaces consume positions while the highlight moves across the text.

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

Sets whether the highlight moves continuously or advances one visible character at a time.

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

### Create a soft shine
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
