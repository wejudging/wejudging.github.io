在现代应用中，流量转发和域名解析是部署服务的关键环节。尤其是需要处理多域名场景时，基于 **SNI（Server Name Indication）** 的流量转发可以显著简化配置管理和提高服务性能。在本文中，我将通过一个基于 `docker-compose` 的配置示例，介绍如何利用 NGINX 的 `ssl_preread` 功能实现 SNI 识别，并根据域名转发流量到不同的后端服务。

---

## 配置场景概述

假设有以下需求：
1. 根据请求的域名，将流量转发到不同的后端服务。
   - 如果域名是 `*.weijiajin.com`，流量转发到 `web` 服务。
   - 如果域名是 `feelheart.eastasia.cloudapp.azure.com`，流量转发到 `trojan` 服务。
   - 如果域名不匹配上述规则，默认转发到 `web` 服务。
2. 后端服务的端口不同：
   - `web` 服务监听 `ip:443`。
   - `trojan` 服务监听 `ip:8443`。
3. 使用 Docker 容器运行 NGINX，支持动态更新。

---

## 配置文件解析

以下是完整的配置内容和解析。

### 1. Docker Compose 配置

```yaml
services:
  nginx:
    image: nginx:latest
    container_name: nginx
    ports:
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    restart: always
```

### 2. NGINX 配置文件
```
stream {
    # SNI 识别域名并映射到后端服务
    map $ssl_preread_server_name $backend_name {
        *.weijiajin.com web;
        feelheart.eastasia.cloudapp.azure.com trojan;
        default web;
    } 

    # web 服务的转发配置
    upstream web {
        server 64.110.100.168:443;
    }

    # trojan 服务的转发配置
    upstream trojan {
        server 8.210.144.45:8443;
    }

    # 监听 443 端口，启用 SNI 识别
    server {
        listen 443 reuseport;
        listen [::]:443 reuseport;
        proxy_pass  $backend_name;
        ssl_preread on;
    }
}

# 必须的基础配置
events {}
```