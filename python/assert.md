# 断言

assert(断言)用于判断一个表达式，在表达式条件为false的时候出发异常。

断言可以在条件不满足程序运行的情况下直接放回错误，而不必等待程序运行后出现崩溃的情况。语法格式如下

```python
assert expression [, argments]

# 例
assert False, "我现在只想返回错误"
```

等价于：

```python
# expression 表达式
if not expression:
    raise AssertionError(arguments)
```

实例：

```python
assert True		# 条件为true是正常执行
assert False	# 条件为false时触发异常
```

