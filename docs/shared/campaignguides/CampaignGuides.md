# Campaign guides

Campaign guides are supported by Zoop. Because campaign guides are composed from multiple Strange Eons components, Zoop will merge these images together and generate a single PDF for the campaign guide.

In order for this to work, authors should populate the page number correctly. Zoop will sort the campaign guide images using this page number to create the merged PDF.

However the resulting PDF is not integrated into the TTS saved object. (This is due to issues with support for PDF within the cloud image hosts. This may be addressed in a future version). Instead, Zoop will create campaign guides on your computer and you will need to manually load the PDF into TTS and upload it to Steam (or another location of your choice). The PDF is saved into the **Export images folder** location specified when executing the export. The filename will be CampaignGuide.pdf.

If your project has multiple campaign guide sizes (i.e. 7 by 5 and A4), two campaign guide files will be created with a number in the filename to distinguish them.
