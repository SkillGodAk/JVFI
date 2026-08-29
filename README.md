<p align="center">
  <img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

**繁體中文** | [简体中文](README.zh-CN.md) | [English](README_EN.md)

JVFI 是 Jellyfin 的伺服器端即時補幀插件。播放時由 Jellyfin 官方 `jellyfin-ffmpeg` 產生可自訂幀率的標準轉碼串流，Jellyfin Web、Jellyfin Media Player、Android 與 Android TV 等客戶端不需要另外安裝擴充功能。

## 效果對比

<video src="https://skillgodak.github.io/Jellyfin-Video-Frame-Interpolation/assets/jvfi-comparison.mp4" controls muted loop playsinline></video>

[開啟 60 FPS 對比影片](https://skillgodak.github.io/Jellyfin-Video-Frame-Interpolation/assets/jvfi-comparison.mp4)

同一段 24 FPS 影片、相同解析度與時間範圍，左側為原始節奏，右側為 JVFI 60 FPS 輸出。素材：Sintel，Blender Foundation，CC BY 3.0。

## 主要功能

- 自訂 `23.976–240 FPS` 目標輸出幀率，預設 60 FPS
- 預設保留影片原始解析度，不強制降為 480p 或 1080p
- 支援 Jellyfin Web、Jellyfin Media Player、Android、Android TV 與其他相容客戶端
- 使用 Jellyfin 官方 `jellyfin-ffmpeg`，不需要替換 FFmpeg
- 自動偵測實際可用的解碼、影像處理與編碼能力
- 支援常見 Intel QSV / VAAPI、AMD VAAPI / AMF、NVIDIA NVENC、Rockchip RKMPP 與 Apple VideoToolbox 路徑偵測
- 硬體路徑不可用時自動使用相容模式；無法安全補幀時保留原 Jellyfin 播放流程
- 播放 HUD 顯示補幀狀態、時間軸 FPS、運算產能與管線速度
- 480p、720p、1080p、4K 可分別設定最低輸出位元率
- 設定介面支援繁體中文、英文與日文，並提供簡體中文說明文件

## 從 Jellyfin 擴充庫安裝

在 Jellyfin `控制台` → `插件` → `儲存庫` 新增：

- 名稱：`JVFI`
- 儲存庫網址：

```text
https://skillgodak.github.io/Jellyfin-Video-Frame-Interpolation/manifest.json
```

儲存後回到插件目錄，搜尋 `JVFI`，安裝 **JVFI - Jellyfin Video Frame Interpolation**，再完整重新啟動 Jellyfin。

## 手動安裝

從 [GitHub Releases](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/releases) 下載 ZIP，解壓縮到：

```text
jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

Docker 範例：

```text
/volume1/docker/jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

完整重新啟動 Jellyfin 後載入插件。

## 支援環境

| 項目 | 狀態 |
|---|---|
| Jellyfin 10.11.11 | 目前最低安裝版本與主要驗證版本 |
| Linux ARM64 / RK3588 | 目前主要實測平台 |
| Jellyfin Web | 支援標準轉碼串流 |
| Jellyfin Media Player | 支援標準轉碼串流 |
| Android / Android TV | 支援標準轉碼串流 |
| 其他硬體與較新 Jellyfin 版本 | 啟動時依實際能力檢查結果決定是否啟用 |

## 贊助與聯絡

覺得 JVFI 好用，歡迎自願贊助作者，支持後續 Jellyfin 版本相容、硬體測試與功能維護。

- QQ 群：`1018495751`
- Telegram 群：[加入群組](https://t.me/+l1v_7ag4mJQ3NjI1)
- GitHub Issues：[回報問題](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/issues)

JVFI 是獨立第三方插件，並非 Jellyfin 官方產品。Jellyfin 名稱及相關商標歸其權利人所有。
