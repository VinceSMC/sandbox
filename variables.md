## Variables
Variables allow you to define reusable values that can be referenced throughout your server.
<br>They make it easy to centralize frequently used values such as text and colors.

### Variable placeholders

| # | Placeholder | Type | Description |
|---|---|---|---|
| 1 | `{var--<fileID>_<variableID>}` | Native | Returns the value of a variable. |
| 2 | `%smccore_var--<fileID>_<variableID>%` | PAPI | Returns the value of a variable. |

> [!NOTE]
> Native placeholders are only supported within the SMC plugin ecosystem.  
> PAPI placeholders can be used in any location that supports PlaceholderAPI.

### Syntax
```yaml
VARIABLE_ID:
  value: TEXT
```

### variable id
```yaml
VARIABLE_ID
```
Sets the unique identifier of the variable.

### value
```yaml
value: TEXT
```

Sets the value of the variable.
