# Unofficial AIRA Modular Effects MIDI Implementation v1.2

December 27th, 2018

------

This contents of this publication has no relations with Roland Corporation. Please do not send any inquiries to Roland Corp. Should you have any questions, please send them to myself, Mugenkidou([mugenkidou.wakakusa@gmail.com](mailto:mugenkidou.wakakusa@gmail.com))
When operating MIDI devices according to this publication's contents, please make sure to make any necessary  backups and proceed at your own risk. We will not take any responsibility for any data loss, hardware failure, or other damage.

------

**Table of contents**

* [Commands](#Commands)
* [Main Module](#Main-Module)
* [Sub Module](#Sub-Modules)
* [Patching Operation](#Patching-Operation)
* [Patch Cable Condition](#Patch-Cable-Condition)

------



# Commands

## Data Request 1(RQ1)

F0H, 41H, 10H, 00H, 00H, 00H, idH, 11H, aaH, bbH, ccH, ddH, ssH, ttH, uuH, vvH, sum, F7H

| Offset     | Value | Description      |
| :---------- | --------- | ---------------- |
| 0 | F0 | Exclusive status |
| 1 | 41 | ID number (Roland) |
| 2 | 10 | Device ID (dev: 10H, 7FH) |
| 3 | 00 | Model ID #1 : 00H |
| 4 | 00 | Model ID #2 : 00H |
| 5 | 00 | Model ID #3 : 00H |
| 6 | id | Model ID #4 : 15H - 18H (BITRAZER, DEMORA, TORCIDO, SCOOPER) |
| 7 | 11 | Command ID (RQ1) |
| 8 | aa | Address MSB |
| 9 | bb | Address |
| 10 | cc | Address |
| 11 | dd | Address LSB |
| 12 | ss | Size MSB |
| 13 | tt | Size |
| 14 | uu | Size |
| 15 | vv | Size LSB |
| 16 | sum | Checksum |
| 17 | F7 | EOX (End Of Exclusive) |





## Data Set 1(DT1)

F0H, 41H, 10H, 00H, 00H, 00H, idH, 12H, aaH, bbH, ccH, ddH, eeH, ... , ffH, sum, F7H

| Offset     | Value | Description      |
| :---------- | --------- | ---------------- |
| 0 | F0 | Exclusive status |
| 1 | 41 | ID number (Roland) |
| 2 | 10 | Device ID (dev: 10H, 7FH) |
| 3 | 00 | Model ID #1 : 00H |
| 4 | 00 | Model ID #2 : 00H |
| 5 | 00 | Model ID #3 : 00H |
| 6 | id | Model ID #4 : 15H - 18H (BITRAZER, DEMORA, TORCIDO, SCOOPER) |
| 7 | 12 | Command ID (DT1) |
| 8 | aa | Address MSB |
| 9 | bb | Address |
| 10 | cc | Address |
| 11 | dd | Address LSB |
| 12 | ee | Data |
|  | ... |  |
|  | ff | Data |
|  | sum | Checksum |
|  | F7 | EOX (End Of Exclusive)] |


#Main Module

| Address     |           | Description |
| :---------- | --------- | ----------- |
| 10 00 00 01 | 0aaa aaaa | PARAMETER 1 |
| 10 00 00 02 | 0aaa aaaa | PARAMETER 2 |
| 10 00 00 03 | 0aaa aaaa | PARAMETER 3 |
| 10 00 00 04 | 0aaa aaaa | PARAMETER 4 |
| 10 00 00 05 | 0aaa aaaa | PARAMETER 5 |
| 10 00 00 06 | 0aaa aaaa | PARAMETER 6 |
| 10 00 00 07 | 0aaa aaaa | PARAMETER 7 |
| 10 00 00 08 | 0aaa aaaa | PARAMETER 8 |



## Main Module Parameters

| PARAMETER    | BITRAZOR            | DEMORA         | SCOOPER             | TORCIDO         |
| ------------ | ------------------- | -------------- | ------------------- | --------------- |
| PARAMETER 1  | LPF/HPF             | HOLD           | SYNC TRIG           | LO BOOST        |
| PARAMETER 2  | BYPASS              | BYPASS         | SCATTER             | BYPASS          |
| PARAMETER 3  | SAMPLE RATE         | TIME           | SCATTER DEPTH       | DIST            |
| PARAMETER 4  | FILTER CUTOFF       | FEEDBACK       | SCATTER TYPE        | TONE            |
| PARAMETER 5  | RATE DOWN           | WIDTH          | PITCH               | TUBE WARM       |
| PARAMETER 6  | RESONANCE           | DRY/WET        | FILTER              | DRY/WET         |
| PARAMETER 7  | SAMPLE RATE LEVEL   | TIME LEVEL     | SCATTER DEPTH LEVEL | DIST LEVEL      |
| PARAMETER 8  | FILTER CUTOFF LEVEL | FEEDBACK LEVEL | SCATTER TYPE LEVEL  | TONE LEVEL      |
| PARAMETER 9  | RATE DOWN LEVEL     | WIDTH LEVEL    | PITCH LEVEL         | TUBE WARM LEVEL |
| PARAMETER 10 | RESONANCE LEVEL     | DRY/WET LEVEL  | FILTER LEVEL        | DRY/WET LEVEL   |



# Sub Modules

| Address     |           | Description  |
| :---------- | --------- | ------------ |
| 10 10 00 00 | 000a aaaa | SUB MODULE 1 TYPE|
| 10 10 00 01 | 0aaa aaaa | SUB MODULE 1 PARAMETER 1 |
| 10 10 00 02 | 0aaa aaaa | SUB MODULE 1 PARAMETER 2 |
| 10 10 00 03 | 0aaa aaaa | SUB MODULE 1 PARAMETER 3 |
| 10 10 00 04 | 0aaa aaaa | SUB MODULE 1 PARAMETER 4 |
| 10 10 00 05 | 000a aaaa | SUB MODULE 2 TYPE|
| 10 10 00 06 | 0aaa aaaa | SUB MODULE 2 PARAMETER 1 |
| 10 10 00 07 | 0aaa aaaa | SUB MODULE 2 PARAMETER 2 |
| 10 10 00 08 | 0aaa aaaa | SUB MODULE 2 PARAMETER 3 |
| 10 10 00 09 | 0aaa aaaa | SUB MODULE 2 PARAMETER 4 |
| 10 10 00 0A | 000a aaaa | SUB MODULE 3 TYPE|
| 10 10 00 0B | 0aaa aaaa | SUB MODULE 3 PARAMETER 1 |
| 10 10 00 0C | 0aaa aaaa | SUB MODULE 3 PARAMETER 2 |
| 10 10 00 0D | 0aaa aaaa | SUB MODULE 3 PARAMETER 3 |
| 10 10 00 0E | 0aaa aaaa | SUB MODULE 3 PARAMETER 4 |
| 10 10 00 0F | 000a aaaa | SUB MODULE 4 TYPE|
| 10 10 00 10 | 0aaa aaaa | SUB MODULE 4 PARAMETER 1 |
| 10 10 00 11 | 0aaa aaaa | SUB MODULE 4 PARAMETER 2 |
| 10 10 00 12 | 0aaa aaaa | SUB MODULE 4 PARAMETER 3 |
| 10 10 00 13 | 0aaa aaaa | SUB MODULE 4 PARAMETER 4 |
| 10 10 00 14 | 000a aaaa | SUB MODULE 5 TYPE|
| 10 10 00 15 | 0aaa aaaa | SUB MODULE 5 PARAMETER 1 |
| 10 10 00 16 | 0aaa aaaa | SUB MODULE 5 PARAMETER 2 |
| 10 10 00 17 | 0aaa aaaa | SUB MODULE 5 PARAMETER 3 |
| 10 10 00 18 | 0aaa aaaa | SUB MODULE 5 PARAMETER 4 |
| 10 10 00 19 | 000a aaaa | SUB MODULE 6 TYPE|
| 10 10 00 1A | 0aaa aaaa | SUB MODULE 6 PARAMETER 1 |
| 10 10 00 1B | 0aaa aaaa | SUB MODULE 6 PARAMETER 2 |
| 10 10 00 1C | 0aaa aaaa | SUB MODULE 6 PARAMETER 3 |
| 10 10 00 1D | 0aaa aaaa | SUB MODULE 6 PARAMETER 4 |



## Sub Module Parameters

|      | Sub Module Type        | Parameter 1      | Parameter 2   | Parameter 3   | Parameter 4  |
| ---- | ---------------------- | ---------------- | ------------- | ------------- | ------------ |
| 00   | EMPTY                  | -                | -             | -             | -            |
| 01   | LFO                    | WAVE             | RATE          | MOD IN LEVEL  | OUTPUT LEVEL |
| 02   | ADSR                   | ATTACK           | DECAY         | SUSTAIN       | RELEASE      |
| 03   | NOISE                  | TYPE 1           | TYPE 2        | LEVEL 1       | LEVEL 2      |
| 04   | SAMPLE & HOLD          | RATE             | MOD IN LEVEL  | TRIGGER IN SW | -            |
| 05   | RING MOD               | MOD SW           | -             | -             | -            |
| 06   | FILTER 6dB             | TYPE             | CUTOFF        | MOD IN        | RESONANCE    |
| 07   | FILTER 12dB            | TYPE             | CUTOFF        | MOD IN        | RESONANCE    |
| 08   | TONE                   | TYPE             | FREQUENCY     | LEVEL         | -            |
| 09   | AMP                    | AMP 1            | AMP 2         | LEVEL 1       | LEVEL 2      |
| 10   | MIXER                  | LEVEL 1          | LEVEL 2       | LEVEL 3       | LEVEL 4      |
| 11   | STEREO MIXER           | LEVEL 1          | LEVEL 2       | PAN 1         | PAN 2        |
| 12   | CURVE CONV             | CURVE TYPE       | REVERSE SW    | -             | -            |
| 13   | GATE DIVIDER           | MULTIPLE/DIVIDE  | -             | -             | -            |
| 14   | TRIG TO CV DELAY TIME  | MULTIPLE/DIVIDE  | -             | -             | -            |
| 17   | TUBE CLIP              | GAIN             | OUTPUT LEVEL  | -             | -            |
| 18   | COMPRESSOR             | THRESHOLD        | RATIO         | ATTACK        | RELEASE      |
| 19   | NOISE GATE             | THRESHOLD        | DECAY         | -             | -            |
| 20   | 3 BAND EQ              | HI               | MID           | LOW           | -            |
| 21   | LOGIC OPERATION        | INPUT LEVEL 1    | INPUT LEVEL 2 | LOGIC TYPE    | OUTPUT       |
| 22   | CROSS FADER            | CROSS FADE       | CURVE TYPE    | -             | -            |
| 23   | SWITCHER               | ON OFF SW        | SW TYPE       | -             | -            |
| 24   | ENVELOPER              | THRESHOLD        | RELEASE       | OUTPUT LEVEL  | -            |
| 25   | TRIGGER TO LFO RATE CV | MULTIPLE /DIVIDE | -             | -             | -            |
| 26   | FILTER 18dB            | TYPE             | CUTOFF        | MOD IN        | RESONANCE    |
| 27   | FILTER 24dB            | TYPE             | CUTOFF        | MOD IN        | RESONANCE    |
| 28   | FORMANT FILTER         | FORMANT 1        | FORMANT 2     | BALANCE       | -            |
| 29   | SAW OSCILLATOR         | RANGE            | FINE          | COLOR         | OUTPUT LEVEL |
| 30   | SQR OSCILLATOR         | RANGE            | FINE          | COLOR         | OUTPUT LEVEL |
| 31   | MIDI NOTE TO CV/GATE   | OCTAVE           | TRANSPOSE     | GATE POLARITY | -            |



# Patching Operation


| Address     |   |                           Description                       |
|-------------|----|------------------------------------------------------------|
| 10 20 ss dd | 0000 000a |  0 - 1 (DISCONNECT, CONNECT) |

Connect or disconnect ss and dd by virtual patch cable.



## Patching Source(ss)

| ss   | Patching Source   |
| ---- | ----------------- |
| 00   | INPUT 1           |
| 01   | INPUT 2           |
| 02   | GRF 1             |
| 03   | GRF 2             |
| 04   | GRF 3             |
| 05   | GRF 4             |
| 06   | GRF 5             |
| 07   | GRF 6             |
| 08   | MAIN MODULE OUT 1 |
| 09   | MAIN MODULE OUT 2 |
| 0A   | SUB MODULE1 OUT 1 |
| 0B   | SUB MODULE1 OUT 2 |
| 0C   | SUB MODULE2 OUT 1 |
| 0D   | SUB MODULE2 OUT 2 |
| 0E   | SUB MODULE3 OUT 1 |
| 0F   | SUB MODULE3 OUT 2 |
| 10   | SUB MODULE4 OUT 1 |
| 11   | SUB MODULE4 OUT 2 |
| 12   | SUB MODULE5 OUT 1 |
| 13   | SUB MODULE5 OUT 2 |
| 14   | SUB MODULE6 OUT 1 |
| 15   | SUB MODULE6 OUT 2 |



##Patching Destination(dd)

| dd   | Patching Destination |
| ---- | -------------------- |
| 00   | OUTPUT 1             |
| 01   | OUTPUT 2             |
| 02   | MAIN MODULE IN 1     |
| 03   | MAIN MODULE IN 2     |
| 04   | MAIN MODULE IN 3     |
| 05   | MAIN MODULE IN 4     |
| 06   | MAIN MODULE IN 5     |
| 07   | MAIN MODULE IN 6     |
| 08   | MAIN MODULE IN 7     |
| 09   | MAIN MODULE IN 8     |
| 0A   | SUB MODULE 1 IN 1    |
| 0B   | SUB MODULE 1 IN 2    |
| 0C   | SUB MODULE 1 IN 3    |
| 0D   | SUB MODULE 1 IN 4    |
| 0E   | SUB MODULE 2 IN 1    |
| 0F   | SUB MODULE 2 IN 2    |
| 10   | SUB MODULE 2 IN 3    |
| 11   | SUB MODULE 2 IN 4    |
| 12   | SUB MODULE 3 IN 1    |
| 13   | SUB MODULE 3 IN 2    |
| 14   | SUB MODULE 3 IN 3    |
| 15   | SUB MODULE 3 IN 4    |
| 16   | SUB MODULE 4 IN 1    |
| 17   | SUB MODULE 4 IN 2    |
| 18   | SUB MODULE 4 IN 3    |
| 19   | SUB MODULE 4 IN 4    |
| 1A   | SUB MODULE 5 IN 1    |
| 1B   | SUB MODULE 5 IN 2    |
| 1C   | SUB MODULE 5 IN 3    |
| 1D   | SUB MODULE 5 IN 4    |
| 1E   | SUB MODULE 6 IN 1    |
| 1F   | SUB MODULE 6 IN 2    |
| 20   | SUB MODULE 6 IN 3    |
| 21   | SUB MODULE 6 IN 4    |



# Patch Cable Condition

| Address     |             |                 Description                       |
|-------------|-------------|--------------------------------------------------|
| 10 21 00 00 | 0aaa aaaa | INPUT 1 PATCH CABLE CONDITION 1                    |
| 10 21 00 01 | 0bbb bbbb | INPUT 1 PATCH CABLE CONDITION 2                    |
| 10 21 00 02 | 0ccc cccc | INPUT 1 PATCH CABLE CONDITION 3                    |
| 10 21 00 03 | 0ddd dddd | INPUT 1 PATCH CABLE CONDITION 4                    |
| 10 21 00 04 | 0eee eeee | INPUT 1 PATCH CABLE CONDITION 5                    |
| 10 21 00 05 | 0fff ffff | INPUT 1 PATCH CABLE CONDITION 6                    |
| 10 21 00 06 | 0aaa aaaa | INPUT 2 PATCH CABLE CONDITION 1                    |
| 10 21 00 07 | 0bbb bbbb | INPUT 2 PATCH CABLE CONDITION 2                    |
| 10 21 00 08 | 0ccc cccc | INPUT 2 PATCH CABLE CONDITION 3                    |
| 10 21 00 09 | 0ddd dddd | INPUT 2 PATCH CABLE CONDITION 4                    |
| 10 21 00 0A | 0eee eeee | INPUT 2 PATCH CABLE CONDITION 5                    |
| 10 21 00 0B | 0fff ffff | INPUT 2 PATCH CABLE CONDITION 6                    |
| 10 21 00 0C | 0aaa aaaa | GRF 1 PATCH CABLE CONDITION 1                      |
| 10 21 00 0D | 0bbb bbbb | GRF 1 PATCH CABLE CONDITION 2                      |
| 10 21 00 0E | 0ccc cccc | GRF 1 PATCH CABLE CONDITION 3                      |
| 10 21 00 0F | 0ddd dddd | GRF 1 PATCH CABLE CONDITION 4                      |
| 10 21 00 10 | 0eee eeee | GRF 1 PATCH CABLE CONDITION 5                      |
| 10 21 00 11 | 0fff ffff | GRF 1 PATCH CABLE CONDITION 6                      |
| 10 21 00 12 | 0aaa aaaa | GRF 2 PATCH CABLE CONDITION 1                      |
| 10 21 00 13 | 0bbb bbbb | GRF 2 PATCH CABLE CONDITION 2                      |
| 10 21 00 14 | 0ccc cccc | GRF 2 PATCH CABLE CONDITION 3                      |
| 10 21 00 15 | 0ddd dddd | GRF 2 PATCH CABLE CONDITION 4                      |
| 10 21 00 16 | 0eee eeee | GRF 2 PATCH CABLE CONDITION 5                      |
| 10 21 00 17 | 0fff ffff | GRF 2 PATCH CABLE CONDITION 6                      |
| 10 21 00 18 | 0aaa aaaa | GRF 3 PATCH CABLE CONDITION 1                      |
| 10 21 00 19 | 0bbb bbbb | GRF 3 PATCH CABLE CONDITION 2                      |
| 10 21 00 1A | 0ccc cccc | GRF 3 PATCH CABLE CONDITION 3                      |
| 10 21 00 1B | 0ddd dddd | GRF 3 PATCH CABLE CONDITION 4                      |
| 10 21 00 1C | 0eee eeee | GRF 3 PATCH CABLE CONDITION 5                      |
| 10 21 00 1D | 0fff ffff | GRF 3 PATCH CABLE CONDITION 6                      |
| 10 21 00 1E | 0aaa aaaa | GRF 4 PATCH CABLE CONDITION 1                      |
| 10 21 00 1F | 0bbb bbbb | GRF 4 PATCH CABLE CONDITION 2                      |
| 10 21 00 20 | 0ccc cccc | GRF 4 PATCH CABLE CONDITION 3                      |
| 10 21 00 21 | 0ddd dddd | GRF 4 PATCH CABLE CONDITION 4                      |
| 10 21 00 22 | 0eee eeee | GRF 4 PATCH CABLE CONDITION 5                      |
| 10 21 00 23 | 0fff ffff | GRF 4 PATCH CABLE CONDITION 6                      |
| 10 21 00 24 | 0aaa aaaa | GRF 5 PATCH CABLE CONDITION 1                      |
| 10 21 00 25 | 0bbb bbbb | GRF 5 PATCH CABLE CONDITION 2                      |
| 10 21 00 26 | 0ccc cccc | GRF 5 PATCH CABLE CONDITION 3                      |
| 10 21 00 27 | 0ddd dddd | GRF 5 PATCH CABLE CONDITION 4                      |
| 10 21 00 28 | 0eee eeee | GRF 5 PATCH CABLE CONDITION 5                      |
| 10 21 00 29 | 0fff ffff | GRF 5 PATCH CABLE CONDITION 6                      |
| 10 21 00 2A | 0aaa aaaa | GRF 6 PATCH CABLE CONDITION 1                      |
| 10 21 00 2B | 0bbb bbbb | GRF 6 PATCH CABLE CONDITION 2                      |
| 10 21 00 2C | 0ccc cccc | GRF 6 PATCH CABLE CONDITION 3                      |
| 10 21 00 2D | 0ddd dddd | GRF 6 PATCH CABLE CONDITION 4                      |
| 10 21 00 2E | 0eee eeee | GRF 6 PATCH CABLE CONDITION 5                      |
| 10 21 00 2F | 0fff ffff | GRF 6 PATCH CABLE CONDITION 6                      |
| 10 21 00 30 | 0aaa aaaa | MAIN MODULE OUT 1 PATCH CABLE CONDITION 1          |
| 10 21 00 31 | 0bbb bbbb | MAIN MODULE OUT 1 PATCH CABLE CONDITION 2          |
| 10 21 00 32 | 0ccc cccc | MAIN MODULE OUT 1 PATCH CABLE CONDITION 3          |
| 10 21 00 33 | 0ddd dddd | MAIN MODULE OUT 1 PATCH CABLE CONDITION 4          |
| 10 21 00 34 | 0eee eeee | MAIN MODULE OUT 1 PATCH CABLE CONDITION 5          |
| 10 21 00 35 | 0fff ffff | MAIN MODULE OUT 1 PATCH CABLE CONDITION 6          |
| 10 21 00 36 | 0aaa aaaa | MAIN MODULE OUT 2 PATCH CABLE CONDITION 1          |
| 10 21 00 37 | 0bbb bbbb | MAIN MODULE OUT 2 PATCH CABLE CONDITION 2          |
| 10 21 00 38 | 0ccc cccc | MAIN MODULE OUT 2 PATCH CABLE CONDITION 3          |
| 10 21 00 39 | 0ddd dddd | MAIN MODULE OUT 2 PATCH CABLE CONDITION 4          |
| 10 21 00 3A | 0eee eeee | MAIN MODULE OUT 2 PATCH CABLE CONDITION 5          |
| 10 21 00 3B | 0fff ffff | MAIN MODULE OUT 2 PATCH CABLE CONDITION 6          |
| 10 21 00 3C | 0aaa aaaa | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 3D | 0bbb bbbb | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 3E | 0ccc cccc | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 3F | 0ddd dddd | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 40 | 0eee eeee | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 41 | 0fff ffff | SUB MODULE 1 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 42 | 0aaa aaaa | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 43 | 0bbb bbbb | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 44 | 0ccc cccc | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 45 | 0ddd dddd | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 46 | 0eee eeee | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 47 | 0fff ffff | SUB MODULE 1 OUT 2 PATCH CABLE CONDITION 6         |
| 10 21 00 48 | 0aaa aaaa | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 49 | 0bbb bbbb | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 4A | 0ccc cccc | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 4B | 0ddd dddd | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 4C | 0eee eeee | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 4D | 0fff ffff | SUB MODULE 2 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 4E | 0aaa aaaa | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 4F | 0bbb bbbb | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 50 | 0ccc cccc | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 51 | 0ddd dddd | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 52 | 0eee eeee | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 53 | 0fff ffff | SUB MODULE 2 OUT 2 PATCH CABLE CONDITION 6         |
| 10 21 00 54 | 0aaa aaaa | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 55 | 0bbb bbbb | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 56 | 0ccc cccc | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 57 | 0ddd dddd | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 58 | 0eee eeee | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 59 | 0fff ffff | SUB MODULE 3 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 5A | 0aaa aaaa | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 5B | 0bbb bbbb | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 5C | 0ccc cccc | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 5D | 0ddd dddd | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 5E | 0eee eeee | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 5F | 0fff ffff | SUB MODULE 3 OUT 2 PATCH CABLE CONDITION 6         |
| 10 21 00 60 | 0aaa aaaa | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 61 | 0bbb bbbb | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 62 | 0ccc cccc | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 63 | 0ddd dddd | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 64 | 0eee eeee | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 65 | 0fff ffff | SUB MODULE 4 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 66 | 0aaa aaaa | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 67 | 0bbb bbbb | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 68 | 0ccc cccc | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 69 | 0ddd dddd | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 6A | 0eee eeee | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 6B | 0fff ffff | SUB MODULE 4 OUT 2 PATCH CABLE CONDITION 6         |
| 10 21 00 6C | 0aaa aaaa | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 6D | 0bbb bbbb | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 6E | 0ccc cccc | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 6F | 0ddd dddd | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 70 | 0eee eeee | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 71 | 0fff ffff | SUB MODULE 5 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 72 | 0aaa aaaa | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 73 | 0bbb bbbb | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 74 | 0ccc cccc | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 75 | 0ddd dddd | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 76 | 0eee eeee | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 77 | 0fff ffff | SUB MODULE 5 OUT 2 PATCH CABLE CONDITION 6         |
| 10 21 00 78 | 0aaa aaaa | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 1         |
| 10 21 00 79 | 0bbb bbbb | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 2         |
| 10 21 00 7A | 0ccc cccc | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 3         |
| 10 21 00 7B | 0ddd dddd | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 4         |
| 10 21 00 7C | 0eee eeee | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 5         |
| 10 21 00 7D | 0fff ffff | SUB MODULE 6 OUT 1 PATCH CABLE CONDITION 6         |
| 10 21 00 7E | 0aaa aaaa | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 1         |
| 10 21 00 7F | 0bbb bbbb | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 2         |
| 10 21 00 80 | 0ccc cccc | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 3         |
| 10 21 00 81 | 0ddd dddd | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 4         |
| 10 21 00 82 | 0eee eeee | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 5         |
| 10 21 00 83 | 0fff ffff | SUB MODULE 6 OUT 2 PATCH CABLE CONDITION 6         |



## Patch Cable Condition Description

| Bits      |Description |Value                                       |
|----------|-----------------------------------------------------------------|-----------------------------------------------------------------|
| 0aaa aaaa |    |                                                            |
|     bit 7 | -  | - |
|     bit 6 | -  | - |
|     bit 5 | -  | - |
|     bit 4 | -  | - |
|     bit 3 | SUB MODULE 2 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | SUB MODULE 2 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | SUB MODULE 2 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
| 0bbb bbbb |    |                                                            |
|     bit 7 | SUB MODULE 1 IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 6 | SUB MODULE 1 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 5 | SUB MODULE 1 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 4 | SUB MODULE 1 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 3 | MAIN MODULE MOD IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | MAIN MODULE MOD IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | MAIN MODULE MOD IN 3| 0 - 1 (NOT CONNECTED, CONNECTED) |
| 0ccc cccc |    |                                                            |
|     bit 7 | MAIN MODULE MOD IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 6 | MAIN MODULE MOD IN 5 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 5 | MAIN MODULE MOD IN 6 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 4 | MAIN MODULE IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 3 | MAIN MODULE IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | OUTPUT 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | OUTPUT 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
| 0ddd dddd |    |                                                            |
|     bit 7 | -  | - |
|     bit 6 | -  | - |
|     bit 5 | -  | - |
|     bit 4 | -  | - |
|     bit 3 | SUB MODULE 6 IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | SUB MODULE 6 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | SUB MODULE 6 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
| 0eee eeee |    |                                                            |
|     bit 7 | SUB MODULE 6 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 6 | SUB MODULE 5 IN 4| 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 5 | SUB MODULE 5 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 4 | SUB MODULE 5 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 3 | SUB MODULE 5 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | SUB MODULE 4 IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | SUB MODULE 4 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
| 0fff ffff |    |                                                            |
|     bit 7 | SUB MODULE 4 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 6 | SUB MODULE 4 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 5 | SUB MODULE 3 IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 4 | SUB MODULE 3 IN 3 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 3 | SUB MODULE 3 IN 2 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 2 | SUB MODULE 3 IN 1 | 0 - 1 (NOT CONNECTED, CONNECTED) |
|     bit 1 | SUB MODULE 2 IN 4 | 0 - 1 (NOT CONNECTED, CONNECTED) |



## Sub Module Ins
| Sub Module Type |Sub Module In 1 | Sub Module In 2 | Sub Module In 3 | Sub Module In 4 |
|-----|----|----|----|----|
| EMPTY       | -          | -          | -          | -          |
| LFO         | RATE       | SYNC TRG IN  | WAVE       | -          |
| ADSR        | GATE IN    | ATTACK     | DECAY      | RELEASE    |
| NOISE       | TYPE 1     | TYPE 2     | LEVEL 1    | LEVEL 2    |
| SAMPLE& HOLD      | AUDIO IN 1 | AUDIO IN 2 | MOD IN     | TRIGGER IN |
| RING MOD    | AUDIO IN   | AUDIO MOD IN | MOD SW TRIGGER IN | -          |
| FILTER 6dB  | AUDIO IN 1 | AUDIO IN 2 | MOD IN     | RESONANCE IN |
| FILTER 12dB | AUDIO IN 1 | AUDIO IN 2 | MOD IN     | RESONANCE IN |
| TONE        | AUDIO IN 1 | AUDIO IN 2 | FREQUENCY IN | LEVEL IN   |
| AMP         | AMP IN1    | AMP IN2    | AUDIO/CV IN1 | AUDIO/CV IN2 |
| MIXER       | AUDIO IN1  | AUDIO IN2  | AUDIO IN3  | AUDIO IN4  |
| STEREO MIXER | AUDIO IN1-L | AUDIO IN1-R | AUDIO IN2-L | AUDIO IN2-R |
| CURVE CONV  | CV IN 1    | CV IN 2    | CURVE TYPE IN | -          |
| GATE DIVIDER | TRIGGER IN | MULTIPLE/DIVIDE IN | -          | -          |
| TRIG TO CV DELAY TIME | TRIGGER IN | MULTIPLE/DIVIDE IN | -          | -          |
| MIDI CLOCK TO GATE | MULTIPLE/DIVIDE IN | -          | -          | -          |
| SHORT DELAY | AUDIO IN   | DELAY TIME IN | FEEDBACK IN | DRY/WET IN |
| TUBE CLIP   | AUDIO IN1  | AUDIO IN2  | GAIN IN    | OUTPUT LEVEL IN |
| COMPRESSOR  | AUDIO IN1  | AUDIO IN2  | THRESHOLD IN | -          |
| NOISE GATE  | AUDIO IN1  | AUDIO IN2  | THRESHOLD IN | DECAY IN   |
| 3 BAND EQ   | AUDIO IN   | HI IN      | MID IN     | LOW IN     |
| LOGIC OPERATION | AUDIO IN1  | AUDIO IN2  | LOGIC TYPE IN | OUTPUT LEVEL IN |
| CROSS FADER | AUDIO IN1  | AUDIO IN2  | CROSS FADE IN | -          |
| SWITCHER    | AUDIO/CV IN1 | AUDIO/CV IN2 | ON OFF SW TRIGGER | -          |
| ENVELOPER   | AUDIO IN   | THRESHOLD IN | RELEASE IN | OUTPUT LEVEL IN |
| TRIGGER TO LFO RATE CV | TRIGGER IN | MULTIPLE/DIVIDE IN | -          | -          |
| FILTER 18dB | AUDIO IN 1 | AUDIO IN 2 | MOD IN     | RESONANCE IN |
| FILTER 24dB | AUDIO IN 1 | AUDIO IN 2 | MOD IN     | RESONANCE IN |
| FORMANT FILTER | AUDIO IN   | FORMANT 1 IN | FORMANT 2 IN | BALANCE IN |
| SAW OSCILLATOR | CV IN      | FINE IN    | COLOR IN   | SYNC TRIGGER IN |
| SQR OSCILLATOR | CV IN | FINE IN | COLOR IN | SYNC TRIGGER IN |
| MIDI NOTE TO CV/GATE | OCTAVE IN  | TRANSPOSE IN | -          | -          |



## Sub Module Outs
| Sub Module Type | Sub Module Out 1 | Sub Module Out 2 |
|-----------|-------------|-------------|
| EMPTY       | -           | -           |
| LFO         | LFO OUT     | LFO INVERSE OUT |
| ADSR        | ENVELOPE OUT   | ENVELOPE INVERSE OUT   |
| NOISE       | NOISE OUT 1 | NOISE OUT 1 |
| SAMPLE& HOLD      | S&H OUT 1   | S&H OUT 2   |
| RING MOD    | RING MOD OUT   | -           |
| FILTER 6dB  | FILTER OUT 1 | FILTER OUT 2 |
| FILTER 12dB | FILTER OUT 1 | FILTER OUT 2 |
| TONE        | TONE OUT1   | TONE OUT2   |
| AMP         | AMP OUT1    | AMP OUT2    |
| MIXER       | MIX OUT     | -           |
| STEREO MIXER     | MIX OUT L   | MIX OUT R   |
| CURVE CONV  | CONVERT OUT 1 | CONVERT OUT 2 |
| GATE DIVIDER       | GATE OUT    | -           |
| TRIG TO CV DELAY TIME | DELAY TIME CV |             |
| MIDI CLOCK TO GATE | CLOCK GATE OUT | START/STOP GATE OUT |
| SHORT DELAY | DELAY OUT   | -           |
| TUBE CLIP   | CLIP OUT1   | CLIP OUT2   |
| COMPRESSOR  | COMPRESSION OUT1 | COMPRESSION OUT2 |
| NOISE GATE  | NOISE GATE OUT1 | NOISE GATE OUT2 |
| 3 BAND EQ   | EQ OUT      |             |
| LOGIC OPERATION | LOGIC OUT1  | LOGIC OUT2  |
| CROSS FADER | CROSS FADE OUT | CROSS FADE INV OUT |
| SWITCHER    | SWITCH OUT  | GATE OUT    |
| ENVELOPER   | ENVELOPE OUT | ENVELOPE INVERSE |
| TRIGGER TO LFO RATE CV | RATE CV OUT | -           |
| FILTER 18dB | FILTER OUT  | -           |
| FILTER 24dB | FILTER OUT  | -           |
| FORMANT FILTER | FILTER OUT  | -           |
| SAW OSCILLATOR | OSC OUT     | OSC SYNC OUT |
| SQR CV IN OSCILLATOR | OSC OUT     | OSC SYNC OUT |
| MIDI NOTE TO CV/GATE | NOTE CV OUT | NOTE GATE OUT |
