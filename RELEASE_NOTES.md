# JVFI 0.7.5

## 新增

- 新增「同時觀看上限」，可限制同一時間啟用 JVFI 補幀的播放數量。
- 達到設定上限後，新開始的播放將不啟用 JVFI 補幀，並維持 Jellyfin 原本的播放方式。
- 已經取得補幀的播放不會受到後續新播放影響，會持續補幀直到該次播放結束。

## 改善

- 改善「套用使用者」介面，讓每位使用者與其套用媒體庫的層級更容易辨識。

---

# English

## Added

- Added a **Concurrent Viewing Limit** to control how many playback sessions can use JVFI frame interpolation at the same time.
- When the configured limit is reached, newly started playback will not use JVFI interpolation and will follow Jellyfin's original playback behavior.
- Playback sessions that have already started with interpolation will continue normally until that playback session ends.

## Improvements

- Improved the **Users** section so each user's selected libraries are easier to distinguish.
