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