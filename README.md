# Privacy Policy for Kea

**Last updated: 26 September 2026**

Kea is a hardware button remapper for Android, published by **TechiBoy Studios**
(package `com.techiboystudios.kea`). This policy explains what the app does with your
information. It is short because Kea collects nothing.

## What Kea collects

**Nothing.** Kea does not collect, store on any server, transmit, sell or share any
personal information, usage data, device identifiers, contacts, location, or analytics of
any kind. There is no account, no sign-in, and no server.

## Why that claim is verifiable

Kea does not request the `INTERNET` permission. An Android app without it cannot open a
network connection at all, so it is not technically capable of sending your data
anywhere, whatever any policy might say. You can confirm this yourself in
**Settings → Apps → Kea → Permissions**, or by inspecting the app's manifest.

Kea contains no analytics SDK, no crash-reporting SDK, no advertising SDK and no tracking
libraries. The third-party code in the app is: Google's AndroidX libraries, the Kotlin
standard library, the Google Play Billing Library (for Kea Pro, below), the Glyph
Developer Kit (used only on phones with Glyph lights), and the optional Shizuku client
described below.

## Accessibility Service

Kea uses an `AccessibilityService`. Android provides no other way for an app to notice
hardware button presses while it is not on screen, and that is its main job.

What the service does, and when:

- **Detects your button presses.** Each press is matched against the button you taught
  Kea and acted on at once. Presses are not logged, stored or transmitted.
- **Knows which app is in front,** by its package name only, so that the actions you set
  up behave correctly in that app. This is kept in memory and never stored.
- **Reads what is on screen only at the moment you trigger certain actions,** and only
  for that action:
  - **Copy** and **Paste** find the text field you are using.
  - **Voice recording** and **Call recording** find your recorder's widget on the home
    screen and tap it for you.
  - A few other actions check which window is active, so they act on the app you are
    using rather than on Kea.
- **Performs taps and gestures** only as part of an action you triggered, such as tapping
  the recorder widget.

What Kea reads is used immediately, on your device, and then discarded. It is never
saved, never logged and never sent anywhere, and without internet access it could not be.

The service is declared `isAccessibilityTool="false"` because Kea is a general utility
rather than an assistive tool for users with disabilities.

## Kea Pro purchases

Kea Pro is an optional one-time purchase made through **Google Play**. Google handles the
payment and your payment details under Google's own privacy policy; Kea never sees them.
Kea only learns from the Play Store app on your phone whether Pro has been bought, and
remembers that on your device.

The Google Play Billing Library adds the `ACCESS_NETWORK_STATE` permission, which lets it
check whether the phone is online. It is not internet access: Kea still cannot open a
connection. The purchase itself is carried out by the Play Store app.

## What is stored on your device

Your settings, which are: the action bound to each gesture and key, your App Sidebar
items and layout, your Action Lab combos, your timing, appearance, overlay, sound and
haptic preferences, your overlay position, whether Kea Pro is unlocked, and the hardware
fingerprint of the button you taught Kea.

These live in Kea's private app storage. They never leave your phone unless you choose
**Backup & restore → Export settings**, which writes a file to a location you pick and
then control. Uninstalling Kea deletes this data.

## Permissions, and why each exists

| Permission | Why |
|---|---|
| Accessibility service | Detect presses of your hardware button, and run the actions described above |
| Display over other apps | Draw the on-screen confirmation and the App Sidebar |
| Modify system settings | Only for the rotation lock and auto-brightness actions |
| Do Not Disturb access | Only for the Do Not Disturb and ringer actions |
| Answer phone calls | Only for the End call action |
| Microphone | Only if you turn on microphone audio for screen recordings. Off by default |
| Music and audio | Only for the Recordings screen, which lists and plays the voice and call recordings already on your phone |
| Set alarm | Only for the Set a timer action |
| Vibrate | Haptic confirmation on a press |
| Wake lock | Only for the Wake screen action. Held for a moment, then released |
| Foreground service, media projection | Only for the Screen recording action |
| Notifications | The ongoing notification Android requires while a recording runs |
| Glyph lights | Only for the Glyph torch and Glyph timer actions, on phones that have them |
| Shizuku | Only for the optional features described below |
| Google Play billing, network state | Only to buy Kea Pro through Google Play |

Kea does not request internet access, location, contacts, camera, photos, phone state, or
any other permission not listed here.

## Screen recording, voice and call recording

Screen recordings are written to your device's own media storage through Android's
MediaProjection API, after the system consent dialog. Recording only starts when you
trigger it. Microphone capture is off by default and used only inside a recording you
started.

Voice and call recording are made by your phone's own recorder app; Kea only starts
it. Those recordings are stored by that app, under its own policy.

Kea never uploads recordings or audio anywhere, and cannot, having no network permission.

## Links to other apps

The About screen can open Google Play (to rate or share Kea), your email app, and
TechiBoy Studios' social media pages. These open in their own apps or your browser, and
whatever you do there is covered by those services' own policies. Kea itself sends
nothing.

## Shizuku

Some optional features can use [Shizuku](https://shizuku.rikka.app/), a separate app you
would install yourself: the camera shutter action, and switching off your phone's own
action on the button.

When used, Kea asks Shizuku to run a single shell command on the device. No data is sent,
and nothing leaves your phone. If Shizuku is not installed, these features are simply
unavailable and everything else works normally.

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

## Contact

Questions about this policy or the app: **techiboystudios@gmail.com**
