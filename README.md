# MagicPods✨ for Linux

Use AirPods, Beats, and compatible Galaxy Buds on SteamOS or Linux with full control and battery monitoring. MagicPods seamlessly integrates your headphones with Steam Deck and Steam Machine, bringing iOS-style functionality to your gaming setup.

<p align="center"><a href="https://store.steampowered.com/app/4486410/MagicPods_for_Linux/"><img src="./docs/images/steambadge.webp"  width="156"/></a></p>

![](./docs/images/linux-banner.webp)

Tested on Kubuntu 26.04, Ubuntu 26.04, and SteamOS 3.7.24.

### 🎨 Features

#### Battery Monitoring

View battery levels inside the app, in the tray widget, or through the [MagicPodsDecky](https://github.com/steam3d/MagicPodsDecky) plugin for Decky Loader. Works with all AirPods, most Beats, and many other Bluetooth headphones.

#### Noise Control

Switch between available noise control modes directly from the app. Noise cancellation, transparency, adaptive, and off modes are supported on AirPods, Beats, and Galaxy Buds (model dependent).

#### Pop-Up Animation

An iPhone-style pop-up window appears when you open the charging case of your AirPods or Beats, showing battery information.

### Advanced Controls

Customize how your AirPods or Beats behave with support for Conversation Awareness, Personalized Volume, Adaptive Audio tuning, and configurable touch controls.

## ⚡ This fork: AirPods Mac-parity (hi-res mic + seamless handoff)

This branch (`hailey/mac-parity`) ports the remaining AirPods behaviors that
make them feel like they do on a Mac. The core submodule is pinned to
[haileyok/MagicPodsCore](https://github.com/haileyok/MagicPodsCore) branch
`hailey/handoff`.

**What's added on top of upstream:**

- **Hi-res microphone** — Apple's voice codec (AAC-ELD 64 kHz, AACP opcode
  `0x58`) instead of BlueZ's 8 kHz HFP mics. With MagicPods running, a
  PulseAudio source named **`AirPodsHiRes`** appears: select it as your mic in
  any app (Google Meet, Discord, browsers). A2DP playback stays at full
  quality while the mic is active — no profile switch, no 8 kHz downgrade.
- **Seamless handoff (Smart Routing)** — the AACP `0x10` takeover protocol:
  see connected devices, hijack the buds from another Apple host (your
  iPhone), and release them back, from the headphones page in the app.
- All upstream features (battery, noise control, pop-up, advanced controls)
  are unchanged.

**Build:** clone with submodules (`git clone --recurse-submodules -b
hailey/mac-parity https://github.com/haileyok/MagicPodsLinux.git`), then build
the core and the app per upstream's instructions. For a fully declarative
setup, [haileyok/dotfiles](https://github.com/haileyok/dotfiles) builds and
installs both from these branches via a Nix flake — see the "AirPods /
earbuds" section of its README for the full recipe, including the BlueZ
DeviceID handshake and the two WirePlumber settings.

**Caveats (learned live on AirPods Pro 2 + PipeWire):** WirePlumber must not
autoswitch to HFP when an app opens the mic
(`bluetooth.autoswitch-to-headset-profile = false`); heavy PipeWire churn can
poison the compat layer's routing — fix with `systemctl --user restart
pipewire pipewire-pulse wireplumber` and restart any apps that were playing
audio. Hi-res mic was verified end-to-end on AirPods Pro 2; upstream tested
AirPods Pro 3 only.

## 🎧 Headphones supported

| Apple            | Beats                  | Samsung           |
| ---------------- | ---------------------- | ----------------- |
| AirPods 1        | PowerBeats Pro         | Galaxy Buds       |
| AirPods 2        | PowerBeats Pro 2       | Galaxy Buds Plus  |
| AirPods 3        | PowerBeats 3           | Galaxy Buds Live  |
| AirPods 4        | PowerBeats 4           | Galaxy Buds Pro   |
| AirPods 4 (ANC)  | Beats Fit Pro          | Galaxy Buds 2     |
| AirPods 5        | Beats Studio Buds      | Galaxy Buds 2 Pro |
| AirPods 5 (WCC)  | Beats Studio Buds Plus | Galaxy Buds FE    |
| AirPods Pro      | Beats Studio Pro       | Galaxy Buds 3     |
| AirPods Pro 2    | Beats Solo 3           | Galaxy Buds 3 Pro |
| AirPods Pro 3    | Beats Solo Pro         |                   |
| AirPods Max      | Beats Studio 3         |                   |
| AirPods Max 2024 | Beats X                |                   |
|                  | Beats Flex             |                   |
|                  | Beats Solo Buds        |                   |


## 🚀 Getting started

1. Download MagicPods from [Steam](https://store.steampowered.com/app/4486410/MagicPods_for_Linux/) or build it from source.
2. Add your headphones to the Bluetooth devices list.
3. Launch MagicPods and connect your headphones for the initial setup.
4. Done! Battery animations, charge levels, and additional settings are now available.

## 🧪 Ideas and bugs

Join the community on [Discord](https://discord.com/invite/UyY4PY768V) to suggest ideas or report issues.
