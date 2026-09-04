## Enchantments

Enchantment files define enchantments that can be applied to certain items.
<br>A definition can use a Minecraft enchantment or provide custom behavior through events and effects.

### Syntax

```yaml
enabled: BOOLEAN
display: DISPLAY
item: ITEM
category: CATEGORY_ID
targets: LIST
registry: REGISTRY
application: APPLICATION
conditions: CONDITIONS
levels: LEVELS
formulas: FORMULAS
progression: PROGRESSION
events:
 - type: EVENT_TYPE
```

### enabled
```yaml
enabled: BOOLEAN
```
> *Default value:* `true`

If set to true, enables the enchantment.

### display
```yaml
display: DISPLAY
```
Sets the display properties of the enchantment.
<br>Check the [Display](shared/display.md) section for more information.

### item
```yaml
item: ITEM
```
Sets the item properties of the enchantment book.
<br>Check the [Items](shared/items.md) section for more information.

### category
```yaml
category: CATEGORY_ID
```
Sets the display category of the enchantment from `options.categories.entries` in the main config.yml.
<br>When omitted, the category is selected from the enchantment targets.

### targets
```yaml
targets: LIST
```

> *Example:*
> ```yaml
> targets:
>  - pickaxe
>  - axe
> ```

> *Supported values:* `sword`, `axe`, `pickaxe`, `shovel`, `hoe`, `bow`, `crossbow`, `fishing-rod`, `shears`, `helmet`, `chestplate`, `leggings`, `boots`

Sets the item types that can receive the enchantment.

### registry
```yaml
registry: REGISTRY
```
Sets the registry properties of the enchantment.
<br>Check the [Registry](enchantments/registry.md) section for more information.

### application
```yaml
application: APPLICATION
```
Sets the costs for applying the enchantment.
<br>Check the [Application](enchantments/application.md) section for more information.

### conditions
```yaml
conditions: CONDITIONS
```
Sets the requirements for applying and using the enchantment.
<br>Check the [Conditions](shared/conditions.md) section for more information.

### levels
```yaml
levels: LEVELS
```
Sets properties for specific enchantment levels.
<br>Check the [Levels](enchantments/levels.md) section for more information.

### formulas
```yaml
formulas: FORMULAS
```
Sets reusable formulas for the enchantment.
<br>Check the [Formulas](shared/formulas.md) section for more information.

### progression
```yaml
progression: PROGRESSION
```
Sets progression tracked on the enchanted item.
<br>Check the [Progression](shared/progression.md) section for more information.

### events
```yaml
events:
 - type: EVENT_TYPE
```
Sets the events that trigger the enchantment behavior.
<br>Check the [Event Types](event-types/index.md) section for more information.
