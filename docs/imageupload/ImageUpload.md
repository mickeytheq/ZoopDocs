# Image upload

Part of Zoop's core function is to upload images exported from Strange Eons to a cloud location that is publically accessible.

This is used by multiple Zoop functions including exporting to TTS and exporting to card databases such as arkham.build.

Zoop provides several image upload options which require different configurations and have different levels of complexity.

Please consult the table below for options and some light comparison. A ^ indicates a caveat, review the notes.

| Image host | Recommended | Setup complexity | Free option? | Rate-limiting? | Notes |
| --- | --- | --- | --- | --- | --- |
| [Imgur](Imgur.md) | Yes | Low | Yes | Yes | |
| [Imgbb](Imgbb.md) | Yes^ | Low | Yes | Yes | Long-term reliability issues occasionally reported |
| [Cloudinary](Cloudinary.md) | Yes | Low | Yes | Yes | |
| [Dropbox](DropboxOAuth.md) | Yes | Medium | No | Unknown | |
| [Steam Cloud](SteamCloud.md) | Yes^ | Low | Yes | Unknown | Recently added, limited testing. Unusual configuration/pre-requisites, consult the link for details |
| [AWS S3](AwsS3.md) | Yes^ | High | No | No | Free-option with time-limited free-tier only |
| [Cloudflare R2](CloudflareR2.md) | Yes^ | High | Yes^ | No | Free-option with time-limited free-tier only |
| [FTP](Ftp.md) | No | High | No | No | For advanced uses/niche use cases only |
| [Local](Local.md) | Yes^ | Low | N/A | N/A | Suitable for local testing |
