## Effects
Effects allow you to apply reusable visual styles and animations to text.
<br>They can create gradients, highlights, pulses, rainbow colors, typewriter animations, scrolling text, and other dynamic output without configuring every frame manually.

### Effect placeholders

| # | Placeholder | Type | Description |
|---|---|---|---|
| 1 | `{effect--<fileID>}` | Native | Returns the current rendered state of an effect. |
| 2 | `%smccore_effect--<fileID>%` | PAPI | Returns the current rendered state of an effect. |

> [!NOTE]
> Native placeholders are only supported within the SMC plugin ecosystem.  
> PAPI placeholders can be used in any location that supports PlaceholderAPI.

### Syntax
```yaml
enabled: BOOLEAN
text: TEXT
style: STYLE
playback: PLAYBACK
layers: LAYERS
timeline: TIMELINE
```

### enabled
```yaml
enabled: BOOLEAN
```
> *Default value:* `true`

Sets whether the effect is enabled.
<br>When disabled, the placeholder returns the resolved source text without applying the configured effect.

### text
```yaml
text: TEXT
```
> *Supports:*
> - [`PlaceholderAPI`](https://wiki.placeholderapi.com/) — Allows effects to use values returned by any installed PlaceholderAPI expansion.
> - [`Variables`](variables.md) — Allows effects to use values returned by SMC-Core variable placeholders.
> - [`Logics`](logics.md) — Allows effects to use values returned by SMC-Core logic placeholders.
> - [`Metrics`](metrics.md) — Allows effects to use values returned by SMC-Core metric placeholders.

Sets the source text to which the effect is applied.
<br>Supported placeholders are resolved before the configured styles and layers are rendered.

### style
```yaml
style: STYLE
```
Sets the default color and formatting applied to the effect.
<br>Check the [Style](effect-components/style.md) section for more information.

### playback
```yaml
playback: PLAYBACK
```
Sets how the effect timeline is played, rendered, and synchronized between viewers.
<br>Check the [Playback](effect-components/playback.md) section for more information.

### layers
```yaml
layers: LAYERS
```
> *Structure:*
> ```yaml
> layers:
>  - type: LAYER_TYPE
> ```

Sets the layers applied throughout the complete effect.
<br>Root layers remain active during every timeline stage and are applied in their configured order. Later layers can modify the output produced by earlier layers.
<br>Check the [Layer Types](effect-components/layer-types) section for more information.

### timeline
```yaml
timeline: TIMELINE
```
Sets the ordered stages that make up the effect.
<br>Check the [Timeline](effect-components/timeline.md) section for more information.
