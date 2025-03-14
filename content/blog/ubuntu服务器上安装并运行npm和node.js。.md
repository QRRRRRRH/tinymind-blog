---
title: Ubuntu服务器上安装并运行npm和Node.js。
date: 2025-03-14T05:41:39.547Z
---

看起来你需要在Ubuntu服务器上安装并运行npm和Node.js。你已经上传了打包好的文件到root目录，但系统提示你npm命令不存在。

以下是解决步骤：

1. 首先安装Node.js和npm：
```bash
apt update
apt install nodejs npm
```

2. 安装完成后，验证安装：
```bash
nodejs --version
npm --version
```

3. 现在你可以进入root目录并运行npm命令：
```bash
cd /root
npm i
```

如果你需要特定版本的Node.js，或者希望管理多个Node.js版本，可以考虑使用nvm（Node Version Manager）：

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install node  # 安装最新版Node.js
# 或者安装特定版本
# nvm install 18  # 安装Node.js 18.x
```

安装完成后，你就可以在root目录中运行npm命令来安装依赖并启动你的应用了。