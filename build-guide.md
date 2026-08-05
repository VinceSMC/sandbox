# Skyblock Spawn Build Guide

This document defines the purpose and required direction of each current structure within the Skyblock Spawn. The structure numbers match the numbered builds in the build world and must remain unchanged.

The NPC tables only contain current NPCs from `location_village`. NPCs assigned to a numbered structure are listed directly beneath it. NPCs that belong to an area rather than a specific structure are listed separately at the end. Planned NPCs without a current NPC definition are not included in the tables.

## Spawn Areas

| Area | Purpose | Current Structures | NPCs |
|------|---------|--------------------|-----:|
| Village (Center) | The main settlement containing most buildings, services, merchants, and villagers. | `1`, `2`, `4`–`12`, `16`–`18`, `22` | 33 |
| Mining District | The main location for mining-related services and the Blacksmith. | `21` | 3 |
| Mob Camp | A dedicated area for mob-related content. | — | 0 |
| Combat Settlement | The main location for combat services, equipment, and enchanting. | `19`, `20` | 1 |
| The Forest | The main location for woodcutting, foraging, and wood-related merchants. | `15` | 3 |
| Farm | The main location for crops, animals, and farming-related content. | `13`, `14` | 1 |
| Fishing Forest | A water-rich forest dedicated to fishing-related content. | `3` | 2 |
| Mountain | A dedicated mountain area. Its exact gameplay purpose has not yet been defined. | — | 0 |
| **Total** |  | **22 structures** | **43** |

## Current Structures

### 1. Auction House

**Area:** Village (Center)

**Purpose:** Allows players to buy and sell items through the Auction House.

**Direction:** The current structure is approved and should remain largely unchanged. Complete the interior with additional detail. Small modifications are welcome where they clearly strengthen the build.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 1 | Auction Agent | Counter | Opens the Auction House interface. | `loc-village-auctioneer-01` |
| 2 | Auction Agent | Counter | Opens the Auction House interface. | `loc-village-auctioneer-02` |
| 3 | Auction Agent | Counter | Opens the Auction House interface. | `loc-village-auctioneer-03` |
| 4 | Auction Agent | Counter | Opens the Auction House interface. | `loc-village-auctioneer-04` |
| 5 | Auction Warden | Interior | Acts as the senior Auction House authority and opens the Auction House interface. | `loc-village-warden` |

### 2. The Bank

**Area:** Village (Center)

**Purpose:** Allows players to manage their Coins. A vault beneath the Bank provides access to personal storage after it has been unlocked through the Banker upstairs.

**Direction:** The current structure is approved and its main design should be preserved. Focus any revisions on making the basement and vault feel more detailed, secure, and substantial. The exact scope of these changes is still open.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 6 | Banker | Main Floor | Manages Coin deposits, withdrawals, savings, interest, and the team bank. | `loc-village-banker` |
| 7 | Gareth | Main Floor | Acts as the Bank's head guard. | `loc-village-head-guard` |
| 8 | Edric | Basement Vault | Opens the player's Personal Vault after access has been purchased. | `loc-village-vault-manager` |

### 3. Fisherman's Hut

**Area:** Fishing Forest

**Purpose:** Serves as the main location for fishing-related content. A merchant at the dock buys and sells fish.

**Direction:** Place the hut in a fishing-themed area with plenty of water and a clear dock. The current structure is approved. It may be updated with newer Minecraft materials where this noticeably improves the build without changing its identity.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 9 | Fish Merchant | Dock | Opens the Fish Merchant shop. | `loc-village-fish-merchant` |
| 10 | Fisherman Todd | Dock | Serves as the main fisherman character. His final interaction has not yet been defined. | `loc-village-fisherman` |

### 4. Bakery

**Area:** Village (Center)

**Purpose:** Houses baking-related NPCs and quests.

**Direction:** The current design is approved and should be retained. Add any final interior or environmental details needed to make the building feel complete.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 11 | Baker | Interior | Is planned to give players a cake when their island is created and on each island anniversary. | `loc-village-baker` |
| 12 | Farm Merchant | Interior or Attached Stall | Opens the Farm Merchant shop. | `loc-village-farm-merchant` |

### 5. Potionarium

**Area:** Village (Center)

**Purpose:** Houses the Alchemist, who sells brewing ingredients and other potion-related items.

**Direction:** Rebuild this structure from scratch. The replacement should be smaller than the current building and should immediately communicate alchemy and brewing through its exterior and interior. The exact visual style has not yet been decided.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 13 | Alchemist | Interior | Opens the Alchemist shop. | `loc-village-alchemist` |

### 6. Resource Foundry

**Area:** Village (Center)

**Purpose:** Allows players to convert one type of resource into another. For example, Island EXP can be converted into Upgrade Tokens used for island upgrades.

**Direction:** Retain the current architectural concept, but give the building a more distinctive identity and make the conversion process visible within the design. The preferred final layout combines the Resource Foundry with the Bar in one larger structure while preserving separate entrances and identities for both features.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 14 | Converter Milo | Foundry Interior | Converts spare resources into other materials and provides access to Upgrade Tokens. | `loc-village-resource-converter` |

