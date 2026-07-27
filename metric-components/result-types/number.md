# number

**Result type**
<br>`number`

**Description**
<br>The number result type returns a formatted numeric value based on an input value.

## Syntax
```yaml
- id: RESULT_ID
  type: number
  input: VALUE
  decimals: NUMBER
  prefix: TEXT
  suffix: TEXT
  format: TEXT
```

### input
```yaml
input: VALUE
```
> *Supports:*
> - `{src_SOURCE_ID}` — Allows results to reference values returned by configured sources.
> - `{calc_CALCULATION_ID}` — Allows results to reference values returned by calculations.

Sets the value that will be formatted and returned.

### decimals
```yaml
decimals: NUMBER
```
Sets the amount of decimal places the number will be formatted with.
<br>If omitted, the number is returned without decimal formatting.

### prefix
```yaml
prefix: TEXT
```
Sets the text prepended to the formatted number.
<br>This is commonly used for currency symbols, labels, or other leading text.

### suffix
```yaml
suffix: TEXT
```
Sets the text appended to the formatted number.
<br>This is commonly used for units or percentages.

### format
```yaml
format: TEXT
```
> *Example formats:*
> - `#,##0`
> - `#,##0.0`
> - `#,##0.00`
> - `0`
> - `0.##`

Sets the number format used to format the returned value.
<br>If omitted, the value is returned without additional number formatting.
