## Logics
Logics allow you to dynamically modify the return value of a placeholder based on the value retrieved from another placeholder.
<br>They make it possible to define rules that determine what output should be returned depending on the evaluated value.

### Logic placeholders

| # | Placeholder | Type | Description |
|---|---|---|---|
| 1 | `{logic--<fileID>_<logicID>}` | Native | Returns the output defined by the matching logic response. |
| 2 | `%smccore_logic--<fileID>_<logicID>%` | PAPI | Returns the output defined by the matching logic response. |

> [!NOTE]
> Native placeholders are only supported within the SMC plugin ecosystem.  
> PAPI placeholders can be used in any location that supports PlaceholderAPI.

### Syntax
```yaml
LOGIC_ID:
  value: TEXT
  default: TEXT
  responses: RESPONSES
```

### logic id
```yaml
LOGIC_ID
```
Sets the unique identifier of the logic.

### value
```yaml
value: TEXT
```
Sets the placeholder whose returned value will be evaluated by the logic.
<br>Supports PAPI placeholders.

### default
```yaml
default: TEXT
```
Sets the value returned when no configured response matches the evaluated value.

### responses
```yaml
responses: RESPONSES
```
> *Structure:*
> ```yaml
> responses:
>  - RESPONSE_TYPE: VALUE
>    return: TEXT
> ```

Defines the rules used to determine which value should be returned.
<br>Check the [Response Types](logic-types) section for more information.




