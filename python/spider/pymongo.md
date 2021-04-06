# pymongo

mongoDB数据库

```sh
pip install pymongo
```

```python
import pymongo

client = pymongo.MongoClient('localhost')
# 创建一个数据库
db = client['newtestdb']
# 声明一个表，然后插入一条数据
print(db['table'].insert_one({'name': 'cmps'}))
# 查询数据
a = db['table'].find_one({'name': 'cmps'})
print(a)

```



