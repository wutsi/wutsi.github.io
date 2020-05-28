# ImageKit.io
Wutsi is integrated with [imagekit.io](https://imagekit.io) for resizing on the fly images, so that we can optimize the image served to mobile users.

# How do it work

# Settings
## Configuration
Configuration File: [application.yml](https://github.com/WutsiTeam/wutsi-blog-service/blob/master/src/main/resources/application.yml)
Configuration Settings:
- `wutsi.toggles.image-kit`: Feature flag for imagekit.io
- `wutsi.image-kit.origin-url`: Base URL served by imagekit.io
- `wutsi.image-kit.endpoint-url`: ImageKit.io base URL

### Example
If `wutsi.image-kit.origin-url=https://s3.amazonaws.com/int-wutsi`, and `wutsi.image-kit.origin-url=https://ik.imagekit.io/cx8qxsgz4d/`, then the URL `https://s3.amazonaws.com/int-wutsi/1/3/foo.png` will be rewritten to  `https://ik.imagekit.io/cx8qxsgz4d/1/3/foo.png`

## Accounts
- Integration: Email=herve.tchepannou@gmail.com
- Production: Email=herve.tchepannou@wutsi.com
