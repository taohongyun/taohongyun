### MySQL常见命令

1. 查看所有库 show databases；

2. 进入库 use 库名；
3. 查看当前库里的所有表 show tables;
4. 查看指定库中的所有表 show table from 库名；
5. 查看自己现在在什么库里边 select database();
6. 创建表 create table 表名（

列名 列类型，

列名 列类型，

......

）

7. 查看表结构 desc 表名；
8. 查看服务器版本 select version ()；



### MySQL语法规范

1. 不区分大小写，但建议关键字大写，表名和列名大写
2. 每条命令用英文的分号结尾
3. 每条命令根据需要，可以进行缩进或者换行
4. 注释

单行：#注释文字

单行注释： --注释文字 （注意--后边必须有空格就）

多行注释：/ * 注释文字 * /



## 基础查询

select...from...

select * from 表名  查看一个表内的全部字段

select 表里某一个 字段名  from 表名  查看表内某一个字段

select 表里某字段名1，表内字段名2  from 表名  查看表内多个字段，要用逗号隔开

注意：

查询列表可以是表中的字段、常量值、表达式、函数

查询的结果是一个虚拟表格

当字段名与关键字重名的时候，必须使用``来声明这是字段不是关键字

当写入多行SQL命令想要执行其中一行时，只要选中在运行就可以。



### 查询字段重命名 AS

select 原名 as 别名 from 表名；

作用

数据库字段一般都是英文名，你查询后的数据为了方便阅读，一般情况下抓取数据时会改成中文

告诫操作，多表抓取字段时可能会有重名

注意

别名中包含特殊字符时，需要用双引号括起来



### 去重复 DISTINCT

select DISTINCT 字段 from 表名;

查找每个字段不重复的信息

 

### 字段链接  CONCAT

SELECT CONCAT(字段名1,字段名2) AS 新字段名 FROM 表名;



### 字段为空改成默认值 IFNULL

SELECT IFNULL(为空的字段，空内容改成什么默认值)  AS 新的字段名  FROM 表名



### 条件查询 where

select 查询字段 from 表名 where 筛选条件：

执行顺序： 先找表再筛选再查询

#### 运算符

| 条件运算 | 说明     | 逻辑运算 | 说明 | 模糊查询         | 说明         |
| -------- | -------- | -------- | ---- | ---------------- | ------------ |
| =        | 等于     | &&       | 与   | like             | 通配搜索     |
| <>       | 不等于   | \|\|     | 或   | between...and... | 时间范围     |
| <=>      | 安全等于 |          |      |                  |              |
| !=       | 不等于   | \|       | 非   | in               | 指定条件范围 |
| <        | 小于     | and      | 与   | in null          | 为NULL值     |
| <=       | 小于等于 | or       | 或   |                  |              |
| >        | 大于     | not      | 非   |                  |              |
| >+       | 大于等于 |          |      |                  |              |





#### 通配搜索 like

like 通配搜索，一般与通配符搭配使用，%代表多个字符，包含0个字符，任意单个字符，指的是就一个

例如商品编码里有A的

select * from 表名 where 商品编码 '%a%'       #不区分大小写

例如商品编码里第一个字符为A的

select * from 表名 where 商品编码 'a%'  

例如商品编码里第三个字符为b 第五个字符为c的

select * from 表名 where 商品编码  '__b _c%'       # 其中一个下划线代表一个字符 



特殊情况：使用\转义字符 或者 ESCAPE关键字

例如商品编码第二字符为_的

select * from 表名 where 商品编码 like '_ \ _%'



#### between... and...  两个值或者日期之间的

例如销售数量在150到250之间的

select * from 表名 where 销售数量 between 150 and 250 

注意

between...and ...这两个值是包含本身的，就相当于大于等于和小于等于

两个值的位置不能互换，也就相当于大于等于左边，小于等于右边

可以配合not将它反过来

select * from 表名 where 销售数量 not between 150 and 250 



#### in 指定条件范围

例如 店号1、3、7这三家店的销售数据

select * from 表名 where in (1,3,7);

注意

使用in 比使用or提高了语句的简洁性

in列表的值必须是一致类型（例如里边是店号就都是店号)

in 列表的值不支持通配符



#### is nul 为空值

select * from 表名 where 销售数据 is null

寻找为空的字符  



## 排序

### 排序查询

升序：select 字段名 from 表名 order by  字段名 ASC  （ASC可以省略默认顺序）

降序：select 字段名 from 表名 order by  字段名 DESC

注意

在同时使用条件查询where和排序查询order by字句时，应该让 排序查询放到条件查询后边

order by后边可以是字段、表达式还有别名

