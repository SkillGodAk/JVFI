<p align="center">
  <img src="assets/jvfi-banner.png" alt="Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

**繁體中文** | [English](README_EN.md)

**JVFI 是免費的 Jellyfin 伺服器端即時補幀插件。**

它會在播放期間要求 Jellyfin 使用官方 `jellyfin-ffmpeg` 轉碼，依照實際硬體能力選擇解碼、處理與編碼路徑，並將低幀率影片輸出為最高 60 FPS 的串流。補幀在伺服器端完成，因此 Jellyfin Web、Jellyfin Media Player、Android 與 Android TV 等標準客戶端不需要另外安裝擴充功能。

> 本公開倉庫提供安裝目錄、版本資訊、說明文件與編譯成品；核心原始碼不公開。JVFI 完全免費使用，但不是開源軟體。

## 主要功能

- 可自訂 `23.976–240 FPS` 目標輸出幀率，預設 60 FPS
- 使用 Jellyfin 官方 `jellyfin-ffmpeg`，不替換官方 FFmpeg
- 自動偵測可用解碼器、硬體加速與編碼器
- Intel QSV / VAAPI、AMD VAAPI、NVIDIA NVENC、Rockchip RKMPP 等能力導向規劃
- 硬體路徑不可用時安全回退至相容模式
- 顯示補幀狀態、時間軸 FPS、運算產能與管線速度
- 支援繁體中文介面
- 伺服器端處理，標準 Jellyfin 客戶端可直接播放輸出串流

## 目前補幀方式

JVFI 0.7.2 使用官方 FFmpeg 現有濾鏡建立自訂幀率相容輸出。硬體引擎可負責解碼、影像處理或編碼，但補幀階段不應被描述為 AI、光流模型或所有平台皆具備的硬體 Motion FRC。實際效能與畫質取決於目標 FPS、處理器、驅動、影片解析度、編碼格式與 Jellyfin 轉碼設定。

## 安裝外掛庫

1. 開啟 Jellyfin 管理控制台。
2. 進入 `插件` → `儲存庫`。
3. 新增儲存庫名稱：`JVFI`。
4. 貼上以下網址：

```text
https://raw.githubusercontent.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/main/manifest.json
```

5. 回到 `目錄`，找到 **Jellyfin Video Frame Interpolation** 並安裝。
6. 完整重新啟動 Jellyfin。

Jellyfin 官方文件也採用 Repository Manifest URL 安裝第三方插件；新增一次儲存庫後，後續版本會直接顯示在插件目錄。

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

## 相容性

| 項目 | 狀態 |
|---|---|
| Jellyfin 10.11.11 | 目前最低建置 ABI 與已驗證版本 |
| Linux ARM64 / RK3588 | 目前主要實測平台 |
| Jellyfin Web | 支援標準轉碼串流 |
| Jellyfin Media Player | 支援標準轉碼串流 |
| Android / Android TV | 支援標準轉碼串流 |
| 較新的 Jellyfin 10.11.x | 允許安裝；啟動時再做攔截點與 FFmpeg 能力檢查 |
| 未來 Jellyfin 主要版本 | 依共享組件 ABI 與攔截點檢查決定，必要時提供對應建置 |

`targetAbi` 只表示最低可安裝版本，不是最高版本鎖。Harmony 攔截點可能隨 Jellyfin 更新改變；通過方法簽名與 FFmpeg capability probe 才啟用補幀，未通過時停用 JVFI 並保留原 Jellyfin 播放路徑。

## 效果對比

同一段 Jellyfin 影片的「原始幀率 / JVFI 60 FPS」短片將放在這裡。示範素材會避免使用沒有再散布權利的商業影片，並保持相同場景、解析度與時間範圍，讓順暢度差異可以公平比較。

## 完全免費

JVFI 不收取安裝費、訂閱費或裝置授權費。

覺得 JVFI 好用，歡迎自願贊助作者，支持後續 Jellyfin 版本相容、硬體測試與功能維護。贊助完全自願，不影響任何功能。

## 聯絡作者

- QQ 群：`1018495751`
- Telegram 群：[加入群組](https://t.me/+l1v_7ag4mJQ3NjI1)
- GitHub Issues：[回報問題](https://github.com/SkillGodAk/Jellyfin-Video-Frame-Interpolation/issues)

## 聲明

JVFI 是獨立第三方插件，並非 Jellyfin 官方產品。Jellyfin 名稱及相關商標歸其權利人所有。
