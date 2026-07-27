# suffix-cycle

**Layer type**
<br>`suffix-cycle`

**Description**
<br>The suffix-cycle layer type cycles through configured suffix values without repeating the source text.

## Syntax
```yaml
- type: suffix-cycle
  values:
   - TEXT
  reserve-width: NUMBER
  cycles: NUMBER
```

### values
```yaml
values:
 - TEXT
```
Sets the ordered suffix values displayed during the active timeline stage.
<br>At least one value must be configured. Each value receives an equal portion of the stage duration.

### reserve width
```yaml
reserve-width: NUMBER
```
> *Supported values:* `0` or greater  
> *Default value:* `0`

Sets the amount of visible character space reserved for the suffix.
<br>Shorter values are padded so the source text does not visually move while the suffix changes.

### cycles
```yaml
cycles: NUMBER
```
> *Supported values:* Greater than `0`  
> *Default value:* `1`

Sets the number of times the complete suffix sequence is played during the active duration.

## Examples

### Cycle through loading dots
```yaml
timeline:
 - duration: 1.6s
   layers:
    - type: suffix-cycle
      values:
       - ""
       - "."
       - ".."
       - "..."
      reserve-width: 3
      cycles: 1
```

### Alternate between two status indicators
```yaml
timeline:
 - duration: 2s
   layers:
    - type: suffix-cycle
      values:
       - " &7[ ]"
       - " &a[✓]"
      reserve-width: 4
      cycles: 2
```
