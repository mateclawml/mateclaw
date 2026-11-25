# 更新日志

格式：日期 · 版本 · 平台。只记对用户有影响的改动。

## 2026-11-25 · 首个公开发行版

- **macOS 1.0.30**：已用 Developer ID 签名并通过 Apple 公证，公开发布，本仓库 Release 提供 `.dmg`，附 SHA-256。
- **Windows 1.1.28**：未启用代码签名，且该版安装包内仍随带 FFmpeg 二进制。为避免公开镜像扩大 GPL 组件的分发范围，**不在本仓库托管**，只在官网提供下载；下一版移除内置 FFmpeg 并完成签名后再在本仓库发布。
- 音视频能力拆成独立开源插件 [mateclaw-media-plugin](https://github.com/mateclawml/media-plugin)（MIT）：macOS 安装包不含 FFmpeg 二进制，插件调用用户自行安装的版本。
- 第三方声明第四节重写：说明「不分发即无源码提供义务」的口径。

## 历史版本

见 [Releases](https://github.com/mateclawml/mateclaw/releases) 页。
