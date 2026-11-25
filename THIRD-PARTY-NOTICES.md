# 麦灵 MateClaw 第三方软件与许可声明（草案）

- 版本：2026-11-25 修订
- 适用：MateClaw 麦灵 macOS 1.0.30、Windows 1.1.28（公开发行版）
- 发布主体：麦灵科技（大城县）有限公司
- 说明：本文件是发布用草案，不构成法律意见；正式发布前请律师复核。

---

## 一、非官方声明

本产品是**基于 OpenClaw 项目制作的独立发行版**，不是 OpenClaw 官方产品。

- OpenClaw 的名称、标识和版权归 OpenClaw Foundation 及其贡献者所有。
- 我们与 OpenClaw 官方**没有**隶属、代理、赞助、认证或背书关系。
- 我们未使用 OpenClaw 官方名义做推广，也未暗示获得官方认可。
- 本产品的中文界面、桌宠、语音、收费墙、安装包和官网均由麦灵科技独立制作和维护。

“MateClaw”“麦灵”的名称与标识归麦灵科技（大城县）有限公司所有。

---

## 二、随包分发的第三方软件

下表按“实际随包”列出。**macOS 版与 Windows 版并不完全相同**，不要互相照抄。

| 组件 | 版本/形态 | 许可 | 主要义务 | 备注 |
|---|---|---|---|---|
| OpenClaw | 随包运行时 | MIT | 保留版权与许可文本 | 上游底座；非官方发行版 |
| Node.js | 随包运行时 | MIT | 保留版权与许可文本 | 运行 OpenClaw |
| Electron / Chromium | Windows 桌面壳 | MIT / BSD 等 | 保留版权与许可文本 | Windows 版 |
| FFmpeg | macOS 1.0.30：**不随包**；Windows 1.1.28：随包一个未修改的预编译可执行文件 | GPLv3 | Windows 版随包分发，须提供对应源码的获取方式（已提供，见第四节） | 详见第四节 |
| Python 运行时及依赖 | 随包 | PSF / MIT / BSD / Apache 等 | 保留各自许可文本 | 逐项见安装包内声明 |
| Ollama | 随包 | MIT | 保留版权与许可文本 | 本地模型运行 |
| Kokoro 语音模型 | 随包 | Apache-2.0 | 保留版权与许可文本 | 中文语音 |
| Sherpa-ONNX | 随包 | Apache-2.0 | 保留版权与许可文本 | 语音识别/唤醒 |
| resvg | 随包 | MPL-2.0 | 保留许可文本；修改文件需公开 | 图标/图形渲染 |
| ripgrep | 随包 | MIT | 保留版权与许可文本 | 文件搜索 |
| Live2D Cubism SDK | 随包 | Live2D 专有许可 | 发布需取得发布许可，或符合免费豁免条件 | 详见第五节 |
| Live2D 官方示例模型 | 随包 5 个 | Live2D 免费素材许可 | 同意协议、署名、不得单独再分发模型文件 | 详见第五节 |
| 自研 3D 帧桌宠 | 随包 | 麦灵自有 | 其中源自 2D 角色的形象仍受原角色条款约束 | 详见第五节 |

> 说明：上表是“发布页需要让用户看得到”的版本，不是完整依赖树。安装包内的 `THIRD-PARTY-NOTICES` 应保留完整许可原文。

---

## 三、上游 OpenClaw 的署名

本产品包含 OpenClaw 项目的代码。OpenClaw 使用 MIT 许可，要求保留版权声明和许可文本。

建议在发布页固定写：

> This product is an independent distribution based on OpenClaw (MIT License). It is not affiliated with, endorsed by, or sponsored by the OpenClaw Foundation. OpenClaw’s name and logo belong to their respective owners.

中文：

> 本产品是基于 OpenClaw（MIT 许可）的独立发行版，与 OpenClaw 官方无隶属、代理、赞助或背书关系。OpenClaw 的名称与标识归其权利人所有。

---

## 四、FFmpeg 专项说明（两个平台情况不同）

### 4.1 现状（2026-11-25）

| 版本 | 包内是否含 FFmpeg | 说明 |
|---|---|---|
| macOS 1.0.30 | 否 | 视频抽帧等功能由开源插件调用用户自装 FFmpeg |
| Windows 1.1.28 | **是**，`resources/brain/bin/ffmpeg.exe` | 拆分之前打的包，未做任何修改，照原样分发 |

