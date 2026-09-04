# Set files

Set files group configured SMC-Enchantments items and add bonuses while matching pieces are equipped. Each piece remains an independent item file with its own material, presentation, recipe eligibility, enchantments, and behavior.

SMC-Enchantments recursively loads lowercase `.yml` files from `sets/`. The file name, without `.yml`, is the set ID. Subfolders organize files only and do not become part of the ID, so every file name must be unique across the complete `sets/` folder.

This page owns the composition of a set file. Core conditions and the shared event, effect, filter, display, and action systems will remain in their canonical reference pages as that documentation is added.

## Syntax

```yaml
enabled: BOOLEAN

display-name: "TEXT"

items:
 - smcenchantments;item;<ItemID>

conditions: CONDITIONS

bonuses:
 - id: BONUS_ID
   display:
     type: DISPLAY_TYPE_ID
     title: "TEXT"
     description: TEXT_OR_LIST
   conditions: CONDITIONS
   events: EVENTS
```

`items` and at least one `bonuses` entry are required for a set to produce useful behavior. The current validator accepts their omission, but an empty definition has no membership or bonus to execute.

## Options

### Definition identity

```text
sets/<optional-folders>/<SetID>.yml
```

> - *Required:* Yes
> - *Structure:* lowercase-kebab file name ending in `.yml`

Defines the set ID through the file name. For example, `sets/armor/cactus-armor.yml` defines `cactus-armor`.

Folder names do not namespace an ID. Two files with the same base name conflict anywhere inside the `sets/` domain.

### `enabled`

```yaml
enabled: BOOLEAN
```

> - *Required:* No
> - *Default value:* `true`

Sets whether the definition contributes membership, lore, and runtime bonuses. A disabled set adds no set presentation or behavior to its configured member items.

### `display-name`

```yaml
display-name: "TEXT"
```

> - *Required:* No

Provides the intended human-readable name of the set in the shipped configuration.

> **Note:** The current runtime does not consume `display-name` for item lore, placeholders, or behavior. This mismatch is documented explicitly instead of presenting the option as functional. Set-bonus presentation currently comes from each bonus `display` block.

### `items`

```yaml
items:
 - smcenchantments;item;cactus-helmet
 - smcenchantments;item;cactus-chestplate
 - smcenchantments;item;cactus-leggings
 - smcenchantments;item;cactus-boots
```

> - *Required:* Yes for set membership
> - *Structure:* list of exact SMC-Enchantments item references

Defines which configured items belong to the set. Every entry must use this request syntax and resolve to an existing item definition:

```text
smcenchantments;item;<ItemID>
```

Only matching items equipped in the helmet, chestplate, leggings, and boots slots count toward `{pieces}`. Duplicate item references are collapsed and do not increase the equipped-piece total.

See [item files](items.md) for the item definition contract.

### `conditions`

```yaml
conditions: CONDITIONS
```

> - *Required:* No
> - *Default value:* no set-wide requirements

Adds a Core condition group that gates every runtime event compiled for the set.

Use bonus-level conditions when a requirement belongs to one bonus instead of the complete set.

### `bonuses`

```yaml
bonuses:
 - id: BONUS_ID
   display: DISPLAY
   conditions: CONDITIONS
   events: EVENTS
```

> - *Required:* Yes for bonus behavior
> - *Structure:* list of bonus definitions

Defines the independently presented and evaluated bonuses belonging to the set. Authored list order controls their presentation order.

Each bonus can have its own display, conditions, and events. A bonus may omit `display` and still execute; it then adds no bonus description to item lore.

### `bonuses[].id`

```yaml
bonuses:
 - id: BONUS_ID
```

> - *Required:* No

Names the authored bonus entry. The current public configuration does not select or expose a set bonus by this ID, so omitting it does not disable the bonus.

### `bonuses[].display`

```yaml
bonuses:
 - display:
     type: set-bonus
     title: "Deflect"
     description: "Reflects part of incoming damage."
```

or:

```yaml
bonuses:
 - display:
     type: set-bonus
     title: "Deflect"
     description:
      - "Reflects part of incoming damage."
      - "Only hostile mobs are affected."
```

> - *Required:* No
> - *Default value:* no description

Defines the bonus title and description composed into every member item's set-bonus lore section.

The optional `type` selects an entry from `messages.yml > text-and-labels.display.types`. When a type is configured, its title and description templates style this display. When the type is omitted, configured title and description lines remain unstyled by a display type.

### `bonuses[].conditions`

```yaml
bonuses:
 - conditions:
     requirements:
      - type: ">="
        input: "{pieces}"
        output: "4"
```

> - *Required:* No
> - *Default value:* no bonus-specific requirements

Adds a Core condition group that gates this bonus and determines whether its lore is presented as active or inactive.

`{pieces}` returns the number of matching set items currently equipped. A simple numeric comparison between `{pieces}` and a fixed threshold also supplies `{pieces_required}` to the configured set-bonus threshold text.

### `bonuses[].events`

```yaml
bonuses:
 - events:
    - type: EVENT_TYPE
      conditions: CONDITIONS
      args: ARGUMENTS
      filters: FILTERS
      options: OPTIONS
      costs: COSTS
      effects: EFFECTS
      actions: ACTIONS
```

> - *Required:* No
> - *Default value:* no executable bonus behavior

Adds event-driven behavior to the bonus. The set and bonus condition groups must pass before a bound event can execute.

The current equipment-set runtime binds these root event types:

- `block-break`
- `block-experience`
- `damage-taken`
- `first-damage-taken`
- `item-active`
- `natural-heal`

Do not configure another root event type in a set merely because the shared event compiler recognizes it. Other event adapters do not currently provide a set binding and therefore cannot execute the bonus reliably.

Event displays belong to item and enchantment behaviors. The set's visible heading and description belong to `bonuses[].display`.

## Related sections

- [Item files](items.md) define each independently configurable set piece.
- [Enchantment files](enchantments.md) define enchantments that set pieces may include or receive.

## Examples

### Create a four-piece defensive bonus

This focused example defines `cactus-armor.yml`. The bonus becomes active while all four configured pieces are equipped.

```yaml
enabled: true

display-name: "Cactus Armor"

items:
 - smcenchantments;item;cactus-helmet
 - smcenchantments;item;cactus-chestplate
 - smcenchantments;item;cactus-leggings
 - smcenchantments;item;cactus-boots

bonuses:
 - id: deflect
   display:
     type: set-bonus
     title: "Deflect"
     description: "Reflect 33% of final incoming damage to the attacking mob."
   conditions:
     requirements:
      - type: ">="
        input: "{pieces}"
        output: "4"
   events:
    - type: damage-taken
      filters:
       - type: entity-class
         target: source
         class: mob
      effects:
       - type: deal-damage
         args:
           target: source
           amount: "{damage_final} * 0.33"
```

Shared configuration banners are omitted because this is a focused syntax example rather than a complete shipped file.
