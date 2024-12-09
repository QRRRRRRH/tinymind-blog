---
title: 修改docker里nginx 目录
date: 2024-12-09T06:35:42.289Z
---

docker run -d -p 80:80 nginx

在 Docker 中安装的 Nginx 的目录位置通常如下：

1. **配置文件**：`/etc/nginx/nginx.conf`
2. **HTML 文件**：`/usr/share/nginx/html`
3. **日志文件**：`/var/log/nginx`

如果你需要访问这些目录，可以按照以下步骤操作：

1. **启动一个临时容器**：
    ```bash
    docker run --name tmp-nginx-container -d nginx
    ```

2. **创建本地目录并拷贝临时容器中的文件到本地路径**：
    ```bash
    mkdir -p /docker/nginx/
    docker cp tmp-nginx-container:/etc/nginx/nginx.conf /docker/nginx/nginx.conf
    docker cp -a tmp-nginx-container:/usr/share/nginx/html /docker/nginx
    docker cp -a tmp-nginx-container:/etc/nginx/conf.d /docker/nginx
    ```

3. **删除临时容器**：
    ```bash
    docker rm -f tmp-nginx-container
    ```

4. **重新映射容器并启动**：
    ```bash
    docker run --name mynginx -e TZ="Asia/Shanghai" -d -p 80:80 \
    -v /docker/nginx/html:/usr/share/nginx/html \
    -v /docker/nginx/nginx.conf:/etc/nginx/nginx.conf \
    -v /docker/nginx/conf.d:/etc/nginx/conf.d \
    -v /docker/nginx/logs:/var/log/nginx nginx
    ```

这样，你就可以在本地目录中找到并管理 Nginx 的配置文件、HTML 文件和日志文件了¹²。

如果你有其他问题，随时告诉我哦！

源: 与 Copilot 的对话， 2024/12/9
(1) docker中nginx的默认路径位置和映射目录启动方式例子解析 .... https://blog.csdn.net/jimn2000/article/details/142755857.
(2) docker中nginx的默认路径位置和映射目录启动 - CSDN博客. https://blog.csdn.net/baidu_21349635/article/details/102738972.
(3) docker怎么查看nginx位置_mob64ca12db3721的技术博客 .... https://blog.51cto.com/u_16213344/8928918.
(4) docker容器查看nginx安装目录_mob64ca12d2a342的技术 .... https://blog.51cto.com/u_16213309/8851667.
