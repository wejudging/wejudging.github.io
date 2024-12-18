### 核心代码

```
import pyautogui
from DrissionPage import Chromium, ChromiumOptions

co = ChromiumOptions().auto_port().incognito()
browser = Chromium(addr_or_opts=co)
tab = browser.get_tab()
tab.get('https://core.particle.network/cloudflare.html?language=en&theme=light&_=0.1.1&siteKey=0x4AAAAAAAaHm6FnzyhhmePw', retry=3, interval=30, timeout=30)

shadow_root_ele1 = tab.ele('x://*[@id="cf-turnstile"]/div').shadow_root
iframe1 = shadow_root_ele1.ele('t:iframe')
tab.wait(2)
shadow_root_ele2 = iframe1('x:/html/body').shadow_root
verify_element=shadow_root_ele2.ele("Verify you are human")
screen_x, screen_y = verify_element.rect.screen_location
page_x, page_y = tab.rect.page_location
click_x, click_y = (screen_x + page_x -20,screen_y - page_y - 5 ,)
pyautogui.moveTo(click_x, click_y, duration=0.01, tween=pyautogui.easeInElastic)
pyautogui.click(clicks=3)
```