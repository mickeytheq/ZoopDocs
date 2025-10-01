# Image upload

Part of Zoop's core function is to upload images exported from Strange Eons to a cloud location that is publically accessible.

This is used by multiple Zoop functions including exporting to TTS and exporting to card databases such as arkham.build.

Zoop provides several image upload options which require different configurations and have different levels of complexity. Zoop does not provide any storage itself so the user must pre-configure one of the options below and provide necessary details to Zoop. Further details are provided in each of the links below.

Please consult the table below for options and some light comparison. A ^ indicates a caveat, review the notes.

Disclaimer: The recommended option is based on community feedback and my own interpretation of how suitable these options are, please do your own research etc.

| Image host | Recommended | Setup complexity | Free option? | Rate-limiting? | Notes |
| --- | --- | --- | --- | --- | --- |
| [Imgur](Imgur.md) | **No** | Low | Yes | Yes | No longer available in the UK so should be avoided |
| [Imgbb](Imgbb.md) | Yes^ | Low | Yes | Yes | Long-term reliability issues occasionally reported |
| [Cloudinary](Cloudinary.md) | Yes | Low | Yes | Yes | |
| [Dropbox](DropboxOAuth.md) | Yes | Medium | Yes^ | Unknown | Free-option with limited space |
| [Steam Cloud](SteamCloud.md) | Yes^ | Medium | Yes | Unknown | Recently added, limited testing. Unusual configuration/pre-requisites, consult the link for details |
| [AWS S3](AwsS3.md) | Yes^ | High | Yes^ | No | Advanced users only. Free-option with time-limited free-tier only |
| [Cloudflare R2](CloudflareR2.md) | Yes^ | High | Yes^ | No | Advanced users only. Free-option with time-limited free-tier only |
| [FTP](Ftp.md) | **No** | High | No | No | For advanced uses/niche use cases only |
| [Local](Local.md) | Yes^ | Low | N/A | N/A | Suitable for local testing |

## Rate-limiting

Many image hosts, particularly free ones, implement rate-limiting. When you are working with a larger projects and uploading many images Zoop may encounter an error from the image host. If the error message contains anything about rate-limiting, too many requests or words to that effect, you can assume you've hit that limit. The workaround is to wait (typically an hour or so) for the limit to reset and try again. Zoop will remember how far you got and pickup from the error. Or you can explore paid options for that or a different image host.
