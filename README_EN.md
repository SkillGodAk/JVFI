<p align="center">
  <img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

[繁體中文](README.md) | [简体中文](README.zh-CN.md) | **English**

JVFI is a server-side real-time frame interpolation plugin for Jellyfin. During playback, it uses the official `jellyfin-ffmpeg` pipeline to produce a standard transcoded stream at a configurable frame rate. Jellyfin Web, Jellyfin Media Player, Android, and Android TV clients do not require a separate extension.

## Features

- Configurable `23.976–240 FPS` target output, with 60 FPS as the default
- Preserves the source resolution by default instead of forcing 480p or 1080p
- Supports Jellyfin Web, Jellyfin Media Player, Android, Android TV, and compatible clients
- Uses the official `jellyfin-ffmpeg` binary without replacing FFmpeg
- Probes actual decoder, processing, and encoder capabilities before selecting a path
- Hardware and interpolation pipeline display follows Jellyfin's actual hardware acceleration settings
- Detects common Intel QSV / VAAPI, AMD VAAPI / AMF, NVIDIA NVENC, Rockchip RKMPP, and Apple VideoToolbox paths
- Falls back to a compatible path when hardware processing is unavailable and preserves normal Jellyfin playback when interpolation cannot run safely
- Optional playback HUD for interpolation status, timeline FPS, compute throughput, and pipeline speed
- Separate minimum bitrate controls for 480p, 720p, 1080p, and 4K output
- Traditional Chinese, English, and Japanese settings UI

## Install from the Jellyfin catalog

Add a repository under `Dashboard` → `Plugins` → `Repositories`:

- Name: `JVFI`
- Repository URL:

```text
https://skillgodak.github.io/JVFI/manifest.json
```

Return to the plugin catalog, search for `JVFI`, install **JVFI**, and fully restart Jellyfin.

## Manual installation

Download the ZIP from [GitHub Releases](https://github.com/SkillGodAk/JVFI/releases) and extract it to:

```text
jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

Docker example:

```text
/volume1/docker/jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

Fully restart Jellyfin to load the plugin.

## Supported environments

| Item | Status |
|---|---|
| Jellyfin 10.11.11 | Current minimum installation version and primary validated release |
| Linux ARM64 / RK3588 | Current primary validation platform |
| Jellyfin Web | Standard transcoded stream supported |
| Jellyfin Media Player | Standard transcoded stream supported |
| Android / Android TV | Standard transcoded stream supported |
| Other hardware and newer Jellyfin versions | Enabled according to runtime capability checks |

## Support the author

If JVFI is useful to you, support for the author is welcome.

### International Support

[Buy Me a Coffee](https://buymeacoffee.com/SkillGodAK)

### Bank transfer

<img src="assets/donate-bank.jpg" alt="Bank transfer QR code" width="360">

### WeChat Pay

<img src="assets/donate-wechat.jpg" alt="WeChat Pay QR code" width="360">

JVFI is an independent third-party project and is not affiliated with the Jellyfin project.