### 排序优先级

select *from 表名 order by 字符1 DESC 字符2 ASC

优先排序字段放在前边的，不同的字段可以指定不同的排序规则



### 按长度排序  LENGTH()

select * from 表名 order by length(商品名称) ASC   升序

select * from 表名 order by length(商品名称) DESC   降序



### 中文列排序  INSTR()

select 字段名 from  表名 order by  instr("顺序"，字段名)



### 按列的位置进行排序

select 字段1，字段2，字段3 from order by 2,3



## 使用函数处理数据

调用 

select 函数名（实参列表） from 表名 

如果函数名里有字段就需要加表名，没有就不用加

CONCAT函数：字段链接

LENGTH函数：按长度排序

IFNULL;函数：判断是否为空

INSTR函数：中文列排序



函数主要有两种，一种是单行函数，另一种是分祖聚合函数

单行函数是输入一个值，返回一个值

聚合函数是输入一个值，返回一个值，做统计时使用



## 常用的文本函数

1. 返回字符串左边的字符

left  字符串或者字符的长度

select left(字段名，几个字符) from 表名

2. 返回字符串的长度

length(字符串或者字节)

select length(字段名) from 商品表

3. 字段连接或者字符串连接

select concat(字段名1，字段名2 ) as 新字段名 from 表名

4. 大写和小写转换

lower 转小写

upper 转大写

select lower(字段名) from 表名

select upper(字段名) from 表名

5. 去掉表格左右空格

trim  去掉左右两边的空格

ltrim  去掉左边的空格

rtrim   去掉右边的空格

6. 字符截取 substr

substr(字符或者字段，起始位置，到结束几个位置)

#结束的位置不写 ，默认截取到最后

7. 返回子串第一次出现的索引 ，如果找不到就返回0

instr(字符串，子串)

8. 左填充和右填充

lpad(字符串，字符位数，'占位')   #占位为填充内容，把字符串的字符数通过填充内容填充到字符位数

rpad(字符串，字符位数，'占位')

注意

如果字符位数比原本字符串字符数少，则就会从填充变成截取

9. 替换

replace(字段名，原内容，替换内容)

## 常用的数学函数

1. 四舍五入 round

round(字段名，四舍五入几位)    # 不标明四舍五入几位，默认到整数

2. 向上取整  ceil、向下取整 floor

ceil(字段名) 向上取整数，大

floor(字段名)  向下取整数，小

3. 截断 truncate

truncate(字段名，截取小数点后边几位)

4. 取余 mod

mod(除数，被除数)



## 常用的日期函数

- 返回当前系统日期 now()

now()

- 返回当前系统日期，不包含时间

curdate()

- 返回当前时间，不包含日期

curtime()

- 获取指定的日期部分

select year(字段名) from 表名

同理 month、day、hour、minute、second

- 将日期格式的字符转换为指定的日期格式

str_to_date(字段名，'%m-%d-%y')

- 将日期格式转化为字符

date_format(字段名，‘%y年%m月%d日’)



## 流程控制函数

if 函数

if(字段名，返回值，否则返回值)



case函数1

select 字段1，字段2，字段3

base 根据此判断的字段

when 根据此判断的字段内的内容 than 要显示的值或者语句

...

else 其他不操作的值

end

from 表单



例：

大类名时果菜的价格上涨10%，肉涨价20%，副食品涨价5%

select '商品名','进价','售价'，

case大类编码

when 01 than 售价*1.1

when 02 than 售价*1.2

when 03 than 售价*1.05

else 售价

end  as 新售价

from 商品表



case函数1

select 字段1，字段2，字段3

base 

when 根据此判断的字段内的内容 than 要显示的值或者语句

...

else  其他不操作的值

end

from 表单



例：

销量大于250的，优；销量大于150的，良；销量大于100的，中；否则差

select '店号','商品编码','销售数量' 

case 

when '销售数量'>250 than 优

when '销售数量'>150 than 良

when '销售数量'>100 than 中

else 差

end

as 评价

from 表单





## 聚合函数

1. 简单的聚合函数

sum 求和 avg 平均  max 最大  min 最小 

select num(字段名) from 表名

select avg(字段名) from 表名

select max(字段名) from 表名

select min(字段名) from 表名

select num(字段名) as 求和，avg(字段名) as 求平均，max(字段名) as 最大值，max(字段名) as 最小值 from 表名

count (distinct，字段名)，查看字段非重复的个数

count(*)  用来统计表中的总行数

2.  分组聚合 group by

语法

select 字段名，聚合函数(字段名)  from 表名  where 条件  group by 分祖表达式  order by 字段名

