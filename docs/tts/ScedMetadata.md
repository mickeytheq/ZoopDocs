# SCED Metadata

The SCED mod supports metadata on cards. When present, this metadata is used by the mod to drive certain activities. For example, metadata on locations allows automatic clue spawning and location connection linking. If you want to learn more about the SCED metadata the documentation for it is [here](https://github.com/argonui/SCED/wiki/Metadata)

Zoop populates this metadata automatically during the export and saved object creation process. Metadata population is supported both when creating new saved objects and updating existing saved objects.

## Supported metadata fields

Some of the available metadata fields are not populated by Zoop. The following table shows the current status of metadata field support.

| Metadata type | SCED metadata field | Support |
| ----- | ------ | ----- |
| Tags | Tags in the card JSON object | Supported |
| Arkham DB card id | GMNotes id and alternate_ids | Supported – see notes below |
| Card class | GMNotes class field | Supported |
| Traits | GMNotes traits field | Supported |
| Starts in play | GMNotes startsInPlay field | Not supported |
| Starts in hand | GMNotes startsInHand field | Not supported |
| Resource cost | GMNotes cost field | Supported |
| Level	| GMNotes level field | Supported |
| Permanent | GMNotes permanent field | Supported |
| Weakness | GMNotes weakness field | Supported |
| Basic weakness count | GMNotes basicWeaknessCount field | Not supported |
| Hidden | GMNotes hidden field | Supported |
| Uses on assets | GMNotes uses field | Supported |
| Bonded cards | GMNotes bonded field | Not supported |
| Skill icons | GMNotes willpowerIcons, intellectIcons, fightIcons, agilityIcons, wildIcons | Supported |
| Dynamic skill icons | GMNotes dynamicSkillIcons | Not supported |
| Negative skill icons | GMNotes negativeSkillIcons | Not supported |
| Victory (non-locations) | GMNotes victory | Supported |
| Agenda doom threshold | GMNotes doomThreshold and doomThresholdPerInvestigator | Supported |
| Act clue threshold | GMNotes clueThreshold and clueThresholdPerInvestigator | Supported |
| Customizations | GMNotes customizations | Partially supported |
| Location clue counts | GMNotes locationFront and locationBack | Supported |
| Location icons and connections | GMNotes locationFront and locationBack | Supported |
| Location victory | GMNotes locationFront and locationBack | Supported |

## Id field

The id field is set to a Zoop generated GUID. This id will be unique per source card in Strange Eons. Where a card has multiple copies in TTS, such as multiple copies of an encounter card or player card, the id will be the same across all copies of this card.

Investigator mini-cards are an exception to the above. They will be the id of the linked investigator card (see the InvestigatorMiniCardFor instruction for more details) with a -m suffix. If there is no investigator linked card the mini-card will not have an id.
