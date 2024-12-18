```
import pyautogui  # 用于自动控制鼠标和键盘
from DrissionPage import Chromium, ChromiumOptions  # DrissionPage 是一个用于浏览器自动化的库，Chromium 类用于控制 Chromium 浏览器

# 1. 配置 Chromium 浏览器选项
co = ChromiumOptions().auto_port().incognito()
# - auto_port(): 自动配置端口
# - incognito(): 启用无痕模式，防止保存浏览历史和缓存

# 2. 启动浏览器
browser = Chromium(addr_or_opts=co)
# - addr_or_opts=co：传入浏览器配置选项

# 3. 获取浏览器当前标签页
tab = browser.get_tab()

# 4. 打开目标页面
url = 'https://core.particle.network/cloudflare.html?language=en&theme=light&_=0.1.1&siteKey=0x4AAAAAAAaHm6FnzyhhmePw'
tab.get(url, retry=3, interval=30, timeout=30)
# - retry=3: 如果加载失败，最多重试 3 次
# - interval=30: 每次重试之间的间隔 30 秒
# - timeout=30: 最大等待时间 30 秒

# 5. 获取 Cloudflare Turnstile 验证的 shadow DOM 元素
shadow_root_ele1 = tab.ele('x://*[@id="cf-turnstile"]/div').shadow_root
# - 通过 XPath 找到包含验证码的元素：//*[@id="cf-turnstile"]/div
# - shadow_root：获取该元素的 shadow DOM 根节点

# 6. 在 shadow DOM 中找到 iframe 元素
iframe1 = shadow_root_ele1.ele('t:iframe')
# - ele('t:iframe'): 通过标签名 "iframe" 获取子元素

# 7. 等待 2 秒，确保页面和 iframe 加载完成
tab.wait(2)

# 8. 获取 iframe 内部的 shadow DOM
shadow_root_ele2 = iframe1('x:/html/body').shadow_root
# - 通过 XPath 'x:/html/body' 定位 iframe 内部的 body 元素
# - shadow_root：获取该元素的 shadow DOM 根节点

# 9. 在 shadow DOM 内找到 "Verify you are human" 的验证元素
verify_element = shadow_root_ele2.ele("Verify you are human")
# - ele("Verify you are human"): 查找包含文本的元素

# 10. 计算目标元素在屏幕和页面中的位置
screen_x, screen_y = verify_element.rect.screen_location  # 获取元素在屏幕上的位置坐标
page_x, page_y = tab.rect.page_location  # 获取标签页的左上角坐标

# 11. 计算鼠标点击位置
click_x, click_y = (screen_x + page_x - 20, screen_y - page_y - 5)
# - 调整坐标位置：
#   - screen_x + page_x - 20: 向左微调 20 像素
#   - screen_y - page_y - 5: 向上微调 5 像素

# 12. 使用 pyautogui 控制鼠标移动和点击
pyautogui.moveTo(click_x, click_y, duration=0.01, tween=pyautogui.easeInElastic)
# - moveTo(): 移动鼠标到指定坐标
# - duration=0.01: 鼠标移动时间为 0.01 秒
# - tween=pyautogui.easeInElastic: 设置鼠标移动的缓动效果

pyautogui.click(clicks=3)
# - click(clicks=3): 点击鼠标 3 次
```