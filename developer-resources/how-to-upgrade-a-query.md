# How to upgrade a query
A little guide of a small query getting upgraded to a big one using different commands/properties 
```
{
  planets {
    id
  }
}
```
Query that show planets ordered by their id (the subgraph doesn't show you all the data if you are asking for a big chunk of data, that's why there only appear some planets and not all of them)
```
{
  planets(where:{planetType:RUINS}) {
    id
  }
}
```
Query that shows planets that are foundries (RUINS=Foundries) ordered by their id
```
{
  planets(where:{planetType:RUINS}) {
    id
    planetLevel
  }
}
```
Query that shows planets that are foundries with their respective level (ordered by their id...)
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8}) {
    id
    planetLevel
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 with their respective level (ordered by their id...)
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8}) {
    id
    planetLevel
    owner {
      id
    }
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 with their respective level and the owner of each foundry
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8}) {
    id
    planetLevel
    owner {
      id
    }
    x
    y
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 with their respective level, owner and coords (Coords only will be shown if the planet has been broadcasted by someone)
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8}) {
    id
    planetLevel
    owner {
      id
    }
    x
    y
    spaceType
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 with their respective level, owner, coords and type of space
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8}, orderBy:planetLevel) {
    id
    planetLevel
    owner {
      id
    }
    x
    y
    spaceType
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 ordered by their level with their respective level, owner, coords and type of space
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8, owner:"0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9"}, orderBy:planetLevel) {
    id
    planetLevel
    owner {
      id
    }
    x
    y
    spaceType
  }
}
```
Query that shows planets that are foundries greater or equal to level 8 owned by "0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9" ordered by their level with their respective level, owner, coords and type of space
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8, owner:"0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9"}, orderBy:planetLevel, first:100) {
    id
    planetLevel
    owner {
      id
     }
     x
     y
     spaceType
   }
 }
 ```

Query that shows the first 100 planets that are foundries greater or equal to level 8 owned by "0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9" ordered by their level with their respective level, owner, coords and type of space
```
{
  planets(where:{planetType:RUINS, planetLevel_gte:8, owner:"0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9"}, orderBy:planetLevel, first:100, skip:100){
    id
    planetLevel
    owner {
      id
     }
     x
     y
     spaceType
   }
 }
```
Query that shows the planets in the range 101-201 that are foundries greater or equal to level 8 owned by "0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9" ordered by their level with their respective level, owner, coords and type of space
