# Wusti Statistics Pipeline

![](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuUBYqj3ILD3LjLDmISpCgGpBJ2rFBIfs3WxZGkE3rGG0sPd59L1HDBr1gOaf8PcvgN3DI0B8kc72N6XyP3NX0G5mPN1Re7AkYKLvcNdfN9XAiQb2TMC4I2dSWJ0UiZwm69ekbzIopEHKHAWW-CWweQBub8GMfnR1b75nEQJcfG3Z0000)

- DailyViewersCSV: This process generates the [daily viewer CSV file](https://github.com/wutsi/wutsi-stats/wiki/Viewers).
- PersistViewers: This process transfer the daily viewer CSV file into the database.
- DailyReadTimeCSV: This process generates the daily read-time CSV file. The file contains the total duration time per story.
- PersistReadTime: This process transfer the daily read-time CSV file into the database.
- PersistWPPReadTime: This process compute the readtime for all monetized stories and store it into the DB.
- PersistEarning: This process compute earnings per user.
- DailyXReadCSV: This process generates the daily xread CSV file. XRead identify when user select a recommended articles from the reader.
- PersistXRead: This process transfer the daily xread CSV file into the database.
- DailyDevicesCSV: This process generates the [device CSV file](https://github.com/wutsi/wutsi-stats/wiki/Devices).
- PersistDevices: This process transfer the daily device CSV file into the database.
- PersistUserDevices: This process store into the database the association between users and their device.


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
