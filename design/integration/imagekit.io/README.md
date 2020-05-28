# ImageKit.io
Wutsi is integrated with [imagekit.io](https://imagekit.io) to optimize the images served to users: 
- Resizing on the fly images, to return smaller images to mobile users.
- Return image in optimized format. Ex: return `.webp` instead of `.png`.

# How do it work

# Settings
## Configuration
Configuration File: [application.yml](https://github.com/WutsiTeam/wutsi-blog-service/blob/master/src/main/resources/application.yml)
Configuration Settings:
- `wutsi.toggles.image-kit`: Feature flag to turn on/off the integration with imagekit.io
- `wutsi.image-kit.origin-url`: Base URL served by imagekit.io
- `wutsi.image-kit.endpoint-url`: ImageKit.io base URL

### Example
If `wutsi.image-kit.origin-url=https://s3.amazonaws.com/int-wutsi`, and `wutsi.image-kit.origin-url=https://ik.imagekit.io/cx8qxsgz4d/`, then the URL `https://s3.amazonaws.com/int-wutsi/1/3/foo.png` will be rewritten to  `https://ik.imagekit.io/cx8qxsgz4d/1/3/foo.png`

## Accounts
#### Integration
- Email: herve.tchepannou@gmail.com

#### Production
- Email: herve.tchepannou@wutsi.com
