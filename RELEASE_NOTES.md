# JVFI 0.7.4

## 更新

- 新增「套用範圍」，可針對每位 Jellyfin 使用者分別指定哪些媒體庫啟用補幀。

## 修正

- 修正部分環境手動指定 RKMPP、Intel QSV 等硬體模式可能無法真正生效的問題。
- 改善「自動模式」：自動模式會優先保留 Jellyfin 已選好的硬體編碼；若 Jellyfin 目前使用軟體編碼，才由 JVFI 自動判斷。

---

# English

## Updates

- Added **Scope** settings, allowing each Jellyfin user to have an independent set of libraries where frame interpolation is enabled.

## Fixes

- Fixed an issue where manually selected hardware modes such as RKMPP and Intel QSV might not actually take effect in some environments.
- Improved **Auto mode**: it keeps the hardware encoder already selected by Jellyfin. If Jellyfin is currently using software encoding, JVFI chooses the hardware automatically.
