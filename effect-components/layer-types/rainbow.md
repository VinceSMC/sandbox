# rainbow

**Layer type**
<br>`rainbow`

**Description**
<br>The rainbow layer type applies a hue spectrum to the source text and can move it during the active timeline stage.

## Syntax
```yaml
- type: rainbow
  saturation: NUMBER
  brightness: NUMBER
  wavelength: NUMBER
  offset: NUMBER
  motion:
    direction: TEXT
    cycles: NUMBER
```

### saturation
```yaml
saturation: NUMBER
```
> *Supported values:* `0` to `100`  
> *Default value:* `100`

Sets the saturation of the generated rainbow colors.

### brightness
```yaml
brightness: NUMBER
```
> *Supported values:* `0` to `100`  
> *Default value:* `100`

Sets the brightness of the generated rainbow colors.

### wavelength
```yaml
wavelength: NUMBER
```
Sets the number of visible character positions occupied by one complete hue rotation.
<br>The value must be greater than zero.

### offset
```yaml
offset: NUMBER
```
> *Supported values:* `0` to `360`  
> *Default value:* `0`

Sets the starting hue offset of the rainbow in degrees.

### motion
```yaml
motion:
  direction: TEXT
  cycles: NUMBER
```
Sets how the rainbow moves during the active timeline stage.
<br>If omitted, the rainbow remains static.

#### direction
```yaml
direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`  
> *Default value:* `left-to-right`

Sets the direction in which the hue spectrum moves.

#### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of complete hue rotations performed during the active duration.

## Examples

### Apply a static rainbow
```yaml
layers:
 - type: rainbow
   saturation: 100
   brightness: 100
   wavelength: 12
   offset: 0
```

### Move a rainbow across the text
```yaml
timeline:
 - duration: 4s
   layers:
    - type: rainbow
      saturation: 100
      brightness: 100
      wavelength: 12
      offset: 0
      motion:
        direction: left-to-right
        cycles: 1
```