### 7. The Tinkery

**Area:** Village (Center)

**Purpose:** Houses two NPCs. The Engineer manages the Gem Reactor, which generates Gems over time and can be upgraded for greater production speed and storage capacity. Gearson sells Booster Capsules that grant players special abilities.

**Direction:** Preserve the current exterior, which is approved. Redesign the interior so it feels like an active workshop rather than an empty building. A visible Gem Reactor machine must be the main interior feature, with a clear area for each NPC.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 15 | Gearson | Upper Floor | Sells the Booster Capsule. | `loc-village-gearson` |
| 16 | Thalen | Lower Floor | Introduces the Gem Reactor, accepts Concentrated Stone, and opens the Gem Reactor once unlocked. | `loc-village-engineer` |

### 8. The Builder

**Area:** Village (Center)

**Purpose:** Houses a merchant who sells building blocks.

**Direction:** Preserve the overall exterior direction and its use of newer materials. Give the entrance more depth and detail. A secondary facade in a contrasting style may be used, although the exact entrance treatment is still open. The white building beside it may be changed or replaced, but it should continue to frame the route into the next area. Integrate the complete structure more naturally with the surrounding village through its palette, terrain, paths, and neighboring buildings.

### 9. Cosmetics Building (Currently Unnamed)

**Area:** Village (Center)

**Purpose:** Provides access to cosmetic content. Players unlock cosmetics in the underground area and purchase them with Gems from a shop upstairs.

**Direction:** Rebuild the current structure from scratch. The replacement should feel like a distinctive cosmetics destination and clearly support both the underground unlock area and the upstairs shop. The exact architectural theme has not yet been decided.

### 10. Filler Structure 1

**Area:** Village (Center)

**Purpose:** Adds visual balance to the village and provides an exterior location for an unlockable trading NPC.

**Direction:** This structure is flexible and may be redesigned or replaced. Preserve its role in completing the surrounding streetscape and provide a natural, visible position for the NPC outside.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 17 | Trader Joe | Outside | Opens the Personal Trades shop. | `loc-village-personal-trades` |

### 11. The Bar

**Area:** Village (Center)

**Purpose:** Houses a merchant who sells drinks that provide players with different effects.

**Direction:** Merge the Bar with the Resource Foundry rather than giving it a separate standalone building. Both features should share one larger footprint while retaining their own entrances, interior areas, and visual identities. The exact connection between the two interiors is still open.

### 12. Filler Structure 2 — Watermill

**Area:** Village (Center)

**Purpose:** Acts as a decorative watermill and houses Millard, who sells special sponges capable of absorbing large amounts of water.

**Direction:** Retain the watermill concept in the final build. The current idea is approved and may be refined as needed, with water incorporated naturally into both the structure and its surroundings.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 18 | Millard | Watermill | Sells special water-control sponges and maintains the village fountain. | `loc-village-water-engineer` |

### 13. The Barn

**Area:** Farm

**Purpose:** Supports the Farm area by housing animals and potentially additional NPCs.

**Direction:** Rebuild the current Barn because it does not fit the wider visual style. The replacement should strengthen the Farm area, provide suitable space for animals, and match the surrounding structures. Its exact NPC use has not yet been decided.

### 14. Farmer's House

**Area:** Farm

**Purpose:** Serves as a decorative Farm structure and houses the Farmer NPC, who provides farming-related quests.

**Direction:** The current structure is suitable and may remain. Refine it only where necessary to make it blend naturally with the final Farm area and the rebuilt Barn.

### 15. Lumberjack's House

**Area:** The Forest

**Purpose:** Forms the main wood and foraging location within The Forest. It should contain the Lumberjack and their quests, the Lumber Merchant, and the Carpenter.

**Direction:** Expand this location into a small woodworking cluster rather than using a single isolated house. Add supporting structures or workspaces around the Lumberjack's House so all three NPC roles feel naturally grouped together. The exact number and arrangement of these structures is still open.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 19 | Lumber Merchant | Woodworking Area | Opens the Lumber Merchant shop. | `loc-village-lumber-merchant` |

### 16. Pets

**Area:** Village (Center)

**Purpose:** Serves as the location where players can purchase pets.

**Direction:** Rebuild the current structure because it does not communicate its purpose. The replacement should be immediately recognizable as a pet-related location and provide suitable space for the merchant and pet displays. The exact visual style has not yet been decided.

### 17. Filler Structure 3

**Area:** Village (Center)

**Purpose:** Forms part of the outer village border and creates an additional entrance or exit.

**Direction:** These structures have no direct gameplay function and may be redesigned or replaced. Preserve their spatial purpose by using them to create a complete village edge and a clear secondary gateway.

### 18. Filler Structure 4

**Area:** Village (Center)

**Purpose:** Completes the village streetscape and prevents the surrounding area from feeling empty or unfinished.

