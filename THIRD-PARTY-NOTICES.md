# 麦灵 MateClaw 第三方软件与许可声明（草案）

- 版本：2026-11-16 草案
- 适用：MateClaw 麦灵 macOS 1.0.27、Windows 1.1.26
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
| FFmpeg | **仅 Windows 1.1.26 随包** `brain/bin/ffmpeg.exe` | **GPLv3**（含 x264/x265） | 提供对应源码与构建脚本，或改用非 GPL 构建 | 详见第四节 |
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

## 四、FFmpeg 专项说明（Windows 版必须处理）

### 4.1 现状

Windows 1.1.26 安装包内确实带有：

- 路径：`resources/brain/bin/ffmpeg.exe`
- 大小：约 161 MB
- 构建参数：含 `--enable-gpl`、`--enable-version3`、`--enable-libx264`、`--enable-libx265`
- 组件声明：`libavcodec license: GPL version 3 or later` 等

因此它是 **GPLv3 构建**，随包分发就产生 GPLv3 的源码提供义务。

macOS 1.0.27 安装包内**没有** ffmpeg 可执行文件；视频抽帧功能依赖用户机器上自行安装的 ffmpeg。macOS 版目前不产生“随包分发 FFmpeg”的义务，但功能可用性依赖用户环境。

### 4.2 合规写法（二选一）

**方案 A（推荐）：换成 LGPL 构建，重新出包**

- 关闭 `--enable-gpl`、`--enable-version3`、`--enable-libx264`、`--enable-libx265`。
- 只保留抽帧、转码需要的编码器/解码器。
- 重新回归测试“视频抽帧、音频转换”等用到 ffmpeg 的功能。
- 成本：一次重打包与回归，约两三天。
- 好处：不触发 GPLv3 的“传染”义务，麦灵自有代码保持闭源。

**方案 B：保留 GPLv3 构建，履行源码义务**

- 在发布页提供与二进制**完全对应**的 FFmpeg 源码包和构建脚本；或提供书面要约。
- 源码义务只覆盖 FFmpeg 及其依赖，**不要求公开麦灵自有代码**。
- 成本：要维护一个源码包/下载页，且每次升级 ffmpeg 都要同步。
- 风险：源码包必须“完整对应”，漏一个依赖库就可能不合规。

### 4.3 发布页建议文字

> 本产品的 Windows 版随包包含 FFmpeg（GPLv3 构建），用于视频抽帧与格式转换。FFmpeg 的完整对应源码及构建脚本可通过以下方式获取：[源码包下载链接] 或 [书面要约联系方式]。该源码提供义务仅适用于 FFmpeg 及其依赖组件，不适用于麦灵自有软件。

### 4.4 不要做的事

- 不要在发布页写“本产品完全开源”——FFmpeg 是 GPL，不代表麦灵是开源项目。
- 不要把 FFmpeg 说成“我们自研的音视频引擎”。
- 不要只附一个 GPL 文本、不给源码获取方式。

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

- [ ] Windows 包内 ffmpeg 是 GPL 还是 LGPL，已用 `-version` 或构建参数确认
- [ ] 若保留 GPL：源码包/构建脚本已上传，链接可访问
- [ ] 若换 LGPL：抽帧、转码功能已回归
- [ ] macOS 包内确认无 ffmpeg 可执行文件
- [ ] 5 个 Live2D 模型均有 ReadMe/许可文件
- [ ] 公司最近一个财年销售额是否低于 1000 万日元，已由财务确认
- [ ] 3D 桌宠来源已逐个标注（原创/衍生）
- [ ] 发布页有“非官方声明”
- [ ] 发布页有 EULA、隐私政策、校验值
- [ ] 未使用“完全开源”“官方”“自研音视频引擎”等误导性表述

---

*草案建立：2026-11-16 ｜ 维护：Sky ｜ 依据：安装包实物、Live2D 官网许可原文、项目内生成记录*
