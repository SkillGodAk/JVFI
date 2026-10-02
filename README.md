<p align="center"><img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900"></p>

# Jellyfin Video Frame Interpolation (JVFI)

**繁體中文** | [简体中文](README.zh-CN.md) | [English](README_EN.md)

JVFI 是專為 Jellyfin 設計的伺服器端即時補幀插件。播放影片時，可使用原有的自訂目標幀率補幀，或在合格硬體上啟用「平滑效果 原幀率 X2」。Jellyfin Web、Jellyfin Media Player、Android 與 Android TV 等客戶端不需要另外安裝 JVFI。

## 主要功能

- 支援自訂 `23.976-240 FPS` 輸出，預設 `60 FPS`
- 可選的「平滑效果 原幀率 X2」，關閉時維持原有補幀
- 伺服器端即時補幀，預設保留原始解析度
- 自動偵測原有補幀的硬體加速能力；平滑效果 X2 在 0.7.7 限定 Linux ARM64／Linux x64
- 硬體與補幀管線顯示會依 Jellyfin 實際硬體加速設定同步判斷
- 硬體不可用時使用相容路徑，無法安全補幀時保留 Jellyfin 原始播放流程
- 支援 Jellyfin Web、Jellyfin Media Player、Android、Android TV 與標準轉碼串流客戶端
- 提供即時補幀狀態、處理資訊與安全回退
- 平滑執行環境隨插件一起安裝，只套用於通過自測的 JVFI 轉碼，不替換 Jellyfin 全域 FFmpeg
- 可分別設定 480p、720p、1080p、1440p、4K 最低輸出位元率
- 設定介面支援繁體中文、英文與日文

## 硬體支援

0.7.7 的平滑效果 X2 限定 Linux ARM64／Linux x64。Windows 與 macOS 仍可使用原有補幀，但平滑效果會安全退回原補幀；Windows 平滑管線預計於 0.7.8 完成實測後加入。

目前只有 Linux ARM64 的 Rockchip RK3588／RK3588S 完成 JVFI 平滑效果實機驗證。以下是 Linux 上具備相近解碼、OpenCL 運算與硬體編碼條件的實驗候選，不代表已確認可用；實際能否啟用與是否達到即時速度，仍以該主機完整自測結果為準。

- Linux ARM64／Rockchip：RK3576（效能低於 RK3588，4K 即時能力仍需驗證）
- Linux x64／Intel：N95、N100、N150、N200、N250、Core i3-N300、Core i3-N305、Core 3 N350、Core 3 N355、Core i5-11400、Pentium Gold G7400、Arc A380／A580／A750／A770／B570／B580
- Linux x64／AMD：Radeon RX 6600／6600 XT／6700／6800／6900 系列、RX 7700 XT／7800 XT／7900 系列、RX 9060／9070 系列、Radeon Pro W6800／W7700／W7800／W7900
- Linux x64／NVIDIA：GeForce GTX 1650／1660 系列、RTX 20／30／40／50 系列、T4、RTX A2000／A4000／A5000／A6000

N100 與 N150 在 Linux 上具備 Intel Quick Sync、OpenCL 與 media-driver 所需的基礎條件，因此列為較有機會的低功耗實驗候選；目前尚未在 JVFI 實機驗證，不能保證 1080p 或 4K 的即時處理速度。其他 ARM SoC 因 0.7.7 尚無對應硬體適配器，暫不列入候選。

## 幀率、解析度與位元率

支援 `23.976-240 FPS`，預設 `60 FPS`。JVFI 預設保留 Jellyfin 選擇的影片解析度，不會主動降低畫質。

| 解析度 | 最低位元率 |
|---|---:|
| 480p | 4 Mbps |
| 720p | 8 Mbps |
| 1080p | 16 Mbps |
| 1440p | 30 Mbps |
| 4K | 40 Mbps |

## 平滑效果範圍

平滑效果固定輸出為原幀率 X2，0.7.7 限定 Linux ARM64／Linux x64，目前認可的解析度為 4K 以下（含 4K）。Windows、macOS、其他解析度、HDR／HLG／Dolby Vision、未通過自測或不相容的硬體路徑會安全退回原有補幀，不會阻止 Jellyfin 播放。

## 安裝

### Jellyfin 擴充庫

進入 `控制台 -> 插件 -> 儲存庫`，新增一個儲存庫。

資源庫名稱：`JVFI`

儲存庫網址：

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

<a href="https://buymeacoffee.com/SkillGodAK"><img src="assets/donate-buymeacoffee.svg" alt="Buy Me a Coffee" width="180"></a>

### 銀行收款

<img src="assets/donate-bank.jpg" alt="銀行收款 QR Code" width="180">

### 微信收款

<img src="assets/donate-wechat.jpg" alt="微信收款 QR Code" width="180">

JVFI 是獨立第三方 Jellyfin 插件，並非 Jellyfin 官方產品。