**Direction:** These structures are fully flexible. They may be changed, removed, or expanded to support the updated layout, provided the final area remains cohesive and visually complete.

### 19. The Library

**Area:** Combat Settlement

**Purpose:** Allows players to enchant and upgrade items. It also houses a merchant who sells enchantments.

**Direction:** Place the Library inside the Combat Settlement and develop it together with the Armory. Both structures should share a coherent architectural language, scale, palette, and surrounding environment while remaining visually distinct. How much of the current Library is retained is still open.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 20 | Librarian | Interior | Opens the Librarian shop. | `loc-village-librarian` |

### 20. The Armory

**Area:** Combat Settlement

**Purpose:** Allows players to purchase armor and weapons.

**Direction:** Place the Armory inside the Combat Settlement. The current structure is not approved and should be redesigned. Its new design must complement the Library so both buildings make the Combat Settlement feel intentionally planned and visually unified.

### 21. The Blacksmith

**Area:** Mining District

**Purpose:** Serves as the dedicated blacksmith structure within the Mining District.

**Direction:** Rebuild this structure from scratch. The current version does not match the required style. The replacement should clearly read as a working forge and feel naturally connected to the Mining District.

### 22. Town Hall

**Area:** Village (Center)

**Purpose:** Acts as the village's main progression and information building. Players can upgrade their personal account or island, spend Gems in the Gem Shop, learn more about Skyblock through the Wiki NPC, and access the online store through the Store NPC.

**Direction:** The Town Hall should feel like one of the most important civic buildings in the village. Provide enough interior space for its different services and organize them into clear, easy-to-find areas, with upgrades treated as the primary feature. The exact internal layout is still open.

#### NPCs

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 21 | Darianne | Main Desk | Introduces the Town Hall, guides players through their first Storage Slots upgrade, and opens Player Upgrades. | `loc-village-stewards-desk` |
| 22 | Milesto | Interior | Opens the Achievements menu and explains milestone tracking. | `loc-village-achievements` |
| 23 | Biblio | Interior | Opens the Skyblock Wiki and directs players toward other helpful villagers. | `loc-village-wiki` |
| 24 | Salesman | Interior | Provides access to the Webstore. | `loc-village-salesman` |

## NPCs Without a Numbered Structure

These NPCs belong to a Spawn area but are not currently assigned to one of the numbered structures. They may be placed in smaller stalls, outdoor workspaces, paths, squares, or natural scenes that suit their purpose.

### Village (Center)

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 25 | Hue Merchant | Village | Opens the Hue Merchant shop. | `loc-village-hue-merchant` |
| 26 | Kael's Navigator | Arrival Point | Opens the Server Selector menu. | `loc-village-server-selector` |
| 27 | Elric | Around the Village | Explains Minions, tiers, placement limits, fuel, skins, and storage. | `loc-village-villager-elric` |
| 28 | Faye | Around the Village | Explains the Quest Log, active objectives, progress, and rewards. | `loc-village-villager-faye` |
| 29 | Fenwick | Central Square | Welcomes new players and acts as a central village guide. | `loc-village-villager-fenwick` |
| 30 | Jacob | Around the Village | Explains remote crafting, the Recipe Book, and recipe unlocks. | `loc-village-villager-jacob` |
| 31 | Luna | Around the Village | Explains Collections and the rewards unlocked by gathering resources. | `loc-village-villager-luna` |
| 32 | Merron | Around the Village | Explains island teams, shared progress, and cooperative play. | `loc-village-villager-merron` |
| 33 | Nilo | Around the Village | Explains Player Level, Island Level, and how their experience is earned. | `loc-village-villager-nilo` |
| 34 | Quill | Around the Village | Purpose not yet defined. | `loc-village-villager-quill` |
| 35 | Ravi | Around the Village | Explains direct player trading, trade offers, and safe trading. | `loc-village-villager-ravi` |
| 36 | Simon | Around the Village | Directs players toward the Farm, Mining District, Forest, and other resource areas. | `loc-village-villager-simon` |
| 37 | Taren | Around the Village | Explains personal Storage, Backpacks, storage slots, and how to unlock more space. | `loc-village-villager-taren` |

### Mining District

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 38 | Mine Merchant | Mining District | Opens the Mine Merchant shop. | `loc-village-mine-merchant` |
| 39 | Redstone Merchant | Mining District | Opens the Redstone Merchant shop. | `loc-village-redstone-merchant` |
| 40 | Tobin | Mining District | Opens the Stockkeeper shop, which includes coal for Minion fuel. | `loc-village-stockkeeper` |

### The Forest

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 41 | Flora Specialist | The Forest | Opens the Flora Specialist shop. | `loc-village-flora-specialist` |
| 42 | Nibs | The Forest | Sells one Eldergrove Travel Scroll per player. | `loc-village-nibs` |

### Farm

| # | Name | Location | Notes | NPC ID |
|---:|------|----------|-------|--------|
| 43 | Wesley | Farm | Is planned to introduce players to Minions. | `loc-village-farmhand` |
