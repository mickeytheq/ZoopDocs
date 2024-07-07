# Adding SCED metadata to a saved object not created by Zoop

Some saved objects/content was created before Zoop existed. There is support within Zoop for updating these saved objects with the SCED metadata, sourced from the original Strange Eons project.

**You should not use this functionality if you use Zoop to export your content. The SCED metadata is automatically populated by Zoop in normal usage. This function is ONLY for updating content that was not created by Zoop originally**

In this mode Zoop updates saved objects with only the following

- The GMNotes field for each card containing the Zoop GUID and SCED metadata
- The Tags field for use by SCED

Zoop will make a best effort attempt to match cards in Strange Eons to the existing cards in the target TTS saved object. To do this it will use title and description matching and some light fuzzy matching on title. This will likely work for the majority of cards in a project but it should be expected that there will be some cards that can’t be matched in this manner. For example, if there are two versions of a location with the same title. To resolve this, some manual intervention is required.
To run through this process for your existing Strange Eons project do the following

1.	Get a copy of the TTS saved object for your campaign
2.	Run Zoop and use the Update TTS saved object with SCED metadata option. Select the saved object you prepared in step 1
3.	In the progress log check for the following message - The following cards in Strange Eons did not match to any card in the saved object. Import these using the Zoop create saved object function and manually integrate them:  - followed by a list of cards. Copy and paste this list of cards into a document/notepad somewhere, then close the progress log. We’ll call this the manual card list. 
4.	The cards listed above were not matched automatically by Zoop (see above). These will need to be handled manually
5.	Open TTS and load in the TTS saved object that was just updated by Zoop
6.	Change to the Black seat in TTS

For each card in the manual card list generated above, do the following

1.	In Strange Eons, right click on the card, and select the Zoop -> Zoop GUID GMNotes to clipboard option
2.	A dialog will show with what has been copied to your computer’s clipboard. Understanding the contents isn’t important
3.	In TTS, find the corresponding card (or cards if there are multiple copies) in your saved object. If you have containers such as bags/memory bags you will need to unpack until you can extract the card on its own to the tabletop
4.	Right click on the card. You should see a field near the bottom of the menu with GM in it
5.	Paste your clipboard into this field and hit Enter to save it
6.	Pack the card back into its original location

Repeat the above steps for each card in the manual card list.

Re-pack your saved object back to its starting state and save it.

Finally, run Zoop using the Update TTS saved object with SCED metadata option again (see above). This will insert the correct metadata for each of the cards you manually inserted the GUID for.

**Note that this process modifies both your saved object and your .eon files by adding a unique id to each card. It is recommended that you keep the modified .eon files as your new master copy. In the event that the SCED metadata changes you may need to run through this process again. By keeping the updated .eon files you will avoid having to perform the manual matching process of the manual card list detailed above.**
