# Encounter sets

Encounter sets are defined in Strange Eons in one of two ways

1. In the Preferences of the AHLCG plugin and then picked per card from a drop-down
2. On individual cards as a custom image

The first approach is preferable because

- It gives a first-class name to the encounter set
- The icon is only specified once and therefore any edits are easier to change for the entire set
- On individual cards encounter sets are picked from a list, reducing user error

However the second approach is prevelant in user content as it is easier to find. Zoop handles these in different ways to group cards into encounter sets.

## Encounter set identification

For 1 above identification is straightforward as all cards in the set are linked to the configured encounter set.

For 2 the only available data is a custom image path. Zoop takes the filename of this image (with the extension removed) and uses this to both assign a name to the encounter set and use it as the unique key for grouping.

## When is the encounter set relevant?

The encounter set is relevant when

- Assigning collection numbers - encounter set is an important sorting criteria for cards - see [Automatic numbering](../../automaticnumbering/AutomaticNumbering.md)
- Card database export - encounter set information is exported along with the individual card data - see [Card database export](../../carddatabaseexport/CardDatabaseExport.md)
- When unrolling encounter sets - see [Encounter set unrolling](../encountersetunrolling/EncounterSetUnrolling.md)

## Overriding the encounter set name

When 2 above is used the filename is used to derive the name of the encounter set. This may result in badly/incorrectly named encounter sets.

The recommended way of fixing this is to switch to option 1 above. Alternatively you can override the encounter set name by using an [instruction](../shared/instructions/Instructions.md#instruction---override-encounter-set-details)
