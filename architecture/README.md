# High Level Architecture

![](https://www.planttext.com/api/plantuml/img/TL0n3eCm3DpzYdmWNwYe6Agg8mD3nH285I85Ho9E6Qh-lK592nAj9z_vxBDT1LOpnya107cDeeqSh7Y2I75VLY1xvurSiE_4WGquF-o07RnA-xbjIX9vH68xABQUcgmBkNRntZYidOyw4zT96RnPpgWU5H6wa5RQAOMKfx8T99SDGYPN_CTq4tn7VnntO-1mRYhzF1Og99r-zWO0)

```plantuml
@startuml

node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
}

node AWS
node AuthenticationServices
node GoogleCloud
node ImageKit
node Channels


GoogleCloud --> Wutsi 
AWS --> Wutsi
Wutsi --> AuthenticationServices
Wutsi --> Channels
ImageKit --> Wutsi

[wutsi-blog-web] -> [wutsi-blog-service]

@enduml
```

# Components
- [wutsi-blog-web](wutsi-blog-web)
- [wutsi-blog-service](wutsi-blog-service)
