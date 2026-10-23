---
layout: post
title:  "Minivan Media Player"
date:   2022-10-10 12:00:00 -0600
categories: raspberry-pi media minivan
---



We recently purchased a Toyota Sienna, and it came with an in-car media system. This is my solution to provide entertainment to the car.

| <img src='/assets/pi/pi-setup.jpg' width='600' alt='Rasperry pi 4, power supply, SSD'/> |
|--|
| Raspberry Pi + SSD + HDMI + Power Supply | 

## Limiting Factors

* We’re an iOS household, so an Android solution isn’t ideal.
* We don’t pay for the car’s cellular connection.

## Research

[Post in /r/ToyotaSienna](https://www.reddit.com/r/ToyotaSienna/comments/kzki65/2021_limited_entertainment_system_iphone/)

## 2022 Toyota Sienna Media Specs

|--------|-----|
| **Screen Size:** |  11.6” screen (10.1 x 5.7) |
| **Resolution:** | 126PPI / 1,273 x 718 |
| **Power:** | 110v plug |
| **Adapter:** | HDMI |


## Attempted Entertainment Solutions

* **DLNA / Miracast**
  You can cast media to the device via DLNA, but I haven’t found an iOS application that does* this well. Gallery Cast let me cast from an Android device, but I was unable to change the* aspect ratio of the phone, leaving significant letterboxing / distortion.
* **iOS – Lightning-to-HDMI dongle**
  Works well, but I only have one phone & need it for GPS / CarPlay.
* **Android – USB-C hub to HDMI**
  Works
* **Amazon Fire Tablet**
  Does not work
* **Netflix**
  Doesn’t work. Guessing it’s an HDCP issue?
* **Nintendo Switch**
  Works great

## Parts

* Raspberry Pi 4
* Raspberry Pi 4 power supply
* [Short Micro HDMI to HDMI cable](https://www.amazon.com/dp/B00A830AWW?ref=ppx_pop_mob_ap_share)
* [USB 3.0 SSD](https://www.amazon.com/SAMSUNG-Portable-SSD-500GB-MU-PC500T/dp/B0874YS2N7)

## Setup

[LibreELEC](https://libreelec.tv/) is a lightweight operating system designed to let [Kodi](https://kodi.tv/) run in a dedicated fashion on less powerful hardware.

## Install [LibreELEC](https://libreelec.tv/) onto the Raspberry Pi

Note: When attempting to write to the microSD card with the [LibreELEC](https://libreelec.tv/) application from MacOS Monterrey, I ran into issues.

```
2022-04-06 14:14:34.606 LibreELEC USB-SD Creator[13702:6746712] XType: com.apple.fonts is not accessible.
2022-04-06 14:14:34.606 LibreELEC USB-SD Creator[13702:6746712] XType: XTFontStaticRegistry is enabled.
PasteBoard: Error creating pasteboard: com.apple.pasteboard.clipboard [-4960]
PasteBoard: Error creating pasteboard: com.apple.pasteboard.find [-4960]
2022-04-06 14:14:35.529 LibreELEC USB-SD Creator[13702:6746712] The application with bundle ID com.apple.ScriptEditor.id.LibreELEC is running setugid(), which is not allowed. Exiting.
```

As a workaround, I found archive of all images: https://archive.libreelec.tv/ & snagged the [latest RPi4 image at the current time](https://archive.libreelec.tv/LibreELEC-RPi4.arm-10.0.2.img.gz).

## Getting Content Onto the Device

Via the [Kodi](https://kodi.tv/) administration screen, you can enable an SMB mount. This will enable you to mount the device as a network drive for copying files over.

If you’re a bit-miser, you can first compress your movies to the exact size needed in the car to make sure you’re not wasting any space. I use ffmpeg to downsample, saving the files over the SMB mount to the Pi.

`ffmpeg -i "./VIDEO_NAME.mkv" -vf scale=1274:718 "/media/kodi-videos/VIDEO_NAME.mp4"`

## Controlling the Device

* Use a mouse 
  * **Tired:** Bluetooth mice whose batteries run out.
  * **Wired:** Always-dependable, old-fashioned wired mice.
* [Kodi](https://kodi.tv/) uses an on-screen keyboard, so a mouse is all you should need for any action you wish to take.
* [Sybu for Kodi (iOS)](https://apps.apple.com/us/app/sybu-for-kodi-and-xbmc/id567524653) I’m still getting the hang of this application. My hope was that I could fully control [Kodi](https://kodi.tv/) from the front seat of the van.
  * At present, I’ve only had luck in using the mobile application as a dumb mouse of sorts, selecting on-screen items, which requires me to be in the back seat.
  * The other caveat for using this application is that you need to figure out how to setup wifi for your phone to talk to the Pi.

## Setting up Wifi

Using your home wifi / ethernet works great for getting content onto the device. If you want to use the mobile application to interact with [Kodi](https://kodi.tv/), you’ll need to find a way to wireless connect to it.

I’m still working through setting up wifi on the device and will update as I try new potential solutions. Here’s what I’ve tried so far:

### Using the In-Car Wifi

In-car cellular wifi is one of the dumber features recently released with cars. We chose not to extend the service after the free month ended, but I was curious if I could still hijack the service for use in communicating between devices in the car. Unfortunately, it’s a captive portal, and devices are unable to even connect to the access point unless they’ve paid for service.

### Using the Raspberry Pi as an access point

[Kodi](https://kodi.tv/) has an option to use the Raspberry Pi as an access point. This allows you to control the application via the mobile app, but has the downside of connecting you to a wifi network that does not have internet connectivity. By default, your phone will continue to try & automatically connect to the network, which will prevent your phone from doing anything requiring an internet connection.

### Using the Phone’s Shared Wifi

[Kodi](https://kodi.tv/) doesn’t detect my iPhone’s Personal Hotspot. Doesn’t show up in the list of available networks.

TODO: Using the Phone’s Shared Wifi by modifying wpa_supplicant via Shell?
That’s not going to work. [LibreELEC](https://libreelec.tv/) uses Connman (details) (more details on the issue)

## TODOs

* Truncate cables
* Clean up empty menus in [Kodi](https://kodi.tv/)
