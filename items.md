# Item files

Item files define physical SMC-Enchantments items. A configured item can set its material and presentation, include existing enchantments, control which enchantments it accepts, track item-bound progression, and run custom behavior.

SMC-Enchantments recursively loads lowercase `.yml` files from `items/`. The file name, without `.yml`, is the item ID. Subfolders organize files only and do not become part of the ID, so every file name must be unique across the complete `items/` folder.

This page owns the composition of an item file. Core configured-item options and the shared condition, formula, progression, event, effect, filter, and action systems will remain in their canonical reference pages as that documentation is added.

## Syntax

```yaml
enabled: BOOLEAN

display-name: "TEXT"

item: ITEM

category: CATEGORY_ID

targets:
 - ENCHANTMENT_TARGET

options:
  enchantable: BOOLEAN

conditions: CONDITIONS

formulas:
  FORMULA_ID: FORMULA

progression: PROGRESSION

events: EVENTS
```

Only `item` and `item.material` are required. Every other root option is optional and applies only when configured.

## Options

### Definition identity

```text
items/<optional-folders>/<ItemID>.yml
```

> - *Required:* Yes
> - *Structure:* lowercase-kebab file name ending in `.yml`

Defines the item ID through the file name. For example, `items/tools/treecapitator.yml` defines `treecapitator`.

Folder names do not namespace an ID. Two files named `grappling-hook.yml` conflict anywhere inside the `items/` domain.

Configured items can be requested through Core with:

```text
smcenchantments;item;<ItemID>
```

### `enabled`

```yaml
enabled: BOOLEAN
```

> - *Required:* No
> - *Default value:* `true`

Sets whether the item enters the active item and execution catalogs. A disabled definition is not generated automatically or available through its item reference.

### `display-name`

```yaml
display-name: "TEXT"
```

> - *Required:* No
> - *Default value:* no root display-name override

Sets the configured item's display name unless `item.display-name` provides a more specific override.

When omitted, Core and Minecraft retain the name produced by the configured item material. The local `{item_display-name}` placeholder falls back to the item definition ID when no root display name exists.

### `item`

```yaml
item:
  material: ITEM_REFERENCE
```

> - *Required:* Yes
> - *Structure:* a Core configured-item mapping containing `material`

Defines the physical item through Core's configured-item contract. It supports Core fields such as material, amount, display name, lore, rarity, tags, glow, unbreakable state, color, model data, and supported Minecraft components.

`material` accepts a Minecraft material or a registered Core item reference. It must resolve to a usable item.

An item-level `display-name` overrides the root `display-name`. Authored `lore` contributes item-specific detail lines; event displays, enchantments, requirements, progression, and set bonuses are composed into their semantic lore sections by the shared item layout rather than copied into this list manually.

### `item.enchantments`

```yaml
item:
  material: IRON_SWORD
  enchantments:
   - type: sharpness
     level: 2
   - type: "minecraft:unbreaking"
     level: 3
```

> - *Required:* No
> - *Default value:* `level: 1`
> - *Structure:* list of enchantment entries

Adds existing enchantments to every generated instance of the item. These are real installed enchantments and use the same presentation and runtime behavior as enchantments applied later through the enchanting menu or anvil.

`type` is required and accepts:

- a local enchantment ID such as `sharpness`;
- an SMC-Enchantments request such as `smcenchantments;enchantment;sharpness`; or
- a Minecraft namespaced key such as `minecraft:unbreaking`.

`level` accepts a positive integer or a placeholder string that resolves to a positive integer for the current viewer. When omitted, the level is `1`.

The referenced definition must exist when a local SMC-Enchantments ID is used. See [enchantment files](enchantments.md) for the definition contract.

### `category`

```yaml
category: CATEGORY_ID
```

> - *Required:* No
> - *Supported values:* IDs configured under `config.yml > options.categories.entries`

Overrides the presentation category for the item.

When omitted, SMC-Enchantments first uses explicit item targets. If no targets are configured, it infers targets from the resolved material. It then selects the first category matching those targets or falls back to `config.yml > options.categories.default`.

### `targets`

```yaml
targets:
 - sword
```

