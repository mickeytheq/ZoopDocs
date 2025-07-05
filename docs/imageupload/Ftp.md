# FTP image upload

FTP image upload sends image files to a FTP server. This is advanced option that is not generally recommended for typical users.

## Usage

You will need an FTP server and have already setup credentials. This article will not describe how to do this, knowledge is assumed.

## Setting up

When prompted by Zoop you will need to enter the relevant FTP information such as host, port, username and password. In addition you can enable TLS security.

You will also need to specify a relative directory from the FTP root for Zoop to upload files to. Finally you need to specify a URL prefix. Zoop needs to build a URL to put in its output file so you need to define what mapping from the FTP filesystem is to a publically visible URL and enter this URL here. Zoop will prefix this on all generated URLs and add a relative path consistent with each upload files target location on the FTP server.