注意：select 后边的字段必须是group by 后出现的字段，条件和排序可以省略

3. group by 基础应用

查询每家店铺的最小销售数量

select 店号,min(销售数量) as 最小销售数量 from 表名 group by 店号

查询每个大类对应的商品数

select 大类名,count(*) as 每个大类对应的商品数 from 表名 group by 大类名

查询店号为137的每家店铺，1号到3号的最小销量小于120

select 店号,min(销售数量)  as 最小销量 from 表名 where 日期 between '2020-01-01' in '2020-01-03' group by 店号 in (1,3,7) having  最小销量 < 120

注，查询自定义字段的时候用having

4. 按表达式或者函数分组

分祖也可以按表达式或者函数分组

例：

select 字段名 聚合函数(字段名) as 别名  from 表名  group by 聚合函数的字段名或者别名

5. 按多个字段分组

例：

select 字段1，字段2，字段3  from 表单  group by  字段1，字段2，字段3

6. 分组后再排序

select 字段  from 表单  group by 字段  order by 字段 asc/desc

7. limit 排名函数

select 字段  from 表单  group by 字段  order by 字段 asc/desc  limit 3

取前三名

使用limit 排名前 一定要排序

8. limit 分页

select * from 表名 limit 行数

## 多表合并

### 多表数据合并 union

  将两张表合并不去重复，select * from 表一 **union all**  select * from 表二

  将两张表合并去重复，select * from 表一 **union**   select * from 表二

注意：

union 和 union all  都要求select语句具有相同的列数，而且字段顺序也相同



## 连接查询

### 多表配合使用

根据多个表之间的关系查询其中数据，实现多表操作

select a/b.重复的字段，不重复的字段1，不重复的字段2...

form 表1 a  ，表2 b

where a.重复字段 = b.重复字段

注

凡是字段名再from表中是唯一的，字段名前可以省略表名

### 内部连接 from+where

同上

语法：select 字段名 from 表1，表2  where 表1.字段名 = 表2.字段名

### 内部连接 join on 

select  字段1 字段2 

from 表一

join 表二

on  表一.连接的字段名1 = 表二.连接的字段名2







# 增删改

## 增数据

insert into 表名(字段1，字段2，字段3)  values(增加的内容,增加的内容2...)

insert into 表名  values(增加的内容,增加的内容2...)  # 增加的内容必须和表名中的内容对应 没有的用null占位

insert into 表名 set 字段1 = 添加的值，字段2 = 添加的值...

插入多行

insert into 表名(字段1，字段2，字段3)  values(增加的内容,增加的内容2...)，(增加的内容,增加的内容2...)，(增加的内容,增加的内容2...)...

insert into 表名  values(增加的内容,增加的内容2...)，values(增加的内容,增加的内容2...)，values(增加的内容,增加的内容2...)...

添加子查询

insert into 表名1

select 字段1，字段2，字段3... from 表名2



## 改数据

### 修改单表数据

update 表名

set 字段名1= 新值1，字段名2 = 新值2...

where  条件查询

### 修改多表数据

update 表名1 别名1

inter  join  表名2  别名2

on 连接条件

set 字段名1 = 新值名1

where 筛选条件

### 删除数据

条件删除

单表删除：delete from 表名 筛选条件

多表删除：delete  删除内容的表名1的别名1  from 删除内容的表名1和别名1  join 连接删除内容的表名和别名  on  连接条件 where  条件查询

整表删除： truncate table 表名





回滚和自增

自增 identity (m,n) m、n 默认为1，1

# 补充

## 数据库中的元素

数据库   datacase

表   table

字段  field

记录  record

## 常用的数据类型

整数  int

小整数  tinyint

小数 declmal（总共几位数，小数点后边几位）

字符串 varchar

TINYINT UNSIGNED  无符号小整数 

## 创建表格

create table 表名（字段名  数据类型...）  #多个字段名字段类型需要逗号隔开

## 增（插入）

- insert into  表名  values (...)
- insert into  表名 （字段名1，字段名2）  values (...)

## 查

select * from 表名

## 改

update  表名 set 字段1 = 值1... where

## 删

delete from 表名 where  条件查询

truncate table  表名

## 删除表

drop table 表名

## 创建表约束

**主键 primary key**  值不能重复  **auto_increment** 代表值自动增长

**非空 not null**  不允许填空值

**唯一 unique** 不允许 重复

**默认值 default** 当不填写此值时会使用默认值，如果填写值以填写值为准

语法

create table 表名（字段名 数据类型 约束）

## 自增长auto_increment 

delete 后自增长 不从头开始

truncate 后自增长 从头开始

