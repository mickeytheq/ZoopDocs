# Instructions

* TOC
{:toc}

Zoop supports embedding instructions on cards. These instructions will drive behaviour during Zoop processes.

Each instruction is a single line in the comments field of the card. An instruction always starts with #TTSZ# to identify it to Zoop as a specific instruction. Immediately after the second # you specify the name of the instruction and any parameters for that instruction. Each instruction and its parameters are documented below.

Parameter values are enclosed in double quotes. If you need a genuine double quote in a parameter value, put two double quotes instead of one. For example

`#TTSZ#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="""Booo"" to a goose",CopyCardFace="Back")`

Instructions and their parameters are case sensitive.

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

`#TTSZ#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="Shared Back",CopyCardFace="Back")`
 
## Instruction - Swap card faces

This instruction swaps the front and back of the card faces. Primarily useful when Strange Eons supports the combination of front/back you want, e.g. Story and Location, but you want the front to be the back and vice versa.

Instruction key: SwapCardFaces

Parameters: None

### Example

The following example will swap the faces

`#TTSZ#SwapCardFaces`
 
## Instruction - Override a card's image

This allows you to have Zoop completely replace a card faces output image with a custom one from your computer. The normal Strange Eons image is completely replaced.

Instruction key: OverrideCardFaceImage
Parameters:

| Parameter key | Details |
| --- | --- |
| ReplaceFace | The card face you want to replace. Must be either “Front” or “Back” |
| OverrideImagePath | Relative path from this card to the image file you want to use instead |

### Example

The following example will replace the output image of the front face of the current card with the specified file.

`#TTSZ#OverrideCardFaceImage(ReplaceFace="Front",OverrideImagePath="UseThisInstead.jpg")`


## Instruction - Exclude

This allows you to have Zoop exclude the card from the export process. This can be useful if the card is a work in progress or is used as part of a card such as the source of the ReplaceCardFace instruction.

Instruction key: Exclude

Parameters: None

### Example

The following example will exclude the card

`#TTSZ#Exclude`

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

`#TTSZ#Quantity(Quantity="3")`

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

`#TTSZ#TtsCardOptions(SidewaysCard="true")`

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

`#TTSZ#InvestigatorMiniCardFor(InvestigatorCardTitle="My Custom Investigator")`

## Instruction – Link signatures to investigator

This allows you to link signatures (including weaknesses) to their corresponding investigator card. Zoop uses this in the automated collection numbering to group signatures with the investigator.

Instruction key: InvestigatorSignatureFor

Parameters:

| Parameter key |	Details |
| --- | --- |
| InvestigatorCardTitle | The title of the front face of the card you want to link to. Must match a single card in the scope of that run of Zoop |
| InvestigatorCardFilename | The filename of the card you want to link to (without the .eon extension). Must match a single card in the scope of that run of Zoop |

### Example

`#TTSZ#InvestigatorSignatureFor(InvestigatorCardTitle="My Custom Investigator")`

## Instruction - Investigator deckbuilding option

This allows you to specify the deckbuilding options on a card.

Its typical usage is on an investigator card to specify the deckbuilding. You can, and generally will need to, specify multiple instances of this instruction on a each investigator.

**Secondary class selection and other more complicated deckbuilding is not currently supported**. If you have an deckbuilding that is not supported then the workaround is to specify a single DeckbuildingOption with all classes listed and levels 0 to 5. This will allow all cards to be available and the player will have to self-manage following the deck-building rules.

It is also supported on player cards for the rare cases that a player card alters the deckbuilding of the owning deck when added.

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
| Exclude | Must be "true" or "false". If true then the rules defined by this option are an exclusion |

Some example of official investigators/cards below

**Roland Banks**

Straight-forward classes and levels

`#TTSZ#DeckbuildingOption(Classes="Guardian,Neutral",MinimumLevel="0",MaximumLevel="5")`
`#TTSZ#DeckbuildingOption(Classes="Seeker",MinimumLevel="0",MaximumLevel="2")`

**Zoe Samaras**

Example of a limited number of cards from level 0

