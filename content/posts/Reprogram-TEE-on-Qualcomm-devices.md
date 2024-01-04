---
title: Reprogram-TEE-on-Qualcomm-devices
date: 2024-01-04T12:18:34+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1701198067596-2a67e93c9372?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQzNDE3NjV8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1701198067596-2a67e93c9372?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQzNDE3NjV8&ixlib=rb-4.0.3
---

# [chiteroman/Reprogram-TEE-on-Qualcomm-devices](https://github.com/chiteroman/Reprogram-TEE-on-Qualcomm-devices)

# Reprogram TEE on Qualcomm devices
Guide to reprogram the TEE on Qualcomm devices to fix lost attestation keys.

## Why?

If you are here it is because your phone has lost the TEE attestation keys, possibly due to flashing the persist partition of your phone.

If opening [Key Attestation Demo](https://github.com/vvb2060/KeyAttestation) does not give you any error, do **NOT** follow this guide.

If you want to pass the Strong verdict from Play Integrity you could, but that is not the purpose of this guide and I will **NOT** provide instructions for that.

## WARNINGS:

- Your data will be lost, so backup your phone data first.
- The original keys that your phone may include in the TEE will be lost.
- I am not responsible for any other problems that may arise, these instructions are made on a POCO X3 Pro (vayu) and work perfectly, they may not work as they should on other phones.

## You will need:

- A working brain.
- A working computer.
- An unlocked bootloader.
- A valid keybox.xml file, you can use this one in the repo.
- The engineering ROM for your device.

## Instructions:

1. Flash engineering ROM.
2. Phone must be connected to PC, then execute this commands IN ORDER:

> adb root

> adb disable-verity

> adb reboot

> adb root

> adb remount


> adb shell mkdir –p /data/nativetest64/qti_keymaster_tests/

> adb push keybox.xml /data/nativetest64/qti_keymaster_tests/

> adb shell

> cd /data/nativetest64/qti_keymaster_tests/

> LD_LIBRARY_PATH=/vendor/lib64/hw KmInstallKeybox {KEYBOX FILE} {KEYBOX DEVICE ID} {ATTEST PROPS?}

{KEYBOX FILE}: Should be "keybox.xml"

{KEYBOX DEVICE ID}: Open keybox file and search for "DeviceID", repo keybox uses "X705F100000000"

{ATTEST PROPS?}: Boolean, should be true/false, I recommend setting it as false always, not all TEE support this.

So, for the keybox in the repo you must run:

> LD_LIBRARY_PATH=/vendor/lib64/hw KmInstallKeybox keybox.xml X705F100000000 false