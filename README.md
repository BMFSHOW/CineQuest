<p align="center">
  <img src="https://cinequest.bmfvr.com/img/logo.png" alt="CineQuest logo" width="96">
</p>

<h1 align="center">CineQuest</h1>

<p align="center">
  <b>Record your Meta Quest 3 in a wider, Cinematic view, right from the headset.</b><br>
  Free. Clips can copy to your PC by themselves, sorted by game.
</p>

<p align="center">
  <a href="https://github.com/BMFSHOW/CineQuest/releases/latest/download/CineQuest-Setup.exe"><b>Download for Windows</b></a>
  &nbsp;·&nbsp;
  <a href="https://cinequest.bmfvr.com">Website and setup guide</a>
  &nbsp;·&nbsp;
  <a href="https://github.com/BMFSHOW/CineQuest/issues">Report a bug</a>
</p>

![CineQuest open in the headset during a Cinematic recording](https://cinequest.bmfvr.com/img/cinematic-frame.jpg)

## What it does

- **Normal to Cinematic:** a slider sets how wide the recording is, up to 96° across instead of 64°.
- **Shortcut recording:** hold the Meta button and pull the trigger, the same shortcut you already use. A chime tells you when it starts and when it's saved.
- **Up to 4K:** 720p, 1080p, 1440p or 4K, in 16:9, 9:16, 1:1, 4:3 or 21:9.
- **Sound in Cinematic:** game and mic as separate tracks, left and right, or mixed. Meta's wide-view recorder saves picture only, so CineQuest records the sound itself.
- **Filed by game:** clips are named and sorted by the game they came from.
- **Optional PC app:** copies new clips to your PC over Wi-Fi.
- **Your choice of motion:** the stabiliser is off by default. Horizon lock is available in the normal view.

## What you need

- Meta Quest 3. This is the only headset it's made and tested on.
- Developer Mode turned on, which needs a free Meta developer organisation.
- A Windows 10 or 11 (64-bit) PC and a USB-C data cable, for setup.
- The same Wi-Fi network on the Quest and PC, if you want clips copied automatically.

## Install

1. Turn on Developer Mode in the Meta Horizon phone app.
2. Download and run [`CineQuest-Setup.exe`](https://github.com/BMFSHOW/CineQuest/releases/latest/download/CineQuest-Setup.exe) (about 83 MB).
3. Plug in your Quest and follow the steps on screen.

The [full setup guide](https://cinequest.bmfvr.com) has pictures of every step and takes about 10 minutes. After setup, the PC isn't needed for recording.

**"Windows protected your PC":** the installer isn't code-signed yet, so Windows may show this warning. If you choose to continue, click **More info**, then **Run anyway**.

**Can't find the app?** Look in your Library under Unknown sources. If that tab isn't there, which has happened after a Quest update, search for CineQuest.

## What it does to your headset

CineQuest needs deeper access than a normal app, so here is exactly what it does.

Meta doesn't offer an official way for apps to record in Cinematic. CineQuest gets there by giving itself an ADB (Android debugging) connection on the headset and using that to control Meta's own recording services.

**During setup:**

- The PC app downloads Google's Android platform-tools and uses them to install CineQuest.
- It runs `adb tcpip 5555` so the headset app can connect to itself. You approve this in the headset by choosing **Always allow**.
- CineQuest uses that connection to give itself these permissions:
  - `WRITE_SECURE_SETTINGS`, so it can turn wireless debugging back on after a restart
  - `MANAGE_EXTERNAL_STORAGE`, so it can move and file recordings
  - permission to run in the background, and an exemption from battery optimisation

**While it runs:**

- It starts when the headset boots and keeps wireless debugging on.
- It reads the system log to notice your record shortcut.
- It changes Meta's capture settings, and temporarily changes the eye field of view while recording in Cinematic.
- It lists installed apps so it can name clips after your games (`QUERY_ALL_PACKAGES`).
- It records game audio, and your microphone if you turn that on.

**Network and privacy:**

- There are no accounts, ads or analytics, and CineQuest doesn't upload your clips or data to any online service.
- The only internet download is Google's platform-tools during PC setup.
- The PC app copies clips directly over your local network. It pairs with a 6-digit code and uses a token after that, but **the connection isn't encrypted (plain HTTP)**, so use it on a network you trust.
- Developer Mode and debugging access make any headset less locked down. Only devices you've approved can connect over ADB, but if that trade-off doesn't suit you, CineQuest isn't for you.

## What to expect

CineQuest is an early, pre-1.0 personal project.

- **It depends on undocumented Meta features.** A Quest update could break it at any time, and it isn't guaranteed to work on every OS version.
- **Stabiliser:** Meta's stabiliser can leave black bars at the edges in Cinematic. Better smoothing is being worked on.
- **Quick head turns:** a brief black edge can show at the side of a Cinematic recording.
- **Start delay:** recording starts about 2 seconds after the shortcut press, and can take around 5 seconds right after a restart. A chime plays just before recording starts.
- **Reported, not yet reproduced:** after sleep, the record dot disappearing while recording continues. After a restart, Cinematic recordings coming out as regular 16:9. If either happens to you, please report it.

Please update to the latest release. Versions before 0.3.1 could freeze the headset when recording with the CineQuest window open.

## Source code

CineQuest isn't open source right now. This repository hosts the downloads, documentation and bug reports. Source may be released once the app reaches 1.0, but that isn't a promise.

## Uninstall

- **PC:** Settings → Apps → Installed apps → CineQuest PC. Your recordings stay where they are.
- **Headset:** uninstall CineQuest from your Library like any other app. To undo the rest, turn off Developer Mode.

## Bugs and questions

[Open an issue](https://github.com/BMFSHOW/CineQuest/issues/new/choose) and include your CineQuest version and what you pressed. Most questions are answered in the [FAQ](https://cinequest.bmfvr.com/#faq).

## Legal

© 2026 CineQuest. All rights reserved. You're welcome to download and use the app for free, but please don't redistribute it or reuse its code or assets without permission.

CineQuest is provided as is, with no warranty. You use it at your own risk.

CineQuest is an independent project, not affiliated with or endorsed by Meta. Meta and Quest are trademarks of Meta Platforms, Inc.

CineQuest uses open-source software. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
