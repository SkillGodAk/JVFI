<p align="center">
  <img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

[繁體中文](README.md) | **简体中文** | [English](README_EN.md)

JVFI 是 Jellyfin 的服务器端实时补帧插件。它提供原有的自定义目标帧率补帧，以及在合格硬件上启用的可选“平滑效果 原帧率 X2”。Jellyfin Web、Jellyfin Media Player、Android 和 Android TV 等客户端无需另外安装扩展。

## 主要功能

- 自定义 `23.976–240 FPS` 目标输出帧率，默认 60 FPS
- 可选“平滑效果 原帧率 X2”，关闭后维持原有补帧
- 默认保留视频原始分辨率，不强制降低到 480p 或 1080p
- 支持 Jellyfin Web、Jellyfin Media Player、Android、Android TV 与其他兼容客户端
- 使用 Jellyfin 官方 `jellyfin-ffmpeg`，无需替换 FFmpeg
- 自动检测实际可用的解码、图像处理与编码能力
- 硬件与补帧管线显示会根据 Jellyfin 实际硬件加速设置同步判断
- 支持常见 Intel QSV / VAAPI、AMD VAAPI / AMF、NVIDIA NVENC、Rockchip RKMPP 与 Apple VideoToolbox 路径检测
- 硬件路径不可用时自动使用兼容模式；无法安全补帧时保留原 Jellyfin 播放流程
- 平滑运行环境随插件一起安装，只用于通过自检的 JVFI 转码，不会替换 Jellyfin 全局 FFmpeg
- 播放 HUD 显示补帧状态、时间轴 FPS、运算吞吐与管线速度
- 480p、720p、1080p、1440p、4K 可分别设置最低输出码率
- 设置界面支持繁体中文、英文和日文

## 从 Jellyfin 插件目录安装

在 Jellyfin `控制台` → `插件` → `存储库` 中新增一个存储库：

- 名称：`JVFI`
- 存储库网址：

```text
https://skillgodak.github.io/JVFI/manifest.json
```

保存后返回插件目录，搜索 `JVFI`，安装 **JVFI**，再完整重启 Jellyfin。

## 手动安装

从 [GitHub Releases](https://github.com/SkillGodAk/JVFI/releases) 下载 ZIP，解压到：

```text
jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

Docker 示例：

```text
/volume1/docker/jellyfin/config/plugins/Jellyfin Video Frame Interpolation/
```

完整重启 Jellyfin 后加载插件。

## 支持环境

| 项目 | 状态 |
|---|---|
| Jellyfin 10.11.11 | 当前最低安装版本与主要验证版本 |
| Linux ARM64 / RK3588 | 当前主要实测平台 |
| Jellyfin Web | 支持标准转码流 |
| Jellyfin Media Player | 支持标准转码流 |
| Android / Android TV | 支持标准转码流 |
| 其他硬件与较新 Jellyfin 版本 | 启动时根据实际能力检查结果决定是否启用 |

0.7.7 的平滑效果 X2 限定 Linux ARM64／Linux x64。Windows 与 macOS 仍可使用原有补帧，但平滑效果会安全退回原补帧；Windows 平滑管线计划在 0.7.8 完成实测后加入。

目前只有 Linux ARM64 的 Rockchip RK3588／RK3588S 完成 JVFI 平滑效果实机验证。以下 Linux 型号只是具备相近解码、OpenCL 运算与硬件编码条件的实验候选，不代表已经确认可用；能否启用以及是否达到实时速度，仍以每台主机的完整自检结果为准。

- Linux ARM64／Rockchip：RK3576（性能低于 RK3588，4K 实时能力仍需验证）
- Linux x64／Intel：N95、N100、N150、N200、N250、Core i3-N300、Core i3-N305、Core 3 N350、Core 3 N355、Core i5-11400、Pentium Gold G7400、Arc A380／A580／A750／A770／B570／B580
- Linux x64／AMD：Radeon RX 6600／6600 XT／6700／6800／6900 系列、RX 7700 XT／7800 XT／7900 系列、RX 9060／9070 系列、Radeon Pro W6800／W7700／W7800／W7900
- Linux x64／NVIDIA：GeForce GTX 1650／1660 系列、RTX 20／30／40／50 系列、T4、RTX A2000／A4000／A5000／A6000

N100 与 N150 在 Linux 上具备 Intel Quick Sync、OpenCL 和 media-driver 所需的基础条件，因此列为较有希望的低功耗实验候选；目前尚未使用 JVFI 实机验证，不能保证 1080p 或 4K 的实时处理速度。其他 ARM SoC 因 0.7.7 尚无对应硬件适配器，暂不列入候选。

## 平滑效果范围

平滑效果固定输出为原帧率 X2，0.7.7 限定 Linux ARM64／Linux x64，目前认可的分辨率为 4K 以下（含 4K）。Windows、macOS、其他分辨率、HDR／HLG／Dolby Vision、未通过自检或不兼容的硬件路径会安全退回原有补帧，不会阻止 Jellyfin 播放。

## 赞助作者

如果 JVFI 对你有帮助，欢迎支持作者。

### 海外赞助

<a href="https://buymeacoffee.com/SkillGodAK"><img src="assets/donate-buymeacoffee.svg" alt="Buy Me a Coffee" width="180"></a>

### 银行收款

<img src="assets/donate-bank.jpg" alt="银行收款二维码" width="180">

### 微信收款

<img src="assets/donate-wechat.jpg" alt="微信收款二维码" width="180">

JVFI 是独立第三方插件，并非 Jellyfin 官方产品。Jellyfin 名称及相关商标归其权利人所有。
