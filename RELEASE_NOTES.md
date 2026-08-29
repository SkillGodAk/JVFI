# JVFI 0.7.2

- Adds a configurable 23.976–240 FPS output target; the default remains 60 FPS.
- Uses the selected target consistently in FFmpeg, HUD, and live session metrics.
- Uses the official Jellyfin FFmpeg pipeline.
- Adds universal hybrid 60 FPS planning and capability probing.
- Restores practical default bitrate ceilings for 480p, 720p, 1080p, and 4K.
- Adds runtime telemetry, HUD state, and safe fallback behavior.
- Validated against Jellyfin 10.11.11 on the current RK3588 reference system.

This release contains compiled binaries only. Core source code is not published.
