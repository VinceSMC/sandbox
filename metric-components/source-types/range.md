# range

**Source type**
<br>`range`

**Description**
<br>The range source type returns a value based on a matching numeric range.
<br>The configured [`input`](#input) value is evaluated against the defined ranges to determine the returned value.

## Syntax
```yaml
- id: SOURCE_ID
  type: range
  input: VALUE
  default: VALUE
  ranges: LIST
```

### input
```yaml
input: VALUE
```
> *Supports:*
> - [`PlaceholderAPI`](https://wiki.placeholderapi.com/) — Allows metrics to retrieve values from any installed PlaceholderAPI expansion.
> - `variables` — Allows metrics to retrieve values from SMC-Core variable placeholders.
> - `logics` — Allows metrics to retrieve values from SMC-Core logic placeholders.

Sets the numeric value that will be evaluated against the configured ranges.

### default
```yaml
default: VALUE
```
Sets the value returned when no configured range matches the evaluated value.
<br>If omitted, the source returns `0`.

### ranges
```yaml
ranges: LIST
```
> *Example range:*
> ```yaml
> ranges:
>  - from: NUMBER
>    to: NUMBER
>    value: VALUE
> ```
Sets the configured ranges used to determine the returned value.
<br>Supports placeholders and variables.

