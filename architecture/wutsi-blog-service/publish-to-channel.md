# Publishing Stories To Channels
When authors publish stories, the story is published to website so that reader can start reading.
In parallel, the stories are publish to other channels to reach other users:
 - Social networks: Ex: Twitter, Facebook
 - Push Notifications
 - etc.

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
