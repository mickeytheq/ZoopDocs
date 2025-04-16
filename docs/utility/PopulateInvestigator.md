# Populate investigator

**This feature is a work in progress. If you find it does not work as described below, please check your card text carefully first, and then submit a bug report**

This utility attempts to populate an investigator card and related cards with [instructions](../shared/instructions/Instructions.md) derived from the free-text on the back of the investigator card.

Specifically this will

- Create one or more [DeckbuildingOption](../shared/instructions/Instructions.md#instruction---investigator-deckbuilding-option) instructions from the **Deckbuilding Options** section
- Create a [DeckbuildingRequirements](../shared/instructions/Instructions.md#instruction---deckbuildingrequirements) instruction from the **Deck Size** section
- Add the [InvestigatorSignatureFor](../shared/instructions/Instructions.md#instruction--link-signatures-to-investigator) instruction to each signature card specified in the **Deckbuilding Requirements** section
- Create a [DeckbuildingOption](../shared/instructions/Instructions.md#instruction---investigator-deckbuilding-option) instruction from the **Deckbuilding Restrictions** section

This function uses free-text parsing which is very fragile and prone to not work at all/correctly when there are minor changes or errors in the structure or content of the source text. Therefore to use this authors are encouraged to format their investigator cards as close to official cards as possible. Of particular importance is:

- Using the same header names as official cards, e.g. **Deckbuilding Restrictions** not **Additional Restrictions**
- Following the same structure as official cards for deckbuilding options, e.g. **Guardian cards (icon) level 0-3** not **Level 0-3 Guardian cards**
- Check for typos. A one character typo in a headeer, trait, character class, signature card title etc will likely break the function
- Use the correct **<t>Trait</t>** formatting (not <b><i></i></b> or anything else)

In addition signature cards must be in the **same folder as the investigator card** for the signature linking to work.

## Usage

Right click on an investigator card and select `Utility -> Populate investigator`

If a non-investigator is selected an error will occur.

When using this function read the Zoop log **carefully** to check for errors and see what Zoop did or did not do.
