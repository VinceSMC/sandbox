# timeline

**Effect component**
<br>`timeline`

**Description**
<br>The timeline component defines the ordered stages that make up an effect and determines how long each stage remains active.

## Syntax
```yaml
timeline:
 - duration: DURATION
   text: TEXT
   style:
     color: TEXT
     format: TEXT
   layers:
    - type: LAYER_TYPE
```

The complete cycle duration is calculated automatically by adding the duration of every configured stage.
<br>A timeline is required for every playback mode except `static`.

### duration
```yaml
duration: DURATION
```
> *Supported units:*
> - `ms` — Milliseconds, for example `350ms`.
> - `s` — Seconds, for example `2.8s`.
> - `m` — Minutes, for example `1m`.
> - `t` — Minecraft ticks, for example `20t`.

Sets how long the timeline stage remains active.
<br>The duration must be greater than zero and must include a supported unit.

### text
```yaml
text: TEXT
```
Sets the source text used during the timeline stage.
<br>Supports the same placeholders, colors, and formatting codes as the root `text` option.
<br>If omitted, the root `text` value is used. An empty value can be used to display an intentionally blank stage.

### style
```yaml
style:
  color: TEXT
  format: TEXT
```
Sets the style overrides applied during the timeline stage.
<br>Any omitted style option continues using its root value.
<br>Check the [Style](style.md) section for more information.

### layers
```yaml
layers:
 - type: LAYER_TYPE
```
Sets the layers applied only while the timeline stage is active.
<br>Stage layers are applied after the root layers and in their configured order. Later layers can modify the output produced by earlier layers.
<br>Check the [Layer Types](layer-types) section for more information.

> [!NOTE]
> Animated root layers use the progress of the complete timeline. Animated stage layers use the progress of their active stage.

## Examples

### Create a three-second pause
```yaml
timeline:
 - duration: 3s
```

### Apply a temporary style and layer
```yaml
timeline:
 - duration: 1s
   style:
     color: "&f"
   layers:
    - type: pulse
      peak-color: "&#FFE75A"
      cycles: 1
      easing: sine-in-out
```

### Override the source text with a blank stage
```yaml
timeline:
 - duration: 500ms
   text: ""
```
