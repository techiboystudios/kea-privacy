# Privacy Policy for Kea

**Last updated: 18 August 2026**

Kea is a hardware key remapper for Android, published by **TechiBoy Studios**
(package `com.techiboystudios.kea`). This policy explains what the app does with your
information. It is short because Kea collects nothing.

## What Kea collects

**Nothing.** Kea does not collect, store, transmit, sell or share any personal
information, usage data, device identifiers, contacts, location, or analytics of any
kind. There is no account, no sign-in, and no server.

## Why that claim is verifiable

Kea does not request the `INTERNET` permission. An Android app without it cannot open
a network connection at all, so it is not technically capable of sending your data
anywhere, whatever any policy might say. You can confirm this yourself in
**Settings → Apps → Kea → Permissions**, or by inspecting the app's manifest.

Kea contains no analytics SDK, no crash-reporting SDK, no advertising SDK and no
tracking libraries. The only third-party code in the app is Google's AndroidX
libraries, the Kotlin standard library, and the optional Shizuku client described
below.

## Accessibility Service

Kea uses an `AccessibilityService` for one purpose: to detect presses of a hardware
button. Android provides no other way for an app to observe hardware key events while
it is not in the foreground.

The service is declared with `canRequestFilterKeyEvents` and receives key events only.
It does **not** request `canRetrieveWindowContent`, so it cannot read the text, images
or contents of any screen, in Kea or in any other app. It does not log, store or
transmit key events. Each press is matched against the key you taught Kea and then
acted upon locally, on your device.

The service is declared `isAccessibilityTool="false"` because Kea is a general utility
rather than an assistive tool for users with disabilities.

## What is stored on your device

Your settings, which are: the action bound to each gesture, your timing preferences,
your chosen appearance and accent colour, your overlay position, and the hardware
fingerprint of the key you taught Kea.

These live in Kea's private app storage. They never leave your phone unless you
choose **Backup & restore → Export settings**, which writes a file to a location you
pick and then control. Uninstalling Kea deletes this data.

## Permissions, and why each exists

| Permission | Why |
|---|---|
| Accessibility service | Detect presses of your hardware button. The app cannot work without it |
| Display over other apps | Draw the small on-screen confirmation after a press |
| Modify system settings | Only if you bind the rotation lock or auto-brightness actions |
| Do Not Disturb access | Only if you bind the Do Not Disturb or ringer actions |
| Vibrate | Haptic confirmation on a press |
| Wake lock | Only if you bind the wake-screen action. Held for a moment, then released |
| Foreground service, media projection | Only if you bind the screen-recording action |
| Notifications | The ongoing notification Android requires while a recording runs |
| Microphone | Only if you turn on microphone audio for screen recordings. Off by default |

Kea does not request internet access, location, contacts, storage access, phone state,
or any other permission not listed here.

## Screen recording and microphone

If you bind the screen-recording action, recordings are written to your device's own
media storage through Android's MediaProjection API, after the system consent dialog.
Recording only ever starts when you press your button. Microphone capture is off by
default and is used only inside a recording you started. Kea never uploads recordings
or audio anywhere, and cannot, having no network permission.

## Shizuku

Two optional features can use [Shizuku](https://shizuku.rikka.app/), a separate app you
would install yourself: the camera shutter action, and helping you switch off a phone
manufacturer's own action on the button.

When used, Kea asks Shizuku to run a single shell command on the device. No data is
sent, and nothing leaves your phone. If Shizuku is not installed, these two features
are simply unavailable and everything else works normally.

## Children

Kea is not directed at children and collects no data from anyone, of any age.

## Deleting your data

There is no data held anywhere for us to delete. Uninstalling Kea removes its settings
from your device. Any backup file you exported yourself remains wherever you saved it,
under your control.

## Changes to this policy

If this policy changes, the updated version will be published at this address and the
date at the top will be updated.

## Contact

Questions about this policy or the app: **techiboystudios@gmail.com**
