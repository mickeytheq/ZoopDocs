# Card database export

This function allows an author to export their card information from Strange Eons into formats accepted by online card databases.

Currently supported is

- [arkham.build](https://arkham.build/)

## Instructions

This tool will obey [instructions](../shared/instructions/Instructions.md) defined on the cards.

## Preparation

Zoop can automatically extract most card content from Strange Eons files to build a card database. This includes

- Overall type of the card (e.g. investigator, asset, event, skill, treachery, location, act, agenda)
- Basic fields such as titles, subtitles, traits, flavour and illustrator
- Player card attributes including slot(s), cost, level, class(es), type, icons, keywords (e.g. myriad, permanent, exceptional, bonded) and game text
- Location shroud and clues
- Rendered card images, front and back faces
- Collection numbers
- Encounter sets and encounter set numbers - see [Encounter Sets](../shared/encounterset/EncounterSet.md) for details
- Enemy statistics, keywords and game text
- Victory
- Act and agenda numbering

The following are not currently supported

- Customisable upgrade options
- Whether a card can exile

The following are needed by card databases however cannot be extracted automatically by Zoop

- Investigator deckbuilding - to provide this use one or more [DeckbuildingOption](../shared/instructions/Instructions.md#instruction---investigator-deckbuilding-option) instructions and one [DeckbuildingRestrictions](../shared/instructions/Instructions.md#instruction---deckbuildingrestrictions) instruction on each investigator card
- Which cards are signatures and to which investigator a signature belongs - to provide this use [InvestigatorSignatureFor](../shared/instructions/Instructions.md#instruction--link-signatures-to-investigator) instruction on each signature card

If you have investigators and signatures in your project **you may see errors** if the above are not added.

## Usage

In Strange Eons right click on one folder containing your content and select the **Zoop -> Export to card database** option. Typically you will do this in the root folder to include all of the project's content.

You will first see the option dialog

![image](https://github.com/user-attachments/assets/e5fad817-a230-467e-bcee-6599fa89ec7e)

The options are

| Option | Details |
| --- | --- |
| Logging Level | Generally, you can leave this on Normal. If you want more details or feedback on the process set it to the other options for more logging. This does not impact the behaviour or output in any way |
| Card data export target | Pick the target card database. This will change the options below |
| Image storage to | Selects the cloud host to upload card images.<br>See the [FAQ](../FAQ.md) for how to configure various cloud image accounts.<br>The Always fail option is primarily for testing and should not be used for normal usage.<br>Some cloud hosts implement rate limiting. Therefore, when uploading a lot of new files you may run into an error that mentions a non-200 status was returned and a message mentioning rate limiting. If this happens, either wait a period of time (minutes/hours) and try again or switch to the other cloud host |
| Export images folder | The folder on your local computer where you want Zoop to export all the card images. A temporary area such as C:\Temp is appropriate for this. |

### arkham.build options

If the target is arkham.build then you will see the following options

After you have set the options, you will see the image options.

| Option | Details |
| --- | --- |
| Project file | A local project file to save the card information to. You will need to specify a location for this first (it won't exist initially, Zoop will create it). The extention should be `json` |
| Settings | Click the Edit button to enter or update the project settings |

To create a new project, enter a file path that you want to use for your project. Then click **Settings** to configure the settings for that project. You only need to do this once per project file.

### arkam.build project settings

| Option | Details |
| --- | --- |
| Name | User-displayable title for the project |
| Description | Optional. Free-text description for the project |
| Author | Name of the author of the project |
| Language | ISO-639 2-letter language code. 'en' for English |
| Your project URL | Optional. A link to a website that describes/houses the project |
| Project content types | One or more of the avaiable options. Select all that apply (Scenario is for stand-alone) |
| Project status | Describes what state the project is in |

The arkham.build mode is **incremental**. This allows you to insert cards into one project file from one or more Strange Eons projects. For example if you have a campaign with one Strange Eons project per scenario you can use Zoop to create the project file and settings once, then run the export multiple times, once for each Strange Eons project. Zoop will keep adding cards to the project file. Zoop will also incorporate any changes made to cards previously exported in the project file.

**However** the above incremental nature means Zoop will never delete cards from the project file. If you need to remove cards from the project file the safest way is to delete it, use Zoop to re-create it, and run all the exports again. Alternatively you can manually edit the resulting project file but that is not recommended.

### Image options

After selecting the Zoop options you will be asked to select the options for the [Image Export](../shared/imageoptions/ExportImageOptions.md)

After completing the above you will then see the [progress dialog](../shared/progressdialog/ProgressDialog.md).

### Output

Zoop will export the card information into the target database/file and upload images of each card face to the select image storage. The cloud links from the upload will be inserted into the card database.
