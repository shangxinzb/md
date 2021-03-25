# repr()函数

## 描述

repr()函数将对象转化为供解释器读取的形式

### 语法

```python
repr(objrect)
```

### 参数

- object 	对象

### 返回值

返回一个对象的string格式。

## 实例

```python
_str = 'hello'
repr(_str)
# "'hello'"

_dict = {'today': '2021-3-25 11:52:28', 'temperature': '13℃'}
repr(_dict)
# {'today': '2021-3-25 11:52:28', 'temperature': '13℃'}

"""
以上方法在pycharm中执行，并没有以返回双引号
在cmd中执行repr(obj)
返回的内容是带""双引号的
"""
```

