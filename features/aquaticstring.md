---
description: >-
  Using AquaticString you can format messages with minimessage & legacy
  formatting with ease
---

# AquaticString

## How it works?

After Initializing AquaticLib, the lib itself automatically detects what server software are you using.\
Of course Minimessage is not supported on Spigot servers, however this features has been mainly created to be able to SELL plugins on SpigotMC website. To be able to sell a plugin on SpigotMC, your plugin must be fully functional on Spigot servers.

However another reason of this is that not all of the customers want to use Minimessage, so legacy formatting is still an option.

You can also change the formatting manually in the code using:

```kotlin
AbstractAquaticSeriesLib.INSTANCE.AbstractAquaticSeriesLib(Format.LEGACY)
```



## Usage

### Converting

To format is String or Collection of String you can simply do:

```kotlin
val aquaticString = "yourString".toAquatic()
val aquaticList = listOf("your","string").toAquatic()
```

### Replacing

```kotlin
val aquaticString = "yourString".toAquatic()
val player: Player = ...
aquaticString.replace("%player%", player.name)
```

### Sending messages

```kotlin
val aquaticString: AquaticString = ...
val player: Player = ...
aquaticString.send(player)
aquaticString.broadcast()
```

### Actionbar

```kotlin
val aquaticString: AquaticString = ...
val player: Player = ...

aquaticString.sendActionBar(player)
```

### Entity display name

```kotlin
val aquaticString: AquaticString = ...
val entity: Entity = ...

aquaticString.setEntityName(entity)
```

### Creating Inventory

```kotlin
val aquaticString: AquaticString = ...
val invSize: Int = 9
val invType: InventoryType = InventoryType.CHEST

AbstractAquaticSeriesLib.INSTANCE.adapter.inventoryAdapter.create(
    aquaticString,
    YOUR_INVENTORY_HOLDER,
    invSize
)

AbstractAquaticSeriesLib.INSTANCE.adapter.inventoryAdapter.create(
    aquaticString,
    YOUR_INVENTORY_HOLDER,
    invType
)
```

### Creating & Showing BossBar

<pre class="language-kotlin"><code class="lang-kotlin">val aquaticString: AquaticString = ...
val color: AquaticBossBar.Color = AquaticBossBar.Color.WHITE
val style: AquaticBossBar.Style = AquaticBossBar.Style.SOLID
val progress: Double = 1.0 // 1 = 100%
val player: Player = ...

<strong>val bossbar: AquaticBossBar = AbstractAquaticSeriesLib.INSTANCE.adapter.bossBarAdapter.create(
</strong>    aquaticString,
    color,
    style,
    progress
)

bossbar.addPlayer(player)
bossbar.removePlayer(player)
</code></pre>

### ItemStack Displayname & Lore

```kotlin
val itemstack: ItemStack = ...
val itemmeta: ItemMeta = itemstack.itemMeta ?: return

val newName: AquaticString = ...
val newLore: List<AquaticString> = ...

itemstack.displayName(newName)
itemstack.lore(newLore)
val itemstackName: AquaticString = 
    AbstractAquaticSeriesLib.INSTANCE.adapter.itemStackAdapter.getAquaticDisplayName(itemstack)
val itemstackLore: List<AquaticString> = 
    AbstractAquaticSeriesLib.INSTANCE.adapter.itemStackAdapter.getAquaticLore(itemstack)

itemmeta.displayName(newName)
itemmeta.lore(newLore)
val itemmetaName: AquaticString = 
    AbstractAquaticSeriesLib.INSTANCE.adapter.itemStackAdapter.getAquaticDisplayName(itemmeta)
val itemmetaLore: List<AquaticString> = 
    AbstractAquaticSeriesLib.INSTANCE.adapter.itemStackAdapter.getAquaticLore(itemmeta)
```

### Title

```kotlin
val title: AquaticString = ...
val subTitle: AquaticString = ...
val fadeIn: Int = ...
val stay: Int = ...
val fadeOut: Int = ...
val player: Player = ...

AbstractAquaticSeriesLib.INSTANCE.adapter.titleAdapter.send(
    player,
    title,
    subTitle,
    fadeIn,
    stay,
    fadeOut
)
```
