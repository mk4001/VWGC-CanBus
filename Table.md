Master: Table 1

| IDs | Description | Result1 | Result2 |
| --- | --- | --- | --- |
| 18EF70C9 | Display ON/OFF |Sat ON/OFF | Lights ON/OFF |
| 18EF70EB | Sat ON/OFF | Lights ON/OFF | 
| 18EF71EB | It receives a lot of things |
| 18EF72EB | Lights ON/OFF |
| 18EF73EB |
| 18EF71C9 | Camping Mode ON/OFF | WiFi ON/OFF | SoundSystem ON/OFF/BT |
| 18EF71EB | Camping Mode ON/OFF | WiFi ON/OFF | SoundSystem ON/OFF/BT |
| 18EF72EB | 230V ON/OFF |
| 18EF73EB | 230V ON/OFF | Grey Water Level at 7ºByte with 1º Byte=01 |

------

Messages: Table 2
| Content | IDs | Message | means | note |
| --- | --- | --- | --- | --- |
| Waters level %|18EF73EB|00 00 00 00 0B 00 04 00|ClearW = 11% 4ºB - GreyW = 4% 6ºB - ClearW is EMPTY if 0ºB = 01|
| Battery Current (A)|18EF72EB|50 00 00 8A 59 00 07 02|The 6º Byte is the Ampere [+], the 0ºB > 0 = charging|Charging
| Battery Current (A)|18EF72EB|00 00 00 0A 4C 00 FF 01|The 6º Byte are the Amperes [-] where FF=-1, FE=-2, FD=-3... MOD 2|Discharging
| rem time battery|18EF70EB|01 00 3A 26 00 00 00 00|The 2ºB is h, the 3ºB min|
| Battery Voltage (V)|18EF72EB|00 00 00 0A 50 00 FF 01|Value in 5B translated into DEC: the ten +5 and you get the whole part, the unit is the decimal part.|
| Battery percentage|18EF72EB|00 00 00 0A 50 00 FF 01|Value in 4B is the percentage /10 (ES: 0A -> 10*10 = 100)|
| Display goes ON|18EF70C9|00 40 00 00 00 00 00 00|using I/O Button|
| Display goes OFF|18EF70C9|00 00 00 00 00 00 00 00|using I/O Button|
| Door Locked|18EF70EB|00 04 3A 26 00 00 00 00|1B = 04 and then: 00|
| Set Color|18EF60C9|1E.00.64.2F.00.00.00.00|Set to color Y|
| Set Color|18EF60C9|08.00.64.25.00.00.00.00|Set to color R|
| Set Color|18EF60C9|7D.00.64.23.00.00.00.00|Set to color G|
| Set Color|18EF60C9|F5.00.64.2F.00.00.00.00|Set to color B|

------

Commands: Table 3
| Content | 1º seq | 2º seq | result |
| --- | --- | --- | --- |
| Camping Mode ON/OFF | cansend can0 18EF71C9#00.40.00.00.00.00.00.00|||
| WiFi ON/OFF | cansend can0 18EF71C9#00.01.00.00.00.00.00.00 | cansend can0 18EF71C9#00.00.00.00.00.00.00.00 | ON |
| SAT ON/OFF | cansend can0 18EF70C9#00.50.00.00.00.00.00.00 | | OK |
| Step Auto ON/OFF | cansend can0 18EF71C9#04.00.00.00.00.00.00.00 | cansend can0 18EF71C9#00.00.00.00.00.00.00.00| |
| Step OUT | cansend can0 18EF71C9#10.00.00.00.00.00.00.00 |||
| Step IN | cansend can0 18EF71C9#40.00.00.00.00.00.00.00 |||
| Ambient Lights ON/OFF | cansend can0 18EF70C9#04.40.00.00.00.00.00.00 | | OK |
| External Lights ON/OFF | cansend can0 18EF70C9#00.41.00.00.00.00.00.00 | cansend can0 18EF70C9#00.40.00.00.00.00.00.00 | OK |
| Internal Lights ON/OFF | cansend can0 18EF70C9#01.40.00.00.00.00.00.00 | | so&so |
