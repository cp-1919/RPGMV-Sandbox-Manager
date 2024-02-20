# Principle
## Copy event
First of all, you should set the Mapid which contains the event templates.(You should set them in plugin)

Then, dirctly call functions in PocketEvent:

`PKD_EPManager.Scene().pSpawnEPEvent(evId, x, y)`

It will return an Event Object. If you need to control the event, store it

## Control event
Firstly, you should get the Event Object.Here are two ways
>1. Create by PocketEvent:
>   `const ev = PKD_EPManager.Scene().pSpawnEPEvent(evId, x, y)`
>
>3. Get by eventId
>   `const ev = $gameMap._events[eventId]`

1. Move the event
```
// directly transfer to (x,y)
ev._realX = x
ev._realY = y

// movevto (x,y)
ev._x = x
ev._y = y
```

## Change Map tiles
Different from traditional plugins, mz3d rewrited all the classes for blending the map. If you want to change the specific tile, you need to do following things:
```
//1.change the tile
$dataMap.data[pos] = tileId
//2.refresh
mz3d.reloadMap()
```
You do not need to change other datas, because mz3d only get the mapData from $dataMap.(that means you do not need to rewrite Game_Map.prototype)
