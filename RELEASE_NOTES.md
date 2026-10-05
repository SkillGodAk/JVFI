# JVFI 0.7.7 Dev 1.0

## 更新內容

- 改善 RK3588／RK3588S 在 4K「平滑效果 原幀率 X2」播放時，部分固定畫面會突然卡頓的問題。
- 重新調整補幀分析前的資料傳輸方式，減少 GPU 與 CPU 之間不必要的等待與資料搬移。
- 補幀演算法與輸出畫面內容不變，主要是改善資料供應流程與播放穩定性。
- 保留原本的安全回退機制；不相容的環境仍會退回原有補幀。

## 目前測試狀態

- Linux ARM64／Rockchip RK3588、RK3588S：已完成實機驗證。
- Windows x64／NVIDIA、Intel、AMD：平滑 X2 尚未完成實機驗證。
- Linux x64 仍維持實驗候選狀態，未列為已完成實機驗證。

> GitHub 版本名稱為 **0.7.7 Dev 1.0**；Jellyfin 外掛版本號為 **0.7.7.1**，讓已安裝 0.7.7.0 的使用者可以正常收到更新。

---

# English

## Changes

- Improved a fixed-scene stutter issue seen during 4K **Smooth — source FPS X2** playback on RK3588/RK3588S.
- Reworked the motion-analysis data path to reduce unnecessary GPU/CPU waiting and data transfers.
- The interpolation algorithm and rendered frame results are unchanged; this update focuses on data-flow and playback stability.
- Existing safe fallback behavior remains in place for incompatible environments.

## Current validation status

- Linux ARM64 / Rockchip RK3588 and RK3588S: real-hardware validation completed.
- Windows x64 / NVIDIA, Intel, AMD: Smooth X2 has not yet completed real-hardware validation.
- Linux x64 remains experimental and is not listed as real-hardware validated.

> GitHub release name: **0.7.7 Dev 1.0**. Jellyfin plugin version: **0.7.7.1** so installations on 0.7.7.0 can detect the update.
