# Privacy Policy for Kea

**Last updated: 21 October 2026** (for Kea 2.0)

Kea is a hardware button remapper for Android, published by **TechiBoy Studios**
(package `com.techiboystudios.kea`). This policy explains what the app does with your
information. It is short because Kea collects almost nothing. There is no account, no
analytics and no advertising. Kea's AI features run on your phone: what you see on screen, the
text Kea reads and your pictures are not sent to us or anywhere else by Kea. A few things do
leave the phone, and each is listed under "Internet access" below: the check that a Kea Pro
purchase is genuine, downloads of language packs and models, the diagnostics that Google's
ML Kit sends to Google, and link previews if you use Kea Board.

## What Kea collects

**Nothing about you.** Kea itself does not collect, sell or share any personal information,
advertising identifiers, contacts, location or analytics. There is no account and no sign-in.
Kea's own server receives only the Kea Pro purchase check described under "Kea Pro purchases",
and only if you own Kea Pro.

Kea uses Google libraries (ML Kit, Google Play services, Play Billing, Play Integrity) that
can talk to Google on their own, under Google's privacy policy. They are described below.

## Internet access

Kea requests the `INTERNET` permission. It is used for these things and no others:

- **The Kea Pro purchase check**, only once you own Pro. See "Kea Pro purchases".
- **Language packs and models from Google.** Screen translation downloads a language pack
  (about 30 MB each) when you add a language or first translate from or into it. Google Play
  services downloads the ML Kit models for text recognition, language identification, face
  detection, subject cut-out and image labels. After that they work offline.
  Translation packs are fetched through ML Kit; the other models through Google Play services.
