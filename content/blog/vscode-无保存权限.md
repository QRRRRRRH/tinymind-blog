---
title: vscode 无保存权限
date: 2025-01-24T08:07:55.741Z
---

Q
PS C:\Users\Qrh12> nvm install 18.20.2
>>
nvm : 无法将“nvm”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径正确，然后再
试一次。
所在位置 行:1 字符: 1
+ nvm install 18.20.2
+ ~~~
    + CategoryInfo          : ObjectNotFound: (nvm:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
。。。还是无法解决


确认NVM安装：

手动下载安装
访问 https://github.com/coreybutler/nvm-windows/releases
下载 nvm-setup.exe
以管理员身份运行安装程序
安装后验证
打开新的PowerShell窗口
输入 nvm version
临时解决方案
直接下载并安装Node.js 18.20.2 官方安装包
从官网 https://nodejs.org 下载
如仍无法解决，可能需要：

重启电脑
检查杀毒软件是否阻止
重新安装Node.js
 Copy
Retry



Q
在vscode里面不行 ，在系统的可以


对于VSCode中无法识别nvm命令的情况：

配置VSCode终端
打开VSCode设置
搜索"terminal.integrated.env"
添加系统PATH环境变量
手动配置
VSCode设置 -> settings.json
添加：
json

Copy
"terminal.integrated.env.windows": {
  "PATH": "${env:PATH};C:\\Path\\To\\Nvm"
}
重启VSCode
完全关闭并重新打开
如仍不行，建议使用系统命令提示符或PowerShell安装和管理Node版本。