# freitag-script

## 1. 淘宝自动登录脚本

* 配置 mitmproxy
```python
TARGET_URL = 'https://g.alicdn.com/secdev/sufei_data/3.6.8/index.js'
INJECT_TEXT = 'Object.defineProperties(navigator,{webdriver:{get:() => false}});'

def response(flow):
 if flow.request.url.startswith(TARGET_URL):
  flow.response.text = INJECT_TEXT + flow.response.text
  print('注入成功')
```

* 启动代理
```bash
mitmdump -s HttpProxy.py -p 9000
```
