# MongoDB

# 第一天

```
第一天

MongoDB （芒果数据库）


数据存储阶段

文件管理阶段（.txt  .doc  .xls）

优点 ： 使用简单方便
        数据能够长期保存
	可以存储大量数据

缺点 ： 数据一致性差
        数据的查找修改不方便
	数据冗余

数据库管理阶段

优点 ： 数据组织结构化，降低冗余
        提高增删改查效率
	方便扩展
	方便程序调用，做自动化的处理
缺点 ： 数据库使用特定的语句操作，相对复杂


几个概念

数据 ：能够输入到计算机中并被识别处理的信息的集合

数据结构：研究一个数据集合中，数据之间关系的学科

数据库： 按照数据结构，存储数据的仓库。在数据库管          理系统管理下在一定介质上的数据集合。

数据库管理系统 ：管理数据库的软件，用于建立维护数                   据库

数据库系统 ：由数据库和数据库管理系统等开发工具组              成的集合


关系型数据库

采用关系模型来组织数据结构的数据库 （二维表）

Oracle  DB2   SQLServer  MySql   Sqlite

优点：容易理解，逻辑类似常见的表格
      使用方便，都使用sql语句，sql语句很成熟
      数据一致性高，冗余低，完整性好
      技术成熟，可以使用外部关联等复杂操作

缺点：每次都需要sql语句的解析，消耗大
      不能很好的满足并发需求，特别是海量数据爆发，读写能力不足
      关系型数据库每一步操作都要加锁，以保证操作的原子性，增加了数据库负担
      数据的一致性有时会导致空间浪费


非关系型数据库 （NoSql--》not only sql）

优点 ： 高并发，读写能力强
        普遍比关系型数据库容易扩展
	弱化了数据结构，降低数据一致性

缺点 ： 通用性差，没有sql语句一样的一致化操作
        操作过于冗长，容易混乱
	没有join等复杂操作，很多也不支持事务等操作

NoSql 使用情况
1. 对数据一致性要求低
2. 数据库需要处理海量并发
3. 需要处理速度较快，比如做一个临时的中间过度存储    器
4. 数据库构建比较方便的构建非关系模型

Nosql分类：

键值型数据库：Redis
列存储数据库
文档型数据库：MongoDB
图形数据库

MongoDB 数据库  （非关系型数据库--》文档型数据库）

1. 由c++编写的数据库管理系统
2. 支持丰富的增删改查操作
3. 支持丰富的数据类型
4. 支持众多的编程语言接口（python  PHP  C++  c#）
5. 使用方便，便于部署。相对成熟。

MongoDB安装

自动安装
sudo apt-get install mongodb

默认安装位置 :  /var/lib/mongodb 
配置文件：/etc/mongodb.conf
命令集： /usr/bin   /usr/local/bin
(软件安装后提供功能性的命令)

手动安装
1.下载Mongodb(开源)
www.mongodb.com-->get mongodb --> community server

选择想要下载的版本

2. 选择合适的位置解压（/usr/local  /opt）
tar 解压后得到 MongoDB文件夹

3. 将命令集 （解压后文件夹中bin目录）添加到环境变    量
PATH=$PATH:/opt/mongo/bin
export PATH
将以上两句添加如 /etc/rc.local

4. 重启系统

Mongodb 命令

设置数据库存储位置
mongod  --dbpath   目录

e.g.    mongod  --dbpath  dbs

设置数据库端口
mongod  --port  8080 
*默认端口  27017


mongo 
进入mongo shell界面：mongodb的交互界面，操作数据库

退出界面 ： quit() 或  ctrl + c 

mongodb数据库组织形式

键值对 ---》 文档 ---》 集合 ---》数据库

------------------------
ID   |   NAME   |   AGE
------------------------
1    |   Lily   |   17
------------------------
2    |   Lucy   |   18
------------------------

{
  "_id":1,
  "NAME":"Lily",
  "AGE":17
},
{
  "_id":2,
  "NAME":"Lucy",
  "AGE":18
}

mysql 和 mongodb 概念比价

mysql        mongodb        含义

database     database       数据库

table        collection     表/集合

column       field          字段/域

row          document       记录/文档

index        index          索引


创建数据库

use databaseName 

e.g.  use stu  #创建一个stu数据库

* use 实际上是表示选择某个数据库使用。当这个数据库不存在时会自动创建。
* 使用use后数据不会马上被创建，而是在实际写入数据时才会创建


查看当前系统中数据库
show  dbs

系统数据库：
admin：存放用户及其权限
local： 存储本地数据
config：存储分片信息

数据库的命名规则
1. 使用utf-8字符
2. 不能有空格，点，/ \  '\0'字符
3. 长度不超过64字节
4. 不和系统数据库重名

db：mongodb系统全局变量，代表当前正在使用的数据库

* 如果没有use任何数据库情况下 db表示test。此时插入数据则创建test数据库


数据库备份和恢复

备份：mongodump -h dbhost -d    dbname   -o dbdir
                   主机      要备份数据库   目录

e.g.   
将stu数据库备份到student目录中
mongodump -h  127.0.0.1 -d stu -o student

恢复：mongorestore -h  dbhost:port -d dbname  path
                       主机           数据库  目录

e.g.
将stu数据库恢复到student数据库中
mongorestore -h 127.0.0.1:27017 -d student  student/stu

数据库的监测
mongostat

insert query update delete: 每秒执行增删改查次数
command ： 每秒运行命令次数
flushes ： 每秒清理缓存次数
vsize ：使用的虚拟内存
res：物理内存

mongotop 
监测每个数据库的读写时长

 ns         total     read       write
数据集合    总时长    读时长    写时长


删除数据库
db.dropDatabase()

删除db代表的数据库

创建集合 

db.createCollection(collection_name)

e.g.   
创建一个class1的集合
db.createCollection("class1")

创建集合2
当向一个集合中插入数据的时候，如果这个集合不存在则会自动创建

db.collecionName.insert(...)

e.g.  如果class2不存在则自动创建    db.class2.insert({"name":'Tom','age':17,'sex':'m'})

查看数据库中集合
show collections
show tables

集合命名规则
1. utf-8 字符
2. 不能有'\0'
3. 不要以system.开头，因为这是系统保留集合前缀
4. 不要和关键字重复


删除集合
db.collectionName.drop() 

e.g.   db.class.drop()   #删除class这个集合

集合的重命名

db.collectionName.renameCollection("new_name")

e.g.  将class2重命名为class0
db.class2.renameCollection("class0")


文档

mongodb中数据的组织形式 --》 文档

mongodb文档 ：以键值对形式组成的类似字典的数据描               述形式

键： 即文档的域

键的命名规则：
1. utf-8字符串
2. 不含有'\0' 通常不用 .  $
3. 一个文档中的键不能重复

* 文档中的键值对是有序的
* mongodb中数据严格区分大小写

值： 即文档存储的数据    支持bson数据

JavaScript ---》 json ---》bson

类型             值

整型            整数
布尔类型        true  false
浮点型          小数
Array           数组
Timestamp       时间戳
Date            时间日期
Object          内部文档
Null            空值 null
String          字符串
Symbol          特殊字符串
Binary data     二进制字串
code            代码
regex           正则表达式
ObjectId        ObjectId字串

ObjectId 

"_id" : ObjectId("5b503b7f38d0e992e1270560")

_id : 当在mongo代表中插入文档时，如果不指定_id则会自动添加这个域，作为主键。

ObjectId() 值是系统自动生成的不重复字串标识

24位   8位  文档创建时间
       6位  机器ID
       4位  进程ID
       6位  计数器

集合中的文档：
1. 集合中的文档不一定有相同的域
2. 集合中的文档多少不一定相同
3. 集合中的文档，值的类型不一定相同

集合设计
1. 集合中的文档尽可能描述同一类数据
2. 同一类数据不要过多分散在多个集合中存放
3. 集合中文档的结构层次不宜过多


插入文档

db.collectionName.insert()

插入单个文档

e.g.
db.class0.insert({name:"HanMei",age:17,sex:'w'})

* 插入数据时域名可以不加引号
* 查看插入结果  db.class.find()
* _id 为系统自动添加主键，如果自己写_id则为自己设   定的值，但是仍然不可重复
* 一个集合中的文档是有序的

插入多个文档
db.collectionName.insert([{},{},{}])

e.g. 
db.class2.insert([{name:'阿宝',age:32},{name:'阿哲',age:31},{name:'阿蓉',age:26}])

save() 插入文档

db.collectionName.save()

e.g.   db.class1.save({name:'Lily',age:13,sex:'w'})

* 如果不加_id域时用法同insert()
* 如果加_id，此_id值存在则save表示修改该文档。

作业 ：
1. 关系型数据库和非关系型数据库区别
2. 复习mysql 增删改查
3. 练习mongo 数据库集合创建删除，文档插入命令
```

