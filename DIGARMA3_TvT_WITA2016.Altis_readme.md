# Where is the Agent? (WIP)

# Config

##  cfgMission

Attribute                   | Explanation
----------------------------|---------------------------------------------------------------------------------------------------------
scoreboardDurationCurrent   | How long will the scoreboard for the current game be displayed on mission end?
scoreboardDurationAlltime   | How long will the all time scoreboard be displayed on mission end?
scoreboardSaveTag           | The tag that the statistics are saved under on the server.
pointsForCivKill            | Points added to agent when he or his bodyguards kill a civilian.
pointsForBluKill            | Points added to agent when he or his bodyguards kill a BLUFOR player.
locationDistance            | How far away from a location will INDEP spawn? (minimum, maximum)
heliDistance                | How far away from INDEP start position will the crashed helicopter spawn? (minimum, maximum)
locationTypeWeight          | How likely is it, that INDEP will start near this location type. (number 0-1, sum does not have to be 1)
bluforSpawnDistanceVariance | How much does BLUFOR spawn distance to INDEP vary?
bluforBaseAreaSize          | Radius around BLUFOR start position that is considered part of their base.
bluforSpawnDistances        | How far away from INDEP does BLUFOR start? Values correspond with (close,normal,far) mission parameters.
bluforMoneyStartFactor      | Factor for amount of BLUFOR starting money. Higher means more.
bluforMoneyGainFactor       | Factor for amount money BLUFOR gains over time. Higher means more.
bluforVehicleUnlockTime2    | Time before BLUFOR gets access to level 2 vehicles.
bluforVehicleUnlockTime3    | Time before BLUFOR gets access to level 3 vehicles.
timeBeforeFirstTrack        | How long before agents are tracked for the first time?
agentMarkerInterval         | How often will agents be tracked? (minimum, maximum)
agentMarkerVariance         | How inaccurate will agent markers be?
agentMarkerFadeout          | How long will agent markers be visible?
agentMarkerIntervalBase     | How often will agents be tracked if they are inside BLUFOR's base area?
agentMarkerVarianceBase     | How inaccurate will their markers be while inside BLUFOR's base area?
agentMarkerFadeoutBase      | How long will their markers be visible while inside BLUFOR's base area?
indepStartVehicles          | Classnames of all starting vehicles for INDEP. Picked at random.
cacheAmountFactor           | Factor for amount of caches. Higher means more.
cacheMinDist                | Minimum distance that caches have to have to each other.
cacheIndepStartDist         | Minimum distance to INDEP start position that caches have to have.
cacheMarkerVarianceIndep    | How inaccurate will cache markers be for INDEP?
cacheMarkerVarianceBlufor   | How inaccurate will cache markers be for BLUFOR?

### civVehicles

Attribute               | Explanation
------------------------|-----------------------------------------------------------------------------------------------
randomFuel              | Random amount of fuel in all empty civilian vehicles. (0-1), (minimum, maximum)
carLocationAmountFactor | Factor for car amount in locations. Higher means more.
carLocationMinDist      | Minimum distance that cars in locations have to have to each other.
carRoadAmountFactor     | Factor for car amount outside of locations. Higher means more.
carRoadMinDist          | Minimum distance that cars outside of locations have to have to each other.
carType                 | Classnames of all civilian cars that can spawn.
heliAirportAmountFactor | Factor for helicopter amount on airports. Higher means more.
heliFuelFixValue        | What min. value does the fuel of an Air type vehicle get set to, when an INDEP player gets in?
heliTypes               | Classnames of all helicopters that can spawn.
boatCoastAmountFactor   | Factor for boat amount on the coast. Higher means more.
boatTypes               | Classnames of all boats that can spawn.

## cfgCaches
Caches with absolute amounts of items by category (see `cfgCacheContents`). It has all the attributes of `cfgCacheContents` and some additional ones:

Attribute            | Explanation
---------------------|------------------------------------------------------------------------------------------
probability          | Probability for any spawned cache to be this one. (number 0-1)
magazinesPerRifle    | Amount of magazines for each rifle in this cache.
magazinesPerHandgun  | Amount of magazines for each handgun in this cache.
magazinesPerLauncher | Amount of rockets for each launcher in this cache.
cacheStores          | Array of all stories that can spawn with this cache. If empty, all stories are available.
cacheContainers      | Classnames off all containers that this cache can be.

## cfgCacheContents
Classnames of all things that can spawn in caches. Categorized.

Attribute       | Explanation
----------------|--------------------------------------------------
riflesWest      | Rifles that can take western optics.
riflesEast      | Rifles that can take eastern optics.
snipersWest     | Sniper rifles that can take western optics.
snipersEast     | Sniper rifles that can take eastern optics.
handguns        | Handguns.
launchersWest   | Western launchers.
launchersEast   | Eastern launchers.
accessoriesWest | Accessories that fit on western rifles.
accessoriesEast | Accessories that fit on eastern rifles.
sightsWest      | Non-magnifying sights that fit on western rifles.
sightsEast      | Non-magnifying sights that fit on eastern rifles.
scopesWest      | Magnifying scopes that fit on western rifles.
scopesEast      | Magnifying scopes that fir on eastern rifles.
sniperScopesWest| Sniper scopes that fit on western snipers.
sniperScopesEast| Sniper scopes that fit on eastern snipers.
grenades        | Grenades.
items           | Inventory items except for medical equipment.
medical         | Medical items.
backpacks       | Backpacks.

## cfgCacheStories
Config for story objects that get placed near a cache.

Attibute | Explanation
---------|--------------------------------------------------------------------------
size     | Radius in m around story position that has to be empty for this to spawn.
onRoad   | Does this have to be on a road?
onCoast  | Does this have to be on the coast?
script   | The script to execute to spawn this story. Passed parameters are center of story and direction.

# Creating Cache Stories
There is an export script available for you to create stories with. In multiplayer it will only work if you are the host.

Go to the salt desert Almyra on Altis. Your player position is the center position of the cache. Use Zeus to place story objects around you. Once you are done, open the debug console and execute `[] execVM "exportStory.sqf"`. Now go to the `cacheStories` folder, create a new file and name it after your story (e.g. `myCoolStory.sqf`). Paste your clipboard into that file and save. Open `cfgCacheStories.hpp` and create a new story that uses your newly created script. For example:

```sqf
class myCoolStory {
    size = 20;
    onRoad = 0;
    onCoast = 0;
    script = "cacheStories\myCoolStory.sqf";
};
```

Now add that story to any cache in `cfgCaches.hpp` that you want to use it for. For example:

```sqf
class myCoolCache {
    //OTHER ATTRIBUTES OMITTED

    cacheStories[] = {
        "someOtherStory",
        "yetAnotherStory",
        "myCoolStory"
    };
};
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)