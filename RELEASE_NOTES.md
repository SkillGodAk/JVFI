# JVFI 0.7.7

## 更新

- 新增「平滑效果 原幀率 X2」。

## 平滑效果目前範圍

- 平滑效果固定輸出為原幀率 X2。
- 目前認可的解析度為 4K 以下（含 4K）。
- 其他解析度、HDR／HLG／Dolby Vision、未通過自測或不相容的硬體路徑，會安全退回原有補幀，不會阻止 Jellyfin 播放。

## 實驗性硬體候選

目前只有 Rockchip RK3588／RK3588S 完成實機驗證。以下型號具備相近或更高等級的硬體條件，或具備 Jellyfin 硬體轉碼與運算能力，但尚未完成 JVFI 實機驗證；只有在實際主機通過自測後才會啟用平滑效果。

- ARM／Rockchip：RK3576（效能低於 RK3588，僅列為較低階實驗候選）。
- Intel N 系列：N95、N100、N150、N200、N250、Core i3-N300、Core i3-N305、Core 3 N350、Core 3 N355。
- Intel Core／Arc：Core i5-11400、Pentium Gold G7400，以及 Arc A380、A580、A750、A770、B570、B580。
- AMD Radeon：RX 6600／6700／6800／6900 系列、RX 7700 XT、7800 XT、7900 GRE／XT／XTX、RX 9060／9060 XT、9070／9070 XT，以及 Radeon Pro W6800、W7700、W7800、W7900。RX 6400／6500 沒有合適的硬體編碼器，不列入候選。
- NVIDIA：GTX 1650／1660 系列、RTX 2060／2070／2080、RTX 3050／3060／3070／3080／3090、RTX 4060／4070／4080／4090、RTX 5050／5060／5070／5080／5090，以及 T4、RTX A2000、A4000、A5000、A6000。

以上全部屬於實驗功能。列入名單只表示具備進入自測的基本條件，不代表已確認可用，也不保證能達到即時播放速度。

---

# English

## Changes

- Added **Smooth effect — source FPS X2**.

## Current Smooth X2 scope

- Smooth effect always outputs source FPS X2.
- The currently accepted resolution range is up to and including 4K.
- Other resolutions, HDR/HLG/Dolby Vision, failed self-tests, and incompatible hardware paths safely fall back to the original interpolation path without blocking Jellyfin playback.

## Experimental hardware candidates

Only Rockchip RK3588/RK3588S has completed real-hardware validation. The following models have comparable or higher hardware capabilities, or provide the media and compute features required to enter JVFI qualification, but remain unvalidated. Smooth X2 is enabled only after the current host passes its self-test.

- ARM/Rockchip: RK3576 (lower performance than RK3588; listed only as a lower-tier experimental candidate).
- Intel N-series: N95, N100, N150, N200, N250, Core i3-N300, Core i3-N305, Core 3 N350, and Core 3 N355.
- Intel Core/Arc: Core i5-11400, Pentium Gold G7400, and Arc A380, A580, A750, A770, B570, and B580.
- AMD Radeon: RX 6600/6700/6800/6900 series, RX 7700 XT, 7800 XT, 7900 GRE/XT/XTX, RX 9060/9060 XT, 9070/9070 XT, and Radeon Pro W6800, W7700, W7800, and W7900. RX 6400/6500 are excluded because they lack a suitable hardware encoder.
- NVIDIA: GTX 1650/1660 series, RTX 2060/2070/2080, RTX 3050/3060/3070/3080/3090, RTX 4060/4070/4080/4090, RTX 5050/5060/5070/5080/5090, T4, and RTX A2000/A4000/A5000/A6000.

All entries above are experimental. Inclusion means only that the model has the basic requirements to enter self-test; it does not confirm compatibility or guarantee real-time playback speed.
