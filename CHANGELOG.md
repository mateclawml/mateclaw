# 更新日志

格式：日期 · 版本 · 平台。只记对用户有影响的改动。

## 2026-11-25 · 首个公开发行版

- **macOS 1.0.30**：已用 Developer ID 签名并通过 Apple 公证，公开发布，本仓库 Release 提供 `.dmg`，附 SHA-256。
- **Windows 1.1.28**：同样在本仓库 Release 提供（`MateClaw-Windows-1.1.28.zip`，与官网文件完全一致）。该版**未启用代码签名**，Windows 会提示「未知发布者」；签名证书正在走微软审核流程，线下购买的那套这次不用。
- Windows 1.1.28 安装包内仍随带一个未修改的 FFmpeg 可执行文件（GPL）。已按 GPLv3 第 6 条以书面提供方式履行义务：源码获取渠道与联系邮箱见 [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) 第四节。下一版移除。
- 音视频能力拆成独立开源插件 [mateclaw-media-plugin](https://github.com/mateclawml/media-plugin)（MIT）：macOS 1.0.30 安装包不含 FFmpeg 二进制，插件调用用户自行安装的版本。
- 两个安装包均未做任何修改，发布页附双平台 SHA-256；官网下载入口在 README 与发行说明中给出。

## 历史版本

见 [Releases](https://github.com/mateclawml/mateclaw/releases) 页。
