### route.json配置
```yaml
{
"rules": [
            {
                "type": "field",
                "domain": [
                    "chatgpt.com",
                    "openai.com",
                    "oaistatic.com",
                    "oaiusercontent.com",
                    "openai.com.cdn.cloudflare.net",
                    "openaiapi-site.azureedge.net",
                    "openaicom-api-bdcpf8c6d2e9atf6.z01.azurefd.net",
                    "openaicomproductionae4b.blob.core.windows.net",
                    "production-openaicom-storage.azureedge.net",
                    "claude.ai",
                    "anthropic.com",
                    "gemini.google.com",
                    "proactivebackend-pa.googleapis.com",
                    "ai.google.dev",
                    "alkalimakersuite-pa.clients6.google.com",
                    "makersuite.google.com",
                    "bard.google.com",
                    "deepmind.com",
                    "deepmind.google",
                    "generativeai.google",
                    "apis.google.com" 
                ],
                "outboundTag": "chatgpt"
            }
        ]
}
```

### outbound.json配置
```yaml
[
{
            "tag": "direct",
            "protocol": "freedom",
            "settings": {}
        },
 {
      "protocol": "socks",
      "tag": "chatgpt",
      "settings": {
        "servers": [
          {
            "address": "ip",
            "port": 端口,
            "users": [
              {
                "user": "用户名",
                "pass": "密码",
                "level": 0
              }
            ]
          }
        ]
      }
    }
    ,
{
"protocol": "blackhole",
"settings": {},
"tag": "blocked"
}
]
```
