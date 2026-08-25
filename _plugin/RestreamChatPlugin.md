---
hide: false
title: Restream 聚合聊天
auther: wan0ge
plugin_author: wan0ge
plugin_name: Restream 聚合聊天
plugin_desc: 通过 Restream Chat API 把多平台的聊天集成至弹幕姬（无需连接 B 站）
plugin_version: 1.3.0
plugin_update_datetime: 2026-08-25 13:30:00 +0800
plugin_update_desc: |-
  初始发布：通过 Restream Chat API 聚合 Twitch/YouTube/Kick 等多平台直播聊天至弹幕姬。
plugin_dllink: /resource/RestreamChatPlugin/RestreamChatPlugin.dll
plugin_dlnote: 下载 RestreamChatPlugin.dll 放入 我的文档\弹幕姬\plugins\ 重启弹幕姬即可
---

通过 Restream Chat API 把 Twitch / YouTube / Kick 等多平台直播聊天聚合为弹幕姬弹幕，无需连接 B 站直播间。

插件界面
---
<img class="shadow" src="https://www.danmuji.org/resource/RestreamChatPlugin/preview.png" alt="插件界面" />

插件功能
---
- 多平台聊天聚合（Twitch / YouTube / Kick 等）
- Restream OAuth 授权登录，令牌过期自动续期
- 代理设置：直连 / 系统代理 / 自定义地址
- 表情包图片渲染（独立浮层可选）
- 中文 / 日本語 / English 本地化
- 单文件部署（已内嵌 Newtonsoft.Json）

安装方法
---
下载 `RestreamChatPlugin.dll`，放入 `我的文档\弹幕姬\plugins\`，重启弹幕姬即可。插件首次运行会在 `Plugins\RestreamChatPlugin\` 下自动创建数据目录，用于存放配置与表情缓存。

使用说明
---
使用前需先准备 Restream 应用：在 [Restream 开发者后台](https://developers.restream.io/apps) 创建应用，记下 Client ID 与 Client Secret，并把回调地址（Redirect URI）设为 `http://localhost:8989/callback`。

在弹幕姬「插件」选项卡找到 **Restream 聚合聊天**，右键「管理」打开设置窗口，在第①步填入 Client ID 与 Client Secret；点击「授权」登录 Restream 并允许 Chat API 访问，授权回调到本机后选择代理模式（默认系统代理），点击「保存并连接」或右键「启用」即可开始接收多平台聊天。

开源仓库
---
源代码与问题反馈：<https://github.com/wan0ge/RestreamChatPlugin>

更新日志
---
- 2026-08-25 初始发布 v1.3.0