#  第二天





```
复习

1.关系型数据库和非关系型数据库比较
2.MongoDB 文档型数据库
   
    创建数据库： use database
    删除数据库： db.dropDatabase()

    创建集合： db.createCollection()
               db.collection.insert()
    删除集合： db.collection.drop()
    重命名  ： db.collection.renameCollection()
    
    查看数据库： show  dbs
    查看集合： show collections    
               show  tables

3. 文档   bson

www.mongodb.com --> docs  查找文档帮助

插入文档 ： insert()   save() 
***********************************************

获取集合对象
 db.getCollection('class1') ===》 db.class1
    
e.g. 
db.getCollection('class1').insert({name:'Marry',age:16,sex:'w'})


查找操作

mysql ：  select ... from  table  where ....

mongo :  db.collection.find(query,field)

查找所有内容
db.collection.find()  ----> select * from table

find(query,field)
功能 ： 查找数据
参数 ： query： 筛选条件，相当于where子句
        field： 选定要展示的域
返回值 ： 返回查找到的文档

query : 以键值对形式给出筛选条件
        {name:'Lily'}
e.g.  db.class1.find({name:'Lily'})

field : 以键值对的形式给出要展示（不展示）的域，         域名为键，值为1表示展示，0表示不展示

* 如果某个域设置为0则表示不展示该域其他的均展示
* 如果某个域设置为1则表示展示该域其他的均不展示
* _id必须设置为0才不会显示
* 除了_id其余设置的值必须相同

e.g.  db.class1.find({name:'Lily'},{_id:0,name:1,age:1})

findOne(query,field)
功能 ： 只查找第一条复合条件的文档
参数返回值同find()

e.g.  db.class1.findOne({sex:'w'},{_id:0})


query 更多筛选功能

操作符：使用$符号标注的一个有特殊意义的字符串。用以表达一定的含义。比如 $lt 表示小于

比较操作符
$eq  等于

e.g.    db.class1.find({age:{$eq:13}},{_id:0})
        db.class1.find({age:13},{_id:0})

$lt  小于 <

e.g.  年龄小于15
db.class1.find({age:{$lt:15}},{_id:0})

* 字符串也可以比较大小

$lte  小于等于  <=

e.g.  小于等于15
db.class1.find({age:{$lte:15}},{_id:0})

$gt  大于  >

e.g. 大于15
db.class1.find({age:{$gt:15}},{_id:0})

$gte  大于等于  >=

e.g  大于等于15   
db.class1.find({age:{$gte:15}},{_id:0})

$ne   不等于  !=

e.g.  不等于13
 db.class1.find({age:{$ne:13}},{_id:0})

* 如果某个文档不存在查找的域，则不等于可以匹配到该文档

$in  包含

e.g.  年龄包含 在11，12，13，14的
db.class1.find({age:{$in:[11,12,13,14]}},{_id:0})

$nin  不包含

e.g. 年龄不是13，14
db.class1.find({age:{$nin:[13,14]}},{_id:0})

逻辑操作符

query 逗号分隔的条件即为与关系
e.g. 年龄大于13 小于16
> db.class1.find({age:{$gt:13,$lt:16}},{_id:0})
e.g. 年龄大于13且性别为女
> db.class1.find({age:{$gt:13},sex:'w'},{_id:0})

$and 逻辑与

e.g.   年龄大于13 并且姓名大于Lily db.class1.find({$and:[{age:{$gt:13}},{name:{$lt:'Lily'}}]},{_id:0})

$or 逻辑或

e.g.  年龄大于15或者为男生
db.class1.find({$or:[{age:{$gt:15}},{sex:'m'}]},{_id:0})

$not  逻辑非

e.g.  年龄不大于15
db.class1.find({age:{$not:{$gt:15}}},{_id:0})

$nor  既不也不

e.g.  既不大于16 也不是女生
db.class1.find({$nor:[{age:{$gt:16}},{sex:'w'}]},{_id:0})


条件混合

年龄大于16并且为男生  或者 年龄小于14
 db.class1.find({$or:[{age:{$gt:16},sex:'m'},{age:{$lt:14}}]},{_id:0})


年龄大于16或者为女生  并且 姓名大于 Jame
db.class1.find({name:{$gt:'Jame'},$or:[{age:{$gt:16}},{sex:'w'}]},{_id:0})


数组  

[1,2,3,4]

数组查找

查看数据中是否包含某一项

e.g.  如果score数组中包含67即可
db.class3.find({score:67},{_id:0})
db.class3.find({score:{$gt:90}},{_id:0})


$all
查找数据中同时包含多项

e.g. 同时包含64  75
db.class3.find({score:{$all:[64,75]}},{_id:0})


$size 
通过数组元素个数查找

e.g. 
db.class3.find({score:{$size:3}},{_id:0})

$slice 
取出数组的部分进行显示  放在field中

e.g.  显示数组中前两项
db.class3.find({},{_id:0,score:{$slice:2}})

e.g.  跳过第一项显示后面一项
db.class3.find({},{_id:0,score:{$slice:[1,1]}})


其他查找方法

$exists
判断一个域是否存在

e.g.  查找存在age域的文档
db.class1.find({age:{$exists:true}},{_id:0} )

* true 表示有这个域 false表示筛选无这个域

$mod
余数查找

e.g.  查找除以2余数为1的 
 db.class1.find({age:{$mod:[2,1]}},{_id:0} )

$type 
找出值为指定类型的文档

e.g.  查找age数据类型为1的文档
 db.class1.find({age:{$type:1}},{_id:0} )

具体数字和类型的匹配
Type	            Number	
Double	             1		 
String	             2		 
Object	             3		 
Array	             4	
Binary data	     5	
ObjectId	     7		 
Boolean        	     8	
Date	             9		 
Null	             10	
RE	             11	  
Symbol	             14		
32-bit integer	     16	 
Timestamp	     17		 
64-bit integer	     18	


查找结果相关函数

distinct()
功能：查看集合某个域的取值范围

e.g. 查看集合中age域值的范围  
db.class1.distinct("age")

pretty()
功能： 格式化显示查找结果

e.g.   db.class1.find().pretty()  


limit(n)
功能： 显示查找结果的前n条

e.g.  显示查找结果的前三条  
db.class1.find({},{_id:0}).limit(3)

skip(n)
功能 ： 跳过前n条显示

e.g.  跳过前三条显示后边的内容
db.class1.find({},{_id:0}).skip(3)

count()
功能 ： 计数统计

e.g. 统计男生数量
db.class1.find({sex:'m'},{_id:0}).count()


sort({域：1/-1})
功能 ： 对查找结果排序
参数 ： 以键值对的形式给出
        1 表示按照升序排序， -1表示降序排序

e.g.  按照年龄升序
db.class1.find({},{_id:0}).sort({age:1})

复合排序：当第一排序项相同时比较第二排序项

e.g. 
db.class0.find({},{_id:0}).sort({age:1,name:1})

函数的连续调用
当函数返回文档集合时还可以继续调用函数

e.g.  查找班级年龄最大的三个
db.class1.find({},{_id:0}).sort({age:-1}).limit(3)

文档的删除操作

delete  from table  where  ...

db.collection.remove(query,justOne)
功能 ： 删除文档
参数 ： query  筛选要删除的文档 相当于where
               用法同查找
	justOne ： 布尔值，默认为false 表示删除所有。如果设置为true 只删除第一条符合条件的文档。
e.g. 
db.class2.remove({name:"阿蓉"})

e.g.  justOne为true则只删除第一条符合条件的
db.class0.remove({age:17},true)

删除集合中所有文档

e.g.  删除class2中所有文档
db.class2.remove({})


练习 ：
1. 创建数据库  名字 grade
  use  grade
2. 数据库中创建集合 class
3. 集合中插入文档，格式如下
   {name:'zhang',age:10,sex:'m',hobby:['a','b']}
   age范围  4-15
   hobby 范围 
   [draw  dance  sing  pingpong    basketball  football  running  computer]  

4. 查找练习
   查看班级所有人信息
    find()

   查看班级年龄8岁的同学信息
   find({age:8})
   
   查看年龄大于10岁的学生信息
   find({age:{$gt:10}})
   查看年龄在8-11岁之间的学生信息
   find({age:{$gte:8,$lte:11}})

   查看年龄为9岁且为男生的学生
    find({age:9,sex:'m'})

   找到年龄小于7岁或大于12岁的学生
   find({$or:[{age:{$lt:7}},{age:{$gt:12}}]})
 
   找到年龄为8岁或者11岁的学生
   find({age:{$in:[8,11]}})

   找到有两项兴趣爱好的学生
   find({hobby:{$size:2}})

   找到兴趣中有draw的学生
   find(hobby:'draw')

   找喜欢画画又喜欢跳舞的学生
   find(hobby:{$all:['draw','dance']})

   统计兴趣有三项的学生人数
   find({hobby:{$size:3}}).count()

   找到本班年龄第二大的同学 
   find().sort({age:-1}).skip(1).limit(1)

   查看兴趣的范围
   找到年龄最小的三个同学
    find().sort({age:1}).limit(3)

5. 删除所有年龄大于12或者小于7岁的同学

remove({$or:[{age:{$lt:7}},{age:{$gt:12}}]})


修改操作
update  table  set  ... where ...

db.collection.update(query,update,upsert,multi)
功能 ： 修改文档
参数 ： query ： 筛选需要修改的文档，相当where
                 用法同查找
        update： 要修改什么内容 相当set。往往需要          配合修改操作符
	upsert：bool值 默认false 如果query的文档不         存在则不做操作
	        设置为true 则如果文档不存在根据query和update内容插入新文档
	multi： bool值 默认false 如果删选到多条文         档则只修改第一条。
	        设置为true则表示修改所有筛选到的文档

e.g.  年龄修改为18 db.class0.update({name:'HanMei'},{$set:{age:18}})

e.g.  如果筛选内容不存在则插入 
 db.class0.update({name:'Jame'},{$set:{age:18}},true)

e.g.  如果匹配到多条，则修改所有
db.class0.update({sex:'w'},{$set:{name:'小芳'}},false,true)

作业 ： 1. 操作一遍增删改查已经解除的操作符
        2. 学习一下魔法方法 __call__ 
	3. 网络程序
```



