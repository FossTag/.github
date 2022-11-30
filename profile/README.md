# FossTag - Free and Open Source Laser Tag System

A free software and open hardware project to create a laser tag system.

> **Warning:** This is starting off as an educational system for me (@pserwylo) to learn electronics. I hope one day it will evolve into something usable by others.

## Components

### [@FossTag/Tagger](https://github.com/FossTag/Tagger) + [@FossTag/TaggerFirmware](https://github.com/FossTag/TaggerFirmware)

Repurpose your old nerf-or-similar toy guns that were destined for the trash heap. 
Rip their guts out, and replace them with this Arduino based PCB, an infrared LED, a trigger switch, and optionally some LEDs and/or speakers for feedback.

<img src="/images/Tagger/conversions/02-Blue/right.jpg?raw=true" height="200"
/> <img src="/images/Tagger/conversions/01-Grey/inside.jpg?raw=true" height="200"
/> <img src="/images/Tagger/pcbs/v0.1/Tagger-PCB-v0.1-a.jpg?raw=true" height="200"
/> <img src="/images/Tagger/pcbs/prototype/Tagger-Prototype-top.jpg?raw=true" height="200" />

### [@FossTag/Sensor](https://github.com/FossTag/Sensor)

In order to tell when you get tagged by someone else, your tagger must be connected to at least one IR sensor.

This sensor is a PCB designed to host one or two TSOP IR receivers, with the option of daisy-chaining multiple sets of sensors together (e.g. two sensors on a headband, two on a vest - front and back, one on the tagger, etc).

<img src="/images/Sensor/prototype.jpg?raw=true" height="200" />

### Other ideas

This project has a lot of potential for building cool and interesting components.
Depending on how successful we are with the Tagger and Sensor, then it would be good to investigate some of the following ideas.

#### Referee taggers

Those officiating a game should be able to send specific command signals to everyone on the field. Examples include:
* Before the game, while everyone is in the same room:
  * Tell each tagger which team it is on (if playing a team game).
  * Set game rules so everyone's tagger is playing the same game.
  * Set each tagger to a specific gun (e.g. so not all players have the same type of gun).
* After the game:
  * Gather statistics
  * Check for tampering or cheating somehow by reconciling stats.

#### Target

Static targets which can be shot by taggers and respond both visually and with audio feedback.

Potential uses could be for calibrating tagger, practice ranges, or additional point scoring during games.

<img src="/images/Target/prototype-a.jpg?raw=true" height="200" />

The prototype above is naive in that it lights the LED when receiving any IR signals at 38kHZ.
There is no microcontroller that is parsing the specific messages sent from a tagger.
Although still helpful for calibration, in practice this means we are also not validating checksums either, and so stray signals are more likely to hit this even when you are not targeting it.
It also suffers from a lack of audio feedback, making it hard to tell if you've hit it when used outdoors in daytime.

#### Wifi/Bluetooth connectivity

Allow players to know where their peers are, how the game is progressing, show mini maps of their team or their base.

#### Mobile app

Allow mobile communication (e.g. via headsets), view game summary/statistics, view player locations by integrating GPS data, live video streams.
The list really is endless here - it just depends on what the best value features would be.

#### Capture the flag beacon

A beacon which can be captured by players and returned to a base. It would use some form of proximity sensor to know when it was returned, indicating the game is won by one particular team.

Would probably need some sort of broader interaction with a game server to keep track of the whole game state.

#### Grenade

Devies which have multiple IR LEDs facing outward on all angles, and are robust enough to be thrown.

After pressing a button then it will wait a certain amount of time before firing (e.g. using a capacitor or 555 in monostable mode).

#### Trip wire

Either a physical wire which fires when knocked loose, or an infrared version which works like a long distance optocoupler.