- **Diagnostics that Google ML Kit sends to Google** when you use these features. Google
  describes them in [its ML Kit data disclosure](https://developers.google.com/ml-kit/android-data-disclosure):
  device manufacturer, model and Android version, Kea's package name and version, performance
  figures such as latency, feature settings such as image size, event types such as model
  downloads, error codes, and for translation and language identification the languages
  involved. Google states that this is used for diagnostics and usage analytics, is encrypted
  in transit and is not passed to third parties. Kea cannot see or turn off this traffic. It
  does not include the text or images being processed.
- **AI packages from Kea's GitHub releases.** The optional packs come from
  `github.com/techiboystudios/kea-ai-models` (releases): the Board search encoder, the English
  dictionary for Look up, and the Chinese, Japanese and other screen-reading packs. You start
  most of these by tapping Download on Kea AI, then AI packages. Reading packs for a
  translation language are fetched automatically when you choose that language in Translate
  settings, without a second prompt (including on mobile data). Kea sends a plain request for
  the file and its release list (`manifest.json`); GitHub sees ordinary request details such as
  your IP address. Only github.com and GitHub's release file hosts are accepted, and each file
  is checked against a known SHA-256 hash before it is used.
- **Link previews in Kea Board (Kea Pro).** See "Kea Board". They are off by default and can be
  switched on in Board settings.
- **Google Play.** Buying and restoring Kea Pro goes through Google Play (see "Kea Pro
  purchases"). Google Play Billing and Play Integrity are Google's code and may send their own
  diagnostics to Google.

Kea contains no analytics SDK, no crash-reporting SDK, no advertising SDK and no tracking
libraries of its own. The third-party code in the app is:

- Google's AndroidX and Jetpack Compose libraries, the Kotlin standard library, kotlinx
  coroutines and serialization;
- the **Google Play Billing Library** and the **Play Integrity API** (for Kea Pro);
- **Google ML Kit** and Google Play services: text recognition (Latin, Chinese, Japanese,
  Korean and Devanagari), language identification, translation, face detection, subject
  segmentation, selfie segmentation and image labeling;
- **MediaPipe Tasks (Text Embedder)**, for offline Board search;
- **ONNX Runtime**, a small build made by TechiBoy Studios from source, which runs the
  Chinese and Japanese reading models (its library declares no permissions);
- **Tesseract** (through Tesseract4Android, with Leptonica, libjpeg-turbo and libpng), which
  reads the other scripts with downloaded language data;
- **PaddleOCR** models (Chinese and Japanese reading), Open English WordNet and Wiktionary
  data (dictionary) and Google's Universal Sentence Encoder model (Board search), all of which
  are data files you download, not code;
- the **Glyph Developer Kit** (used only on phones with Glyph lights);
- **Shizuku** (the optional client described below) and a small hidden-API helper library
  (LSPosed HiddenApiBypass) used for pop-up windows. Neither sends anything anywhere.

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
  - **Read aloud** and **Read screen** read the text of the app in front, skipping password
    fields, and hand it to your phone's own text-to-speech engine to speak.
  - **Grab text, Smart actions, Look up, Screen translation, Redacted screenshot, Cut out
    and Screenshot to Board** take a screenshot of the screen at the moment you press and
    read it on your phone (see "On-device AI features"). Where an app blocks screenshots,
    Grab text falls back to the text the app exposes. **Screen translation** stays on until
    you tap Done or press again: while it is on, it takes a new screenshot each time the
    screen scrolls or changes, so the translation follows you. It declines to run on the
    lock screen and in apps whose package name looks like banking, payment, wallet or
    password apps.
  - **Save page to Board** reads the address shown in Chrome's address bar, and **Save place
    to Board** reads the place details shown in Google Maps. **Collect to Board** reads the
    text you have selected.
  - **Context actions** (Kea Pro) check, at the moment you press, whether you are in a call,
    playing media, using the camera, or in a game, browser, maps, messaging, YouTube or
    meeting app, using Android's audio state and the package name or category of the app in
    front.
  - A few other actions check which window is active, so they act on the app you are
    using rather than on Kea.
- **Performs taps and gestures** only as part of an action you triggered, such as tapping
  the recorder widget or holding the bottom of the screen to start your phone's Circle to
  Search.

What Kea reads is used immediately, on your device, and then discarded. It is never
logged and never sent anywhere. It is saved only when you ask: a picture you save with **Save**
(to Pictures/Kea), content you add to Kea Board, or text and images you copy with **Copy**.
Anything you copy goes on Android's clipboard, where other apps can read it under Android's
own rules.

The service is declared `isAccessibilityTool="false"` because Kea is a general utility
rather than an assistive tool for users with disabilities.

## On-device AI features

Grab text, Smart actions, Look up, Screen translation, Redacted screenshot, Cut out and Kea
Board are part of Kea Pro. They run on your phone. Read aloud and Read screen are free and use
your phone's own text-to-speech engine, which Kea does not choose or download; that engine
is set in Android and is covered by its own policy.

- **Grab text** reads the text in a screenshot and lets you copy or share it.
- **Smart actions** find links, email addresses, phone numbers and one-time codes in that
  text by pattern matching, and offer to open, copy or send them.
- **Look up** reads the word you point at and finds it in an English dictionary you download.
  Its pronunciation is spoken by your phone's own text-to-speech engine.
- **Screen translation** reads the screen, detects the language and translates it on the
  phone with ML Kit, drawing the result over the app. Language packs are downloaded as
  described under "Internet access".
- **Redacted screenshot** finds email addresses, phone numbers, one-time codes and card
  numbers by pattern matching, and faces with ML Kit, and covers them. You can then save the
  result to Pictures/Kea or share it.
- **Cut out** lifts the main subject of a photo on screen using ML Kit. You can copy it,
  share it, drag it into another app, save it to Pictures/Kea, or keep it as a sticker. A
  sticker is saved to Pictures/Stickers and added to a sticker pack in Kea's private
  storage, which WhatsApp can read when you choose to add it. Kea also puts the sticker on
  the clipboard.
- **Kea Board** is described in its own section below.

How text is read: Kea uses Google ML Kit text recognition (run through Google Play services)
for most scripts. If you downloaded a reading pack, Chinese and Japanese are read with
PaddleOCR models through ONNX Runtime, and scripts ML Kit cannot read (for example Arabic,
Hebrew, Thai, Cyrillic and several Indian scripts) are read with Tesseract. All of this runs
on your phone. Semantic search in Board uses MediaPipe with a downloaded encoder.

What is stored: a screenshot taken for these features is held in memory while the feature is
open and then discarded. When you share or keep a result, Kea writes a temporary copy to its
private cache folder so the receiving app can read it; Kea does not delete these copies
itself, so they stay until Android or you clear Kea's cache. Kea keeps a small local counter
of AI use (the date, hour and name of the feature, a count, and the last 40 running times) to
show on its AI pages. It holds no content, the counts are kept for 90 days, it is never sent anywhere and it is
not part of the backup file.

## Kea Board

Kea Board (Kea Pro) stores the text, links, notes, places and images you add: by share, by
drag and drop, with a button action, or by tapping Add clipboard. It does not watch the
clipboard; the clipboard is read only when you tap Add clipboard. Items are stored in Kea's
private storage and not uploaded. Images you add are also read on the phone to index the text
in them for search, and labelled by an ML Kit model (for example "dog" or "receipt"); the
labels and text are stored with the item.

- **Search by meaning** uses the encoder you download from AI packages. Without it, Board
  falls back to keyword matching. Board does not upload search queries, saved text, images or
  embeddings.
- **Link previews** (off by default, switch on in Board settings) run when Board shows a
  saved link that has no preview yet, or when you refresh previews. Kea fetches the address
  you saved over HTTPS from that website, reads its title, description, picture and icon, and
  downloads the picture and icon the page names, which may be on other hosts. Those websites
  see the address, your IP address and a user agent named `Kea-LinkPreview/2.0`. Kea sends
  no cookies, account information or other clips. For YouTube links, Kea instead asks
  YouTube's oEmbed service (`youtube.com/oembed`), sending the video link, and downloads the
  thumbnail address that YouTube returns. Kea refuses addresses that point to your local
  network. A failed request leaves the link usable. Previews are kept in Kea's private storage.
- **Retention.** Unpinned items expire after the period you choose (the default is 24 hours;
  codes that look like verification codes have their own shorter period, 10 minutes by
  default). Pinned items stay until you remove them. Android can delay the background
  cleanup. You can also set limits on how many items of each type are kept and remove items
  yourself.
- Board content is not included in Backup & restore exports and is not in Android cloud
  backup. Uninstalling Kea removes it.

## Kea Pro purchases

Kea Pro is an optional one-time purchase made through **Google Play**. Google handles the
payment and your payment details under Google's own privacy policy; Kea never sees them.
Kea keeps the purchase receipt Google Play signs on your device, and the signed answer from
Kea's server described below.

Once you own Kea Pro, Kea checks the purchase with Kea's own server (a Google Cloud function
using Firebase, in India) when you buy or restore it, and then about once a day while you are
online. The request contains only:

- the purchase token Google Play issued for your purchase;
- the app's package name and the product name (`kea_pro_lifetime`);
- an identifier for this phone: Android's per-app device ID, combined with Kea's package name
  and scrambled (one-way hashed) on your phone before it is sent. Every app sees a different
  one, so it cannot be used to link Kea to any other app, and it changes if the phone is
  factory reset. (On the rare phone with no usable ID, a random number saved in Kea is used
  instead);
- a **Play Integrity token** and a one-time random value tied to it. Kea requests the token
  from Google Play services, only at the moment of this check and not for people without Pro.
  It is a signed statement from Google about whether this copy of Kea is the genuine version
  installed from Google Play.

No name, email, Google account, phone model, settings or usage are sent by Kea. The server
passes the Play Integrity token to Google to read it, and asks Google Play whether the
purchase token is a genuine, unrefunded Kea Pro purchase. It answers yes or no, signed so
the app can trust the answer. Kea's server uses the integrity result only to refuse Pro to a
copy of Kea that was modified or re-signed by someone else. It ignores the parts of Google's
answer about the phone itself, such as root, and an unreadable result never takes Pro away.
Only a signed refusal about your purchase ever turns Pro off; a server that cannot be reached
does not.

The server stores only one-way hashes of the purchase token and of the phone identifier, with
the time each phone was last checked, to limit one purchase to five phones in use, and never
the originals. It does not store the Play Integrity token. Reinstalling Kea on the same phone
counts once. A purchase record is deleted automatically when none of its phones has checked
in for 30 days. When the server turns down a modified copy it may write a short technical
reason to its log, without your purchase token or phone identifier. Google's standard Cloud
request logs may briefly record the connecting IP address. If you never buy Kea Pro, Kea never
contacts the server. Uninstalling Kea deletes the identifier; to have the stored hashes
removed, email us.

The Google Play Billing Library and Play Integrity are Google's code and, with internet
access available, may communicate with Google under Google's privacy policy. The purchase
itself is carried out by the Play Store app.

## What is stored on your device

Your settings, which are: the action bound to each gesture and key (including per-app
profiles and the apps you picked), your App Sidebar items and layout, your Action Lab combos,
your action wheels, your context-action choices, your timing, appearance, overlay, sound and
haptic preferences, your overlay positions, your screen recording choices, and the hardware
fingerprint of the button you taught Kea (its scan code and device name). If you turn on
**Most used first** for an action wheel, Kea also counts how often you open each card from
that wheel, so it can put your favourites nearest the middle. Only cards opened through the
wheel are counted.

Also kept on the phone: your Screen translation language and the language packs and AI
packages you have downloaded; **Kea Notes**, the notes you write with Quick note or on the
Notes page; Kea Board content; stickers you keep; the Kea Pro receipt (stored encrypted and
bound to the phone) and the last signed answer from Kea's server; and the local AI use
counter described above.

These live in Kea's private app storage. Kea opts out of Android cloud backup and device
transfer. Your settings and Kea Notes leave your phone only if you choose **Backup &
restore → Export settings**, which writes a file to a location you pick and then control.
That file does not include Board content, the Pro receipt or downloaded packages, and
importing it never grants Pro. Uninstalling Kea deletes this data. You can delete downloaded
packages in AI packages and language packs in Screen translation settings.

## Permissions, and why each exists

Permissions marked "adb or Shizuku" are ones Android does not let you grant in the normal
permission screens. They are optional, and the features that need them are simply
unavailable until you grant them.

| Permission | Why |
|---|---|
| Accessibility service | Detect presses of your hardware button, take screenshots and read the screen for the actions described above, and perform taps and gestures |
| Display over other apps | Draw the on-screen confirmation, the App Sidebar, Kea Board and the AI overlays |
| Modify system settings | Only for the rotation lock and auto-brightness actions |
| Do Not Disturb access | Only for the Do Not Disturb and ringer actions |
| Answer phone calls | Only for the End call action |
| Microphone (record audio) | Only if you choose audio for screen recordings: your phone's own sound, the microphone, or both. Android requires this permission even to capture the phone's own sound. Off by default (no audio) |
| Music and audio (and, on Android 12 and lower, storage) | Only for the Recordings screen, which lists and plays the voice and call recordings already on your phone. The storage permission is declared for Android 12 and lower only; Kea requires Android 13 or later, so it has no effect |
| Set alarm | Only for the Set a timer action |
| Vibrate | Haptic confirmation on a press |
| Wake lock | Only for the Wake screen action. Held for a moment, then released |
| Foreground service, media projection | Only for the Screen recording action |
| Notifications | The ongoing notification Android requires while a recording runs |
| Usage access | Only if you turn on **Suggest an app** for the App Sidebar or use its **Most used** app filter. Kea asks Android which apps you used most (the last two days for the suggestion, the last week for the filter), on your phone, when it needs to. Only the result is used; it is not stored or sent anywhere. You grant it yourself in Settings, and can take it back there |
| Write secure settings (adb or Shizuku) | Only for Night Light, Extra dim and Glyph controls, and to let the Quick Settings tile switch Kea's own accessibility service back on. Granted once by you through Shizuku or a computer (adb). Kea uses it only for these purposes |
| Glyph lights | Only for the Glyph torch and Glyph timer actions, on phones that have them |
| Shizuku | Only for the optional features described below |
| Google Play billing, network state | Only to buy Kea Pro through Google Play, and to warn before a large download on mobile data |
| Internet | The Kea Pro purchase check, downloading language packs, models and AI packages, ML Kit's diagnostics, and Board link previews (see "Internet access") |

Some declarations are not permissions Kea asks you for. They only decide who may reach Kea,
and Android grants them to the system, not to Kea:

- **Digital assistant entry** (`BIND_VOICE_INTERACTION`): Kea can be chosen as your phone's
  default digital assistant so that a power-button hold starts the action you set. Kea does not
  listen to your voice for this. The entry requires the caller to be the system.
- **Quick Settings tile** (`BIND_QUICK_SETTINGS_TILE`): lets only the system place Kea's
  on/off tile in the shade.
- **`INTERACT_ACROSS_USERS_FULL`**: guards the Shizuku connection point so only Shizuku itself
  can use it. Kea does not request it.
- **Package visibility**: Kea lists specific apps it can launch or work with (for example
  recorder, wallet, camera, WhatsApp and ChatGPT apps) instead of requesting access to your
  full app list. Its app pickers also list the apps that have a launcher icon.

Pocket mode, if you turn it on, reads your phone's proximity and motion sensors to ignore
presses in a pocket. These sensors need no permission and the readings are not stored.

Kea does not request location, contacts, camera, photos, phone state, or any other
permission not listed here.

## Screen recording, voice and call recording

Screen recordings are written to your device's own media storage through Android's
MediaProjection API, after the system consent dialog. Recording only starts when you
trigger it. Audio is off by default. If you choose your phone's own sound, Kea captures it
during the recording, using a temporary private file that is combined into the final
recording when it stops. Microphone capture is used only inside a recording you started.

Voice and call recording are made by your phone's own recorder app; Kea only starts
it. Those recordings are stored by that app, under its own policy.

Kea never uploads recordings, audio, screenshots or anything it reads from the screen.

## Links to other apps

The About screen can open Google Play (to rate or share Kea), your email app, and
TechiBoy Studios' pages on YouTube, Instagram, X and Threads. The Kea Pro screen can open this
policy. The ChatGPT action opens the ChatGPT app, or its Google Play page if it is not
installed, and the Wallet scan action opens Google Wallet. These open in their own apps or
your browser, and whatever you do there is covered by those services' own policies. Kea
itself sends nothing when it opens them.

## Shizuku and adb

Some optional features can use [Shizuku](https://shizuku.rikka.app/), a separate app you
would install yourself, or a one-time command from a computer over adb. Through Shizuku, Kea
can run only a fixed list of shell commands, checked both in Kea and in the Shizuku process:
list installed and disabled packages (to find your phone's own button handler), switch Battery
Saver or NFC on and off, send the camera key, turn Night Light, Extra dim, Flip to Glyph and
the Glyph lights on or off, send the End call key, perform a held touch for Circle to Search,
disable or re-enable your phone's own button handler app when you ask it to, and grant Kea
the write secure settings permission described above. Nothing else is accepted.

When used, no data is sent, and nothing leaves your phone. If Shizuku is not installed, these
features are simply unavailable and everything else works normally.

## Children

Kea is not directed at children and collects no data from anyone, of any age.

## Deleting your data

Uninstalling Kea removes its settings, Kea Notes, Board content, downloaded packages and
stickers from your device. Any backup file you exported yourself, and any image you saved to
Pictures/Kea or Pictures/Stickers or shared, remains wherever you put it, under your control.

If you own Kea Pro, our server holds only the hashed purchase token and hashed phone
identifiers described under "Kea Pro purchases". They are one-way hashes, so we cannot tell
which record belongs to whom and cannot find yours from an email. Instead, a record is
deleted automatically 30 days after a phone last checked in: uninstall Kea, or stop using
Kea Pro, and it is gone within about 30 days.

Data that Google holds under its own policies (for Google Play purchases, Play Integrity and
ML Kit diagnostics) is managed by Google, not by us.

## Changes to this policy

If this policy changes, the updated version will be published at this address and the
date at the top will be updated.

## Contact

Questions about this policy or the app: **techiboystudios@gmail.com**
