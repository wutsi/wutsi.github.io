![](https://www.planttext.com/api/plantuml/img/TP513e8m44NtFKKlmCezmH1rXPf0miAmcD89DaARj4M2XhkBG34HcDNCvC_B_srWB6XRLoKXKd6aQMsDe6z2-xerty5ZfIgy1bb65rk3-Ybop4WtdUyhU2cvJsE7Y7VPr1pYiUDWWO51Ed0u6uNTZ0Zl82MMnX6IHbYBUi8S8KUcrCEDGkC02qjLSngXCL08MVmSNQ6jKDeJM6oWTT0eEK-4YmPPZ0a8MIJs_FMyQqlgzMhdVbinFz66nF-ptDiAKFB-Ypu0)

```plantuml
@startuml

node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
}

node AmazonAWS {
    [S3]
    [SES]
    database wutsidb{
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
