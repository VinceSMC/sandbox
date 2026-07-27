# style

**Effect component**
<br>`style`

**Description**
<br>The style component sets the default color and formatting applied to the source text.

## Syntax
```yaml
style:
  color: TEXT
  format: TEXT
```

### color
```yaml
color: TEXT
```
Sets the default color applied to the source text.
<br>Supports legacy and hexadecimal color codes. When configured, it overrides colors already present in the resolved source text.

### format
```yaml
format: TEXT
```
Sets the formatting applied to all visible characters in the source text.
<br>Supports formatting codes such as `&l`, `&o`, `&n`, `&m`, and `&k`.

If the style component is omitted, the formatting already present in the resolved source text is preserved until a layer modifies it.
<br>A timeline stage can override either option without redefining the other.

## Examples

### Apply a bold blue style
```yaml
style:
  color: "&b"
  format: "&l"
```

### Override only the color during a stage
```yaml
timeline:
 - duration: 1s
   style:
     color: "&f"
```