# 第三天

```
复习 ： 

1. 查找操作   find(query,field)   findOne()

   操作符 ： 比较  $lt  $lte  $gt  $gte  $ne  $eq
                   $in  $nin
	     逻辑 $and  $or   $not  $nor

             数组  $all  $size 

	     其他  $exists   $mod   $type

2. 函数 ： pretty()  limit()   skip()  sort()
           count()
   其他函数： distinct()   getCollection()

3.  删除文档    remove(query,justOne)
                remove({})

4.  修改操作  update(query,update,upsert,multi)

==================================================

修改操作符

$set
修改一个域的值，或者增加一个域

e.g.  修改功能 如果该域不存在则增加这个域
db.class0.update({age:20},{$set:{name:'小薇'}})

$unset
删除一个域

e.g.   sex后面为空表示删除一个域
db.class0.update({name:'Jame'},{$unset:{sex:''}})

$rename 
修改一个域的名称

e.g.  将sex域名修改为gender
db.class0.update({},{$rename:{sex:'gender'}},false,true)


$setOnInsert
如果update执行了插入文档操作，表示补充插入内容 

e.g.  如果执行插入操作则将setOnInsert中内容也插入
db.class0.update({name:'Tom'},{$set:{age:17},$setOnInsert:{gender:'m',tel:'12345'}},true)

* 在update参数中可以同时写多个修改器

$inc
加减修改器

e.g. 所有人年龄增加1
db.class0.update({},{$inc:{age:1}},false,true)

* $inc值可以是正数负数整数小数

$mul
乘法修改器

e.g. Tom年龄 乘以2
db.class0.update({name:'Tom'},{$mul:{age:2}})

* $mul值可以是正数负数整数小数


$max
指定了某个域值的下限，如果小于指定值则修改为指定值

e.g.  将年龄不到20的修改为20
db.class0.update({},{$max:{age:20}},false,true)

$min
指定了某个域值的上限，如果大于指定值则修改为指定值

e.g.  年龄大于25的修改为25 
db.class0.update({},{$min:{age:25}},false,true)


数组修改器

$push  向数组中添加一项

e.g. 
db.class3.update({name:'小明'},{$push:{score:5}})

$pushAll  向数组中添加多项

e.g.
db.class3.update({name:'小红'},{$pushAll:{score:[5,10]}})

$pull  从数组中删除一项

e.g.
db.class3.update({name:'小红'},{$pull:{score:10}})

*数组可以有重复值，如果删除则会把所有指定的值都删除

$pullAll  删除数组中多项

e.g.  
db.class3.update({name:'小明'},{$pullAll:{score:[67,5]}})


$each   对多个值逐一操作

e.g.  
db.class3.update({name:'小明'},{$push:{score:{$each:[5,10]}}})

$position  指定插入位置 

e.g.  需要搭配$each使用，将数据从1号位置插入
db.class3.update({name:'小红'},{$push:{score:{$each:[10],$position:1}}})

$sort  对数组进行排序

e.g.  和each一起使用，对数组score进行排序
db.class3.update({name:'小红'},{$push:{score:{$each:[],$sort:1}}})

$pop  弹出一项

e.g.   1表示弹出最后一项 -1表示删除第一项  
db.class3.update({name:'小红'},{$pop:{score:-1}})

$addToSet  向数组中添加一项，不能和已有的内容重复

e.g.  添加87，不能和已有数据重复
db.class3.update({name:'小红'},{$addToSet:{score:87}})


时间类型

mongodb中存储时间格式 ： ISODate()

方法1 ：  new Date()   自动生成当前时间

e.g. 
db.class2.insert({title:'Python入门',date:new Date()})

方法2 ： ISODate()  生成当前时间

e.g. 
db.class2.insert({title:'Python精通',date:ISODate()})

方法3  Date()  将生成的当前时间变为字符串存储

e.g. 
db.class2.insert({title:'Python疯狂',date:Date()})

ISODate()
功能 ： 生成时间类型存储
参数 ： 参数指定时间
         "2018-07-01 12:10:56"
	 "20180701 12:10:56"
	 "20180701"

e.g. 
db.class2.insert({title:'Python崩溃',date:ISODate("2018-07-01 01:12:12")})


时间戳

valueOf()
将时间转换为时间戳

e.g.
db.class2.insert({title:'Python放生',date:ISODate().valueOf()})


Null  ----》 null

1. 如果某个域存在却没有值，可以设置为null

e.g.  
db.class2.insert({title:'Python涅槃',price:null})

2. 如果某个域不存在可以使用null匹配

e.g.  找到date域不存在的文档
 db.class2.find({date:null},{_id:0})


Object 内部文档

文档内某个域的值还是一个文档，则这个文档为内部文档

* 当需要使用内部文档某个域的时候，可以使用外部文档 . 的方法引用内部文档。但是注意此时需要加引号

e.g.
db.class4.find({'book2.title':'python Web'},{_id:0})

e.g. 
db.class4.update({'book1.title':'python爬虫'},{$set:{'book1.price':48.8}})

数组的下标引用

* 使用数组时，可以使用数组域 . 数组序列下标的方式引用数组的具体某一项

e.g. 
db.class3.find({'score.0':98},{_id:0})

e.g.
db.class3.update({name:'小明'},{$set:{'score.0':100}})


查找结果的有序性

即可以对find的查找结果使用[]的方式引用具体某一条

e.g.
db.class1.find({},{_id:0})[1]

练习 ： 
使用之前的grade数据库

1. 将小红年龄修改为8岁，兴趣爱好变为跳舞画画
｛$set:{age:8,hobby:[‘draw’,'dance']}｝

2. 追加小明兴趣爱好 唱歌
 {$push:{hobby:'sing'}}

3. 追加小王兴趣爱好，吹牛，打篮球
{$pushAll:{hobby:['chuiniu','basketball']}}

4. 小李兴趣多了跑步唱歌，但是要确保和之前的不重复
{$addToSet:{hobby:{$each:['running','sing']}}}

5. 班级所有人年龄加1
{$inc:{age:1}},false,true

6. 删除小明的sex属性
{$unset:{sex:''}}

7. 删除小李的第一个爱好 
{$pop:{hobby:-1}}

8. 删除小红的兴趣画画和唱歌
{$pullAll:{hobby:['draw','sing']}}


索引

指建立指定键值对及所在文档中存储位置的对照清单。使用索引可以方便我们快速查找，减少遍历次数，提高查找效率。

mongodb创建索引

ensureIndex()
功能 ： 创建索引
参数 ： 索引域，索引类别和选项        

e.g.  根据name 创建索引
db.class1.ensureIndex({name:1})

* 1表示正序 -1逆序

查看一个集合中的索引

db.class1.getIndexes()

* _id是系统自动创建的索引

自定义索引名称

db.class1.ensureIndex({name:1},{name:'name_index'})

删除索引
dropIndex()
功能 ： 删除索引
参数 ： 要删除的索引，可以是索引名称或者索引键值对

e.g.   db.class1.dropIndex('age_index')
e.g.   db.class1.dropIndex({name:-1})

dropIndexes()
删除所有索引  除了_id

e.g. db.class1.dropIndexes()


索引类型

复合索引
根据多个域创建一个索引

e.g. 
db.class1.ensureIndex({name:1,age:-1})


数组和子文档索引

如果对某个域创建索引，值为数组或者子文档，则通过数组或子文档进行查找时也是索引查找

覆盖索引

查找返回的内容，仅仅是索引表存储的内容，不需要再去原数据库查找

唯一索引

创建索引时希望集合中创建索引的域的值均不重复


e.g.
db.class1.ensureIndex({name:1},{unique:true})

* 创建唯一索引的域的值不可以重复


稀疏索引（间隙索引）

只针对有指定域的文档创建索引表，如果某个文档没有该域则不做索引处理

e.g.  创建age域的稀疏索引
db.class1.ensureIndex({age:1},{sparse:true})


索引约束
1. 当数据发生更新 ，索引也要随之更新。影响插入，    修改，删除操作的效率
2. 索引表也需要占有一定的磁盘空间

综上 ：当数据量比较小，或者需要频繁的进行数据修       改操作而不是查找操作的时候，不适合创建索引


聚合操作

对文档的更高级的筛选整理统计

db.collection.aggregate()
功能 ： 聚合函数，完成聚合操作
参数 ： 聚合条件 ---》 聚合操作符

聚合操作符

$group  分组聚合  需要配合分组统计操作符使用
      
      $sum  ： 求和 
      
      e.g. 
      db.class1.aggregate({$group:{_id:'$sex',
		            分组  按sex内容分组
       num:            {$sum:1}}})
     自定义统计域       统计什么

       e.g. 统计所有男生和女生的年龄之和
	db.class1.aggregate({$group:{_id:'$sex',num:{$sum:'$age'}}})

     $avg   求平均
     
     e.g.  求每个性别的平均年龄
     db.class1.aggregate({$group:{_id:'$sex',num:{$avg:'$age'}}})

     $max  求最大值
     
     e.g.  求每组年龄的最大值
     db.class1.aggregate({$group:{_id:'$sex',max:{$max:'$age'}}})

     $min  求最小值

     e.g.  求每组年龄的最小值
     db.class1.aggregate({$group:{_id:'$sex',min:{$min:'$age'}}})

$project 
用于修改文档的显示效果

e.g. 
db.class1.aggregate({$project:{_id:0,sex:0}})

e.g.   指定显示域名
db.class1.aggregate({$project:{_id:0,Name:'$name',Age:'$age'}})


$match  过滤数据

e.g.  过滤年龄大于16的
db.class1.aggregate({$match:{age:{$gt:16}}})

作业 ： 熟练mongodb增删改查操作
        熟练 索引操作
```





