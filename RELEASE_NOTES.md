# JVFI 0.7.7

## 更新

- 新增「平滑效果 原幀率 X2」。

## 平滑效果目前範圍

- 平滑效果固定輸出為原幀率 X2。
- 0.7.7 限定支援 Linux ARM64 與 Linux x64。
- 目前認可的解析度為 4K 以下（含 4K）。
- Windows 與 macOS 可繼續使用原有補幀；勾選平滑效果時會安全退回原補幀。
- 其他解析度、HDR／HLG／Dolby Vision、未通過自測或不相容的硬體路徑，也會安全退回原有補幀，不會阻止 Jellyfin 播放。

## 實驗性硬體候選

目前只有 Linux ARM64 的 Rockchip RK3588／RK3588S 完成實機驗證。

以下型號僅為具備基本硬體條件，不代表已確認可用，也不保證即時播放速度。只有實際主機完整自測通過後，才會啟用平滑效果。

- Linux ARM64／Rockchip：RK3576（效能低於 RK3588，僅列為較低階實驗候選）。
- Linux x64／Intel N 系列：N95、N100、N150、N200、N250、Core i3-N300、Core i3-N305、Core 3 N350、Core 3 N355。
- Linux x64／Intel Core／Arc：Core i5-11400、Pentium Gold G7400，以及 Arc A380、A580、A750、A770、B570、B580。
- Linux x64／AMD Radeon：RX 6600／6600 XT／6700／6800／6900 系列、RX 7700 XT、7800 XT、7900 GRE／XT／XTX、RX 9060／9060 XT、9070／9070 XT，以及 Radeon Pro W6800、W7700、W7800、W7900。RX 6400／6500 沒有合適的硬體編碼器，不列入候選。
- Linux x64／NVIDIA：GTX 1650／1660 系列、RTX 2060／2070／2080、RTX 3050／3060／3070／3080／3090、RTX 4060／4070／4080／4090、RTX 5050／5060／5070／5080／5090，以及 T4、RTX A2000、A4000、A5000、A6000。

0.7.7 的平滑效果 X2 限定 Linux ARM64／Linux x64。Windows 與 macOS 仍可使用原有補幀；平滑效果會安全退回原補幀。Windows 平滑管線預計於 0.7.8 完成實測後加入。

---

# English

## Changes

- Added **Smooth effect — source FPS X2**.

## Current Smooth X2 scope

- Smooth effect always outputs source FPS X2.
- Version 0.7.7 is limited to Linux ARM64 and Linux x64.
- The currently accepted resolution range is up to and including 4K.
- Windows and macOS retain the original interpolation path; enabling Smooth safely falls back to it.
- Other resolutions, HDR/HLG/Dolby Vision, failed self-tests, and incompatible hardware paths also safely fall back to the original interpolation path without blocking Jellyfin playback.

## Experimental hardware candidates

Only Rockchip RK3588/RK3588S on Linux ARM64 has completed real-hardware validation.

The following models only meet the basic hardware requirements. They are not confirmed compatible and real-time playback performance is not guaranteed. Smooth effect is enabled only after the actual host passes its complete self-test.

- Linux ARM64/Rockchip: RK3576 (lower performance than RK3588; listed only as a lower-tier experimental candidate).
- Linux x64/Intel N-series: N95, N100, N150, N200, N250, Core i3-N300, Core i3-N305, Core 3 N350, and Core 3 N355.
- Linux x64/Intel Core/Arc: Core i5-11400, Pentium Gold G7400, and Arc A380, A580, A750, A770, B570, and B580.
- Linux x64/AMD Radeon: RX 6600/6600 XT/6700/6800/6900 series, RX 7700 XT, 7800 XT, 7900 GRE/XT/XTX, RX 9060/9060 XT, 9070/9070 XT, and Radeon Pro W6800, W7700, W7800, and W7900. RX 6400/6500 are excluded because they lack a suitable hardware encoder.
- Linux x64/NVIDIA: GTX 1650/1660 series, RTX 2060/2070/2080, RTX 3050/3060/3070/3080/3090, RTX 4060/4070/4080/4090, RTX 5050/5060/5070/5080/5090, T4, and RTX A2000/A4000/A5000/A6000.

Smooth X2 in version 0.7.7 is limited to Linux ARM64 and Linux x64. Windows and macOS retain the original interpolation path, and Smooth safely falls back to it. Windows Smooth support is planned for version 0.7.8 after real-hardware validation.
