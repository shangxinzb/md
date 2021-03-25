# JSON

JSON(JavaScript Object Notation)是一种轻量级的数据交换合适

- json.dumps()：对数据进行编码
- json.loads()：  对数据进行解码

Python编码为JSON类型转换对应：

| Python     | JSON   |
| ---------- | ------ |
| list,tuple | array  |
| dict       | object |
| str        | string |
| int, float | number |
| True       | true   |
| False      | false  |
| None       | null   |

## 应用：

```python
import json

# Python 字典类型转换为 JSON 对象
data = {
    'no' : 1,
    'name' : 'Runoob',
    'url' : 'http://www.runoob.com'
}

# 编码
json_str = json.dumps(data)
# 解码
json.loads(json_str)
```

## 文件编码、解码

- json.dump()
- json.load()

```python
# 写入json数据
with open('data.json', 'w') as f:
    json.dump(data, f)
    
# 读取数据
with open('data.json', 'r') as f:
    json.load(f)
```

