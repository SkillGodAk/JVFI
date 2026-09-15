# JVFI 0.7.6

## 更新

- 改善高位深 SDR 影片的補幀相容性，10-bit 等影片不再單純因位深而被誤判為 HDR 並跳過 JVFI。
- 改善不同影片格式的處理方式，讓更多 Jellyfin 可正常解碼的 SDR 影片能進入 JVFI 補幀。
- 優化硬體補幀流程，會依最終輸出格式自動選擇合適的處理方式，避免不必要的格式轉換與效能損耗。
- 改善 RKMPP、Intel QSV、VAAPI、NVIDIA 等硬體路徑的相容性。
- 修正 Jellyfin 12.x 載入插件資訊時可能出現的 metadata 相容性問題。
- HDR、HLG 與 Dolby Vision 目前仍維持 Jellyfin 原本的處理方式，不強制套用 JVFI 補幀。

---

# English

## Changes

- Improved frame interpolation compatibility for high bit-depth SDR videos. 10-bit content is no longer treated as HDR based on bit depth alone.
- Improved video-format handling so more SDR content that Jellyfin can decode can enter the JVFI interpolation pipeline.
- Optimized the hardware interpolation path by automatically selecting an appropriate working format based on the final output, avoiding unnecessary format conversions and performance overhead.
- Improved compatibility across RKMPP, Intel QSV, VAAPI, NVIDIA, and other hardware paths.
- Fixed a plugin metadata compatibility issue that could appear when loading JVFI on Jellyfin 12.x.
- HDR, HLG, and Dolby Vision currently continue to use Jellyfin's original processing path and are not forced through JVFI interpolation.
