# Like

## Sequence Diagram
### Create Like

![](http://www.plantuml.com/plantuml/png/PP11QyCm38Nl-XKwjeTHTlLXj9JT2ckM_G774KpCiprPpiY_dvCiq92BURptMJpfdDMAbcyF5wTHyEgPWWB08l3f1M_yHTSOLABt90RlR-q7deRdawy12lqKoWfRQltNaWpioA0Jiag7V_e83-7AlbEAcJNAkCTxgxQpcV2tQ6ROudN0uXjicnisXMI4NQ4ANLBoxAno3Ay31RsNpdF-d9PAYvpj0qslcKlDnX40pXJwUgO_)
``` plantuml
@startuml
Actor Client

Client -> LikeController: POST /v1/like request
LikeController -> LikeService: create(request)
LikeService -> LikeRepository: create(request)
database wutsi
LikeRepository -> wutsi: SQL Query

LikeController --> ApplicationEventPublisher: publishEvent(event: LikeEvent)
@enduml
```

### Delete Like
![](http://www.plantuml.com/plantuml/png/POz1QWCn34NtEeMMoQA4RcTH4a9tWIQTNi2P-L1HnNPbUKfktun3e4CtjdXw7xwsnODvlIZj1a_6UnL49xh__FJ21_d2FaMtf0hh-FZMV_1cUjxeRS66xuhYjBGUkHusoO2EHoWSAndNz8S_j7VaLCIJNHVc63oSGm7_L2z2ItFEDjvnVphmgSAkzA_6JThbh384bnHV9qG_rhDA-PnFoVUnuHNcjsjz6bZJ5d6i5_q5)
``` plantuml
@startuml
Actor Client

Client -> LikeController: DELETE /v1/like/search/<like-id>
LikeController -> LikeService: delete(id)
LikeService -> LikeRepository: delete(id)
database wutsi
LikeRepository -> wutsi: SQL Query

LikeController --> ApplicationEventPublisher: publishEvent(event: LikeEvent)
@enduml
```

