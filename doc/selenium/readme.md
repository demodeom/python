# Selenium

推荐使用 Firefox 浏览器

## 一、驱动

### 1.1 驱动下载

#### 1.1.1 Google Chrome 驱动下载

Google Chrome 驱动下载地址  [https://googlechromelabs.github.io/chrome-for-testing/](https://googlechromelabs.github.io/chrome-for-testing/)

Chrome 浏览器版本和Driver驱动版本要一致，否则可能出现未知错误

**Chrome 浏览器如何查看版本?**

在浏览器地址栏输入 **chrome://version/** 即可查看版本

```
chrome://version/
```

#### 1.1.2 Firefox 驱动下载

Firefox驱动可以在  [GitHub Release](https://github.com/mozilla/geckodriver/releases) 下载

```
https://github.com/mozilla/geckodriver/releases
```



```
https://mirror.ghproxy.com/https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-linux64.tar.gz

https://mirror.ghproxy.com/https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-win64.zip
```




### 1.2 驱动安装

将驱动文件存放目录添加到系统环境变量 Path， 以  火狐浏览器 驱动为例

```bash

```



## 二、浏览器基础操作

1. 初始化驱动
2. 打开页面
3. 操作页面
4. 关闭浏览器



### 2.1 初始化浏览器

初始化 Firefox 浏览器

```python
from selenium.webdriver import Firefox
browser_driver = Firefox()
```

初始化 GoogleChrome

```python
from selenium.webdriver import Chrome
browser_driver = Chrome()
```

### 2.2  打开页面

```python
url = "https://www.baidu.com"
browser_driver.get(url)
```



### 2.3 操作页面

1. 模拟用户输入
2. 模拟用户点击
3. 模拟用户滑动
4. 模拟用户滚动页面
5. ....

### 2.4 关闭浏览器

```python
browser_driver.close()
```

## 三、小例子

使用 火狐浏览器 打开 **https://www.baidu.com**

```python
from selenium.webdriver import Firefox

# 1. 初始化浏览器
browser_driver = Firefox()

# 2. 访问 https://www.baidu.com
url = "https://www.baidu.com"
browser_driver.open(url)

# 3. 操作页面 。。。

# 4. 关闭浏览器
browser_driver.close()
```



## 四、元素查找



### 4.1 查找元素

- find_element() 查找单个元素
- find_elements()  查找多个元素





### 4.2 元素查找方式

1. 通过 ID 属性 查找
2. 通过 class 属性 查找
3. 通过 name 属性 查找
4. 通过 超链接文本内容 查找
5. 通过 标签名 查找
6. 通过 XPATH 路径 查找
7. 通过 Css 选择器 查找



#### 4.2.1 通过 ID属性 查找

```html

```

#### 4.2.2 通过 class 属性 查找

```python
browser_driver.find_element(By.ID, "userName")
```

#### 4.2.3 通过 name 属性 查找

```python
browser_driver.find_elements(By.CLASS_NAME, "userName")
```



## 五、操作



### 5.1 页面操作

1. 获取 页面标题
2. 获取 当前页面地址
3. 刷新页面
4. 页面 后退
5. 页面 前进

获取 页面标题

```python
# 获取浏览器标题
title = browser_driver.title
```

获取 当前页面地址

```python
# 获取浏览器当前地址
current_url= browser_driver.current_url
```

刷新页面

```python
# 浏览器后退
browser_driver.back()
```

页面 后退

```python
# 浏览器前进
browser_driver.forward()
```

页面 前进

```python
# 刷新当前页面
browser_driver.refresh()
```



### 5.2 Cookie 操作

1. 添加 Cookie
2. 获取 单个 Cookie
3. 获取全部 Cookies
4. 删除 单个 Cookie
5. 删除所有 Cookie

添加 Cookie

```python
# 添加 Cookie
browser_driver.add_cookie({"name": "foo", "value": "bar"})
```

获取 Cookie

```python
# 获取 单个 Cookie
browser_driver.get_cookie("foo")
```

获取全部 Cookie

```python
# 获取全部 Cookies
browser_driver.get_cookies()
```

删除 Cookie

```python
# 删除 Cookie
browser_driver.delete_cookie("foo")
```

删除所有 Cookie

```python
# 删除所有 Cookie
browser_driver.delete_all_cookies()
```



```python
# 当sameSite属性设置为 Strict, cookie不会与来自第三方网站的请求一起发送
browser_driver.add_cookie({"name": "foo", "value": "value", 'sameSite': 'Strict'})

# 当您将cookie sameSite属性设置为 Lax, cookie将与第三方网站发起的GET请求一起发送.
browser_driver.add_cookie({"name": "foo1", "value": "value", 'sameSite': 'Lax'})
```

### 5.3 模拟操作

1. 模拟输入
2. 模拟点击

模拟输入

```python
user_phone_input = browser_driver.find_element(By.ID, "phone")
user_phone_input.send_keys(user_phone)
```

模拟点击

```python
login_btn = browser_driver.find_element(By.ID, "loginBtn")
login_btn.click()
```

综合例子

```python
from selenium.webdriver import Firefox
from selenium.webdriver.common.by import By

login_url = "https://passport2.chaoxing.com/login"
user_phone = "15627804803"
user_password = "12345678"

# 1. 初始化浏览器
browser_driver = Firefox()

# 2. 打开登陆页面
browser_driver.get(login_url)

# 3. 模拟输入用户手机号
user_phone_input = browser_driver.find_element(By.ID, "phone")
user_phone_input.send_keys(user_phone)

# 4. 模拟输入密码
user_password_input = browser_driver.find_element(By.ID, "pwd")
user_password_input.send_keys(user_password)

# 5. 模拟点击
login_btn = browser_driver.find_element(By.ID, "loginBtn")
login_btn.click()
```

### iframe 或 frameset

切换iframe, 方法1

```python
# 存储网页元素
iframe = driver.find_element(By.CSS_SELECTOR, "#modal > iframe")

# 切换到选择的 iframe
driver.switch_to.frame(iframe)
```



切换iframe, 方法2

```python
# 通过 id 切换框架
driver.switch_to.frame('buttonframe')
```



切换iframe, 方法3

```python
# 基于索引切换到第 2 个 iframe
iframe = driver.find_elements(By.TAG_NAME,'iframe')[1]

# 切换到选择的 iframe
driver.switch_to.frame(iframe)
```

离开 iframe

```python
# 切回到默认内容
driver.switch_to.default_content()
```