`#TTSZ#DeckbuildingOption(Classes="Guardian,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Preson Fairmont**

Exclusion example

`#TTSZ#DeckbuildingOption(Classes="Rogue,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Classes="Survivor",MinimumLevel=0,MaximumLevel=2)`
`#TTSZ#DeckbuildingOption(Exclude="true",Traits="Illicit")`

**Amanda Sharpe**

Trait + card type example

`#TTSZ#DeckbuildingOption(Classes="Seeker,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Traits="Practiced",CardTypes="Skill",MinimumLevel=0,MaximumLevel=3)`

**Finn Edwards**

Mix of traits, levels and classes

`#TTSZ#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=3)`
`#TTSZ#DeckbuildingOption(Traits="Illicit",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Classes="Seeker,Survivor",MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Bob Jenkins**

Weird level zero options

`#TTSZ#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Classes="Survivor",MinimumLevel=0,MaximumLevel=0)`
`#TTSZ#DeckbuildingOption(Classes="Rogue",MinimumLevel=1,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=0,CardCountLimit=5)`

**Akachi Onyele**

Regular expression matching

`#TTSZ#DeckbuildingOption(Classes="Mystic,Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(TextRegex="Uses (\d+ charges)",MinimumLevel=0,MaximumLevel=4)`
`#TTSZ#DeckbuildingOption(Traits="Occult",MinimumLevel=0,MaximumLevel=0)`

**Michael McGlen**

Exact text matching

`#TTSZ#DeckbuildingOption(Classes="Rogue",MinimumLevel=0,MaximumLevel=3)`
`#TTSZ#DeckbuildingOption(Classes="Neutral",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(Traits="Firearm",MinimumLevel=0,MaximumLevel=5)`
`#TTSZ#DeckbuildingOption(TextExact="Firearm",MinimumLevel=0,MaximumLevel=5)`

**Versatile**

A card altering deck-building

`#TTSZ#DeckbuildingOption(MinimumLevel=0,MaximumLevel=0,CardCountLimit=1)`

## Instruction - DeckbuildingRequirements

This allows you to specify the deckbuilding requirements for an investigator. This instruction is only valid on investigator cards.

Instruction key: DeckbuildingRequirements

Parameters:

| Parameter key |	Details |
| --- | --- |
| DeckSize | Number of cards in the deck |

### Example

`#TTSZ#DeckbuildingRequirements(DeckSize=30)`

## Instruction - Override encounter set details

This allows you to override Zoop defaults for an encounter set. See [Encounter Sets](../../encounterset/EncounterSet.md) for more information.

Instruction key: EncounterSet

Parameters:

| Parameter key |	Details |
| --- | --- |
| Name | Override name of the encounter set |

### Example

`#TTSZ#EncounterSet(Name="Chilling Cold")`

## Instruction – Specify SCED location metadata

This instruction allows overriding some of the default SCED metadata that determines how locations functions. The SCED mod automatically draws lines between connecting locations. You can use this instruction to add/replace a location’s icons and connections and/or force a non-location card to act like a location for connection purposes. See [SCED metadata](../../tts/ScedMetadata.md) for further details on metadata.

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

`#TTSZ#ScedMetadataLocation(CardFace="Front",ForceLocationType="true",Icons="MadeUp",IconsAction="Replace",Connections="Triangle,Square",ConnectionsAction="Append")`

This example adds a connection to the location with the “MadeUp” icon, for both the front and back faces of the card.

`#TTSZ#ScedMetadataLocation(CardFace="Front",Connections="MadeUp",ConnectionsAction="Append")`
`#TTSZ#ScedMetadataLocation(CardFace="Back",Connections="MadeUp",ConnectionsAction="Append")`

## Instruction – SCED metadata - extra token

This instruction allows specifying the extraToken metadata used by the SCED mod to spawn additional action tokens for investigators. This instruction is only valid on investigator cards. See [SCED metadata](../../tts/ScedMetadata.md) for further details on metadata.

**Applies to TTS exports only**

Instruction key: ScedMetadataExtraToken

Parameters:

| Parameter key	| Details |
| --- | --- |
| ExtraToken | The string you want to be placed in the extraToken metadata field

### Example

`#TTSZ#ScedMetadataExtraToken(ExtraToken="Fight")`
