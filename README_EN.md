<p align="center">
  <img src="assets/jvfi-banner.png" alt="Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

[繁體中文](README.md) | **English**

JVFI is a free server-side real-time frame interpolation plugin for Jellyfin. It uses the official `jellyfin-ffmpeg` pipeline and produces a standard transcoded stream at a configurable 23.976–240 FPS target, so supported Jellyfin clients do not require a browser extension.

> This public repository contains the plugin catalog, documentation, branding, and compiled releases. The core source code is not published. JVFI is free to use, but it is not open-source software.

## Features

- Configurable 23.976–240 FPS server-side output, defaulting to 60 FPS
- Uses the official Jellyfin FFmpeg binary
- Capability-based decoder, accelerator, and encoder selection
- Safe compatibility fallback when a hardware path is unavailable
- Frame-generation status, timeline FPS, compute throughput, and pipeline speed
- Standard transcoded playback for Jellyfin Web, Media Player, Android, and Android TV

## Install from the Jellyfin catalog

Add this URL under `Dashboard` → `Plugins` → `Repositories`:

```text
https://raw.githubusercontent.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/main/manifest.json
```

Open the plugin catalog, install **Jellyfin Video Frame Interpolation**, then fully restart Jellyfin.

## Compatibility

Version 0.7.2 uses Jellyfin 10.11.11 as its minimum build ABI and current validated baseline, with Linux ARM64 / Rockchip RK3588 as the main reference system. `targetAbi` is a minimum installation requirement, not a maximum-version lock. Newer servers are accepted only when the runtime method-signature and FFmpeg capability checks pass.

## Free to use

JVFI has no installation fee, subscription, or per-device license. Voluntary donations are welcome and help fund compatibility and hardware testing.

## Contact

- QQ group: `1018495751`
- Telegram: [Join the group](https://t.me/+l1v_7ag4mJQ3NjI1)
- GitHub Issues: [Report a problem](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/issues)

JVFI is an independent third-party project and is not affiliated with the Jellyfin project.
