# Wusti Statistics Pipeline

![](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuUBYqj3ILD3LjLDmISpCgGpBJ2rFBIfs3WxZGkE3rGG0sPd59L1HDBr1gOaf8PcvgN3DI0B8kc72N6XyP3NX0G5mPN1Re7AkYKLvcNdfN9XAiQb2TMC4I2dSWJ0UiZwm69ekbzIopEHKHAWW-CWweQBub8GMfnR1b75nEQJcfG3Z0000)

- DailyViewersCSV: This process generates the [daily viewer file](https://github.com/wutsi/wutsi-stats/wiki/Viewers).
- PersistViewers: This process persists information from the daily viewer file into the database.
- DailyReadTimeCSV: This process generates the daily read-time file.
- PersistReadTime: This process persists information from the daily read-time file into the database.
- DailyXReadCSV: This process generates the daily xread file. XRead identify when user select a recommended articles from the reader.
- PersistXRead: This process persists information from the daily xread file into the database.


```plantuml
@startuml

(*) --> DailyViewersCSV
DailyViewersCSV --> PersistViewers

(*) --> DailyReadTimeCSV
DailyReadTimeCSV --> PersistReadTime
PersistReadTime --> PersistWPPReadTime

(*) --> PersistEarning
PersistWPPReadTime --> PersistEarning

(*) --> DailyXReadCSV
DailyXReadCSV --> PersistXRead

(*) --> DailyDevicesCSV
DailyDevicesCSV --> PersistDevices
DailyDevicesCSV --> PersistUserDevices

@enduml
```
