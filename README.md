<p align="center"><img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900"></p>

# Jellyfin Video Frame Interpolation (JVFI)

**繁體中文** | [简体中文](README.zh-CN.md) | [English](README_EN.md)

JVFI 是專為 Jellyfin 設計的伺服器端即時補幀插件。播放影片時，JVFI 會將影片處理為使用者設定的目標幀率，讓低幀率影片播放得更流暢。Jellyfin Web、Jellyfin Media Player、Android 與 Android TV 等客戶端不需要另外安裝 JVFI。

## 主要功能

- 支援自訂 `23.976-240 FPS` 輸出，預設 `60 FPS`
- 伺服器端即時補幀，預設保留原始解析度
- 自動偵測硬體加速能力，支援 Intel、AMD、NVIDIA、Rockchip 與 Apple 常見平台
- 硬體不可用時使用相容路徑，無法安全補幀時保留 Jellyfin 原始播放流程
- 支援 Jellyfin Web、Jellyfin Media Player、Android、Android TV 與標準轉碼串流客戶端
- 提供即時補幀狀態、處理資訊與安全回退
- 可分別設定 480p、720p、1080p、4K 最低輸出位元率
- 設定介面支援繁體中文、英文與日文，並提供簡體中文說明

## 硬體支援

JVFI 依伺服器實際能力選擇處理方式，不只依硬體型號判斷。

| 硬體平台 | 狀態 |
|---|---|
| Rockchip RK3588 / RK3588S | 已實機測試 |
| Intel、AMD、NVIDIA | 已加入支援，持續測試中 |
| Apple 裝置 | 已加入相容支援，持續測試中 |
| 純 CPU 環境 | 可使用，效能依處理器而定 |

## 幀率、解析度與位元率

支援 `23.976-240 FPS`，預設 `60 FPS`。JVFI 預設保留 Jellyfin 選擇的影片解析度，不會主動降低畫質。

| 解析度 | 最低位元率 |
|---|---:|
| 480p | 4 Mbps |
| 720p | 8 Mbps |
| 1080p | 16 Mbps |
| 4K | 40 Mbps |

## 安裝

### Jellyfin 擴充庫

進入 `控制台 -> 插件 -> 儲存庫`，新增：

```text
https://skillgodak.github.io/JVFI/manifest.json
```

回到插件目錄搜尋 `JVFI`，安裝後完整重新啟動 Jellyfin。

### 手動安裝

從 [GitHub Releases](https://github.com/SkillGodAk/JVFI/releases) 下載插件 ZIP，解壓縮到 Jellyfin 的 `config/plugins/` 目錄，再完整重新啟動 Jellyfin。

## 使用方式

安裝並重新啟動後，進入 `控制台 -> 插件 -> JVFI`，開啟插件並設定目標幀率，播放影片即可由伺服器端處理補幀。

## 即時狀態

JVFI 可顯示啟用狀態、目標 FPS、即時處理速度與補幀工作狀態。實際呈現幀率仍可能受到播放器、顯示器與裝置性能影響。

## 相容性

| 項目 | 狀態 |
|---|---|
| Jellyfin 10.11.11 | 目前主要支援與測試版本 |
| Linux ARM64 / RK3588 | 已實機測試 |
| Jellyfin Web / Media Player | 支援 |
| Android / Android TV | 支援標準轉碼串流 |

## 贊助作者

覺得 JVFI 好用，歡迎支持作者。

### 國外贊助

[Buy Me a Coffee](https://buymeacoffee.com/SkillGodAK)

### 銀行收款

<img src="assets/donate-bank.jpg" alt="銀行收款 QR Code" width="360">

### 微信收款

<img src="assets/donate-wechat.jpg" alt="微信收款 QR Code" width="360">

JVFI 是獨立第三方 Jellyfin 插件，並非 Jellyfin 官方產品。
