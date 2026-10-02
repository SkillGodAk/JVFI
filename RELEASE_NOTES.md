# JVFI 0.7.7

## 更新

- 新增可選的「平滑效果 原幀率 X2」。未開啟時完整保留 0.7.6 原有的可自訂幀率補幀。
- 正式安裝包內建 Linux ARM64 與 Linux x64 的 JVFI 私有 FFmpeg 薄殼、AVFilter 與 Base3 核心；只作用於通過驗證的 JVFI 平滑轉碼，不會替換 Jellyfin 全域 FFmpeg。
- 新增硬體端到端自測與安全回退。Rockchip RKMPP 已實機驗證；Linux x64 的 Intel QSV／VAAPI、AMD VAAPI 與 NVIDIA CUDA／NVENC 只有在目前主機完成解碼、平滑補幀與硬體編碼自測後才會啟用。
- 修正長片平滑播放的初始化與視窗數量限制。
- 修正 4K 跳播後的音畫時間戳、EAC3 轉 AAC 可能無聲，以及播放退出後轉碼仍持續執行的問題。
- 改善 4K 高動態場景的 H.264 輸出品質，修正 23.976→47.952 FPS 未套用高幀率位元率保護，並新增 1440p 獨立位元率級距。
- 保留 Jellyfin 原有 HLS 分段、GOP、關鍵幀與起始編號契約，改善開始播放與跳播等待時間。

## 平滑效果目前範圍

- 平滑效果固定輸出為原幀率 X2。
- 目前核准的 Base3 surface 為 `1920x1080` 與 `3840x2160`。
- 其他解析度、HDR／HLG／Dolby Vision、未通過自測或不相容的硬體路徑，會安全退回原有補幀，不會阻止 Jellyfin 播放。

---

# English

## Changes

- Added the optional **Smooth effect — source FPS X2** mode. When it is disabled, the complete configurable frame-rate interpolation path from 0.7.6 remains unchanged.
- The release package now bundles JVFI's private FFmpeg shim, AVFilter, and Base3 core for Linux ARM64 and Linux x64. They are applied only to qualified JVFI smooth transcodes and never replace Jellyfin's global FFmpeg installation.
- Added end-to-end hardware self-tests and safe fallback. Rockchip RKMPP is hardware-validated; Intel QSV/VAAPI, AMD VAAPI, and NVIDIA CUDA/NVENC on Linux x64 are enabled only when decode, Smooth X2, and hardware encode pass on the current host.
- Fixed long-playback initialization and window-count limits.
- Fixed audio/video timestamps after 4K seeks, possible missing audio during EAC3-to-AAC transcoding, and transcoding processes continuing after playback stopped.
- Improved H.264 quality for high-motion 4K content, fixed the high-frame-rate bitrate guard for 23.976→47.952 FPS, and added a separate 1440p bitrate tier.
- Preserved Jellyfin's HLS segment, GOP, keyframe, and start-number contracts to improve playback startup and seeking.

## Current Smooth X2 scope

- Smooth effect always outputs source FPS X2.
- The currently qualified Base3 surfaces are `1920x1080` and `3840x2160`.
- Other resolutions, HDR/HLG/Dolby Vision, failed self-tests, and incompatible hardware paths safely fall back to the original interpolation path without blocking Jellyfin playback.
