# Components

![](https://www.planttext.com/api/plantuml/img/VP512u8m5CVl-nJ3-qxTGx6KY2uPT8WTtdJ8S7EXCw7mkxVfa0fjfyT-l_Tdxori3JIcKnAXE-GLb1m7aOAdhd5qpGByGjYUMxQXljXdKrM00GQjrS-xsRD2tvbMJCg0Xe_KLEjISXnBtHLpRXAVV72gG4ZgEX0Qhp4XMnz7cDGbwJcZ67bnaThENzzP2UISQLtH1UpuGTa77eLPusxuBzJovY5oxl4umpfstN-es-SwzjjS5Yo_zC8Otb2tDHJokh0_-GO0)

```plantuml
@startuml

Actor Bob

[Firebase] --> [wutsi-blog-web] 
[Google] <--> [wutsi-blog-web]
[Facebook] <--> [wutsi-blog-web]
[Twitter] <--> [wutsi-blog-web]

Bob -> [wutsi-blog-web]
[wutsi-blog-web] -> [wutsi-blog-service]
[wutsi-blog-web] --> [ImageKit]
[wutsi-blog-web] --> [Amazon S3]

@enduml
```
