# Dropbox image upload

Dropbox is a paid storage solution which provides APIs for uploading files that Zoop uses.

## Usage

Using Dropbox you need to go through an OAuth process the first time you use it. Zoop will require an initial set of credentials and will then redirect you to the Dropbox website to authorise Zoop to use your Dropbox account.

## Setting up an account

You’ll need a dropbox account first, then follow these steps

1.	Go to https://www.dropbox.com/developers/apps/
    1.	You will need to provide your dropbox login if you haven’t already
2.	Click Create app
3.	For Choose an API select Scoped access option
4.	For Choose the access type you need select App folder
    1.	**Under no circumstances should you use the Full dropbox option**. This will create an access token that gives access to all your files. Using App folder limits Zoop to a specific dedicated folder within your dropbox
5.	For Name your app input a name
    1.	I recommend that you create one app per campaign/set of content you are producing. This will avoid any name clashing with cards that have the same name in different campaigns
6.	Click Create app. You should see a new screen with a bunch of tabs including Settings and Permissions 
7.	Click the Permissions tab
8.	Under Files and Folders tick the following options – this permission allows Zoop to upload files to your dropbox
    1. 	`files.content.write`
9.	Under Collaboration tick the following options – this permission allows Zoop to create shared links to uploaded files in your dropbox, allowing TTS to download them
    1.	`sharing.write`
    1.	`sharing.read`
10. Click Save
11.	Click the Settings tab
12. Open Strange Eons and run Zoop
13. Select the `Dropbox (OAuth2)` option for image storage
14. Copy the App key and App secret from the Dropbox settings screen into the Zoop options dialog
    1. In Zoop, you will see a message in a greyed out `Access token` editor stating `Authorisation required`
15. Click the `Authorise` button
    1. Your web browser should open. Dropbox will ask you to confirm the access being requested
16. In the browser you will see an authorisation token. Copy this from the browser and paste it into the Zoop dialog asking for it
17. Click OK on the dialog
    1. Returning to the options dialog the `Access token` editor should now show `Access token created`
18. You should **not** need to perform steps 14-16 again. The access token should automatically refresh on future uses of Zoop
