# pulse

**Layer type**
<br>`pulse`

**Description**
<br>The pulse layer type interpolates the current colors toward a configured peak color and then returns them to their original colors.

## Syntax
```yaml
- type: pulse
  peak-color: TEXT
  cycles: NUMBER
  easing: TEXT
```

### peak color
```yaml
peak-color: TEXT
```
Sets the color reached at the center of the pulse.
<br>Supports legacy and hexadecimal color codes. The starting and ending colors are taken from the style and layers already applied before the pulse.

### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of complete base-to-peak-to-base pulses performed during the active duration.

### easing
```yaml
easing: TEXT
```
> *Supported values:* `linear`, `sine-in-out`, `ease-in`, `ease-out`  
> *Default value:* `sine-in-out`

Sets how the color transition accelerates and decelerates throughout the pulse.

| Easing | Description |
|---|---|
| `linear` | Changes the color at a constant rate. |
| `sine-in-out` | Starts and ends gradually with a smooth transition. |
| `ease-in` | Starts gradually and accelerates toward the peak. |
| `ease-out` | Starts quickly and slows toward the end. |

## Examples

### Pulse warning text toward yellow
```yaml
timeline:
 - duration: 700ms
   layers:
    - type: pulse
      peak-color: "&#FFE75A"
      cycles: 1
      easing: sine-in-out
```

### Play two quick linear pulses
```yaml
timeline:
 - duration: 600ms
   layers:
    - type: pulse
      peak-color: "&f"
      cycles: 2
      easing: linear
```
