# wutsi-blog-web
![](https://www.planttext.com/api/plantuml/img/TP2n2i8m48RtUufxWKok8gs38ewwXGv9F48mwK5oRS6dDpgMvDRl--7ZXY8cov8YmEY4CvxP0kXBo6HDeGcLEg7U5Yb1sSXURMGd17rbzh7YOulNlN5acTzTuRa54Sez3ZK3cyDzoaugbDVWg2N-p5iodkv1UdnCviCpFWuruNy3pQ_wdIy0)

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
