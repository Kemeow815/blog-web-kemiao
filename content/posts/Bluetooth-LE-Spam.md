---
title: Bluetooth-LE-Spam
date: 2023-11-05T12:15:53+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1698681062595-20766b790815?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTkxNTc2NzR8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1698681062595-20766b790815?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTkxNTc2NzR8&ixlib=rb-4.0.3
---

# [simondankelmann/Bluetooth-LE-Spam](https://github.com/simondankelmann/Bluetooth-LE-Spam)

# Bluetooth LE Spam <a href="https://discord.gg/JHyKE8mZkE">![Discord](https://img.shields.io/discord/1170266776731406386?label=Discord&link=https%3A%2F%2Fdiscord.gg%2FJHyKE8mZkE)</a>

This project focuses on utilizing the built-in Bluetooth Low Energy (BLE) functionality of Android smartphones to create Phantom Bluetooth Device Advertisements, similar to what is known, for instance, in the case of the Flipper Zero. While there are other apps available that provide similar functionality, the objective of this app is to enhance convenience and user-friendliness in the process.

> **_NOTE:_**  This project is in its early stages of development. Contributions from anyone are welcome.

<h4><a href="https://discord.gg/JHyKE8mZkE">Join the Discord Server</a></h4>

## Requirements
- Android 8.0 (API level 26) or later
> If you don't know your API level vist [SDK Platform release notes](https://developer.android.com/tools/releases/platforms). You also can view your Android version in the settings app.

## Functionality
### Google Fast Pair
This app is capable of spoofing BLE advertisers that mimic the usage of the Google Fast Pair Service, leading to an influx of unwanted pop-up notifications on the receiving device.

For additional information about the Google Fast Pair Service, you can find it [here](https://developers.google.com/nearby/fast-pair/landing-page)

### Microsoft Swift Pair
This app can spoof BLE advertisers that mimic devices supporting the Microsoft Swift Pairing Service. If Swift Pair notifications are enabled on a nearby Windows 10 (or later) device, it will receive a flood of notifications regarding nearby devices.

For additional information about the Microsoft Swift Pair Service, you can find it [here](https://learn.microsoft.com/en-us/windows-hardware/design/component-guidelines/bluetooth-swift-pair)

### Apple Device Popups
This app can spoof various Apple devices via Bluetooth Low Energy, which can be detected by iOS devices, resulting in a flood of unwanted popups on the receiving iOS device.

### Apple Action Modals
By spoofing Bluetooth Low Energy advertisers, this app can prompt iOS devices to open unwanted modals and popups, imitating certain Apple-specific actions."

### Kitchen Sink
Utilizing this functionality, the app randomly generates BLE advertisement packages based on all other features. This leads to the highest number of affected devices in the vicinity.

## Range
Since the official Bluetooth Low Energy API provided by Google's Android SDK allows you to set the TX Power level and include it in the advertiser's payload, but doesn't permit direct modification of the byte values actually transmitted in the payload, the range of the Fast Pair functionality is somewhat limited. The receiving devices calculate the transmitter's proximity based on the actual received signal strength and the transmitted byte in the payload, which contains the TX Power level the transmitter used. However, devices like the Flipper Zero have the capability to modify this byte, significantly extending their range.

## Installation
You can clone the repository and open it in Android Studio to install the app, or simply use the installable APK files from the [Release Section](https://github.com/simondankelmann/Bluetooth-LE-Spam/releases)

## Credit
- [mh from mobile-hacker.com](https://www.mobile-hacker.com/author/boni11/) for the [Article / Guideline](https://www.mobile-hacker.com/2023/09/07/spoof-ios-devices-with-bluetooth-pairing-messages-using-android/) about using the nRF Connect App to Spoof iOS Devices

- [Willy-JL](https://github.com/Willy-JL) , [ECTO-1A](https://github.com/ECTO-1A) , [Spooks4567](https://github.com/Spooks4576) for their contribution in the BLE Spam App on the Flipper Zero

- [FuriousMAC](https://github.com/furiousMAC) and [Hexway](https://github.com/hexway) for their prior researches

- And special thanks to anyone else who has been involved in prior research and publications related to this topic.

## Screenshots
![](./Assets/Screenshots/ScreenshotFastPairing.jpeg)
![](./Assets/Screenshots/ScreenshotSwiftPair.jpeg)
![](./Assets/Screenshots/ScreenshotContinuityDevicePopUps.jpeg)
![](./Assets/Screenshots/ScreenshotContinuityActionModals.jpeg)
![](./Assets/Screenshots/ScreenshotKitchenSink.jpeg)

## Disclaimer
Disclaimer for Bluetooth Low Energy Protocol Investigation Repository

This repository contains code for the investigation and experimentation of the Bluetooth Low Energy (BLE) protocol. Please be aware of the following disclaimers before using or contributing to this repository:

1. Purpose: The code and information provided in this repository are intended for educational and research purposes. It is not intended for any malicious or harmful activities.

2. Legal Compliance: Users are responsible for ensuring that their use of the code and information in this repository complies with all applicable laws and regulations, including those governing wireless communication and intellectual property rights.

3. No Warranty: The code and information provided in this repository are provided "as is" without any warranties, expressed or implied. The authors and contributors are not responsible for any consequences resulting from the use of this code.

4. Risks: Experimenting with BLE protocols can have potential security and privacy implications. Users should exercise caution and use this code responsibly, respecting the privacy and security of devices and systems.

5. Contribution Guidelines: If you contribute to this repository, ensure that your contributions are in compliance with the project's goals and the repository's license. By contributing, you agree to license your contributions under the same license as this repository.

6. Support: This repository is not maintained for production use. The authors and contributors may not provide support or updates regularly.

By using and contributing to this repository, you agree to these disclaimers and guidelines. If you do not agree, please refrain from using or contributing to this repository.

For any questions or concerns, please contact the repository maintainers.


