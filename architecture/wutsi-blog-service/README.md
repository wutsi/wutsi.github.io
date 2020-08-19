![](https://www.planttext.com/api/plantuml/img/TP712eCm38RlVOg-G4-xYqEsdTm62Xw6XsY3AzCMsZfnmtUVK-jWQav9-FFn9_6D1MthgYH4AeuqgQqHz4re7xVcMx2iL0LhC4lfecjGFqMEAUccyNq5BoNtIUGGqIwTaaCqPXmiP62G3fnHris0u0vIOcdSVDm8Qr5Fa2Fac2drSANGEA22KjMSXcWC548MFpzNQ2kKzWGM6sWTD8pF4-6YGHQZVq8M-p9lVTkr9cMzshdVLim7sf1uVvPxMpvAtZ_e0m00)

```plantuml
node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
}

node AmazonAWS {
    [S3]
    [SES]
    database wutsi{
    }
}

node Channels {
    [Twitter]
    [Facebook]
    [Firebase Cloud Messaging]
}

node PaymentGateway {
    [MTN]
    [Orange]
}



[wutsi-blog-web] -> [wutsi-blog-service]
[wutsi-blog-service] --> Channels
[wutsi-blog-service] --> AmazonAWS
[wutsi-blog-service] -> PaymentGateway


@enduml
```

# Designs
- [Publish to Channel](publish-to-channel.md)
- [Like](like.md)
- [Statistics](statistics.md)
