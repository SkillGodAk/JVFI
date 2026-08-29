<p align="center">
  <img src="assets/jvfi-banner.png" alt="JVFI - Jellyfin Video Frame Interpolation" width="900">
</p>

# Jellyfin Video Frame Interpolation (JVFI)

[繁體中文](README.md) | **简体中文** | [English](README_EN.md)

JVFI 是 Jellyfin 的服务器端实时补帧插件。播放时由 Jellyfin 官方 `jellyfin-ffmpeg` 生成可自定义帧率的标准转码流，Jellyfin Web、Jellyfin Media Player、Android 和 Android TV 等客户端无需另外安装扩展。

## 主要功能

- 自定义 `23.976–240 FPS` 目标输出帧率，默认 60 FPS
- 默认保留视频原始分辨率，不强制降低到 480p 或 1080p
- 支持 Jellyfin Web、Jellyfin Media Player、Android、Android TV 与其他兼容客户端
- 使用 Jellyfin 官方 `jellyfin-ffmpeg`，无需替换 FFmpeg
- 自动检测实际可用的解码、图像处理与编码能力
- 支持常见 Intel QSV / VAAPI、AMD VAAPI / AMF、NVIDIA NVENC、Rockchip RKMPP 与 Apple VideoToolbox 路径检测
- 硬件路径不可用时自动使用兼容模式；无法安全补帧时保留原 Jellyfin 播放流程
- 播放 HUD 显示补帧状态、时间轴 FPS、运算吞吐与管线速度
- 480p、720p、1080p、4K 可分别设置最低输出码率
- 设置界面支持繁体中文、英文和日文，并提供简体中文说明文档

## 从 Jellyfin 插件目录安装

在 Jellyfin `控制台` → `插件` → `存储库` 中新增：

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

## 赞助作者

如果 JVFI 对你有帮助，欢迎支持作者。

### 银行收款

<img src="assets/donate-bank.jpg" alt="银行收款二维码" width="360">

### 微信收款

<img src="assets/donate-wechat.jpg" alt="微信收款二维码" width="360">

JVFI 是独立第三方插件，并非 Jellyfin 官方产品。Jellyfin 名称及相关商标归其权利人所有。