音视频能力本身已拆为独立开源插件：[mateclawml/media-plugin](https://github.com/mateclawml/media-plugin)（MIT）。插件不含 FFmpeg 二进制，只调用用户自己安装的 FFmpeg。**Windows 下一版将移除包内 FFmpeg**，届时两个平台一致。

### 4.2 源码提供（针对 Windows 1.1.28）

Windows 1.1.28 随包分发的是**未修改**的预编译 FFmpeg 可执行文件，按 GPLv3 分发。我们按第 6 条（b）项以书面提供方式履行义务：

- 获取渠道一：<https://ffmpeg.org/download.html>（与该二进制对应的上游源码）。
- 获取渠道二：发信到 **opensource@mateclawml.com**，写明「索取 Windows 1.1.28 内含 FFmpeg 对应源码」，我们在三个工作日内提供源码或可长期访问的获取方式。
- 该书面提供自本版发布起三年内有效。
- 我们未修改该二进制；如需构建配置与打包方式，同样可通过上述邮箱索取。

### 4.3 发布页应写的文字

> macOS 1.0.30 安装包内不含 FFmpeg 二进制，音视频功能由独立开源插件调用你本机安装的 FFmpeg。Windows 1.1.28 是拆分之前的打包，仍内置一个未修改的 FFmpeg 可执行文件，下一版移除；其源码获取方式见第三方声明。

### 4.4 不要做的事

- 不要在**新**版本安装包里继续打入 GPL 版 ffmpeg。
- 不要在发布页写「本产品完全开源」。
- 不要把 FFmpeg 说成「我们自研的音视频引擎」。
- 不要让插件去静默下载 GPL 的 ffmpeg 再分发；插件只提示用户自行安装，或引导到 FFmpeg 官方发行渠道。

---

## 五、Live2D 专项说明

### 5.1 随包模型

当前 macOS 1.0.27 包内 `models/` 有 5 个模型：

- `hiyori`
- `mao_pro`
- `natori`（名执尽）
- `shizuku`（雫）
- `wanko`（汪子）

这 5 个都是 **Live2D 官方示例模型/免费素材**，不是“开源模型”。其 ReadMe 明确：

- 需要同意《Free Material License Agreement》和《Terms of Use》。
- **General Users 和 Small-Scale Enterprises（最近一个财年销售额低于 1000 万日元）** 可以通过接受免费素材许可进行**商业使用**。
- 超过该规模的主体，只能用于**内部或监修目的**；特定宣传用途需 Live2D 书面批准。
- 不能单独再分发模型文件；需要署名。

### 5.2 Cubism SDK

Live2D Cubism SDK 本体是**专有许可**，不是开源。发布使用 SDK 制作的内容时：

- 个人和小规模事业者（同样以 1000 万日元为界）可免发布许可和费用；
- 超过规模的企业需要签 SDK Release License（Publication License Agreement）并付费；
- 无论规模，都不能单独再分发 SDK。

### 5.3 自研 3D 桌宠与 2D 角色的关系

必须纠正一个说法：**3D 角色不是与 2D 角色“没有连带关系”。**

现有 `名执尽3D`、`晓伊3D` 是“参考 2D 形象 → AI 生成 3D 形象 → 生成动作视频 → 抽帧抠绿”的产物（见 2026-10-13 晓伊 3D 生成记录）。它们描绘的是同一个角色形象，属于原角色形象的**衍生形象**。

因此：

- 原 2D 角色允许商用，3D 衍生形象才允许商用；
- 原 2D 角色不允许商用，3D 版也不能靠“自己做的”绕开；
- 署名要求同样适用于 3D 版；
- 如果 3D 形象是**完全另起炉灶的新角色**（新名字、新设定、新原画，不以现有 2D 角色为参考），才不受原角色条款约束。现有这两个不是。

### 5.4 发布页建议文字

> 本产品包含 Live2D Cubism SDK 及 Live2D 官方示例模型。Live2D Cubism 是 Live2D Inc. 的商标。示例模型按 Live2D 免费素材许可使用，版权归 Live2D Inc. 及原画作者所有。本产品中的 3D 桌宠如源自上述角色形象，同样受相应条款约束。

---

## 六、源码与许可文本的获取

- 安装包内应附 `THIRD-PARTY-NOTICES.txt`，包含各组件许可原文或链接。
- 发布页应提供：
  - 本声明；
  - 软件最终用户许可协议（EULA）；
  - 隐私政策；
  - FFmpeg 源码获取方式（如保留 GPL 构建）。
- 联系邮箱：**[待开通：opensource@mateclawml.com]**（建议同时保留 `support@mateclawml.com`）。

---

## 七、发布前检查清单

- [ ] Windows 包内**无** ffmpeg 可执行文件（已确认移除）
- [ ] 插件仓库可访问，README 写清 FFmpeg 自行安装方式
- [ ] 未装 FFmpeg 时，插件给出明确提示而不是静默失败
- [ ] macOS 包内确认无 ffmpeg 可执行文件
- [ ] 5 个 Live2D 模型均有 ReadMe/许可文件
- [ ] 公司最近一个财年销售额是否低于 1000 万日元，已由财务确认
- [ ] 3D 桌宠来源已逐个标注（原创/衍生）
- [ ] 发布页有“非官方声明”
- [ ] 发布页有 EULA、隐私政策、校验值
- [ ] 未使用“完全开源”“官方”“自研音视频引擎”等误导性表述

---

*草案建立：2026-11-16 ｜ 维护：Sky ｜ 依据：安装包实物、Live2D 官网许可原文、项目内生成记录*
