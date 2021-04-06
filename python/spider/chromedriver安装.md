# Chromedriver安装

[Chromedriver下载地址](http://chromedriver.storage.googleapis.com/index.html)

1. 查看当前安装的Google浏览器版本号
2. 根据版本号找到对应的Chromedriver应用版本
3. 下载后，将Chromedriver.exe放到 `/python/Script/`文件夹中

## 检查是否安装成功

```python
from selenium import webdriver

# 声明一个google浏览器
chrome = webdriver.Chrome()
# 打开百度
chrome.get('http://www.baidu.com')
```