# 第四天



```
复习：

1. 数据的修改 
update(query,update,upsert,multi)

修改器 ： $set   $unset  $rename  $setOnInsert
          $inc   $mul  $max  $min 
	  $push  $pushAll  $pull  $pullAll 
	  $each  $position   $sort  $addToSet
	  $pop

时间类型 ： new Date()   ISODate()  Date()
            valueOf()

null : 作为一个域的值，或者表示一个域不存在

内部文档 ：通过 . 获取内部文档某个域的值

索引操作： ensureIndex（{},{}）
           dropIndex()  dropIndexes()
           getIndexes()

聚合操作

aggregate（）

聚合操作
$group   $project   $match
$sum
$avg
$max
$min
**********************************************

聚合操作

$limit  显示前几条文档

e.g.  获取数据的前两个文档
db.class1.aggregate({$limit:2})

$skip  跳过几条文档

e.g.  跳过前两条文档显示后面内容  
db.class1.aggregate({$skip:2})

$sort  排序

e.g.  按年龄升序排序
 db.class1.aggregate({$sort:{age:1}})

聚合管道 ： 将前一个聚合操作得到的结果，给后一个             聚合操作继续使用

db.collection.aggregate([聚合1，聚合2....])


e.g. $match ---> $project  ---> $sort
db.class1.aggregate([{$match:{sex:'m'}},{$project:{_id:0}},{$sort:{age:1}}])
找出文档中有重名的名字
e.g.   $group  ---> $match
db.class1.aggregate([{$group:{_id:'$name',num:{$sum:1}}}])
db.class1.aggregate([{$group:{_id:'$name',num:{$sum:1}}},{$match:{num:{$gt:1}}}])

练习：
增加分数域  score:{chinese:88,math:76,english:76}

1.学生按照性别分组，统计每组人数
aggregate({$group:{_id:'$sex',num:{$sum:1}}})

2. 统计每名男生的语文分数
aggregate([{$match:{sex:'m'}},{$project:{_id:0,name:1,'score.chinese':1}}])

3. 将所有女生按照英语成绩降序排序
aggregate([{$match:{sex:'w'}},{$sort:{'score.englisth':-1}}])


固定集合

mongodb中可以创建大小固定的集合，称之为固定集合

特点 ： 插入速度快，顺序查找速度快
        能够淘汰早期数据
	可以控制集合大小

使用 ： 临时缓存
        日志处理

db.createCollection(collection,{capped:true,size:10000,max:1000})

capped：true    表示创建固定集合
size ： 表示集合的大小  bytes    4.0最小 4096
max ： 表示最多存放多少文档

e.g. 
db.createCollection('log',{capped:true,size:10,max:3})


文件存储

文件存储到数据库方式

1. 存储路径
   将文件在本地的路径以字符串形式存储到数据库

   优点 ： 节省数据库空间
   缺点 ： 当数据库或者文件位置发生变化时文件丢         失。

2. 存储文件本身
   以二进制方式将文件存储到数据库
   
   优点：数据库和文件绑定存在
   缺点 ： 占用空间大，结构化麻烦

mongodb存储二进制文件

* GridFS方法存储大文件  >16M为大文件
* 将文件转化为二进制，进行插入  Binary data

GridFS方案解释

1. 在mongodb中一个数据库创建两个集合共同完成对文    件的存储
2. fs.files 用来存储文件的相关信息，为每一个文件    创建一个文档，存储文件名、文件类型等信息
3. fs.chunks 用来分块存储文件的实际内容

如何存储
mongofiles  -d  dbname   put   file
                数据库       要存储的文件

* 如果数据库不存在自动创建

fs.files
{ "_id" : ObjectId("5b569b8969d72e103282f608"), "chunkSize" : 261120, "uploadDate" : ISODate("2018-07-24T03:22:54.259Z"), "length" : 247759369, "md5" : "a94853f4f64b3e87bf98aea770855615", "filename" : "abc.mp4" }

fs.chunks
{ "_id" : ObjectId("5b569b8969d72e103282f61d"), "files_id" : ObjectId("5b569b8969d72e103282f608"), "n" : 20, "data" : BinData(0,"7Pa7M7M9nZt2bezsz272vbdm/7fhu672fwAAbZKbmR2S7Ndv/.....")}

* 对于同一个文件 fs.files中的_id值等于 fs.chunks中的files_id值

文件提取方法

mongofiles  -d  dbname  get  file

Grid的优缺点
优点 ： 存储方便，提供较好的命令支持
缺点 ： 读写效率低

游标

通过一定的操作获取返回结果的对象

var  cursor = db.class1.find()
cursor.hasNext()  判断是否有next
cursor.next()  获取下一条数据

python操作mongodb 

pymongo模块   第三方模块

安装 
sudo  pip3  install  pymongo

操作步骤
1. 创建mongodb数据库连接对象

conn = pymongo.MongoClient('localhost',27017)

2. 得到数据库对象

db = conn.stu 

3. 获取集合对象

myset = db.class1

4. 增删改查，索引 ，聚合

调用各种myset的属性函数

5. 关闭数据库连接
conn.close()

插入操作

insert()
insert_many()     insert_one()
save()

查找操作

cursor = find()
返回一个结果游标

* 在pymongo中使用操作符的方法与mongo shell中相同，只需要转变为字符串格式加上引号即可

cursor 的属性函数

next()
limit()
skip()
sort([('name',1),('age',-1)])
count()

* 使用了next或者for取游标后就不能使用limit sort操作了

find_one()
返回一个字典

更新操作

update(query,updata,upsert=False,multi=False)
update_many()
update_one()

删除操作
remove(query,multi = True)

multi默认为True表示删除所有筛选内容
如果设置为False则表示删除一条

复合功能函数
find_one_and_delete()


索引操作
ensure_index()   创建索引
list_indexes()   查看索引
drop_index()   删除索引
drop_indexes()  删除所有索引

聚合操作
aggregate([])
参数写法和mongo shell中聚合相同
返回值 ： 返回一个迭代游标 同find()


GridFS  程序提取

import gridfs 

gridfs.GridFS(db)


插入二进制格式数据

import bson.binary 
```

 