# Important note

The data saved in this file is little-endian, meaning that `0xabcd` $= c \times 16^3 + d \times 16^2 + a \times 16^1 + b \times 16^0$.

The addresses in this list are big-endian.

# Locations

Identified locations.

| Address    | Length | Value                      | Notes                                                                                                                                                                                                                                      |
| ---------- | ------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0x00000050 | 4      | Seconds played             | The in game timers round up to the minute. The timers use it as a signed integer, but the bliss challenges use it as an unsigned integer, meaning that you can have spent 100 hours in Reveria with 0 minutes (-1 seconds) played.         |
| 0x0001fb60 | 6      | Dashing skill              | [Skills](#skills)                                                                                                                                                                                                                          |
| 0x0001fbc8 | 6      | Sneaking skill             | [Skills](#skills)                                                                                                                                                                                                                          |
| 0x0001fccb | 4      | Money                      |                                                                                                                                                                                                                                            |
| 0x0001fcd0 | 4      | Money earned               | All-time money earned.                                                                                                                                                                                                                     |
| 0x00021f30 | 3      | "New" lives                | Seems to be an array of bools representing whether or not a player has checked out the "New" lives unlocked. True means that they **haven't**. Lives are sorted by "class" (1st byte = combat, 2nd byte = crafting, 3rd byte = gathering). |
| 0x00021f4a | 14?    | "New" skills/bliss bonuses | Seems to be an array of bools representing whether or not a player has checked the "New" skills/bliss bonuses/etc unlocked. True means that they **have**.                                                                                 |

# Data structures

## Skills

| Shift | Length | Value        | Notes                                                                                                                                                      |
| ----- | ------ | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0     | 4      | Experience   | This is a float.                                                                                                                                           |
| 4     | 1      | Level        | A negative value (leading 1) represents not having the skill. Any value above the maximum level (either 15 or 20) seems to be brought back to the maximum. |
| 5     | 1      | Unidentified | Probably some flags?                                                                                                                                       |
