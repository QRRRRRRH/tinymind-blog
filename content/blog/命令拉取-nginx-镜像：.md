---
title: 命令拉取 Nginx 镜像：
date: 2024-12-08T16:49:34.533Z
---

# 移除旧版本docker
sudo yum remove docker \
 docker-client \
 docker-client-latest \
 docker-common \
 docker-latest \
 docker-latest-logrotate \
 docker-logrotate \
 docker-engine
# 配置docker yum源。
sudo yum install -y yum-utils
sudo yum-config-manager \
--add-repo \
http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
# 安装 最新 docker
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-pl
ugin docker-compose-plugin
# 启动& 开机启动docker； enable + start ⼆合⼀
systemctl enable docker --now
在云服务器上安装 Nginx 前，您需要确保 Docker 已正确安装和运行。根据您提供的信息，似乎 Docker 服务没有启动或配置不正确。请按照以下步骤解决问题并成功拉取 Nginx 镜像：

---

### 1. 检查 Docker 服务是否启动
运行以下命令确认 Docker 是否在运行：
```bash
sudo systemctl status docker
```

- 如果显示服务未运行（`inactive` 或 `dead`），请启动 Docker：
  ```bash
  sudo systemctl start docker
  ```

- 确保 Docker 在服务器启动时自动运行：
  ```bash
  sudo systemctl enable docker
  ```

---

### 2. 确保当前用户有权限运行 Docker
默认情况下，Docker 命令需要 `root` 权限。如果您不想每次都使用 `sudo`，可以将当前用户添加到 Docker 用户组：

```bash
sudo usermod -aG docker $USER
```

然后，重新登录或运行以下命令使更改生效：
```bash
newgrp docker
```

---

### 3. 验证 Docker 是否正常工作
运行以下命令测试 Docker：
```bash
docker version
```
如果可以正常显示版本信息，说明 Docker 已正确安装和运行。

---

### 4. 拉取 Nginx 镜像
确保 Docker 正常后，使用以下命令拉取 Nginx 镜像：
```bash
docker pull nginx
```

---

### 5. 启动 Nginx 容器
拉取完成后，可以运行 Nginx 容器：
```bash
docker run -d -p 80:80 nginx
```

- `-d` 表示后台运行容器。
- `-p 80:80` 将服务器的 80 端口映射到容器的 80 端口。

---

### 6. 检查 Nginx 是否运行
使用以下命令查看运行中的容器：
```bash
docker ps
```

然后访问您的云服务器的 IP 地址，应该会看到 Nginx 的默认欢迎页。

---

如果还有问题，请贴出相关错误信息，我帮您进一步分析！