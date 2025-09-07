# Instructions

* TOC
{:toc}

Zoop supports embedding instructions on cards. These instructions will drive behaviour during Zoop processes.

Each instruction is a single line in the **comments** field of the card. An instruction always starts with `#ZOOP#` to identify it to Zoop as a specific instruction. Immediately after the second # you specify the name of the instruction and any parameters for that instruction. Each instruction and its parameters are documented below.

**Note:** In previous versions of Zoop `#TTSZ#' was the prefix used to identify a zoop instruction. This is still supported but considered legacy.

Parameter values are enclosed in double quotes. If you need a genuine double quote in a parameter value, put two double quotes instead of one. For example

`#ZOOP#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="""Booo"" to a goose",CopyCardFace="Back")`

Instructions and their parameters are case sensitive.

Each instruction can only appear once on each card, unless specifically mentioned against the instruction documentation below.

## Which Zoop utilities use instructions?

The following utilities use/obey these instructions

- TTS export
- Print and Play export
- Card database export
- Automatic numbering

The following utilities ignore all instructions

- Bulk update
- Export and import

The latter group ignore instructions as these utilities are designed to operate on 'raw' cards before any instruction manipulation. Whereas the former group are concerned with how cards will be presented in their final state. For example it is expected that the `Exclude` instruction would allow filtering out of cards during exports for play purposes and collection numbering. However when interacting with the raw card details that would be undesirable.

## Instruction - Replace card face

This allows you to have Zoop replace a card face on a card with a face from a different card. This can be useful for locations that have a common card back or when SEs available options for double sided cards don’t meet your needs.

Multiple instances of this instruction per card are supported.

Instruction key: ReplaceCardFace
Parameters:

| Parameter key | Details |
| --- | --- |
| ReplaceFace | The card face you want to replace. Must be either “Front” or “Back” |
| CopyCardTitle | The title of the front face of the card you want to copy from. Must match a single card in the scope of that run of Zoop. Specify exactly one of this or CopyCardFilename, not both |
| CopyCardFilename | The filename of the card you want to copy from (without the .eon extension). Must match a single card in the scope of that run of Zoop. Specify exactly one of this or CopyCardTitle, not both |
| CopyCardFace | The face of the card you want to copy. Must be either “Front” or “Back” |

### Example

The following example will replace the back face of the current card with the back face of the card titled “Shared Back”

`#ZOOP#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="Shared Back",CopyCardFace="Back")`
 
## Instruction - Swap card faces

This instruction swaps the front and back of the card faces. Primarily useful when Strange Eons supports the combination of front/back you want, e.g. Story and Location, but you want the front to be the back and vice versa.

Instruction key: SwapCardFaces

Parameters: None

### Example

The following example will swap the faces

`#ZOOP#SwapCardFaces`
 
## Instruction - Override a card's image

This allows you to have Zoop completely replace a card faces output image with a custom one from your computer. The normal Strange Eons image is completely replaced.

Multiple instances of this instruction per card are supported.

Instruction key: OverrideCardFaceImage

Parameters:

| Parameter key | Details |
| --- | --- |
| ReplaceFace | The card face you want to replace. Must be either “Front” or “Back” |
| OverrideImagePath | Relative path from this card to the image file you want to use instead |

### Example

The following example will replace the output image of the front face of the current card with the specified file.

`#ZOOP#OverrideCardFaceImage(ReplaceFace="Front",OverrideImagePath="UseThisInstead.jpg")`


## Instruction - Exclude

This allows you to have Zoop exclude the card from the export process. This can be useful if the card is a work in progress or is used as part of a card such as the source of the ReplaceCardFace instruction.

Instruction key: Exclude

Parameters: None

### Example

The following example will exclude the card

`#ZOOP#Exclude`

## Instruction - Quantity

This allows you to specify how many copies of a card should be produced by Zoop. This is used by the export functions and automatic numbering.

Note that Zoop has default behaviour for card quantity that will be correct most of the time but on occasion an override is necessary. For example signature cards default to 1 copy but sometimes, e.g. Stella, you may want more than 1.

This instruction is **ignored by TTS exports**. See [Card quantity](../cardquantity/CardQuantity.md) for details on why this is.

Instruction key: Quantity

Parameters:

| Parameter key | Details |
| --- | --- |
| Quantity | Desired number of copies of the card |

### Example

The following example will product 3 copies of the card rather than the default.

`#ZOOP#Quantity(Quantity="3")`

## Instruction – TTS Card Options

This allows you to override specific properties of the resulting TTS card. Zoop has default logic which this instruction allows you to override. This is a more technical instruction that requires knowledge of how TTS manages card objects.

