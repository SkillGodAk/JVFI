<p align="center">
  <img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

[繁體中文](README.md) | [简体中文](README.zh-CN.md) | **English**

JVFI is a server-side real-time frame interpolation plugin for Jellyfin. During playback, it uses the official `jellyfin-ffmpeg` pipeline to produce a standard transcoded stream at a configurable frame rate. Jellyfin Web, Jellyfin Media Player, Android, and Android TV clients do not require a separate extension.

## Comparison

<!-- JVFI_DEMO -->

The same scene, resolution, and time range: original frame rate on the left and JVFI output on the right. The public demo will use redistributable footage.

## Features

- Configurable `23.976–240 FPS` target output, with 60 FPS as the default
- Preserves the source resolution by default instead of forcing 480p or 1080p
- Supports Jellyfin Web, Jellyfin Media Player, Android, Android TV, and compatible clients
- Uses the official `jellyfin-ffmpeg` binary without replacing FFmpeg
- Probes actual decoder, processing, and encoder capabilities before selecting a path
- Detects common Intel QSV / VAAPI, AMD VAAPI / AMF, NVIDIA NVENC, Rockchip RKMPP, and Apple VideoToolbox paths
- Falls back to a compatible path when hardware processing is unavailable and preserves normal Jellyfin playback when interpolation cannot run safely
- Optional playback HUD for interpolation status, timeline FPS, compute throughput, and pipeline speed
- Separate minimum bitrate controls for 480p, 720p, 1080p, and 4K output
- Traditional Chinese, English, and Japanese settings UI, plus Simplified Chinese documentation

## Install from the Jellyfin catalog

Add this repository under `Dashboard` → `Plugins` → `Repositories`:

- Name: `JVFI`
- Repository URL:

```text
https://skillgodak.github.io/Jellyfin-Video-Frame-Interpolation/manifest.json
```

Return to the plugin catalog, search for `JVFI`, install **JVFI - Jellyfin Video Frame Interpolation**, and fully restart Jellyfin.

## Manual installation

Download the ZIP from [GitHub Releases](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/releases) and extract it to:

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

## Support and contact

Voluntary donations help fund Jellyfin compatibility work, hardware testing, and continued maintenance.

- QQ group: `1018495751`
- Telegram: [Join the group](https://t.me/+l1v_7ag4mJQ3NjI1)
- GitHub Issues: [Report a problem](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/issues)

JVFI is an independent third-party project and is not affiliated with the Jellyfin project.
