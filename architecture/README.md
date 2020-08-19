# High Level Architecture

![](https://www.planttext.com/api/plantuml/img/VL1B3i8W5Do_Kt01hc1gkZ36PHTTc2ueVQ542WayseNnxhQXIcDLLimdCozJ11AUuc00hEkGrP62PdTWyxjE2-2jSOfFs3PinmRqevROR0NoGjwoybY3ZtMrVYBrQ4bBGThPAlb2qaxEAOEbSR5Bn7aG2Y-Q4YfxOIsQ000R9-FyiDuDSqk6aCW5_oZDXdVqgt4J0xiX5kth3l-S7yD0WRQRXty2)

```plantuml
@startuml

node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
    [wutsi-track-service]
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

[wutsi-blog-web] --> [wutsi-blog-service]
[wutsi-blog-web] --> [wutsi-track-service]

@enduml
```

# Components
- [wutsi-blog-web](wutsi-blog-web)
- [wutsi-blog-service](wutsi-blog-service)
- [wutsi-track-service](wutsi-track-service)
