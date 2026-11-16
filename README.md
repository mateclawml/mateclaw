# MateClaw 麦灵

**一款在你自己电脑上跑的中文 AI 助手桌面端。装好就能用，不绑账号，不碰你的数据。**

> ⚠️ 本仓库是**公开的发行与说明页**，不是开源代码仓库。软件源代码不公开。
> 本产品是**基于 OpenClaw（MIT 许可）的独立发行版，与 OpenClaw 官方无隶属、代理、赞助或背书关系。**

---

## 这是什么

麦灵把「一个大模型助手」做成了桌面上随手可用的东西：常驻一个会说话、会动的小助手，能读文件、能做表格、能剪视频抽帧、能写东西、能定时记事。模型由你自己选、自己付费给厂商，我们不经手。

- 系统：macOS 15.7 及以上（Apple 芯片）／ Windows 10 及以上（64 位）
- 界面语言：**目前仅中文**
- 免费版永久免费；全能版一次性买断
- 数据存在你本机；需要联网的功能才会联网

## 下载

到 [Releases](https://github.com/mateclawml/mateclaw/releases) 页下载对应平台安装包，页面附 SHA-256 校验值。

| 平台 | 文件 | 说明 |
| --- | --- | --- |
| macOS（Apple 芯片） | `.dmg` | 已签名并公证，系统 15.7 起 |
| Windows（64 位） | `-setup.exe` | 已代码签名 |

安装前请核对校验值。校验方法：

```bash
# macOS
shasum -a 256 MateClaw-*.dmg
# Windows
certutil -hashfile MateClaw-*-setup.exe SHA256
```

## 安装

**macOS**：打开 `.dmg`，把「麦灵」拖进「应用程序」，首次启动如提示「无法验证开发者」，到「系统设置 → 隐私与安全性」点「仍要打开」。

**Windows**：双击安装包，按提示下一步。首次运行如被 SmartScreen 拦，点「更多信息 → 仍要运行」。

## 关于本仓库

| 内容 | 是否公开 |
| --- | --- |
| 说明文档、截图、发布说明、问题模板 | 公开 |
| 安装包与校验值 | 公开 |
| 软件源代码、构建脚本、签名证书 | 不公开 |
| 收费、激活、支付后端 | 不公开 |

- 许可见 [LICENSE](LICENSE)（仅覆盖本仓库内容，不覆盖软件本体）。
- 第三方组件与许可见 [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)。
- 安全问题请见 [SECURITY.md](SECURITY.md)，**不要**在公开问题区贴漏洞细节。
- 我们**不接受代码合并请求**（Pull Request），因为源代码不公开；欢迎提问题和建议。

## 反馈

- 安装、启动、崩溃 → 用「安装 / 启动问题」模板
- 功能不对、结果异常 → 用「功能异常」模板
- 想要什么功能 → 用「功能建议」模板

请附上：系统版本、麦灵版本号、复现步骤、截图或日志。**不要贴密钥、身份证、聊天记录等敏感内容。**

## 购买与支持

免费版可直接下载使用。全能版与售后支持请到官网：<https://www.mateclawml.com>

本仓库不放价格，也不做收银台。

## 商标与致谢

「MateClaw」「麦灵」为麦灵科技（大城县）有限公司的商标。

感谢 OpenClaw（MIT）、FFmpeg、Live2D Cubism 及所有开源作者。

---

# English

**MateClaw is a desktop AI assistant for Chinese users, running on your own machine.** Bring your own model provider; we never see your keys or your chats.

> ⚠️ This repository is a **public release and documentation page**, not an open-source code repository. The application source code is not public.
> This product is an **independent distribution based on OpenClaw (MIT License)** and is **not affiliated with, endorsed by, or sponsored by the OpenClaw project.**

**Current limitations, stated plainly:**

- **The user interface is Chinese only.** There is no language switcher yet.
- Documentation here is bilingual; the in-app experience is not.
- Windows and macOS builds are separate download files; there is no auto-update between platforms.

**Download** from [Releases](https://github.com/mateclawml/mateclaw/releases) and verify the published SHA-256 checksum. macOS builds are signed and notarized; Windows builds are code-signed.

**Requirements:** macOS 15.7+ (Apple silicon) or Windows 10+ (64-bit).

**Licensing:** repository content is covered by [LICENSE](LICENSE). The application itself is licensed under a separate end-user license agreement available at <https://www.mateclawml.com>. Third-party components are listed in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

**No pull requests, please** — the source is closed. Issues and feature requests are welcome.

**Purchase and support:** <https://www.mateclawml.com>

---

*维护：麦灵科技（大城县）有限公司 ｜ 联系：opensource@mateclawml.com*
