# Wusti Statistics Pipeline

![](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuUBIqD9KqDMrKt19pCof3CjCBKyjAdOE3kD2uuFL103PcSKbK54qlK6fYIaXcRcfSCr80iYwOS9esYD0ud2zC1woHh0O5nUQCSWgmWC2C4s7ohac5kLbvgLpOIh5fWhLRIwfPPd9gOXWGV2HzK95yIa9BKujWYdZSaZDIm560G00)

```plantmul
@startuml

(*) --> DailyViewersCSV
DailyViewersCSV --> PersistViewers

(*) --> DailyReadTimeCSV
DailyReadTimeCSV --> PersistReadTime

(*) --> DailyXReadCSV
DailyXReadCSV --> PersistXRead

PersistReadTime --> PersistWPPReadTime

(*) --> PersistEarning
PersistWPPReadTime --> PersistEarning

(*) --> DailyDevicesCSV
DailyDevicesCSV --> PersistDevices
DailyDevicesCSV --> PersistUserDevices

@enduml
```
