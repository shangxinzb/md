# pymysql

```sh
pip install pymysql
```

```python
import pymysql

# 链接数据库
conn = pymysql.connect(host='localhost', user='root', password='root', port=3306, db='edu')
cursor = conn.cursor()
cursor.execute('select * from dsc_users')
# 获取一条数据
print(cursor.fetchone())
```

