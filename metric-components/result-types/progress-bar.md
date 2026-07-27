# progress-bar

**Result type**
<br>`progress-bar`

**Description**
<br>The progress-bar result type returns a visual progress bar based on a current value relative to a maximum value.

## Syntax
```yaml
- id: RESULT_ID
  type: progress-bar
  current: TEXT
  maximum: TEXT
  symbol: TEXT
  length: NUMBER
  color-filled: TEXT
  color-partial: TEXT
  color-empty: TEXT
```

### current
```yaml
current: TEXT
```
> *Supports:*
> - `{src_SOURCE_ID}` — Allows results to reference values returned by configured sources.
> - `{calc_CALCULATION_ID}` — Allows results to reference values returned by calculations.

Sets the current progress value used to determine how much of the bar should be filled.

### maximum
```yaml
maximum: TEXT
```
> *Supports:*
> - `{src_SOURCE_ID}` — Allows results to reference values returned by configured sources.
> - `{calc_CALCULATION_ID}` — Allows results to reference values returned by calculations.

Sets the maximum value used to determine the total progress of the bar.

### symbol
```yaml
symbol: TEXT
```
Sets the character used to render each segment of the progress bar.

### length
```yaml
length: NUMBER
```
Sets the total amount of symbols used to render the progress bar.

### color-filled
```yaml
color-filled: TEXT
```
Sets the color used for the filled portion of the bar.

### color-partial
```yaml
color-partial: TEXT
```
Sets the color used for the symbol representing the current progress position on the bar.

### color-empty
```yaml
color-empty: TEXT
```
Sets the color used for the empty portion of the bar.

