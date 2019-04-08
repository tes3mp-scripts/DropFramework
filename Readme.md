A set of simple tools to spawn random loot.

Requires [DataManager](https://github.com/tes3mp-scripts/DataManager)!

The script operates with three types of entities: "drops" - a random count of the specified item to be spawned, "roll" - a collection of drops to choose one (or none) from at random, "stock" - a collection of rolls to generate an inventory at random.

`example.lua` shows how to use it (also makes use of [ContainerFramework](https://github.com/tes3mp-scripts/ContainerFramework))

Functions to operate drops:
=====
* `DoorFramework.createDrop(` creates an item drop record to be added to an item roll/  
  `item,` a table with `refId`, `charge`, `enchantmentCharge` and `soul` of the item. All but `refId` are optional.  
  `min,` minimal possible count of `item`  
  `max,` amximal possible count of `item`  
  `distribution` distribution to be used when taking count at random. 'uniform' by default.  
  `)`
  returns `dropId`
* `DropFramework.getDrop(dropId)`
  returns the drop record: (distribution and some fields of `item` could be `nil`)
  ```
  {
    item = item,
    min = min,
    max = max,
    distribution = distribution
  }
  ```
* `DropFramework.removeDrop(dropId)` removes the given drop from DropFramework's data

Functions to operate drops:
=====
* `DropFramework.addDrop(name, dropId)` creates a single-drop roll to stock with `name`
* `DropFramework.addRoll(` adds a roll with specified drops and their chances of being selected (if the sum of chances is `>=1` it's guaranteed not to select nothing)  
  `name,` of the stock to add this roll to  
  `drops,` list of `dropId`s  
  `chances` list of values between `0` and `1`  
  `)`

Functions to operate stocks:
=====
* `DropFramework.addStock(name)` creates an empty stock with `name`
* `DropFramework.removeStock(name)` removes the stock with `name`
* `DropFramework.resolveStock(name)` returns a randomly generated inventory dictated by stock with `name`