**Applies to TTS exports only**

Instruction key: TtsCardOptions

Parameters:

| Parameter key	| Details |
| --- | --- |
| SidewaysCard | Whether the card should be created with the TTS sideways flag. By default Zoop creates cards with this set to false. Must be “true” or “false”. |

### Example

The following example will set the TTS sideways flag of the card to true.

`#ZOOP#TtsCardOptions(SidewaysCard="true")`

## Instruction – Link investigator mini card

This allows you to link an investigator mini card to its corresponding investigator card. This allows Zoop to generate the correct ‘linked’ ids for the SCED mod functionality.
This instruction is only valid on investigator mini cards. If this instruction is used on any other card type an error will be reported.

Instruction key: InvestigatorMiniCardFor

Parameters:

| Parameter key | Details |
| --- | --- |
| InvestigatorCardTitle | The title of the front face of the card you want to link to. Must match a single card in the scope of that run of Zoop |
| InvestigatorCardFilename | The filename of the card you want to link to (without the .eon extension). Must match a single card in the scope of that run of Zoop |

### Example

`#ZOOP#InvestigatorMiniCardFor(InvestigatorCardTitle="My Custom Investigator")`

## Instruction – Link signatures to investigator

This allows you to link signatures (including weaknesses) to their corresponding investigator card. Zoop uses this in the automated collection numbering to group signatures with the investigator.

Multiple instances of this instruction are supported to link the same signature card to multiple investigators.

Instruction key: InvestigatorSignatureFor

Parameters:

| Parameter key |	Details |
| --- | --- |
| InvestigatorCardTitle | The title of the front face of the card you want to link to. Must match a single card in the scope of that run of Zoop |
| InvestigatorCardFilename | The filename of the card you want to link to (without the .eon extension). Must match a single card in the scope of that run of Zoop |

### Example

`#ZOOP#InvestigatorSignatureFor(InvestigatorCardTitle="My Custom Investigator")`

## Instruction - Deckbuilding options

This allows you to specify the deckbuilding options on a card.

Multiple instances of this instruction are supported to create combined deckbuilding options.

Its typical usage is on an investigator card to specify the deckbuilding. You can, and generally will need to, specify multiple instances of this instruction on a each investigator.

If you have an deckbuilding that is not supported then the workaround is to specify a single DeckbuildingOption with all classes listed and levels 0 to 5. This will allow all cards to be available and the player will have to self-manage following the deck-building rules.

It is also supported on player cards for the rare cases that a player card alters the deckbuilding of the owning deck when added. For example Versatile.

Deckbuilding options are evaluated by card databases such as ArkhamDB and arkham.build in **top to bottom order** for each card. This is typically relevant for options that exclude cards, such as Preston. In Preston's case the 'no firearms' option must be first so that all firearms match it and are excluded, instead of matching the rogue 0-5 option which is further down the list.

Instruction key: DeckbuildingOption

Parameters:

| Parameter key |	Details |
| --- | --- |
| Classes | A comma delimited list of card classes. Valid options are Guardian, Rogue, Mystic, Seeker, Suvivor and Neutral |
| MinimumLevel | The minimum inclusive level permitted |
| MaximumLevel | The maximum inclusive level permitted |
| CardCountLimit | Tha maximum number of cards of this condition permitted |
| Traits | A comma delimited list of traits. All traits begin with a capital letter |
| CardTypes | A comma delimited list of card types. Valid options are Asset, Event and Skill |
| TextExact | A string that if it appears on a card (case-insensitive), that card will be available for deckbuilding. Multiple instances of this parameter can be specified and will be treat as an 'or' list |
| TextRegex | A regular expression that if it matches on a card, that card will be available for deckbuilding. Multiple instances of this parameter can be specified and will be treat as an 'or' list |
| Permanent | Must be "true" or "false". Specifies whether cards with(out) the permanent keyword are permitted |
| FactionSelect | A comma delimited list of card classes. Valid options are Guardian, Rogue, Mystic, Seeker, Suvivor and Neutral. This will create a faction selection option when decks are created in downstream systems like arkham.build |
| Name | A name for the deckbuilding option. Mandatory when FactionSelect is specified |
| Exclude | Must be "true" or "false". If true then the rules defined by this option are an exclusion |

### Examples

Some example of official investigators/cards below

**Roland Banks**

Straight-forward classes and levels

`#ZOOP#DeckbuildingOption(Classes="Guardian,Neutral",MinimumLevel="0",MaximumLevel="5")`
`#ZOOP#DeckbuildingOption(Classes="Seeker",MinimumLevel="0",MaximumLevel="2")`

