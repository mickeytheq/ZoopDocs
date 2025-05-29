# Card quantity

When exporting, Zoop has functionality to generate the correct quantity of cards based on default logic and user inputs.

The card quantity behaviour is slightly different betweeen TTS and Print and Play

## TTS

Only one copy of each card is generated except when the [Encounter set unrolling](../encountersetunrolling/EncounterSetUnrolling.md) capability is used. Multiple copies of encounter cards are often desired when assembling the encounter deck for a scenario.

For player cards, typically homebrew authors only want a single copy of each card. Often an investigator project will splay the player cards for easy viewing by a player. But only one copy of each card is needed as it is trivial for the player to copy the necessary number of cards when building their deck. As this varies by the deck being built there is no sensible default number of cards.

## Print and play

Print and play has much stricter requirements on individual card quantity. Because the desire is to have a full set of cards to play in person generating the correct quantity of cards is important.

Zoop implementes the following logic to generate card quantity.

- If the card is identified as an investigator signature, 1 copy is created
- If the card has the exceptional keyword, 1 copy is created
- If the card has Limit X per deck keyword, X copies are created
- If the card has the myriad keyword, 3 copies are created
- If the card has encounter set numbering then [Encounter set unrolling](../encountersetunrolling/EncounterSetUnrolling.md) is used
- If the card is an Asset, Event or Skill, 2 copies are created
- Otherwise 1 copy is created

If multiple of these are true then the highest in the list above will be used.

In addition the [Quantity instruction](../instructions/Instructions.md#instruction---quantity) can be used to override the above defaults. For example if you were trying to create an investigator with 3 copies of their signature, like Stella, then you would use the Quantity instruction to override the default of 1 to 3.
