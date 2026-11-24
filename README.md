# MagicVol

<p align="center">
  把媒体音量分成 10 档：最小一格不再太响，最大一格也不浪费。
</p>

<p align="center">
  <img src="https://img.shields.io/badge/LSPosed-API%20102-3B5F94" alt="LSPosed API 102">
  <img src="https://img.shields.io/badge/作用域-system-3B5F94" alt="作用域 system">
  <img src="https://img.shields.io/badge/Android-10%2B-3B5F94" alt="Android 10+">
  <img src="https://img.shields.io/badge/版本-1.1.2%20(17)-7F6C9B" alt="版本 1.1.2 (17)">
</p>

系统媒体音量通常是 15 或 25 档线性步进，最小一格往往还是偏响，最大一格又用不到。MagicVol 在 `system_server` 里把媒体音量表改成 **10 档**：0 档静音，1–9 档分别设置相对系统最大音量的百分比，只改媒体音量。

## 功能

- **10 档媒体音量**：0 档静音；1–9 档百分比 0–100 可调，保存时自动校正（低档不会高于高档，0/负值回默认，超过 100 按 100 算）。
- **只影响媒体音量**：铃声、通话、闹钟、通知音量保持系统原样。
- **内置「推荐」方案**：7 / 12 / 17 / 22 / 27 / 40 / 60 / 80 / 100%。它只是方案列表里的一个按钮，点「✓ 推荐」才会套用；全新安装仍使用默认档位，不会自动改。
- **多套方案**：保存为方案、重命名、删除，随时切换。
- **按递增快速填档**：输入起始值和递增步长，一次填满 9 个档位（超过 100% 的按 100% 算）。
- **内置测试音频**：设置页可直接播放一段约 3 秒的音频（播放一遍，不循环），边播边调档位、切方案，直接听响度差别；离开页面自动停止。
- **即时生效**：改完档位通过 RemotePreferences 通知 system_server 重新读表，不用重启。

默认档位：`11 / 22 / 33 / 44 / 56 / 67 / 78 / 89 / 100%`

## 使用

1. 安装 APK，在 LSPosed 中启用 MagicVol。
2. 作用域勾选「系统框架」（`system`）。
3. 重启手机（或重启系统框架）让 hook 生效。
4. 打开 MagicVol 设置页，拖动 9 个档位滑块，或选一套方案后点底部的「更新音量设置」。

> 首次启用需要重启一次；之后改档位即时生效。

## 兼容性

- Android 10 及以上（minSdk 29，targetSdk 34）。
- 框架：libxposed API 102（LSPosed 2.x）。
- 仅在 HONOR BRT-AN00 / MagicOS 11.0.0.115（Android 17）实测；其他系统版本请自行体验。不同 ROM 的音量表实现可能有差异，遇到问题请附日志提 issue。

## 签名

APK 使用项目固定的测试签名（与 1.0.x 历史版本相同），可以直接覆盖升级。

## 源码与反馈

- 源码：<https://github.com/Jocoks/MagicVol>
- 问题反馈：<https://github.com/Jocoks/MagicVol/issues>
- 更新日志：<https://github.com/Jocoks/MagicVol/releases>

## 版本

当前 **1.1.2**（versionCode **17**）。

- 1.1.2：新增内置测试音频；「推荐」方案改为纯可选，不再自动套用；升级时还原旧版自动选中的推荐状态（仅一次）。
- 1.1.0：内置「推荐」方案，9 档 7–100%。