## 去重复显示

select distinct 字段 from 表名

## 模糊查询 like 

select 字段名 from 表名 like  '  '

引号内一个_代表一个字符  %代表多个字符

## 范围查找

in 在一个非连续的范围

between ...and ... 在一个连续的范围 

## 总记录数 count 

select count(*) from 表名

## 分组后筛选 having

select * from 表单 group up 字段  having 筛选条件

having 为先分组在筛选条件

## 数据分页 limit 

select * from limit 开始行，获取行数

分页公式 （n-1）*m

## 内连接

select * from 表1  inner  join 表2  on 表1.字段 = 表2.字段

## 隐式内连接

select * from 表1，表2 

where  表1.字段 = 表2.字段

## 多表查询同名字段名 要在前边加上表名

## 自关联

同一张表做连接查询

同一张表的不同字段关联

## 子查询

多个select查询语句嵌套

子查询可以独立运行，主查询不能够独立运行



## sql内置函数

### concat  拼接字符串函数

select concat （参数1，参数2 ...）

参数可以是数字可以是字符串

### length 字符个数

字母 1：3  汉字1：3

select length(参数)

### 截取字符串（left、right、substeing）

左截取

select left(字段，左截取几位)

右截取

select right(字段，左截取几位)

自定义从哪里开始截取

SELECT SUBSTRING(字段，第几位开始截取,截取几位)

## 去除空格

去除左边空格 select ltrim(字段)

去除右边空格 select rtrim(字段)

去除两边空格 select trim(字段)

## 四舍五入

round

select round(字段，保留到几位)

## 随机排序

 select rand()

## 日期函数

SELECT CURRENT_DATE 当前日期

SELECT CURRENT_TIME  当前时间

SELECT now()  当前时间加日期

## 存储调用

CREATE PROCEDURE stu()
BEGIN


select * from 表名；


END

call stu()

## 视图

视图就是对查询的封装

create view 视图名称 as select 语句

类似一张不能够改动的表

## 事务

事务是多条更改数据操作的sql语句的集合、

一个集合的数据一一致性，要么都失败要么都成功

begin 开始事务

rollback 回滚事务，放弃对表的修改

commit 提交事务，对表修改生效

没有begin代表没有事务，没有事务的操作都是实时生效的。

## 回滚事务的操作

### commit 

提交事务，一旦提交，两个操作同时生效

begin

sql语句1

sql语句2

commit

### rollback 

回滚操作，如果开始一个事务，没有执行rollback和commit ，中间系统出问题，默认会执行rollback

begin

sql语句1

sql语句2

rollback

## 索引

create index 索引名称 on 表名(字段名(长度))

如果指定的字段为字符串，需要指定长度，建议长度与定义字段时的长度一致

字段类型如果不是字符串，可以不填写长度部分

## 索引的使用

select * from 表名 where 筛选条件 

where 条件后边的字段，数据库会自动查找是否偶索引。 

## 查看索引

show index from 表名

系统会给主键自动建一个索引

## 删除索引

drop  index 索引名  on 表名

## 索引优缺点

优点

索引大大提高了select，语句的查询速度

缺点

提高了查询速度，降低了更新的速度

但是实际工作中查询占了大部分，所以建立索引是有必要的

大量更新数据时，可以先删除索引，再插入数据，最后再添加索引，这样提高效率

## 查看表的属性

desc 表名

## mysql命令行

Windows cmd 命令窗口连接mysql 

cd 到 mysql 路径下

然后输入 MySQL -h [主机名(不是本机的话填写)] -u[用户名] -p

-h 指定要连接的MySQL的ip地址或者住机名称，如省略则默认本地

-u 指定连接的用户名'

-p 执行命令后会提示输入密码'

## 操作

show databases    (查看所有数据库)

use 数据库名      (打开数据库)

show tables       (查看所有数据库)

set names gbk      (windows 默认 gbk 格式 需要让sql 从utf-8转化成gbk)    

sql 语句

## 创建数据库

create databaase 数据库名 default charset (默认字符集)；

## 删除数据库

drop datebase 数据库名 

drop database if mytest 数据库名





**2. 现有学生表如下:** 自动编号 学号 姓名 课程编号 课程名称 分数 1 2005001 张三 0001 数学 69 2 2005002 李四 0001 数学 89 3 2005001 张三 0001 数学 69 **删除除了自动编号不同, 其他都相同的学生冗余信息** 

delete from sheet5 where 自动编号 not in 

(SELECT tmp.自动编号 from(select min(自动编号) AS 自动编号 from sheet5 group by 姓名)tmp)

SELECT * from sheet5     







11