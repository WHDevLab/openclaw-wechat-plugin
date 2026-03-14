
# openclaw-wechat-plugin

OpenClaw 微信机器人WebHook插件

## 安装

```bash
openclaw plugins install @whdevlab/openclaw-wechat-plugin
```

启用渠道：

```bash
openclaw config set channels.openclaw-wechat-plugin.enabled true
```

## 首次登录

```bash
openclaw channels login --channel openclaw-wechat-plugin
```

终端会显示微信二维码（或浏览器链接），用微信扫码并确认后，浏览器会跳转到新页面，地址栏 URL 形如：

```
https://security.guanjia.qq.com/login?code=001j6y000...&state=64c077c4e078...
```

复制 `code=` 后面的值（到 `&` 之前），在**另一个终端窗口**写入临时文件：

```bash
echo "001j6y0000MiZV1uYB300cEYDG1j6y0x" > ~/.openclaw/wechat-auth-code.tmp
```

也可以直接粘贴完整 URL，会自动提取 `code`：

```bash
echo "https://security.guanjia.qq.com/login?code=001j6y0000MiZV1uYB300cEYDG1j6y0x&state=64c077..." > ~/.openclaw/wechat-auth-code.tmp
```

原窗口会自动检测并完成登录，token 自动保存。然后重启 Gateway：

```bash
openclaw gateway restart
```

