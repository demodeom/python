# 日期时间

Python 语言中，日期时间操作类(datetime)放在 datetime 包中， 需要导入

```python
from datetime import datetime
```

## 获取本地时间

获取本地日期时间(默认)， `datetime.now()` 获取本地的日期时间， 返回值类型 `datetime.datetime` 

```python
datetime_now = datetime.now()
print("类型：", type(datetime_now))
```

获取 `datetime.datetime`  中的年， 注： 4 位的年，例如： 2024

```python
year_now = datetime_now.year
print("4位年：", year_now)
```

获取 `datetime.datetime`  中的月， 注： 月份从 1 开始， 7 代表 7 月

```python
month_now = datetime_now.month
print("月：", month_now)
```



获取 `datetime.datetime`  中的日， 注： 日期从 1 开始， 13 代表 13 日

```python
day_now = datetime_now.day
print("日：", day_now)
```



获取 `datetime.datetime`  中的时， 注： 小时 从 0 开始， 0 - 23

```python
hour_now = datetime_now.hour
print("小时：", hour_now)
```

获取 `datetime.datetime`  中的分钟， 注： 分钟从 0 开始， 0 - 59

```python
minute_now = datetime_now.minute
print("分钟：", minute_now)
```

获取 `datetime.datetime`  中的秒， 注： 分钟从 0 开始，  0 - 59

```python
second_now = datetime_now.second
print("秒：", second_now)
```

获取 `datetime.datetime`  中的微秒

```python
microsecond_now = datetime_now.microsecond
print("微秒：", microsecond_now)
```

获取 `datetime.datetime`  中的星期， 星期从 0 开始， 0-6

```python
week_now = datetime_now.weekday()
print(week_now)
```

## 时期时间格式化

常用的格式化字符

- `%Y` 四位的年份， 比如： 2001, 2101
- `%m` 两位的月份， 比如： 01, 02, 03... 12
- `%d` 两位的日， 比如： 01, 02, 03... 31
- `%H` 两位的小时， 比如： 00, 02, 03... 24
- `%M` 两位的分钟， 比如： 00, 01, 02... 59
- `%S` 两位的秒， 比如： 00, 01, 02... 59 
- `%f` 六位的微秒， 比如： 000000, 000001, 000002... 999999 



```
datetime_now = datetime_now.strftime("%Y%M")
print(datetime_now)
```



## 构造日期时间

1 手动构造日期时间

```python
# 构造日期时间
dt1 = datetime(year=2020, month=12, day=1, hour=12, minute=2, second=32)
print(type(dt1))
```

2 从字符串构造日期时间格式， 比如将 `2020/12/12 12:02:32`

```python
dt_str = "2020/12/12 12:02:32"
dt2 = datetime.strptime(dt_str, "%Y/%m/%d %H:%M:%S")
print(type(dt2))
```

























