# JVFI 0.7.7 Dev 2.0

## 更新內容

- 修正「平滑效果 原幀率 X2」被固定解析度白名單限制的問題。
- 4K 範圍內的偶數尺寸影片可走同一套 Base3 路徑，例如 3840x1640、2560x1440、1920x800、1280x720。
- Render surface 保留原始尺寸與比例，不會為了補幀強制 resize 成 16:9。
- Motion analysis 維持固定 1920x1080 工作域，依實際畫面尺寸自動計算 scale，未使用區域以 padding 處理。
- 不新增 CPU resize / hwdownload 前置轉換。
- 保留 Dev 1.0 的 N218 ARM64 motion-source 傳輸優化。

## 驗證

- 完整單元測試：170 / 170 PASS。
- 3840x1640 等非 16:9 解析度已通過 Base3 命令建立測試，不再退回 framerate。
- 超出 4K envelope 或奇數尺寸仍會安全回退。

> GitHub 版本名稱為 **0.7.7 Dev 2.0**；Jellyfin 外掛版本號為 **0.7.7.2**，讓已安裝 0.7.7.1 Dev 1.0 的使用者能偵測到新版。

---

# English

## Changes

- Removed the fixed-resolution whitelist from Smooth X2.
- Even-sized surfaces within the 4K envelope, including 3840x1640, 2560x1440 and 1920x800, can use the same Base3 path.
- Native render dimensions and aspect ratio are preserved; the video is not forced to 16:9.
- Motion analysis remains bounded to a 1920x1080 work domain with automatic scale selection and padding.
- No CPU resize or hwdownload pre-conversion is added.
- Dev 1.0's N218 ARM64 motion-source transport optimization is retained.

## Validation

- Full unit test suite: 170 / 170 PASS.
- Non-16:9 4K surfaces such as 3840x1640 are accepted by the Base3 command path instead of falling back to framerate.
- Odd-sized or out-of-envelope surfaces still fail closed.

> GitHub release name: **0.7.7 Dev 2.0**. Jellyfin plugin version: **0.7.7.2**, allowing Dev 1.0 installations on 0.7.7.1 to detect the update.