> - *Required:* No
> - *Default value:* inferred from the resolved item material

Overrides the item families used when checking enchantment compatibility. The supported values are the same target IDs documented for [enchantment files](enchantments.md#targets).

When the list is absent or empty, a recognized sword, axe, pickaxe, shovel, hoe, bow, crossbow, fishing rod, shears, or armor material supplies its natural target.

### `options`

```yaml
options:
  enchantable: BOOLEAN
```

> - *Required:* No
> - *Default value:* `enchantable: true`

Defines item-specific behavioral options.

`enchantable` determines whether the item accepts new enchantments through supported enchanting and anvil surfaces. Setting it to `false` does not remove enchantments already configured under `item.enchantments`.

### `conditions`

```yaml
conditions: CONDITIONS
```

> - *Required:* No
> - *Default value:* no root requirements

Adds a Core condition group that gates the item's runtime behaviors and contributes supported requirement presentation.

Event nodes may add their own condition groups for one specific activation. Root and event requirements are both required when both are present.

### `formulas`

```yaml
formulas:
  FORMULA_ID: FORMULA
```

> - *Required:* No
> - *Default value:* no named formulas

Defines numeric constants, Core decimal expressions, or exact per-level numeric tables for item descriptions and execution nodes.

`{formula}` resolves the formula named `default`. `{formula;<FormulaID>}` resolves a named formula. The accepted formula forms and cycle rules are identical to [enchantment formulas](enchantments.md#formulas).

### `progression`

```yaml
progression:
 - id: PROGRESSION_ID
   event: EVENT
   amount: NUMBER_OR_EXPRESSION
   thresholds:
    - value: NUMBER_OR_EXPRESSION
      effects: EFFECTS
```

> - *Required:* No
> - *Default value:* `amount: 1` on a configured progression entry

Adds counters stored on the exact physical item. Each entry requires a stable, definition-local `id`, one event, and one or more thresholds.

`amount` must resolve to a positive integer when the event runs. Threshold values must also resolve to positive integers. Thresholds are evaluated in numeric ascending order and each threshold is crossed once for that item's stored progression state.

Only `value` and `effects` are supported on a threshold entry. Conditions and actions belong to the owning event or an effect node.

The structure is shared with enchantment progression and will move to one dedicated reference when the detailed catalog is authored.

### `events`

```yaml
events:
 - type: EVENT_TYPE
   display: DISPLAY
   conditions: CONDITIONS
   args: ARGUMENTS
   filters: FILTERS
   options: OPTIONS
   costs: COSTS
   effects: EFFECTS
   actions: ACTIONS
```

> - *Required:* No
> - *Default value:* no custom runtime behavior

Adds behavior to the item. Every event entry requires `type`; all other branches are optional and must be supported by that event or its child providers.

`display` defines behavior lore such as an ability name and description. `conditions` and `filters` gate activation. `options` may define supported values such as cooldown or chance. `costs` are reserved atomically before execution. `effects` perform gameplay behavior. `actions` run only after the enclosing activation commits successfully.

The event, effect, filter, and cost families will each receive a catalog page and one leaf page per implemented type. Unknown fields are not extension points and must not be assumed to work merely because YAML accepts them.

> **Work in progress:** `modify-stat` is retained for the future Skills integration and currently performs no runtime operation. `modify-experience` with a non-Minecraft skill is also deferred. Stat placeholders without a provider, including `{strength_player}` and `{defense_target}`, do not yet produce functional arithmetic effects.

## Related sections

- [Enchantment files](enchantments.md) define enchantments that can be installed on these items.
- [Set files](sets.md) group configured items into equipment bonuses.

## Examples

### Create an enchantable sword with a preinstalled enchantment

This focused example defines `undead-sword.yml`, includes Smite II, and permits additional compatible enchantments.

```yaml
enabled: true

display-name: "Undead Sword"

item:
  material: IRON_SWORD
  rarity: common
  unbreakable: true
  enchantments:
   - type: smite
     level: 2

category: combat

targets:
 - sword

options:
  enchantable: true
```

Shared configuration banners are omitted because this is a focused syntax example rather than a complete shipped file.
