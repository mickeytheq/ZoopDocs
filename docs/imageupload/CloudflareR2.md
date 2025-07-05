# Cloudflare R2 image upload

Cloudflare R2 is a general cloud storage solution that can accept and serve image files publically.

It provides AWS S3 API compatibility so there are some similarities between the two methods.

## Usage

Describing how to setup an Cloudflare account and R2 configuration is outside the scope of this article.

## Setting up

Zoop requires an access key, secret key, account id, URL prefix and bucket name to be provided when this option is selected. Zoop will create objects within the R2 bucket with unique names. Zoop will automatically generate the public URL using the provided URL prefix.
