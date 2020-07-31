# wutsi-blog-web
![](https://www.planttext.com/api/plantuml/img/TP4z2y8m48Rt-nM7UoPN4Jz04N5oS90EINh4O9k39bLG_E-chQrIssntx_FULnO-o2AKUGQmr84BNB42nodXgGpUuXCmllEz2eJAs8WxgGJ_ifwAczMKm0iQ-sIPomSxN6TSffEspd7wIvJXGYvOBOEDvB4fuJjuosooMB8EDbAJOhx--1kzrs5Z2rBIVz9u8E-biSxKFXYNKOZvm9xj43WRqk4xrWW0yPuuwEotwa7TGV_1Yjpbqj3UXZ6zEZGioANnQzy0)

```plantuml
@startuml

Actor Bob
node Wutsi {
    [wutsi-blog-web] 
    [wutsi-blog-service]
}

node "Amazon Cloud" {
    [S3]
}

node "Authentication Services" {
    [Google]
    [Facebook]
}

node "Google Cloud" {
    [Firebase Cloud Messaging]
}


[Firebase Cloud Messaging] --> [wutsi-blog-web] 
[Google] <--> [wutsi-blog-web]
[Facebook] <--> [wutsi-blog-web]

Bob -> [wutsi-blog-web]
[wutsi-blog-web] -> [wutsi-blog-service]
[wutsi-blog-web] --> [ImageKit]
[wutsi-blog-web] --> [S3]

@enduml
```
