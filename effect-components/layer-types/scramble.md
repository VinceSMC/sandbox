# scramble

**Layer type**
<br>`scramble`

**Description**
<br>The scramble layer type displays changing randomized characters that progressively settle into the source text.

## Syntax
```yaml
- type: scramble
  characters: TEXT
  settle-direction: TEXT
  preserve-spaces: BOOLEAN
```

### characters
```yaml
characters: TEXT
```
Sets the characters that can be used for the temporary randomized output.
<br>At least one character must be configured.

### settle direction
```yaml
settle-direction: TEXT
```
> *Supported values:* `left-to-right`, `right-to-left`, `random`  
> *Default value:* `left-to-right`

Sets the order in which randomized characters settle into their final source characters.

### preserve spaces
```yaml
preserve-spaces: BOOLEAN
```
> *Default value:* `true`

Sets whether spaces remain fixed instead of being replaced by randomized characters.

## Examples

### Scramble text from left to right
```yaml
timeline:
 - duration: 1.2s
   layers:
    - type: scramble
      characters: "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
      settle-direction: left-to-right
      preserve-spaces: true
```

### Reveal characters in a random order
```yaml
timeline:
 - duration: 2s
   layers:
    - type: scramble
      characters: "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
      settle-direction: random
      preserve-spaces: true
```
