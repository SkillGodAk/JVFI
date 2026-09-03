# JVFI 0.7.4

## 更新

- 新增「套用媒體庫」選擇，可指定哪些 Jellyfin 媒體庫啟用補幀。

## 修正

- 修正部分環境手動指定 RKMPP、Intel QSV 等硬體模式可能無法真正生效的問題。
- 改善「自動模式」：自動模式會優先保留 Jellyfin 已選好的硬體編碼；若 Jellyfin 目前使用軟體編碼，才由 JVFI 自動判斷。

---

# English

## Updates

- Added media library selection, allowing frame interpolation to be enabled only for selected Jellyfin libraries.

## Fixes

- Fixed an issue where manually selected hardware modes such as RKMPP and Intel QSV might not actually take effect in some environments.
- Improved **Auto mode**: it keeps the hardware encoder already selected by Jellyfin. If Jellyfin is currently using software encoding, JVFI chooses the hardware automatically.
