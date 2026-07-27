# string

**Result type**
<br>`string`

**Description**
<br>The string result type returns formatted text based on a calculation result.

## Syntax
```yaml
- id: RESULT_ID
  type: string
  format: TEXT
```

### format
```yaml
format: TEXT
```
> *Supports:*
> - `{src_SOURCE_ID}` — Allows results to reference values returned by configured sources.
> - `{calc_CALCULATION_ID}` — Allows results to reference values returned by calculations.
> - `{res_RESULT_ID}` — Allows results to reference other formatted results.

Sets the formatted text returned by the result.



