# Steam Cloud image uploading

Steam offers a cloud storage solution aka Remote Storage for users and applications to store files to be used by Steam games.

Steam Cloud operates somewhat differently to other image storage solutions:

- Authentication is via the Steam client rather than an API key or similar methods
- All files uploaded are stored against a specific Steam game or application

## Usage

In order to upload files to the Steam Cloud you need to check the following:

1. Your Steam client is running while you are using Zoop
2. Your Steam account allows cloud upload - see `Steam menu > Settings > Cloud > Enable Steam Cloud option`
3. Strange Eons has permission to write the directory it runs from (typically `StrangeEons/bin`)

For 3. you may need to run Strange Eons as admin.

There are no options to select for Steam Cloud within Zoop as all authentication is external/via Steam client.

## FAQ

### I get a `Error writing TTS app id to local file path` error

If you see the following `java.lang.RuntimeException: Error writing TTS app id to local file path: C:\Program Files\StrangeEons\bin\steam_appid.txt` and further down the error stack `Caused by: java.nio.file.AccessDeniedException: C:\Program Files\StrangeEons\bin\steam_appid.txt` then try running Strange Eons as admin. Zoop is trying to write a file the Steam API requires to be in the current directory and sometimes permission is not available
