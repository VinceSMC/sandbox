## Enchantments
Enchantment files define enchantments that can be applied to certain items.
<br>A definition may wrap a Minecraft enchantment or provide custom behavior through events and effects.

### Syntax
```yaml
enabled: BOOLEAN
display: EXPRESSION
item: ITEM
category: CATEGORY_ID ## Do we use this?
targets: LIST
registry: EXPRESSION
application: EXPRESSION
conditions: CONDITIONS
levels: LEVELS
formulas: EXPRESSION
progression: PROGRESSION
events:
 - type: EVENT_TYPE
```

### enabled
```yaml
enabled: BOOLEAN
```
> *Default value:* `true`
If set to true, ...

### display
```yaml
display: EXPRESSION
```
Sets the display properties of the enchantment.
<br>Check the [Display](https://github.com/LINK_HERE) section for more information.


### `item`

```yaml
item: ITEM
```

> - *Required:* No
> - *Inherited from:* `config.yml > item.enchantment`

Overrides the configured item used to represent this enchantment. The definition is merged over the plugin-wide enchantment item, so a definition commonly needs only a field such as `rarity`.

The mapping supports Core configured-item options. An `enchantments` list inside this mapping is ignored for canonical enchantment books; preinstalled enchantments belong to direct [item files](items.md#item).

Exact-level `item` mappings override this root mapping for that level.

### `category`

```yaml
category: CATEGORY_ID
```

> - *Required:* No
> - *Supported values:* IDs configured under `config.yml > options.categories.entries`

Selects the presentation category for the enchantment.

When omitted, SMC-Enchantments selects the first configured category whose targets intersect the enchantment targets. If none matches, it uses `config.yml > options.categories.default`.

### `targets`

```yaml
targets:
 - sword
 - axe
```

> - *Required:* Yes for custom enchantments; no for native-backed enchantments
> - *Structure:* list of enchantment target IDs

Defines which item families can receive the enchantment.

| Target | Item family |
| --- | --- |
| `sword` | Swords |
| `axe` | Axes |
| `pickaxe` | Pickaxes |
| `shovel` | Shovels |
| `hoe` | Hoes |
| `bow` | Bows |
| `crossbow` | Crossbows |
| `fishing-rod` | Fishing rods |
| `shears` | Shears |
| `helmet` | Helmets |
| `chestplate` | Chestplates |
| `leggings` | Leggings |
| `boots` | Boots |

When `registry.reference` points to a Minecraft enchantment and `targets` is omitted or empty, Minecraft owns compatibility. A custom enchantment has no native compatibility source and must configure at least one target.

### `registry`

```yaml
registry:
  reference: "minecraft:sharpness"
  min-level: 1
  max-level: 7
  conflicts:
   - smite
   - "minecraft:bane_of_arthropods"
```

> - *Required:* No
> - *Default value:* minimum `1`; referenced Minecraft maximum, or maximum `1` for a custom enchantment

Defines the enchantment identity, valid level range, and conflicts.

`reference` wraps an enchantment from Minecraft's active registry. When omitted, the definition uses the custom key `smcenchantments:<EnchantmentID>`.

`min-level` and `max-level` accept integers from `1` through `255`, and `min-level` cannot exceed `max-level`. A native-backed definition may deliberately extend its configured maximum beyond the vanilla maximum.

`conflicts` accepts local enchantment IDs and Minecraft namespaced keys. Conflicts are compiled in both directions, so only one side needs to declare the relationship. An enchantment cannot conflict with itself.

> **Warning:** A definition with `registry.reference` must not also configure root `events`. Minecraft owns the native execution and SMC-Enchantments rejects duplicate configured behavior.

### `application`

```yaml
application:
 - type: APPLICATION_COST_TYPE
   formula: "EXPRESSION"
   upgrade-formula: "EXPRESSION"
```

or:

```yaml
application:
 - type: APPLICATION_COST_TYPE
   levels:
     "1": NUMBER
     "2": NUMBER
   upgrade-formula: "EXPRESSION"
```

> - *Required:* No
> - *Default value:* inherited from `config.yml > options.application`
> - *Supported types:* `minecraft:experience-levels`, `minecraft:experience-points`, `smccurrency:<CurrencyID>`

Overrides the plugin-wide costs for applying this enchantment. Every list entry defines one cost, and multiple entries are assessed together.

Each entry requires exactly one of:

- `formula`, containing a Core decimal expression evaluated for the target level; or
- `levels`, mapping exact positive levels to non-negative numeric costs.

`upgrade-formula` optionally adjusts the target cost when the item already contains a lower level. It can use values such as `{cost_target}` and `{cost_current}` from the application context.

An omitted `application` branch inherits the plugin-wide list. An explicit empty list disables application costs for this enchantment:

```yaml
application: []
```

A level table does not interpolate or fall back. A missing exact level contributes no cost for that entry. A resolved cost of `0` is also omitted.

### `conditions`

```yaml
conditions: CONDITIONS
```

> - *Required:* No
> - *Default value:* no additional requirements

Adds a Core condition group to the enchantment. Root requirements combine with exact-level requirements and are used when assessing application and supported runtime activations.

Condition placeholders remain context-dependent. A value intended to gate both application and use must be available in both contexts.

> **Work in progress:** `{level_enchanting}` currently resolves to the temporary value `60` during application and presentation. The future Skills provider will own the real value and complete its runtime availability.

### `levels`

```yaml
levels:
  "LEVEL":
    item: ITEM
    conditions: CONDITIONS
    gui-menu:
      exclude: BOOLEAN
```

> - *Required:* No
> - *Structure:* mapping of exact positive levels within the registry range

Overrides metadata for individual enchantment levels.

- `item` shallowly overrides fields from the root `item` mapping for that exact level.
- `conditions` adds exact-level requirements to the root condition group.
- `gui-menu.exclude` removes that exact level from the enchanting menu when `true`. Its default is `false`.

One level entry does not inherit metadata from another level entry. For example, an item rarity configured at level `5` does not automatically apply at level `6`; configure level `6` explicitly when it needs the same override.

### `formulas`

```yaml
formulas:
  FORMULA_ID: NUMBER
```

or:

```yaml
formulas:
  FORMULA_ID: "EXPRESSION"
```

or:

```yaml
formulas:
  FORMULA_ID:
    "1": NUMBER
    "2": NUMBER
```

> - *Required:* No
> - *Default value:* no named formulas

Defines reusable numeric values for descriptions and execution nodes. A formula may be a numeric constant, a Core decimal expression, or an exact per-level numeric table.

`{formula}` resolves the formula named `default`. `{formula;<FormulaID>}` resolves a named formula. Formulas may reference other formulas, but circular references are rejected.

Per-level tables require positive integer keys and numeric values. They do not interpolate or fall back when the current level has no exact entry.

### `progression`

```yaml
progression: PROGRESSION
```

> - *Required:* No
> - *Default value:* no item-bound progression

Adds progression counters stored on the physical enchanted item. Each progression entry owns an event, an amount, and one or more one-time thresholds whose effects run when crossed.

The detailed progression contract is shared with [item files](items.md#progression) and will be documented once in a dedicated reference rather than duplicated between both pages.

### `events`

```yaml
events: EVENTS
```

> - *Required:* No
> - *Default value:* no custom runtime behavior

Adds custom event nodes to the enchantment. Every event requires a `type` and may attach a typed display, Core conditions, arguments, filters, options, atomic runtime costs, effects, and post-commit Core actions.

Event and effect types form shared catalogs and will receive separate index and leaf pages. Native-backed definitions cannot configure this branch because Minecraft already executes their behavior.

## Related sections

- [Item files](items.md) define physical items that may receive or include enchantments.
- [Set files](sets.md) combine configured items into equipment bonuses.

## Examples

### Wrap and extend a Minecraft enchantment

This focused example defines `sharpness.yml`, uses Minecraft's Sharpness behavior, allows seven configured levels, and keeps levels six and seven out of the enchanting menu.

```yaml
enabled: true

display:
  type: enchantment
  title: "Sharpness"
  description: "Increases melee damage dealt by &a{formula}&7."

item:
  rarity: common

targets:
 - sword
 - axe

registry:
  reference: "minecraft:sharpness"
  max-level: 7

application:
 - type: minecraft:experience-levels
   formula: "5 + (5 * {level})"
   upgrade-formula: "{cost_target} - ({cost_current} * 0.5)"

levels:
  "6":
    item:
      rarity: rare
    gui-menu:
      exclude: true
  "7":
    item:
      rarity: epic
    gui-menu:
      exclude: true

formulas:
  default: "(0.5 * {level}) + 1"
```

Shared configuration banners are omitted because this is a focused syntax example rather than a complete shipped file.
