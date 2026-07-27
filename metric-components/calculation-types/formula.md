# formula

**Calculation type**
<br>`formula`

**Description**
<br>The formula calculation type evaluates a mathematical expression and returns the resulting value.
<br>Calculations are powered by [EvalEx](https://ezylang.github.io/EvalEx/).

## Syntax
```yaml
- id: CALCULATION_ID
  type: formula
  formula: TEXT
```

### formula
```yaml
formula: TEXT
```
> *Supports:*
> - `{src_SOURCE_ID}` — Allows calculations to reference values returned by configured sources.
> - `{calc_CALCULATION_ID}` — Allows calculations to reference values returned by other calculations.
> - [`PlaceholderAPI`](https://wiki.placeholderapi.com/) — Allows calculations to use values returned by any installed PlaceholderAPI expansion.
> - `variables` — Allows calculations to use values returned by SMC-Core variable placeholders.

Sets the mathematical expression that will be evaluated to produce the calculation result.
<br>Values from sources or other calculations can be referenced using placeholders.

## Examples

### Adds two numbers
```yaml
formula: "5 + 10"
```

### Divides a number and multiplies the result
```yaml
formula: "(20 / 4) * 3"
```


