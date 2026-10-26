---
title: "Codex"
linkTitle: "Codex"
weight: 100
date: 2021-01-18
description: >
  Codex 安装配置和运行
---

## 安装

参考 https://learn.chatgpt.com/docs/codex/cli#getting-started

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

输出为:

```bash
==> Installing Codex CLI
==> Detected platform: Linux (x64)
==> Resolved version: 0.164.0
==> Downloading Codex CLI
==> Installing standalone package to /home/sky/.codex/packages/standalone/releases/0.164.0-x86_64-unknown-linux-musl
==> /home/sky/.local/bin is already on PATH
==> Current terminal: codex
==> Future terminals: open a new terminal and run: codex
Codex CLI 0.164.0 installed successfully.
Start Codex now? [y/N] n
```

验证一下:

 ```bash
$ codex --version
codex-cli 0.164.0

$ which codex
/home/sky/.local/bin/codex
```

## 运行

### 登录

```bash
$ codex 
```

显示菜单：

```bash
  Welcome to Codex, OpenAI's command-line coding agent
 
  Choose how you want to use Codex.
 
> 1. Sign in with ChatGPT
     Usage included with Plus, Pro, Business, and Enterprise plans
 
  2. Sign in with Device Code
     Sign in from another device with a one-time code
 
  3. Use an OpenAI API key
     Pay for what you use
 
  4. Use Amazon Bedrock
     Connect using your AWS credentials
 
  Press enter to continue
```

选 1, 会自动打开默认浏览器跳到登录页面，由于默认浏览器一般不会是指纹浏览器，所以不要在这里登录。"ctrl + shift + c" 复制界面上的登录 URL，然后在 ads power 中打开（打开前确认代理已经准备好）。

输入之前申请的 chatgpt plus 用的帐号 aoxiaojian@protonmail.com， 验证码会发到这个邮箱。检查邮箱，从邮件中获取到验证码，输入后登录成功。提示 Select a workspace，我这里只有一个 personal account 可以选择，点击 continue：

```bash
Signed in to Codex
You may now close this page
```

此时 codex  cli 上显示登录成功：

```bash
  Welcome to Codex, OpenAI's command-line coding agent
 
✓ Signed in with your ChatGPT account
 
  You're in control
  Learn about permissions and approvals in the Codex docs
 
  Codex can make mistakes
  Review the code it writes and commands it runs
 
  Included with your ChatGPT plan
  Your plan's rate limits and training data preferences apply
 
  Press enter to continue
```

回车确认，然后开始使用。

> 注意： `/resuem` 操作只能在之前运行环境中进行，也就是说 resume 需要的数据是保留在本地而不是云端，所以不能机器A操作完成后，到机器B上继续。

## 升级

升级前先设置好代理，方便升级过程中下载 codex cli 安装文件。

升级就是重新执行一次安装命令：

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

输出如下：

```bash
==> Installing Codex CLI
==> Detected platform: Linux (x64)
==> Resolved version: 0.164.0
==> Detected existing npm-managed Codex at /home/sky/.nvm/versions/node/v24.21.0/bin/codex
WARNING: Multiple managed Codex installs can be ambiguous because PATH order decides which one runs.
==> Downloading Codex CLI
==> Installing standalone package to /home/sky/.codex/packages/standalone/releases/0.164.0-x86_64-unknown-linux-musl
Uninstall the existing npm-managed Codex now? [y/N] y
==> Running: npm uninstall -g @openai/codex

removed 2 packages in 219ms
==> Current terminal: export PATH="/home/sky/.local/bin:$PATH" && codex
==> Future terminals: open a new terminal and run: codex
==> PATH was added to /home/sky/.zshrc
Codex CLI 0.164.0 installed successfully.
Start Codex now? [y/N] y
==> Launching Codex
```