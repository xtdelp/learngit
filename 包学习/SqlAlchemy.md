# SqlAlchemy

SQLAlchemy是python当中的一个ORM（对象关系映射）工具，简单来说就是运行使用者在python当中快速使用简单的逻辑操作数据库的一种方法，实际的操作都有封装好的工具来完成。

## 1.引擎

类似于scrapy，在SQLAlchemy当中也有一个引擎来帮助用户完成增删改查的功能：

```
sqlalchemy.create_engine(sql://host:port)
```

## 2.创建表

通过sqlalchemy的base功能我们能够轻松的完成表创建

```
base = sqlalchemy.ext.declarative.declarative_base()
class create(base):
	__tablename__="project_name"
	user = Column(Integer)
	id = Column(int, primary_key = True)
```

## 3.创建对话

在对sql进行操作之前，我们首先要创建对话：

```
session = sqlalchemy.orm.sessionmaker(bind=engine)
session = session()
```

## 4.增删改查

和git一样，我们提交数据之后都要`session.commit()`，确认修改。

增：`session.add(create(dict))`可以看作是把字典读取为了数据库的结构，其中key与column会一一对应。

查：`result = session.query(create).filter_by(condition).first()/all()`

删：`result.delete()`

改：`result.attribute=new_value`