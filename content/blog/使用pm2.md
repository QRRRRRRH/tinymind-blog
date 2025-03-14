---
title: 使用PM2
date: 2025-03-14T06:06:50.203Z
---

. 使用PM2（推荐方法）
PM2是Node.js应用程序的生产进程管理器，它可以帮助你保持应用程序的运行，并在服务器重启后自动重启应用。
安装PM2
# 全局安装PM2
npm install -g pm2
使用PM2启动你的Next.js应用
# 进入项目目录
cd /next

# 先构建项目（如果还没构建）
npm run build -- --no-lint

# 使用PM2启动应用
pm2 start npm --name "nextjs-app" -- start
# 生成开机自启脚本
pm2 startup

# 保存当前运行的进程列表，以便开机自启
pm2 save
# 查看应用状态
pm2 status

# 查看日志
pm2 logs nextjs-app

# 重启应用
pm2 restart nextjs-app

# 停止应用
pm2 stop nextjs-app

# 删除应用
pm2 delete nextjs-app