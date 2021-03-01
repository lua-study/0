#A simple test project


表5-1　FLask-SQLAlchemy数据库URL
数据库引擎URL
MySQL mysql://username:password@hostname/database
Postgres postgresql://username:password@hostname/database
SQLite（Unix） sqlite:////absolute/path/to/database
SQLite（Windows） sqlite:///c:/absolute/path/to/database\

表5-2　最常用的SQLAlchemy列类型
类型名Python类型说　　明
Integer int 普通整数，一般是32 位
SmallInteger int 取值范围小的整数，一般是16 位
BigInteger int 或long 不限制精度的整数
Float float 浮点数
Numeric decimal.Decimal 定点数
String str 变长字符串
Text str 变长字符串，对较长或不限长度的字符串做了优化
Unicode unicode 变长Unicode 字符串
UnicodeText unicode 变长Unicode 字符串，对较长或不限长度的字符串做了优化
Boolean bool 布尔值
Date datetime.date 日期
Time datetime.time 时间
DateTime datetime.datetime 日期和时间
Interval datetime.timedelta 时间间隔
Enum str 一组字符串
PickleType 任何Python 对象自动使用Pickle 序列化
LargeBinary str 二进制文件


表5-3　最常使用的SQLAlchemy列选项
选项名说　　明
primary_key 如果设为True，这列就是表的主键
unique 如果设为True，这列不允许出现重复的值
index 如果设为True，为这列创建索引，提升查询效率
nullable 如果设为True，这列允许使用空值；如果设为False，这列不允许使用空值
default 为这列定义默认值
Flask-SQLAlchemy 要求每个模型都要定义主键，这一列经常命名为id。


表5-4　常用的SQLAlchemy关系选项
选项名说　　明
backref 在关系的另一个模型中添加反向引用
primaryjoin 明确指定两个模型之间使用的联结条件。只在模棱两可的关系中需要指定
lazy 指定如何加载相关记录。可选值有select（首次访问时按需加载）、immediate（源对象加
载后就加载）、joined（加载记录，但使用联结）、subquery（立即加载，但使用子查询），
noload（永不加载）和dynamic（不加载记录，但提供加载记录的查询）
50 ｜ 第5 章
选项名说　　明
uselist 如果设为Fales，不使用列表，而使用标量值
order_by 指定关系中记录的排序方式
secondary 指定多对多关系中关系表的名字
secondaryjoin SQLAlchemy 无法自行决定时，指定多对多关系中的二级联结条件


表5-5　常用的SQLAlchemy查询过滤器
过滤器说　　明
filter() 把过滤器添加到原查询上，返回一个新查询
filter_by() 把等值过滤器添加到原查询上，返回一个新查询
limit() 使用指定的值限制原查询返回的结果数量，返回一个新查询
offset() 偏移原查询返回的结果，返回一个新查询
order_by() 根据指定条件对原查询结果进行排序，返回一个新查询
group_by() 根据指定条件对原查询结果进行分组，返回一个新查询


表5-6　最常使用的SQLAlchemy查询执行函数
方　法说　　明
all() 以列表形式返回查询的所有结果
first() 返回查询的第一个结果，如果没有结果，则返回None
first_or_404() 返回查询的第一个结果，如果没有结果，则终止请求，返回404 错误响应
get() 返回指定主键对应的行，如果没有对应的行，则返回None
get_or_404() 返回指定主键对应的行，如果没找到指定的主键，则终止请求，返回404 错误响应
count() 返回查询结果的数量
paginate() 返回一个Paginate 对象，它包含指定范围内的结果


创建迁移仓库
(venv) $ python hello.py db init
migrate 子命令用来自动创建迁移脚本：
(venv) $ python hello.py db migrate -m "initial migration"
迁移应用到数据库中
(venv) $ python hello.py db upgrade


表6-1　Flask-Mail SMTP服务器的配置
配　　置默认值说　　明
MAIL_SERVER localhost 电子邮件服务器的主机名或IP 地址
MAIL_PORT 25 电子邮件服务器的端口
MAIL_USE_TLS False 启用传输层安全（Transport Layer Security，TLS）协议
MAIL_USE_SSL False 启用安全套接层（Secure Sockets Layer，SSL）协议
MAIL_USERNAME None 邮件账户的用户名
MAIL_PASSWORD None 邮件账户的密码


示例7-1　多文件Flask 程序的基本结构
|-flasky
|-app/
|-templates/
|-static/
|-main/
|-__init__.py
|-errors.py
|-forms.py
|-views.py
|-__init__.py
|-email.py
|-models.py
|-migrations/
|-tests/
|-__init__.py
66 ｜ 第7 章
|-test*.py
|-venv/
|-requirements.txt
|-config.py
|-manage.py

表11-1　Flask-SQLAlchemy分页对象的属性
属　　性说　　明
items 当前页面中的记录
query 分页的源查询
page 当前页数
prev_num 上一页的页数
next_num 下一页的页数
has_next 如果有下一页，返回True
has_prev 如果有上一页，返回True
pages 查询得到的总页数
per_page 每页显示的记录数量
total 查询返回的记录总数

| 表格说明  |
|---|
|   |

表11-2　在Flask-SQLAlchemy对象上可调用的方法
方法    说明
iter_pages(left_edge = 2, left_current=2,
right_current=5, right_edge=2) 
一个迭代器，返回一个在分页导航中显示的页数列表。这个列表的最左边显示left_
edge 页，当前页的左边显示left_current 页，当前页的右边显示right_current 页，
最右边显示right_edge 页。例如，在一个100 页的列表中，当前页为第50 页，使用
默认配置，这个方法会返回以下页数：1、2、None、48、49、50、51、52、53、54、
55、None、99、100。None 表示页数之间的间隔

prev() 上一页的分页对象
next() 下一页的分页对象


"""
        添加关注
   SELECT
        follows.follower_id AS follows_follower_id,
        follows.followed_id AS follows_followed_id,
        follows.timestamp AS follows_timestamp,
        users_1.id AS users_1_id,
        users_1.email AS users_1_email,
        users_1.username AS users_1_username,
        users_1.password_hash AS users_1_password_hash,
        users_1.confirmed AS users_1_confirmed,
        users_1.role_id AS users_1_role_id,
        users_1.name AS users_1_name,
        users_1.location AS users_1_location,
        users_1.about_me AS users_1_about_me,
        users_1.member_since AS users_1_member_since,
        users_1.last_seen AS users_1_last_seen,
        users_1.avatar_hash AS users_1_avatar_hash,
        users_2.id AS users_2_id,
        users_2.email AS users_2_email,
        users_2.username AS users_2_username,
        users_2.password_hash AS users_2_password_hash,
        users_2.confirmed AS users_2_confirmed,
        users_2.role_id AS users_2_role_id,
        users_2.name AS users_2_name,
        users_2.location AS users_2_location,
        users_2.about_me AS users_2_about_me,
        users_2.member_since AS users_2_member_since,
        users_2.last_seen AS users_2_last_seen,
        users_2.avatar_hash AS users_2_avatar_hash
    FROM
        follows
    LEFT OUTER JOIN users AS users_1 ON users_1.id = follows.follower_id
    LEFT OUTER JOIN users AS users_2 ON users_2.id = follows.followed_id
"""

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)