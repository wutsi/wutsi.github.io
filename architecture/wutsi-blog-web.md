# wutsi-blog-web
![](https://www.planttext.com/api/plantuml/img/RP6n3eCW48RtUmfUmAcxqJQnQPfE3WwD0-25aYAN0DQXwRiNQwmcmdO_z_tyTnG-S1U6tW10AGCvTYG1bZfapH2yPczWyTp7gSY48PMDA5gsKpswbvROmWTcl6pg1QuF6ta83xH1InuqsNgc_D9v9b8ccloAYaiKHCyLdgzFXePk8IhjK72FR5Plw3rNsgeLklHSuLM7EE6Mpx8yCTPEcThIcG7YgbZ29M6IftULVEsVDvsbgG4Aj5tyioy0)

```plantuml
@startuml

Actor Bob
node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
}

node AWS {
    [S3]
}

node AuthenticationServices {
    [Google]
    [Facebook]
}

node GoogleCloud {
    [Firebase Cloud Messaging]
}

node ImageKit


GoogleCloud --> [wutsi-blog-web] 
[wutsi-blog-web] --> AuthenticationServices

Bob -> [wutsi-blog-web]
[wutsi-blog-web] -> [wutsi-blog-service]
[wutsi-blog-web] --> ImageKit
[wutsi-blog-web] --> AWS

@enduml
```
