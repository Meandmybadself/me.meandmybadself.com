---
layout: post
title:  "Wifi Walkie Talkies"
categories: hardware
---

# Sales Pitch

Walkie Talkies over wi-fi.

## Why?

Because walkie talkies are simple & fun & would be better if they could transcend the limitations of radio waves.

## Development Process

### Determine ideal hardware

#### Raspberry Pi
* Pro: Lots of hardware resources.
    * Could do runtime compression of audio?
* Con: Startup time.
* Con: Can't find them anywhere for purchase.
* Con: Their social team has got some problems to iron out.

I tried building this out with a Pi Zero W using `arecord` piped into `ffmpeg`.  Unfortunately, the startup time was 6 seconds, which wouldn't make for a very good user experience.


#### ESP32

* Pro: Can find them in stores.
* Pro: Cheap
* Pro: Faster startup

### Determine ideal server

After trying an RTMP server, am realizing that a websocket server may work better because it'll potentially allow for duplex`



## Journal
Follow along at: https://www.notion.so/meandmybadself/Development-Journal-339e1b5fbab34b2db0f985f607ee500c
 

