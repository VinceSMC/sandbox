## Effects
Effects allow you to apply reusable visual styles and animations to text.
<br>They can create gradients, highlights, pulses, rainbow colors, typewriter animations, scrolling text, rotating effect sequences, and other dynamic output without configuring every frame manually.

Each file defines one effect. A file can either render its own source text or sequence existing effects that remain defined in their own files.

### Effect placeholders

| # | Placeholder | Type | Description |
|---|---|---|---|
| 1 | `{effect--<fileID>}` | Native | Returns the current rendered state of an effect. |
| 2 | `%smccore_effect--<fileID>%` | PAPI | Returns the current rendered state of an effect. |

> [!NOTE]
> Native placeholders are only supported within the SMC plugin ecosystem.  
> PAPI placeholders can be used in any location that supports PlaceholderAPI.

### Syntax

#### Standard effect
```yaml
enabled: BOOLEAN
text: TEXT
style: STYLE
playback: PLAYBACK
layers: LAYERS
timeline: TIMELINE
```

#### Sequence effect
```yaml
enabled: BOOLEAN
playback: PLAYBACK
sequence: SEQUENCE
```

> [!NOTE]
> Standard effects use `text`, `style`, `layers`, and `timeline` to render their own output.
> <br>Sequence effects use `sequence` to display existing effects in rotation and cannot define those standard rendering options in the same file.

### enabled
```yaml
enabled: BOOLEAN
```
> *Default value:* `true`

Sets whether the effect is enabled.
<br>When a standard effect is disabled, its placeholder returns the resolved source text without applying the configured effect.

### text
```yaml
text: TEXT
```
> *Supports:*
> - [`PlaceholderAPI`](https://wiki.placeholderapi.com/) — Allows effects to use values returned by any installed PlaceholderAPI expansion.
> - [`Variables`](variables.md) — Allows effects to use values returned by SMC-Core variable placeholders.
> - [`Logics`](logics.md) — Allows effects to use values returned by SMC-Core logic placeholders.
> - [`Metrics`](metrics.md) — Allows effects to use values returned by SMC-Core metric placeholders.

Sets the default source text to which the effect is applied.
<br>Supported placeholders are resolved before the configured styles and layers are rendered.
<br>The value can be overridden by a timeline stage or by a sequence entry that references the effect.

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
Sets how the effect timeline or sequence is played, rendered, and synchronized between viewers.
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
Sets the ordered stages that make up a standard effect.
<br>Timeline stages can override the source text, allowing one effect to display different words or messages throughout its cycle.
<br>Check the [Timeline](effect-components/timeline.md) section for more information.

### sequence
```yaml
sequence: SEQUENCE
```
Sets the existing effects displayed one after another through a single effect placeholder.
<br>This can be used to create rotating banners without copying each referenced effect into the same file.
<br>Check the [Sequence](effect-components/sequence.md) section for more information.
