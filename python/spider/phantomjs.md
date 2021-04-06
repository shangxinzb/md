# phantomjs 无界面浏览器

[下载地址](https://phantomjs.org/download.html)

需要将phantomjs配置到环境变量中

```python
from selenium import webdriver

driver = webdriver.PhantomJS(executable_path=r'E:\python_plguin\phantomjs\bin\phantomjs.exe')
driver.get("http://www.baodu.com")
print(driver.page_source)

"""
selenium.common.exceptions.WebDriverException: Message: 'phantomjs' executable needs to be in PATH. 
可执行文件selenium.common.exceptions.WebDriverException: Message: 'phantomjs'需要在PATH中。

回答：在声明PhantomJS的时候，指定驱动路径
executable_path=r'E:\python_plguin\phantomjs\bin\phantomjs.exe'
"""

"""
UserWarning: Selenium support for PhantomJS has been deprecated, please use headless versions of Chrome or Firefox instead
  warnings.warn('Selenium support for PhantomJS has been deprecated, please use headless '

UserWarning: PhantomJS的Selenium支持已经被弃用，请使用Chrome或Firefox的无头版本
警告。警告(“PhantomJS的Selenium支持已弃用，请使用headless”)
- -。我这看的是什么时候的教程。都tm已经弃用了
"""
```



