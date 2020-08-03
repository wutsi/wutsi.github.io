# Publishing Stories To Channels
When authors publish stories, the story is published to website so that reader can start reading.
In parallel, the stories are publish to other channels to reach other users.
The channel supported by Wutsi
 - [Twitter](https://github.com/WutsiTeam/wutsi-blog-service/blob/master/src/main/kotlin/com/wutsi/blog/channel/service/twitter/TwitterChannelPublisher.kt)
 - [Facebook](https://github.com/WutsiTeam/wutsi-blog-service/blob/master/src/main/kotlin/com/wutsi/blog/channel/service/facebook/FacebookChannelPublisher.kt)


## Sequence Diagram
![](https://www.planttext.com/api/plantuml/img/TP512i8m44NtSufPsaKfRekKId4dADGBr3ZIG4ngCYruUvCssA9rauIVUOyVKZfkBFSF1R0NR2nMIf9cW6d7D2smzlchCfgjKOfiZkTJVS5is6Okt6GxUIkohhygwLgqzEp9CNn1iwWcEqX1EKPY4uba5TbtdPAYOMdqOV25pXCKMaH-Z3SKLjziaINm5nxLLTjeJUee7PCEGgFZm6HBu6jYINrKDV7ybCWfOpgy6qkDQ55C0E0QkghyyP6-ON12wK_-hzu0)

``` plantuml
@startuml

Actor Client

Client --> StoryController: POST /v1/story/<id>/publish request
StoryController --> StoryService: publish(request)
StoryController --> ApplicationEventPublisher: publishEvent(event: PublishEvent)
ApplicationEventPublisher --> ChannelListener: onPublish(event)
ChannelListener --> ChannelPublisherSet: publish(event)
loop foreach channel
  ChannelPublisherSet --> ChannelPublisher: publish(event)
end loop
@enduml
```

## Channel Class Diagram
![](https://www.planttext.com/api/plantuml/img/ZP512i8m44NtSufPLY4NA2A5eYi5eLuWhICDreaaqugeTxTjkh9PT1K-lFSdoMHUj9FstW20OI5trHLXNcjcQavjsHXVati3uYE4n8jrhnIBuLZ1Dw8TZ1VYO5cUIXBgY2N5AUw6DEf_4YgrdSqlIABSU8c2N6SgWeY4cuzIixOekLu2XhxpqqZ_v8Nqll-PqjhRKZm_paY0ZFZIB-a7)

```plantuml
@startuml

interface ChannelPublisher{
  publish(story: Story)
}

interface ChannelListener{
  onPublish(event: PublishEvent)
}

ChannelListener --> ChannelPublisherSet
ChannelListener --> StoryService
ChannelPublisherSet <|-- ChannelPublisher
ChannelPublisherSet *-- ChannelPublisher
ChannelPublisher <|-- TwitterChannelPublisher
ChannelPublisher <|-- FacebookChannelPublisher
ChannelPublisher <|-- FCMChannelPublisher

@enduml
```
