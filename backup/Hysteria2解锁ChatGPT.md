```yaml
outbounds:
  - name: ipv4
    type: direct
    direct:
      mode: 4
  - name: openai
    type: socks5
    socks5:
      addr: ip:端口
      username: 用户名
      password: 密码
acl:
  inline:
    - openai(suffix:chatgpt.com)
    - openai(suffix:openai.com)
    - openai(suffix:oaistatic.com)
    - openai(suffix:oaiusercontent.com)
    - openai(suffix:openai.com.cdn.cloudflare.net)
    - openai(suffix:openaiapi-site.azureedge.net)
    - openai(suffix:openaicom-api-bdcpf8c6d2e9atf6.z01.azurefd.net)
    - openai(suffix:openaicomproductionae4b.blob.core.windows.net)
    - openai(suffix:production-openaicom-storage.azureedge.net)
    - openai(suffix:claude.ai)
    - openai(suffix:anthropic.com)
    - openai(geosite:openai)
    - reject(geosite:google@ads)

```
