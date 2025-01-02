该服务基于 `wejudging/cloudflare-gost:latest` 镜像，结合了 Cloudflare 和 Gost，实现高效的代理功能。

#### 配置说明
```yaml
services:
  cloudflare-gost:
    image: wejudging/cloudflare-gost:latest
    container_name: cloudflare-gost
    ports:
      - "28888:28888"
    environment:
      - SOCKS5_MODE=true
    restart: unless-stopped