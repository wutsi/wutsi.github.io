# Like

## Sequence Diagram
### Create Like
![](http://www.plantuml.com/plantuml/png/LSx12i8m3CRnUvuYHpt8yDg3J7OL5BONgDrtACOMqtI-leKvq5CW-VqXH7qnhrQVGkTWMNcGY6H4w-J3YI_nWI4dqom2TNoxZXDtox6JTc35gw8O_Qkj6w5B370S5Dwm--ezpTxytHVmkrg9z6DRkYuTJvatHptItBxy0000)
``` plantuml
@startuml
Actor Client

Client --> LikeController: POST /v1/like request
LikeController --> LikeService: create(request)
@enduml
```

### Delete Like
![](http://www.plantuml.com/plantuml/png/LOx12i8m38RlUOeSzJ2Aro5ZCdVRpRr0RGC6OmjfDb_VoXZeAIJvlf-_B-RLbfV09LXM78Gf6S0siUbmuYSDEPbc4T8Mh-CqpYEwzUIalbmXh-7Xpj-buTZ1lx17t4XN3jHY926Z0ySZGFJcxxuGlXSh33zSrRPZYtF6dOEUKgnbFm00)
``` plantuml
@startuml
Actor Client

Client --> LikeController: DELETE /v1/like/search/<like-id>
LikeController --> LikeService: delete(id)
@enduml
```

### Return number of likes
![](http://www.plantuml.com/plantuml/png/LSwn2W8n383XFK-HKGSfhXtav5P1uUu5QYz3CJQOfkVhMpmAEWMIxuSCnO9QVJASeudYo8co0MmJ3oUyf0UDaas5cTJZxJhDwDQZutPmKMfZIgzAnU3VzdeYNLCaZr-ysyCIBDn38NnNAmb-J4ksfSTPi3iOA2_jnmy0)
``` plantuml
@startuml
Actor Client

Client -> LikeController: POST /v1/like/count request
LikeController -> LikeService: count()
database wutsi
LikeService -> wutsi: To database
@enduml
```

