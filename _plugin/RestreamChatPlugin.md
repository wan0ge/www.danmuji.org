---
hide: false
title: Restream 聚合聊天
auther: wan0ge
plugin_author: wan0ge
plugin_name: Restream 聚合聊天
plugin_desc: 通过 Restream Chat API 把多平台的聊天集成至弹幕姬（无需连接 B 站）
plugin_version: 1.5.0
plugin_update_datetime: 2026-08-26 00:30:00 +0800
plugin_update_desc: |-
  独立浮层置顶增强：采用与弹幕姬自带浮层一致的机制（每秒重新置顶 + WS_EX_TRANSPARENT/TOOLWINDOW 扩展样式 + 失焦重断言），不再被全屏播放器等同样置顶的应用遮挡；动态表情动画渲染修正：改用 GDI+ 逐帧播放 GIF（规避 WPF 首帧缓存不刷新），并修复 Twitch 原生动画表情被当作静态图——Restream 下发的 v1 地址为静态 PNG，改为 v2 动画 GIF 地址下载后逐帧播放。
plugin_dllink: /resource/RestreamChatPlugin/RestreamChatPlugin.dll
plugin_dlnote: 下载 RestreamChatPlugin.dll 放入 我的文档\弹幕姬\plugins\ 重启弹幕姬即可
---

通过 Restream Chat API 把 Twitch / YouTube / Kick 等多平台直播聊天聚合为弹幕姬弹幕，无需连接 B 站直播间。

插件界面
---
<img class="shadow" src="https://www.danmuji.org/resource/RestreamChatPlugin/preview.png" alt="消息效果预览" />

设置窗口
---
<img class="shadow" src="https://www.danmuji.org/resource/RestreamChatPlugin/preview2.png" alt="设置窗口预览" />

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
使用前需先在 Restream 侧准备应用（仅首次）：打开 [Restream](https://restream.io) 注册登录，在后台「Channels」添加并授权直播平台；打开 [Restream 开发者后台](https://developers.restream.io/apps) 创建应用，把 Redirect URI 设为 `http://localhost:8989/callback`、Scopes 勾选 `chat.read`，记下 Client ID 与 Client Secret。

在弹幕姬「插件」选项卡找到 **Restream 聚合聊天**，右键「管理」打开设置窗口，按五个步骤操作：

1. **准备工作（仅首次）**：按上述在 Restream 侧建好应用，窗口内提供 Redirect URI 复制按钮可一键填入。
2. **填入应用凭证**：填入 Client ID 与 Client Secret。
3. **授权并连接**：点击「登录并授权」自动打开浏览器，登录并同意授权后插件通过本地回调自动拿到 token；若失败可用「手动粘贴 code」方式授权。
4. **可选设置**：代理模式默认「直连（不使用代理）」，可改为「系统代理」或填写「自定义代理」；也可直接粘贴手动 access token。
5. **显示与高级**：独立浮层（默认关，开启后把 Twitch / Kappa 等表情渲染成图片）、浮层布局与位置、调试日志。

点击「保存并连接」或右键「启用」即可开始接收多平台聊天。

开源仓库
---
源代码与问题反馈：<https://github.com/wan0ge/RestreamChatPlugin>

更新日志
---
- 2026-08-25 初始发布 v1.3.0
- 2026-08-25 更新 v1.4.0：独立浮层始终置顶；动态表情（BTTV/7TV 动画 GIF）可播放；修正第三方表情地址适配当前 API
- 2026-08-26 更新 v1.5.0：独立浮层置顶增强（全屏播放器等同样置顶应用不再遮挡）；动态表情动画渲染修正（改用 GDI+ 逐帧播放 GIF，并修复 Twitch 原生动画表情被当作静态图——改下 v2 动画 GIF 地址）
