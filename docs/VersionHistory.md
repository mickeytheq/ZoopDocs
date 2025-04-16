# Version History

## 3.0 - TBD

- New feature - export to card database - this exports Strange Eons content to formats accepted by online card databases to allow homebrew content to be used for player deck-building and visibility of campaign/encounter cards - [doco](https://mickeytheq.github.io/ZoopDocs/carddatabaseexport/CardDatabaseExport.html)
- New feature - export to card database - support for arkham.build format
- New feature - populate investigator card - Converts deckbuilding free-text from an investigator card to Zoop instructions - [doco](https://github.com/mickeytheq/ZoopDocs/blob/main/docs/utility/PopulateInvestigator.md)
- Improvement - Added EncounterSet instruction to override default EncounterSet naming - [doco](https://mickeytheq.github.io/ZoopDocs/shared/encounterset/EncounterSet.html)
- Improvement - Added DeckbuildingOption and DeckbuildingRequirement instructions
- New feature - inspect card - a quick view of a card's internals - [doco](https://github.com/mickeytheq/ZoopDocs/blob/main/docs/utility/InspectCard.md)
- New feature - image upload support for AWS S3
- New feature - image upload support for Cloudflare R2
- Improvement - Added progress bar to the progress dialog - useful when running large exports
- Improvement - Zoop process can now be cancelled via the Cancel button on the progress dialog
- Improvement - Encounter set identity for cards using custom image path is now just the filename rather than the full path
- Bugfix - Investigators with non-numeric stats failed to parse
- Improvement - Added support for the slot field to SCED metadata generation
- Improvement - Added support for the signatures to SCED metadata generation
- Improvement - Made the Dropbox OAuth authorisation dialog more user-friendly
- Improvement - Print and play output now overwrites existing files rather than failing
- Bugfix - Investigator backs were sometimes output with the wrong orientation
- Improvement - Added OverrideCardFaceImage instruction to allow overriding a card faces output image with a custom one
- Improvement - Add a cachebust URL parameter to FTP uploads so downstream caches refresh when a card is changed
- Improvement - Tweak the ImageExporter to improve compatibility with Strange Eons 3.4 (I make no promises this will continue to work, you may need to downgrade)
- Improvement - Optimise FTP upload by only creating needed directories once, rather than for each uploaded file

## 2.7 - 10th March 2025

- FTP image upload support has been added. Supports plain FTP and FTPS (FTP with SSL/TLS)
- TTS saved object files are now saved as UTF-8 to better support non-ASCII characters
- Fixed a bug where if victory was only on the back face of a card the metadata was not generated
- Add support for Enemy Location cards - which are just treated as locations for metadata purposes

## 2.6 - 25th February 2025

- Dropbox (OAuth) image upload has been added which automatically refreshes access tokens. Existing Dropbox upload support is deprecated and will be removed in a future version
- Local folder image upload support has been added
- Added Print Ready print and play mode that outputs the card images simply to a local folder
- Added SwapCardFaces instruction to swap front and back of a card
- Added Quantity instruction that allows an author to specify how many copies of a card should be created to override defaults
- Image tags are striped from chaos token effect descriptions before importing into SCED metadata
- Copyright field is now supported by bulk update
- Investigator title has been added to the MPC filename output
- Investigator title has been added to the MPC filename output for investigator mini-cards provided the mini-card is linked via the relevant instruction
- Fixed a bug where investigator cards were not supported by class in the same way as player cards

## 2.5 - 6th September 2024

- Added new feature that adds Cloudinary to the options for uploading images
- Added proper support for Player Purple (customizable upgrade card back) and Concealed card backs for both TTS and Print and Play
- Exporting to TTS investigator cards are now sized consistently with the existing mod investigators
- Exporting to TTS now splits cards into decks according to their orientation and size/scale. For example investigators are grouped separately from other landscape cards and Investigator minicards and concealed cards are grouped separately from other portrait cards
- Added ScedMetadataExtraToken instruction to allow authors to specify the extra action token metadata for use in the mod
- Investigator minicards now gain the title of the corresponding investigator when the InvestigatorMiniCardFor instruction is used
- Investigator minicards now have the Minicard tag
- Fixed a bug where SCED metadata only mode produced an error
- Fixed a bug where empty parameters ("") in instructions were not handled correctly

## 2.4 - 13th July 2024

- Requires the AHLCG plugin version 9 or later
- Zoop manual is now online - https://mickeytheq.github.io/ZoopDocs/ - PDF manual has been retired
- Added new feature Bulk Update that supports updating the same field on multiple cards - supports Collection and Encounter set information
- Added new feature Export/Import that supports exporting card information to Excel for external modification and importing the changes back in - supports primarily free text fields for translation purposes
- Cards with the Exclude instruction are now correctly excluded/ignored when running automatic numbering capability or MPC print and play capability
- Removed support for the automatic XP box scripting on Customizable Upgrade cards. Was too unreliable/flaky
- Fixed support for Act/Agenda portraits
- Print and play export can now execute on a single file
- Print and play output files now contain the act/agenda letter/deck id
- Automatic numbering now has a sorting mode to allow ignoring encounter set numbers
- Automatic numbering when using InvestigatorSignatureFor instruction now sorts asset/event/skill signatures before weaknesses/other signatures
- Story cards with player/encounter cards are now handled correctly
- Instructions that reference other cards may now use the filename instead of the card title
  
## 2.3 - 22nd February 2024

- Fix bug where the 'resume from' functionality did not work when the options dialog loads with the option already selected
- Fixed issue where cancelling a non-dry run of the collection numbering would update the 'continue from' option on the next run incorrectly
- The encounter set column in the collection number now shows the image filename where a custom encounter set image is used
- Add additional explicit card types to the collection numbering ordering logic. See manual for full details on sorting order
- Fixed issue where if an author takes Zoop created cards and puts them inside a 'DeckCustom' type/name of deck container (instead of the usual 'Deck' type) the URLs of the cards in the 'CustomDeck' blocks inside the deck container do not get updated when the individual card URLs are updated

## 2.2 - 17th February 2024

- Fixed an issue with StoryWeakness and InvestigatorWeakness type on enemy and treachery cards

## 2.1 - 17th February 2024

- Support for 'PlayerPurple' card backs (the one used on the back of Customizable cards)
- Support for Concealed and Key cards (from Scarlet Keys)
- TTS export - Updated Player and Encounter card backs to higher resolution versions (aligned with changes made to SCED mod)
- TTS export - Card ID in the metadata is now the Zoop GUID - to support future capability in SCED for homebrew
- PnP export - Strip embedded tags from card titles
- Automatic collection numbering - Added option to continue numbering from the last run
- Automatic collection numbering - As well as collection numbers also sets encounter numbers for cards with encounter sets
- New instruction to link signatures to their corresponding investigator - used by automatic collection numbering to group signatures with their investigator card
  
## 2.0 - 23rd October 2023

- Added initial print and play support with one mode for MPC printing
- Added automatic collection numbering tool
- Minor rebrand from TTS Zoop to Zoop as the scope of the tool has increased beyond TTS
- Fixed a bug where a blank EncounterTotal field caused a NullPointerException
- Files that Zoop doesn’t care about are more gracefully ignored, e.g. deck objects
- Added partial scripting support for customizable cards (the xp boxes)

## 1.10 - 30th June 2023

- Added a requirement to have version 8.19 or later of the AHLCG plugin installed (dated June 25 2023 in the plugin catalogue)
- Added option to specify the filename prefix when creating a new saved object, instead of the default TtsZoop
- Added ScedMetadataLocation instruction to support creating location connections between cards outside of those naturally created by the card’s icons and symbols. This includes support for forcing a non-location card to act like a location
- Changed the default metadata behaviour so cards that have a location on the back but not the front will have the Location type, enabling automatic location connections to work correctly
- Player card titles now have the level in brackets to align with player cards from official content
- Landscape cards are now sized correctly when creating a new saved object or adding new/missing cards to an existing saved object. As a side effect of this change when there is a mix of landscape and portrait cards created in save mode, portrait and landscape cards will be split into separate decks
- Fixed a bug where card backs for assets/events/skills/story assets did not align with the standard card back
- Removed a workaround to get campaign guide images to work. Fixed in the latest AHLCG plugin
- Added more common queries to the FAQ

## 1.9 - 24th April 2023

- Added support for dropbox for image upload (experimental)
- Added documentation for setting up dropbox for use with Zoop
- Optimised how strange eons cards are loaded to reduce memory load
- Added SCED metadata for scenario reference/chaos cards
  
## 1.8 - 15th February 2023

- Added the InvestigatorMiniCardFor instruction to allow linking of an investigator min cards to its corresponding investigator
- Added generation of the ‘id’ field metadata for investigators and investigator mini cards
- Fixed a bug where image placeholders were not correctly updated when image upload completes successfully
- Fixed a bug where fightIcons was used instead of combatIcons in the metadata
- Fixed a bug where ‘Uses’ was being parsed from the Game Text field in Strange Eons instead of the Keywords field
- Added an option to Always fail image upload (primarily used for testing the placeholder image capability)
- Updated documentation with missing step for SCED metadata only mode
  
## 1.7 - 9th January 2023

- Fixed a bug where existing Tags were overwritten when creating the SCED metadata. This bug broke tag-based memory bags
- Minor documentation tweaks

## 1.6 - 5th January 2023

- Added new mode to integrate SCED metadata into existing campaigns not created by Zoop
- Added new option to create local placeholder images when temporary image upload failures occur
- During update mode when falling back to card matching on title, fail the match if the card in the saved object has a Zoop GUID. Some content creators run multiple Strange Eons projects into a single saved object and the previous behaviour would cause problems when two different Strange Eons has the same card by title

## 1.5 - 15th December 2022

- Added support for additional SCED metadata - Permanent, Hidden, Victory on encounter cards and locations, Uses (charges/secrets etc), investigator stats
- Added new feature for update mode where missing cards – those that are in the Strange Eons project but not the saved object – are dropped into a designated bag in the saved object for easier integration
- Fixed a bug where campaign guide portrait images were not present when exported

## 1.4 - 5th December 2022

- Added initial support for SCED metadata
- Fixed a rare bug where Zoop card matching would fail when the source .eon files were replaced

## 1.3 - 21st October 2022

- Added a new Exclude instruction
- Added a new TtsCardOptions instruction
- Added creation of campaign guides to the export process
- Fixed a bug where Zoop would complain about “TTS saved object card with nickname/title <something> does not have a custom deck section with id <something> for card id <something>. Possibly invalid JSON has been generated” when updating existing saved object
- Fixed a bug where the back side of cards would be squished when the card has a sideways/landscape front but a portrait back. For example, an Agenda on the front with an Enemy on the back
- Documentation – Added FAQs for how to create imgur/imgbb accounts and generate API keys for use with Zoop

## 1.2 - 25th September 2022

- Added new feature to support directly updating an existing TTS saved object with changes made in Strange Eons
- Fixed a bug where non-standard location symbols would cause zoop to fail
- Fixed a bug where invalid JSON was being written to the TTS saved object
- Fixed a bug where incorrect CardIDs were being generated for cards
- Fixed a bug where the ‘zoop mode’ in the options was not remembered between runs of Zoop
- Fixed a bug where hidden folders were not visible in the folder/file pickers. On linux in particular the saved object folder may be nested within a hidden folder
  
## 1.1 - 20th September 2022

- Added new Instructions capability (experimental)
- Added ReplaceCardFace instruction that allows replacing a card face on a card with the card face of a different card
- Card subtitle is now copied into the Description field
- Fixed a bug where cards vanish in TTS when there’s only a single card in the deck
- Fixed a bug where Story Assets used an incorrect player card back image
- Fixed a bug where Enemy Weakness cards had an encounter card back instead of a player card back
- Fixed a bug where a null pointer exception is raised the first time Zoop is launched

## 1.0 - 19th September 2022

- Initial release
- Bulk export of card images and metadata
- Support for automated upload of images to imgur and imgbb
- Creation of TTS saved object
- Encounter card unrolling
- Compatible with SE version 3.3.4241
