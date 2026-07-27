# marquee

**Layer type**
<br>`marquee`

**Description**
<br>The marquee layer type scrolls the source text through a fixed-width viewport.

## Syntax
```yaml
- type: marquee
  width: NUMBER
  gap: NUMBER
  direction: TEXT
  cycles: NUMBER
```

### width
```yaml
width: NUMBER
```
Sets the number of visible character positions displayed by the viewport.
<br>The value must be greater than zero.

### gap
```yaml
gap: NUMBER
```
Sets the number of blank character positions inserted between the end and beginning of the source text when it wraps.
<br>The value cannot be negative.

### direction
```yaml
direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`  
> *Default value:* `right-to-left`

Sets the direction in which the source text scrolls.

### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of complete scrolls performed during the active duration.
<br>The stage duration and configured cycle count determine the scrolling speed.

## Examples

### Scroll text from right to left
```yaml
timeline:
 - duration: 5s
   layers:
    - type: marquee
      width: 16
      gap: 4
      direction: right-to-left
      cycles: 1
```

### Scroll text twice from left to right
```yaml
timeline:
 - duration: 8s
   layers:
    - type: marquee
      width: 20
      gap: 6
      direction: left-to-right
      cycles: 2
```
