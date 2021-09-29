# Subgraph tutorial

[The Graph](https://thegraph.com/docs/about/introduction) is a decentralized protocol for indexing and querying data from blockchains. It makes it possible to query data that is difficult to query directly from the smart contract itself.

For Dark Forest the subgraph acts almost as a read only excel spreadsheet client to the game where you can query for any information that is public in the smart contract.

You might want to familiarize yourself with the [df wikis more technical explanation](https://dfwiki.net/wiki/Technical_Explanations) of how the game works in order to understand lazy state and what is actually stored in the blockchain.

Like the contract, the subgraph doesn’t know any map data and can’t tell you anything about (x, y) coordinates. Also, like the contract, the subgraph only knows about planets have been interacted with at least once. However UNLIKE the contract, the subgraph DOES apply voyage arrivals as they occur, and therefore has all the most recent ownership data!

## How to query

The query language is called graphql and can take some getting used to. Thegraph explorer has a nice right column that allows you to investigate the schema to see what columns and fields are available.

A little guide of a small query getting upgraded to a big one using different commands/properties. This query will show you all the planet ids (well the first 100 by default) that the contract knows about.

```bash
{
  planets {
    id
  }
}
```

Query that shows planets that are foundries (RUINS=Foundries) ordered by their id

```bash

{
  planets(where:{planetType:RUINS}) {
    id
  }
}
```

Query that shows planets that are foundries with their respective level (ordered by their id...)

```bash

{
  planets(where:{planetType:RUINS}) {
    id
    planetLevel
  }
}
```

Query that shows planets that are foundries greater or equal to level 8 with their respective level (ordered by their id...)

```bash

{
  planets(where:{planetType:RUINS, planetLevel_gte:8}) {
    id
    planetLevel
  }
}
```

Query that shows planets that are foundries greater or equal to level 8 with their respective level and the owners id of each foundry

```bash

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

Query that shows planets that are foundries greater or equal to level 8 with their respective level, owner and coords (Coords only will be shown if the planet has been broadcasted by someone)

```bash

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

Query that shows planets that are foundries greater or equal to level 8 with their respective level, owner, coords and type of space

```bash
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

Query that shows planets that are foundries greater or equal to level 8 ordered by their level with their respective level, owner, coords and type of space

```bash
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

Query that shows planets that are foundries greater or equal to level 8 owned by "0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9" ordered by their level with their respective level, owner, coords and type of space

```bash
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

Query that shows the first 10 planets that are foundries greater or equal to level 8 owned by "0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9" ordered by their level with their respective level, owner, coords and type of space

```bash
{
  planets(where:{planetType:RUINS, planetLevel_gte:8, owner:"0xb5ce86c2ab9e2403ab47acfbe501845e2480fad9"}, orderBy:planetLevel, first:10) {
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

```bash
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

## Troubleshooting

### lower case

All ids like are lower case like 0x0f45aba574aceba2e0717ca86e910211b34f9db9. Sadly blockscout and metamask can occasionally mix case in ids like 0x0f45aBA574AcEbA2E0717Ca86e910211b34f9db9!

So for example this might return data:

```bash
{
  players(where: {id: "0x0f45aba574aceba2e0717ca86e910211b34f9db9"}) {
      id
  }
}
```

But this won't:

```bash
{
  players(where: {id: "0x0f45aBA574AcEbA2E0717Ca86e910211b34f9db9"}) {
      id
  }
}
```

Theres online [case converters](https://search.brave.com/search?q=tolowercase+online&source=web) that can help if you find yourself in this predicimant

### Leading 0x and padding

User ids (which are actually ethereum wallet addresses) are always shown with a leading 0x  and are zero paddded to 42 characters (0x0f45aba574aceba2e0717ca86e910211b34f9db9) . However planet locationId (00000000004896511cb246d2e6dfcde2dccc1b3855fcf69b53e046b09a929953) do NOT use a 0x in front and are 0 padded to 64 characters.
