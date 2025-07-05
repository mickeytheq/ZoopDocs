# FAQ

## I’m getting an error about getting a status 400 instead of 200. How do I fix that?

Sometimes you will see the following error in Zoop.

> java.lang.RuntimeException: Got status 400 instead of 200. Response body was {"status_code":400,"error":{"message":"Rate limit reached.","code":100},"status_txt":"Bad Request"}

Note the Rate limit reached in the error.

This typically occurs when you are initially using Zoop and your entire project’s files need to be uploaded.

This is caused by the cloud host temporarily refusing uploads because you have upload too much data in a short period of time. To resolve this, you can either wait a period of time and try again (this can be up to a day) or create accounts for both imgur and imgbb and switch between them when you see this error. Alternatively, you can create a paid account for one of the cloud host services as these don’t have rate limits.

## How do I create an imgur/imgbb/Cloudinary/Dropbox account to use with Zoop?

See [image upload](imageupload/ImageUpload.md) for details on the image upload options.

## How do I get multiple copies of a card in TTS?

You can either use the encounter set unrolling feature of Zoop or manually copy the card within TTS

## Does Zoop aggregate images together in a sheet/deck?

No. Each card image is exported and uploaded separately.

## Do I need to keep cards in the bags that Zoop originally exported them in to?

No. Do whatever you want with the produced cards in terms of organisation within your TTS saved object. The Zoop update mode can find the cards wherever they are, for example in a memory bag or a deck or a deck within a memory bag or whatever.

## How does Zoop update existing content?

When a card is exported from Strange Eons for the first time Zoop assigns it a unique id. This id is added to the correspond card in TTS. When you use Zoop’s update mode it searches the target TTS saved object for every card with a Zoop id and finds each corresponding card with the same id in Strange Eons. Then the card information in the TTS saved object is updated to match that in Strange Eons.

## Does Zoop update all the cards every time it is run?

No. Only cards that have changed since the last run of Zoop are exported.

## Can I add manually add scripting within TTS to cards created by Zoop?

Yes. When updating cards Zoop does not touch any scripting attached to cards. When updating Zoop only updates card titles, descriptions, tags, images and SCED metadata.

## Which fields within the TTS saved object does Zoop update?

For readers familiar with the TTS object structure Zoop updates the following fields
- GMNotes – the Zoop unique id and SCED metadata
- FaceUrl and BackUrl in the CustomDeckModel within a card object – the front and back images of the card
- The parent deck’s corresponding FaceUrl and BackUrl - the front and back images of the card (only when the card is within a deck in the TTS saved object)
- Nickname field – the card’s Title in Strange Eons
- Description – the card’s Subtitle field in Strange Eons
- SidewaysCard – if overridden by a Zoop instruction
- Tags - for metadata

## If Zoop fails for some reason (such as a failed image upload) how do I complete my export after the problem is fixed?

Just run Zoop again. It will pick up where it left off.

## How do I use a genuine double quote (“) in a Zoop instruction parameter?

Some Zoop instructions require a card title to be specified. For example a card title that have double quotes in them. To specify a double quote in a Zoop instruction parameter, put the double quote in twice instead of once. For example 

> #TTSZ#ReplaceCardFace(ReplaceFace="Back",CopyCardTitle="""Booo"" to a goose",CopyCardFace="Back")
