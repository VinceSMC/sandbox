# typewriter

**Layer type**
<br>`typewriter`

**Description**
<br>The typewriter layer type reveals or erases the visible characters of the source text over time.

## Syntax
```yaml
- type: typewriter
  mode: TEXT
  direction: TEXT
  cursor: TEXT
  cursor-color: TEXT
  include-spaces: BOOLEAN
```

### mode
```yaml
mode: TEXT
```
> *Supported values:* `reveal`, `erase`

Sets whether the source text is revealed or erased during the active timeline stage.

| Mode | Description |
|---|---|
| `reveal` | Starts with no visible source characters and reveals the complete text. |
| `erase` | Starts with the complete source text and removes its visible characters. |

### direction
```yaml
direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`  
> *Default value:* `left-to-right`

Sets the direction in which the source characters are revealed or erased.

### cursor
```yaml
cursor: TEXT
```
Sets the optional cursor displayed at the current reveal or erase position.

### cursor color
```yaml
cursor-color: TEXT
```
Sets the color applied to the configured cursor.
<br>If omitted, the cursor uses the style at its current position.

### include spaces
```yaml
include-spaces: BOOLEAN
```
> *Default value:* `false`

Sets whether spaces consume separate timing positions.
<br>When disabled, spaces remain part of the output but do not receive their own reveal or erase step.

## Examples

### Reveal text from left to right
```yaml
timeline:
 - duration: 1.4s
   layers:
    - type: typewriter
      mode: reveal
      direction: left-to-right
      cursor: "_"
      cursor-color: "&7"
      include-spaces: false
```

### Reveal, hold, and erase text
```yaml
timeline:
 - duration: 1.4s
   layers:
    - type: typewriter
      mode: reveal
      direction: left-to-right
      cursor: "_"
      cursor-color: "&7"
      include-spaces: false

 - duration: 1.6s

 - duration: 1s
   layers:
    - type: typewriter
      mode: erase
      direction: right-to-left
      cursor: "_"
      cursor-color: "&7"
      include-spaces: false

 - duration: 500ms
   text: ""
```
