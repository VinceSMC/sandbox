# value

**Source type**
<br>`value`

**Description**
<br>The value source type returns a fixed value.

## Syntax
```yaml
- id: SOURCE_ID
  type: value
  value: VALUE
```

### value
```yaml
value: VALUE
```
> *Supports:*
> - [`PlaceholderAPI`](https://wiki.placeholderapi.com/) — Allows metrics to retrieve values from any installed PlaceholderAPI expansion.
> - `variables` — Allows metrics to retrieve values from SMC-Core variable placeholders.
> - `logics` — Allows metrics to retrieve values from SMC-Core logic placeholders.

Sets the fixed value returned by this source.

