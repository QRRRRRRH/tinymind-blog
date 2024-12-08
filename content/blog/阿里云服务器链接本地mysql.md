---
title: 阿里云服务器链接本地mysql
date: 2024-12-08T12:58:03.278Z
---

要使用 `wget` 下载 MySQL RPM 包，您可以按照以下步骤操作：

1. **打开终端**：在您的阿里云Linux服务器上打开终端。

2. **运行 `wget` 命令**：输入以下命令以下载 MySQL RPM 包：
   ```bash
   wget https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
   ```

3. **安装 RPM 包**：下载完成后，运行以下命令以安装 RPM 包：
   ```bash
   sudo rpm -ivh mysql57-community-release-el7-9.noarch.rpm
   ```

4. **更新 YUM 仓库**：安装完成后，更新 YUM 仓库以确保可以从 MySQL 仓库中安装软件包：
   ```bash
   sudo yum update
   ```

5. **安装 MySQL**：最后，运行以下命令以安装 MySQL 服务器：
   ```bash
   sudo yum install mysql-server
   ```

6. **启动 MySQL 服务**：安装完成后，启动 MySQL 服务：
   ```bash
   sudo systemctl start mysqld
   ```

7. **获取临时密码**：首次启动 MySQL 时，会生成一个临时密码。您可以使用以下命令查看临时密码：
   ```bash
   sudo grep 'temporary password' /var/log/mysqld.log
   ```

8. **登录 MySQL**：使用临时密码登录 MySQL：
   ```bash
   mysql -u root -p
   ```

9. **更改初始密码**：登录后，建议立即更改初始密码：
   ```sql
   ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';
   ```

这些步骤应该可以帮助您在阿里云Linux服务器上成功下载并安装 MySQL。如果您遇到任何问题，请随时告诉我！您也可以参考[MySQL官方文档](https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/linux-installation-yum-repo.html)获取更多详细信息。