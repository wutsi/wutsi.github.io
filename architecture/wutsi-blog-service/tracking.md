The Tracking API is used to collecting all users events and store them into CSV files.
Those files are later analyse for extracting valuable statistics.

# Sequence Diagram

![](https://www.planttext.com/api/plantuml/img/VL6vRiCm3Dtv5HoTmGYwUWWI19rhm45tLILWeOgaK9Jx-z4HE6bJT1Br-0uIt4THBEbi0GvQFEFH6d82q5xi-nsUMEcletV2tbhY0SUtwOJRvMKhfODCbqHHu1Vlhfs85wDfm93YtDte6tZi_K7MJ4geOlzeHXF86bVCsMkAiQj3RG2izm59wHcZK01SgLKtPUn9G-uJYmoWjEypZSJHP9UyUsZbcgAieD8wdPFDqwB3seWvxgVo5kgPrWLZ-NKjDTiqhyNGTqzBkG7YqxQ74ApHIenthuKpfWzhubm7QsM5ksemu7isgy132EnpcGz-1G00)

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

alt if view-event
  TrackService --> ApplicationEventPublisher: publishEvent(event: ViewEvent)
end alt

@enduml
```