**Zoe Samaras**

Example of a limited number of cards from level 0

`#ZOOP#DeckbuildingOption(Classes="Guardian,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Preston Fairmont**

Exclusion example

Note that in this case the exclusions MUST come first in the list. Anything before an Exclude=True instruction will be treated as an 'unless'.

`#ZOOP#DeckbuildingOption(Exclude="true",Traits="Illicit")`
`#ZOOP#DeckbuildingOption(Classes="Rogue,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Classes="Survivor",MinimumLevel=0,MaximumLevel=2)`

**Rex Murphy (parallel)**

Example of excluding cards with exceptions.

Note the order is important. Everything after the Exclude option is the base deckbuilding. Then the Exclude is layered on top to remove certain cards from the pool. Then any options above the Exclude are applied to re-add certain cards to the pool.

`#ZOOP#DeckbuildingOption(Classes="Neutral",Traits="Cursed",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Traits="Cursed",MinimumLevel=0,MaximumLevel=4)`
`#ZOOP#DeckbuildingOption(Exclude="true",Traits="Fortune,Blessed")`
`#ZOOP#DeckbuildingOption(Classes="Seeker",MinimumLevel=0,MaximumLevel=3)`
`#ZOOP#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Traits="Gambit",MinimumLevel=0,MaximumLevel=4)`
`#ZOOP#DeckbuildingOption(Traits="Rogue",MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Amanda Sharpe**

Trait + card type example

`#ZOOP#DeckbuildingOption(Classes="Seeker,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Traits="Practiced",CardTypes="Skill",MinimumLevel=0,MaximumLevel=3)`

**Finn Edwards**

Mix of traits, levels and classes

`#ZOOP#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=3)`
`#ZOOP#DeckbuildingOption(Traits="Illicit",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Classes="Seeker,Survivor",MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Bob Jenkins**

Weird level zero options

`#ZOOP#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Classes="Survivor",MinimumLevel=0,MaximumLevel=0)`
`#ZOOP#DeckbuildingOption(Classes="Rogue",MinimumLevel=1,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Akachi Onyele**

Regular expression matching

`#ZOOP#DeckbuildingOption(Classes="Mystic,Neutral",MinimumLevel=0,MaximumLevel=5)`\
`#ZOOP#DeckbuildingOption(TextRegex="Uses \(\d+ charges\)",MinimumLevel=0,MaximumLevel=4)`\
`#ZOOP#DeckbuildingOption(Traits="Occult",MinimumLevel=0,MaximumLevel=0)`

**Michael McGlen**

Exact text matching

`#ZOOP#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=3)`
`#ZOOP#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(Traits="Firearm",MinimumLevel=0,MaximumLevel=5)`
`#ZOOP#DeckbuildingOption(TextExact="Firearm",MinimumLevel=0,MaximumLevel=5)`

**Tony Morgan**

Secondary class (the below line wrapping is a documentation artifact. Zoop instructions must be on a a single line)

`#ZOOP#DeckbuildingOption(Classes="Rogue,Neutral",MinimumLevel=0,MaximumLevel=5)`\
`#ZOOP#DeckbuildingOption(Name="Secondary Class",FactionSelect="Guardian,Seeker,Survivor",`<br>`MinimumLevel=0,MaximumLevel=1,CardCountLimit=10,CardTypes="Event,Skill")`

**Versatile**

A card altering deck-building

`#ZOOP#DeckbuildingOption(MinimumLevel=0,MaximumLevel=0,CardCountLimit=1)`

## Instruction - DeckbuildingRequirements

This allows you to specify the deckbuilding requirements for an investigator. This instruction is only valid on investigator cards.

Instruction key: DeckbuildingRequirements

Parameters:

| Parameter key |	Details |
| --- | --- |
| DeckSize | Number of cards in the deck |

### Example

`#ZOOP#DeckbuildingRequirements(DeckSize=30)`

## Instruction - Override encounter set details

This allows you to override Zoop defaults for an encounter set. See [Encounter Sets](../encounterset/EncounterSet.md) for more information.

You only need to configure this on **one** card in **each** encounter set, not **every** card in each encounter set.

Instruction key: EncounterSet

Parameters:

| Parameter key |	Details |
| --- | --- |
| Name | Override name of the encounter set |

### Example

`#ZOOP#EncounterSet(Name="Chilling Cold")`

## Instruction - Starts in play

Specifies that the card starts in play. May be used by downstream systems to implement appropriate logic.

Instruction key: StartsInPlay

Parameters: None

### Example

`#ZOOP#StartsInPlay`

