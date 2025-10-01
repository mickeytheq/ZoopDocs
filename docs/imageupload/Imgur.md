# Imgur image upload

**No longer available in the UK so should be avoided.**

Imgur is a pretty standard cloud host that offers free image hosting.

## Usage

Using imgur you just need to provide an API key while using Zoop, which is called the Client ID by imgur. See below for details on creating an account and the key.

## Setting up an imgur account

If you already have an account and just need to generate an API key, skip to step 3

1. Go to imgur.com and click sign-up in the top right
2.	Fill in your details to create an account
3.	Login to your account
4.	Go to https://api.imgur.com/oauth2/addclient. You will see a screen titled “Register an Application”
5.	Give it an application name. This doesn’t really matter. Call it Zoop or whatever you want
6.	Select the “Anonymous usage without user authorisation”
7.	Leave the authorisation callback URL blank. If you have an issue with this being required select the middle option of authorisation type first and then switch back to the anonymous option
8.	Leave the application website blank
9.	Enter your e-mail
10.	Enter a description if you want
11.	This will then show a screen with a client ID and client secret
12.	Only the client ID is required for Zoop and is what you should enter in the API key field. If you forget the client ID you can view it by going to the Settings of your account and selecting Applications
