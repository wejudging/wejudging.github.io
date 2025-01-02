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
            "address": "129.146.241.219",
            "port": 18888,
            "users": [
              {
                "user": "weijiajin",
                "pass": "weijiajin",
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
