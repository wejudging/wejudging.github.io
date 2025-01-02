### route.json配置
```yaml
{
"rules": [
            {
                "type": "field",
                "domain": [
                    "openai.com",
                    "chatgpt.com",
                    "whatismyipaddress.com",
                    "ipaddress.my",
                    "whatismyip.com"
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
