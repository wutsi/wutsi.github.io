The Track service is handling all user tracking events.

![](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuUBAoqz9LGWlBIdELAZcKW22w78GHpSf9pzTjpmrALO1MRIaA34vMxSujQWiCparbgiMgjynDx4gFyynF1XcHh0nM98Bmp1TEnn6OHLLq0Mf1nd6nUMGcfS2T340)

```plantuml
@startuml

node Wutsi {
    [wutsi-blog-web] 
    [wutsi-track-service]
}

node AmazonAWS {
    [S3]
}


[wutsi-blog-web] -> [wutsi-track-service]
[wutsi-track-service] --> [S3]


@enduml
```

# Sequence Diagram

![](http://www.plantuml.com/plantuml/png/hP4nJyCm48Lt_ueRqw6gM3kWLXKR4f5IiHltK2nSsvpFuU-JSwguQWDYO8fzzxvtz-9TOasSpqxj3GU2WxFeMQdf2-lr8nn9cuz3y4p1EQGjj2_T4JR3muQb0uIV6HEh6rrbEwJ16jn2pAblBlALkkujY0sXPYorNvZMHdJMYpa5WoarPQcLKYw42AXD3uanAfYbXUl6sXs3_WI2AINjkbEBb6nYoHwdupn5EmPjJ3vdfnd1Gsaa1JVaPMWWd0CckJNJrD5cyhBlGAXFvLK01taBWAK_ku_HMQFP1lyaiZQ_EPlwikDqR0g-VRNuLHGh1JzJC5gAybcszU8IlDoNJAgkSZML7l0EcZDU8gPU4_vFl4wi_fQlIAy3biAYpxMqiaiXArTJxiP3Fhjl)

```plantuml
@startuml
Actor Client

Client --> TrackController: POST /v1/track request
TrackController --> TrackService: push(request)
TrackService --> TrackService: createTrack(request)
TrackService --> Pipeline: process(track)

loop each step
  Pipeline --> Step: process(track)
end loop

Step --> TrackPersister: persist(track)

alt accumulate n tracks
  TrackPersister --> StoreService: store()
end alt

alt if readstart event
  TrackController --> ApplicationEventPublisher: publish(event:ViewEvent)
  ApplicationEventPublisher -> ViewListener: onView(event:ViewEvent)
  ViewListener -> ViewService: save(event:ViewEvent)
end alt
alt if share event
  TrackController --> ApplicationEventPublisher: publish(event:ShareEvent)
  ApplicationEventPublisher -> ShareListener: onShare(event:ShareEvent)
  ShareListener -> ShareService: save(event:ShareEvent)
end alt
@enduml
```

# Tracking File
``StoreService`` is storing all the tracking information to a CSV file having the following format:

- **time**: date/time in millisecond when the event was occured.
- **hitid**: ID assigned to each visit on a page.
- **deviceid**: ID of the device (phone, browser) that fired the event.
- **userid**: ID of the user who fired the event. This information is provided if user is logged in
- **page**: Name of the page where the event was fired.
- **event**: Name of the event fired. See details [here](https://github.com/wutsi/wutsi.github.io/blob/master/design/kpi/Tracking%20File.md#event)
- **productid**: ID of the product associated with the event
- **value**: Value attached with the event.
- **os**: Name of the Operating System of the device that fired the event
- **osversion**: Version of the Operating System of the device that fired the event
- **devicetype**: Type of device: `mobile` or `desktop`
- **browser**: Type of browser
- **ip**: IP of the device that fired the event
- **long**: Longitude  where the event was fired
- **lat**: Latitude where the event was fired
- **traffic**: Source of the traffic.
- **referer**: URL of the referer page
- **bot**: `true` if this event was fired by a bot
- **ua**: User Agent
- **url**: URL where the event was sent

# Events
Here is the list of events:
- **readstart**: User starts reading an article. This event is fired when user enters the page `/read/...`.
- **readend**: User stops reading an article. This event is fired when user leave the page `/read/...`.
- **scroll**: User scrolls up/down when reading an article.
- **xread**: User clicks on article recommendation after reading an article.
- **share-facebook**: User shares and article on Facebook.
- **share-messenger**: User shares and article on Messenger.
- **share-twitter**: User shares and article on Twitter.
- **share-whatsapp**: User shares and article on WhatsApp.
- **login**: User logged in.
- **g_one_tap_show**: Google One-Tap popup opened.
- **pwa_a2hs_show**: The `Add To Homescreen` panel has been displayed
- **pwa_a2hs_install**: User has installed the PWA version of the application.
- **pwa_push_show**: The push notification panel has been displayed
- **pwa_push_install**: User has enabled push notification
- **comment_click**: User click on comment button
- **comment**: User submit a comment
- **like_click**: User click on like button
- **lile**: User submit a like

# Traffic
The Traffic indicate from where the user if comming from
- **direct**: Direct traffic. User entered URL of webpage straight in browser.
- **social_media**: User is coming from social media, by clicking a link of an article showing on Social Media.
- **email**: User coming from email, by clicking a link of an article contained in an email.
- **seo**: User coming from Google/Bing etc.

# Links
- [Statistics](statistics.md)