## Instruction - Starts in hand

Specifies that the card starts in hand. May be used by downstream systems to implement appropriate logic.

Instruction key: StartsInHand

Parameters: None

### Example

`#ZOOP#StartsInHand`

## Instruction – Specify SCED location metadata

This instruction allows overriding some of the default SCED metadata that determines how locations functions. The SCED mod automatically draws lines between connecting locations. You can use this instruction to add/replace a location’s icons and connections and/or force a non-location card to act like a location for connection purposes. See [SCED metadata](../../tts/ScedMetadata.md) for further details on metadata.

Multiple instances of this instruction per card are supported.

**Applies to TTS exports only**

Instruction key: ScedMetadataLocation

| Parameter key	| Details |
| --- | --- |
| CardFace | The card face you want to alter metadata for. Must be either “Front” or “Back”. If you wish to alter both the Front and the Back metadata then use two instructions, one for Front and one for Back |
| ForceLocationType | Must be “true” or “false”. Defaults to “false”. Changes the metadata type of the card to “Location”. Use this if you wish to add icon/connection metadata to a card that is not a Location. |
| Icons	| A pipe (\|) separated string of location symbols. |
| IconsAction	| Must be “Replace” or “Append”. Replace will set the location’s icons to be exactly the value of the Icons parameter. Append will add the value of the Icons parameter to the existing icons. |
| Connections	| A pipe (\|) separated string of location symbols that this card connects to. |
| ConnectionsAction | Must be “Replace” or “Append”. Replace will set the location’s connections to be exactly the value of the Connections parameter. Append will add the value of the Connections parameter to the existing connections. |

### Example

This example forces a card to act as a location that has a “MadeUp” icon and connects to the Triangle and Square location.

`#ZOOP#ScedMetadataLocation(CardFace="Front",ForceLocationType="true",Icons="MadeUp",IconsAction="Replace",Connections="Triangle,Square",ConnectionsAction="Append")`

This example adds a connection to the location with the “MadeUp” icon, for both the front and back faces of the card.

`#ZOOP#ScedMetadataLocation(CardFace="Front",Connections="MadeUp",ConnectionsAction="Append")`
`#ZOOP#ScedMetadataLocation(CardFace="Back",Connections="MadeUp",ConnectionsAction="Append")`

## Instruction – SCED metadata - extra token

This instruction allows specifying the extraToken metadata used by the SCED mod to spawn additional action tokens for investigators. This instruction is only valid on investigator cards. See [SCED metadata](../../tts/ScedMetadata.md) for further details on metadata.

Multiple instances of this instruction per card are supported.

**Applies to TTS exports only**

Instruction key: ScedMetadataExtraToken

Parameters:

| Parameter key	| Details |
| --- | --- |
| ExtraToken | The string you want to be placed in the extraToken metadata field

### Example

`#ZOOP#ScedMetadataExtraToken(ExtraToken="Fight")`

## Instruction – SCED metadata - uses override

This instruction allows overriding the default **uses** metadata that Zoop generates. By default Zoop will scan the keywords field of the card for a construct such as `Uses (3 ammo).` This instruction allows overriding this logic to add uses metadata to cards that do not have it or override the default metadata generated by Zoop.

Multiple instances of this instruction per card are supported.

**Applies to TTS exports only**

Instruction key: ScedMetadataUses

Parameters:

| Parameter key	| Details |
| --- | --- |
| UsesClass | Where in the metadata to add the uses. Valid values are `Card`, `LocationFront` and `LocationBack`. For example to tokens such as doom/clues/ammo to a treachery or player card uses `Card`. Only use LocationFront/Back when overriding Location cards
| Count | Number of tokens
| PerInvestigator | true or false. Whether the count is per investigator. Defaults to false
| Token | The token to spawn. Consult the SCED metadata documentation for valid values
| Type | The type of token to spawn. Consult the SCED metadata documentation for valid values

### Examples

This example places 3 clues on a card when it enters play

`#ZOOP#ScedMetadataUses(UsesClass="Card", Count=3, Token="Resource", Type="Clue")`

This example overrides the front face of a location to have both clues and doom and the back to have clues.

`#ZOOP#ScedMetadataUses(UsesClass="LocationFront", Count=3, PerInvestigator=true, Token="Resource", Type="Clue")`
`#ZOOP#ScedMetadataUses(UsesClass="LocationFront", Count=2, PerInvestigator=false, Token="Resource", Type="Doom")`
`#ZOOP#ScedMetadataUses(UsesClass="LocationBack", Count=1, PerInvestigator=true, Token="Resource", Type="Clue")`
