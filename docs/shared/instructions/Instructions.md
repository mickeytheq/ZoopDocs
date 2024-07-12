# Instructions

Zoop supports embedding instructions on cards. These instructions will drive behaviour during Zoop processes.

Each instruction is a single line in the comments field of the card. An instruction always starts with #TTSZ# to identify it to Zoop as a specific instruction. Immediately after the second # you specify the name of the instruction and any parameters for that instruction. Each instruction and its parameters are documented below.

Parameter values are enclosed in double quotes. If you need a genuine double quote in a parameter value, put two double quotes instead of one. For example

`#TTSZ#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="""Booo"" to a goose",CopyCardFace="Back")`

Instructions and their parameters are case sensitive.

## Which Zoop utilities use instructions?

The following utilities use/obey these instructions

- TTS export
- Print and Play export
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
| CopyCardTitle | The title of the card you want to copy from. Must match a single card in the scope of that run of Zoop |
| CopyCardFilename | The filename of the card you want to copy from (without the .eon extension). Must match a single card in the scope of that run of Zoop |
| CopyCardFace | The face of the card you want to copy. Must be either “Front” or “Back” |

### Example

The following example will replace the back face of the current card with the back face of the card titled “Shared Back”

`#TTSZ#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="Shared Back",CopyCardFace="Back")`
 
## Instruction - Exclude

This allows you to have Zoop exclude the card from the export process. This can be useful if the card is a work in progress or is used as part of a card such as the source of the ReplaceCardFace instruction.

Instruction key: Exclude

Parameters: None

### Example

The following example will exclude the card

`#TTSZ#Exclude`

## Instruction – TTS Card Options

This allows you to override specific properties of the resulting TTS card. Zoop has default logic which this instruction allows you to override. This is a more technical instruction that requires knowledge of how TTS manages card objects.

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
| InvestigatorCardTitle | The title of the investigator card this mini card should be linked to |

### Example

`#TTSZ#InvestigatorMiniCardFor(InvestigatorCardTitle="My Custom Investigator")`

## Instruction – Link signatures to investigator

This allows you to link signatures (including weaknesses) to their corresponding investigator card. Zoop uses this in the automated collection numbering to group signatures with the investigator.

Instruction key: InvestigatorSignatureFor

Parameters:

| Parameter key |	Details |
| --- | --- |
| InvestigatorCardTitle | The title of the investigator card this mini card should be linked to |

### Example

`#TTSZ#InvestigatorSignatureFor(InvestigatorCardTitle="My Custom Investigator")`
 
## Instruction – Specify SCED location metadata

This instruction allows overriding some of the default SCED metadata that determines how locations functions. The SCED mod automatically draws lines between connecting locations. You can use this instruction to add/replace a location’s icons and connections and/or force a non-location card to act like a location for connection purposes.

Instruction key: ScedMetadataLocation

Parameters:

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
