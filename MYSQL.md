# MYSQL_day01



王伟超
wangweichao@tedu.cn
MySQL-Day01笔记
1、MySQL概述
	1、什么是数据库
		数据库是一个存储数据的仓库
	2、都有哪些公司在用数据库
		金融机构、游戏网站、购物网站、论坛网站 ...
	3、提供数据库服务的软件
		1、软件分类
			MySQL、Mariadb、SQL_Server、Oracle、DB2、MongoDB ...
		2、生产环境中,如何选择使用哪个数据库
			1、是否开源
				开源软件：MySQL、Mariadb、MongoDB
				商业软件：Oracle、DB2、SQL_Server
			2、是否跨平台
				跨平台：
				不跨平台：SQL_Server
			3、公司的类型
				商业软件：政府部门、金融机构
				开源软件：游戏网站、购物网站、论坛网站 ...
	4、MySQL特点
		1、关系型数据库
			1、关系型数据库的特点
				1、数据是以行和列的形式存储
				2、表中每一行叫一条记录
				3、表中的每一列叫一个字段
				4、表和表之间的逻辑关联叫关系
			2、示例
				1、关系型数据库存储
					表1、学生信息表
						姓名  年龄  班级
						星矢   25   三班
						水冰月 25   六班
					表2、班级信息表
						班级  班主任
						三班  大空翼
						六班  松人
				2、非关系型数据库存储
					{"姓名":"星矢","年龄":25,"班级":"三班","班主任":"大空翼"}
					{"姓名":"水冰月","年龄":25,"班级":"六班","班主任":"松人"}
		2、跨平台
			可以在Unix、Linux、Windows上运行数据库服务
		3、支持多种编程语言
			Python、Java、php ...
	5、数据库软件、数据库、数据仓库
		1、数据库软件
			是一种软件,可以看得见,可操作,来实现数据库逻辑功能
		2、数据库
			是一种逻辑概念,用来存放数据的仓库,通过数据库软件来实现,侧重存储
		3、数据仓库
			数据仓库主要用于数据挖掘和数据分析
			网购：
				数据库： user --> 用户名和密码
				数据仓库：哪个时间段用户登录量最多,哪个用户一年购物最多...
2、MySQL安装
	1、Ubuntu安装MySQL服务
		1、安装服务端
			sudo apt-get install mysql-server
		2、安装客户端	
			sudo apt-get install mysql-client
		3、Ubuntu安装软件
			sudo apt-get update
			sudo apt-get -f install 修复依赖关系
			sudo apt-get install 软件包
	2、Windows安装MySQL服务
		1、下载MySQL安装包(windows)
			mysql-installer***5.7.***.msi
		2、双击、按照教程安装
3、启动和连接MySQL服务
	1、服务端启动
		sudo /etc/init.d/mysql start
		sudo /etc/init.d/mysql stop
		sudo /etc/init.d/mysql restart
		sudo /etc/init.d/mysql status #查看当前状态
		sudo /etc/init.d/mysql reload #重新加载配置文件
	2、客户端连接
		1、命令格式
			mysql -h主机地址 -u用户名 -p密码
			mysql -hlocalhost -uroot -p123456
		2、本地连接可省略 -h 选项
			mysql -uroot -p123456

			mysql -hlocalhost -uwu_shengjun -p12345 

4、基本SQL命令
	1、SQL命令的使用规则
		1、每条SQL命令必须以 ; 结尾
		2、SQL命令不区分字母大小写
		3、使用 \c 终止当前命令的执行
	2、库的管理
		1、库的基本操作
			1、查看已有的库
				show databases;
			2、创建库
				create database 库名 [character set utf8];
			3、查看创建库的语句(字符集)
				show create database 库名;
			4、查看当前所在库
				select database();
			5、切换库
				use 库名;
			6、查看库中已有表
				show tables;
			7、删除库
				drop database 库名;
		2、库的命名规则
			1、数字、字母、_,但是不能是纯数字
			2、库名区分字母大小写
			3、不能使用特殊字符和mysql关键字
		3、练习
			1、创建库testdb,指定字符集为utf8
				create database testdb character set utf8;
			2、进入到库 testdb
				use testdb;
			3、查看当前所在库
				select database();
			4、创建库 testdb2,指定字符集为 latin1
				create database testdb2 character set latin1;
			5、进入到库 testdb2
				use testdb2;
			6、查看 testdb2 的字符集
				show create database testdb2;
			7、删除库 testdb
				drop database testdb;
			8、删除库 testdb2
				drop database testdb2;
				show databases;
	3、表的管理
		1、表的基本操作
			1、创建表(指定字符集)
				create table 表名(
				字段名1 数据类型,
				字段名2 数据类型,
				字段名3 数据类型
				)character set utf8;
			2、查看创建表的语句(字符集)
				show create table 表名;
			3、查看表结构
				desc 表名;
			4、删除表
				drop table 表名;
		2、练习
			1、创建库 python1
				create database python1;
			2、在python1库中创建表 pymysql,并指定字符集为 utf8
				字段有三个：id name age 数据类型自己定义(比如说：char(20) 、int )
				use python1;
				create table pymysql(
				id int,
				name char(20),
				age int
				);
			3、查看创建表 pymysql 的语句
				show create table pymysql;
			4、查看pymysql的表结构
				desc pymysql;
			5、删除表 pymysql
				drop table pymysql;
			6、删除库 python1
				drop database python1;
	4、注意
		1、所有的数据都是以文件的形式存放在数据库目录/var/lib/mysql
	5、表记录的管理
		1、在表中插入记录
			1、insert into 表名 values(值1),(值2),(值3),...;
			2、insert into 表名(字段名1,字段名2) values(),(),...;
		2、查询表记录
			1、select * from 表名 [where 条件];
			2、select 字段名1,字段名2 from 表名 [where 条件];
			3、示例
				mysql> select * from t2;
				mysql> select * from t2 where id<3;
				mysql> select name,age from t2;
				mysql> select id,name from t2 where id<4;
		3、练习
			1、查看所有库
				show databases;
			2、创建一个新库 studb 
				create database studb;
			3、在 studb 中创建一张表tab1,指定字符集utf8,字段有:
				id name age score 四个 char(15)
				use studb;
				select database();
				create table tab1(
				id int,
				name char(15),
				age int,
				score int
				)character set utf8;
			4、查看 tab1 的表结构
				desc tab1;
			5、在tab1中随便插入2条记录
				insert into tab1 values
				(1,"李白",30,90),(2,"杜甫",30,88);
			6、在tab1中的name和score两个字段插入2条记录
				insert into tab1(name,score) values
				("李清照",25),("王维",28);
			7、查看tab1表中所有记录
				select * from tab1;
			8、查看tab1表中所有人的名字和成绩(score)
				select name,score from tab1;
5、如何更改默认字符集
	1、方法
		通过更改MySQL配置文件实现
	2、步骤
		1、获取root权限
			sudo -i
		2、备份配置文件
			cd /etc/mysql/mysql.conf.d/
			cp  mysqld.cnf  mysqld.cnf.bak
		3、更改mysqld.cnf配置
			subl mysqld.cnf
			[mysqld]
			character_set_server=utf8
		4、重启mysql服务
			sudo /etc/init.d/mysql restart
6、客户端把数据存储到数据库服务器上的过程
	1、先连接到数据库服务器 
	2、选择库
	3、创建或者修改表
	4、断开与数据库的连接  exit; | quit; | \q;
7、数据类型
	1、数值类型
		1、整型(有符号 和 无符号unsigned)
			1、int 大整型(4个字节)
				0~2**32 -1(42亿多)
			2、tinyint 微小整型(1个字节)
				1、有符号(signed)
				2、无符号(unsigned) : 0~255
					age tinyint unsigned,
			3、bigint 极大整型(8个字节)
		2、浮点型
			1、float(4个字节,最多显示7个有效位)
				1、用法
					字段名 float(m,n)  m:总位数,n:小数位位数
					float(5,2) 取值范围？？？-999.99 ~ 999.99
			2、decimal(最多显示28个有效位)
				1、用法
					字段名 decimal(m,n)
				2、存储空间(整数部分和小数部分分开存储)
					规则：将9的倍数包装成4个字节

						余数   字节
						 1-2     1
						 3-4     2
						 5-6     3
						 7-8     4
						decimal(19,9)
							整数部分：10/9=商1余1 4字节+1字节=5字节
							小数部分：9/9=商1余0  4字节+0字节=4字节

	2、字符类型
		1、char(定长)
			char(宽度值) 
		2、varchar(变长)
			varchar(宽度值)
		3、char和varchar的特点
			1、char ：浪费存储空间,性能高
			2、varchar ：节省存储空间,性能低
		4、text / longtest(4G)
	3、练习
		1、创建一个库 studb2,并在studb2中创建表 tab2,字段要求如下：
			id 整型
			name 变长,宽度为20
			class 定长,宽度为7
			age 微小整型,不能输入负数
			height 浮点型,小数位为2位
		
			create database studb2;
			use studb2;
			create table tab2(
			id int,
			name varchar(20),
			class char(7),
			age tinyint unsigned,
			height float(5,2)
			);
		2、查看tab2表结构
			desc tab2;
		3、查看tab2字符集
			show create table tab2;
		4、在tab2中插入2条完整记录
			insert into tab2 values
			(1,"紫衫龙王","AID1805",23,170.36),
			(2,"青翼蝠王","AID1805",25,171.17);
		5、查询所有表记录
			select * from tab2;
		6、在tab2中的name和height两个字段插入2条记录
			insert into tab2(name,height) values
			("金花婆婆",165),("灭绝师太",168.00);
		7、查询所有学生的姓名和身高
			select name,height from tab2;
		8、查询身高大于160的学生信息
			select * from tab2 where height>170;
	4、数值类型的宽度和字符类型的宽度区别
		1、数值类型宽度为显示宽度,只用于select查询显示,和占用存储空间大小无关,用 zerofill 来显示效果
			id int(3) zerofill,
		2、字符类型的宽度超过则无法存储
	3、枚举类型
		1、定义 
			字段值只能在列举的范围内选择
		2、字段名 enum(值1,值2,...)
			 字段名 set(值1,值2,...)
			 插入记录的时候: "girl,Python,Study"
	4、日期时间类型		


8、表字段操作
	1、语法：alter table 表名 执行动作;
	2、添加字段(add)
		alter table 表名 add 字段名 数据类型;
		alter table 表名 add 字段名 数据类型 first;
		alter table 表名 add 字段名 数据类型 after 字段名;
	3、删除字段(drop)
		alter table 表名 drop 字段名;
	4、修改字段数据类型(modify)
		alter table 表名 modify 字段名 新数据类型;
作业：
	1、MySQL中的数据类型有 ____ ____ ____ ____
	2、关系型数据库的核心内容是 关系 即 二维表
	3、char和varchar的区别,各自的特点
	4、
		1、创建一个库 school
		2、在库中创建一个表 students来存储学生信息
			id 显示宽度为3,位数不够用0填充
			name、age(要求不能输入负数)、score(浮点float)、性别(单选)、
			likes(多选)
		3、查看students的表结构
		4、在students中添加一个字段height,加在age字段之后
		5、将score字段的数据类型改为decimal
		6、在students中插入3条完整记录
		7、查看所有学生的姓名和成绩
		8、查看没有及格的学生的信息



# MYSQL_day02

MySQL-Day01回顾
1、MySQL特点
	1、关系型数据库
	2、跨平台
	3、支持多种编程语言
2、MySQL启动连接
	1、服务端启动
		sudo /etc/init.d/mysql start | stop | restart | reload
	2、客户端连接
		mysql -h主机地址 -u用户名 -p密码
	3、注意
		1、MySQL中数据是以文件的形式存储在数据库目录/var/lib/mysql
		2、关系型数据库的核心内容是关系 即 二维表
3、基本SQL命令
	1、库的管理
		1、创建:create database 库名 character set utf8;
		2、查看:show create database 库名;
		3、所在库:select database();
		4、切换库:use 库名;
		5、查看表:show tables;
		6、删除库:drop database 库名;
	2、表的管理
		1、创建: create table 表名(字段名 数据类型,...)char....
		2、查看字符集和存储引擎: show create table 表名;
		3、查看表结构: desc 表名;
		4、删除表: drop table 表名;
	3、表记录管理
		1、插入记录
			insert into 表名(..,..,..) values(),(),(),...;
		2、查询记录
			select 字段名1,字段名2 from 表名 where 条件;
	4、更改库的默认字符集
		1、sudo -i
		2、cd /etc/mysql/mysql.conf.d/
		3、cp mysqld.cnf mysqld.cnf.bak
		4、vi mysqld.cnf
			[mysqld]
			character_set_server=utf8
		5、/etc/init.d/mysql restart
		6、exit
	5、数据类型
		1、数值类型
			1、整型
				1、int
				2、tinyint unsigned
			2、浮点型
				1、float(m,n) 
				2、decimal(m,n)
					decimal(20,2)
						整数部分：18/9=商2余0 4字节
						小数部分：2/9=商0余2  1字节
						占5个字节的存储空间
		2、字符类型
			1、char(定长,浪费存储空间,性能高)
			2、varchar(变长,节省存储空间,性能低)
			3、text  |  longtext
			4、字符宽度、数值类型宽度
				1、数值宽度 ：显示宽度,和存储无关,用zerofill
				2、字符宽度 ：和存储相关,超过指定宽度则无法存储
		3、枚举类型
			1、单选 enum(...)
			2、多选 set(...)  ## "值1,值2,值3,..."
		4、日期时间类型
	6、表字段的操作
		1、添加add
			alter table 表名 add 字段名 数据类型 first|after 字段名
		2、修改modify
			alter table 表名 modify 字段名 新数据类型;
		3、删除drop
			alter table 表名 drop 字段名;
MySQL-Day02笔记
1、数据类型
	1、数值类型
	2、字符类型
	3、枚举类型
	4、日期时间类型
		1、date ：日期 "YYYY-MM-DD"
		2、time ：时间 "HH:MM:SS"
		3、datetime ：日期时间 "YYYY-MM-DD HH:MM:SS"
		4、timestamp ：日期时间 "YYYY-MM-DD HH:MM:SS"
		5、注意
			1、datetime ：不给值默认返回NULL
			2、timestamp ：不给值默认返回系统当前时间
2、日期时间函数
	1、NOW() 返回服务器当前时间
	2、CURDATE() 返回当前日期 
	3、CURTIME() 返回当前时间
		insert into t1 values
		(2,"吕老师",25,CURDATE(),CURTIME(),NOW());
	4、日期时间运算
		1、语法格式
			select ... from 表名 
			where 字段名 运算符 (时间 - interval 时间间隔单位);
			时间间隔单位：
				1 day | 2 hour | 1 minute | 1 year | 3 month

			where id>8
			where meeting > (now() - interval 1 day);
											现在时间 - 1天的时间 = 1天前的时间点
		2、练习
			1、查询1天以内的记录
				select * from t1 where meeting>(now()-interval 1 day);
			2、查询1年以前的记录
				select * from t1 
				where meeting<(now()-interval 1 year);
			3、查询1天以前,3天以内的记录
				select * from t1 where
				meeting<(now()-interval 1 day) and
				meeting>(now()-interval 3 day);
	5、练习
		1、创建库 studb2
			create database studb2;
		2、在库中创建表 stuinfo,字段有3个：
			name、age、phone char(11)
			use studb2;
			create table stuinfo(
			name varchar(20),
			age tinyint unsigned,
			phone char(11)
			);
		3、查看表结构
			desc stuinfo;
		4、在表中第一列添加一个 id 字段
			alter table stuinfo add id int first;
		5、把 phone 的数据类型改为 bigint
			alter table stuinfo modify phone bigint;
		6、在表中最后一列添加一个字段：注册时间 register ,数据类型为：timestamp
			alter table stuinfo add register timestamp;
		7、在表中 id name age phone 四个字段插入1条记录
			insert into stuinfo(id,name,age,phone) values(1,"关羽",23,1363638438);
		8、查询5分钟内的注册信息
			select * from stuinfo where register>(now()-interval 5 minute);
		#####修改字段名######
		alter table 表名 change 原字段名 新字段名 数据类型;
4、表记录管理
	1、删除表记录(delete)
		1、delete from 表名 where 条件;
		2、注意
			delete语句后没有加where条件,表中所有记录全部清除
	2、更新表记录(update)
		1、update 表名 set 字段1=值1,字段2=值2,... where 条件;
		2、注意
			必须加where条件
	3、练习
		1、查找所有蜀国人信息
			select * from hero where country="蜀国";
		2、把id为2的英雄名字改为司马懿,国家改为魏国
			update hero set name="司马懿",country="魏国" where id=2;
		3、查找女英雄的姓名、性别和国家
			select name,sex,country from hero where sex="女";
		4、删除所有魏国的英雄
			delete from hero where country="魏国";
		5、查找所有蜀国男英雄的信息
			select * from hero where country="蜀国" and sex="男";
		6、删除所有的英雄
			delete from hero;
5、运算符操作(查询、修改、删除)	
	1、数值比较&字符比较&逻辑比较
		数值：= 、!= 、> 、>= 、< 、<=
		字符：= 、!=
		逻辑：and 、or
		2、练习
			1、找出攻击力高于150的蜀国英雄的名字和攻击值
				select name,gongji from sanguo where gongji>150 and country="蜀国";
			2、将赵云的攻击力改为666,防御力改为88
				update sanguo set gongji=666,fangyu=88 where name="赵云666";
			3、查找蜀国和魏国的英雄信息
				select * from sanguo where country="蜀国" or country="魏国";
			4、将吴国英雄中攻击值为110的英雄的攻击值设置为100,防御力设置为60
				update sanguo set gongji=100,fangyu=60 where country="吴国" and gongji=110;
	2、范围内比较
		1、运算符
			between 值1 and 值2 
			in(值1,值2,...)
			not in(值1,值2,...)
		2、示例
			1、查找攻击值在100到200之间的蜀国英雄信息
				select * from sanguo where gongji between 100 and 200 and country="蜀国";
			2、找到蜀国和吴国以外的国家的女英雄信息
				select * from sanguo 
				where country not in("蜀国","吴国") and sex="女";
	3、匹配空、非空
		1、空 ：is null
		2、非空 ：is not null
		3、示例
			1、查找姓名为NULL的蜀国男英雄信息
				select * from sanguo
				where name is null and country="蜀国" or sex="男";
			2、查找姓名为 "" 的英雄的id、姓名和国家
				select id,name,country from sanguo where name="";
			3、注意
				1、NULL ：空值,必须用 is 或者 is not 去匹配
				2、""   ：空字符串,只能用 = 或者 != 去匹配
	4、模糊比较
		1、where 字段名 like 表达式
		2、表达式
			1、_ ：匹配单个字符
			2、% ：匹配0到多个字符
		3、示例
			1、名字中至少有2个字符的记录
				select * from sanguo where name like "_%_";
			2、匹配名字为非空NULL的记录
				select * from sanguo where name like "%";
			3、匹配名字中只有三个字符的记录
				select * from sanguo where name like "___";
			4、匹配姓赵的记录
				select * from sanguo where name like "赵%";
6、SQL查询
	1、总结
		3、select ...聚合函数 from 表名
		1、where ...
		2、group by ...
		4、having ...
		5、order by ...
		6、limit ...;
	2、order by
		1、给查询的结果进行排序
		2、order by 字段名 排序方式
		3、排序方式
			1、升序 ：ASC(默认)
			2、降序 ：DESC
		4、练习
			1、将蜀国的英雄按照攻击值从高到低排序
				select * from sanguo 
				where country="蜀国" order by gongji DESC;
			2、将魏蜀两国的男英雄中名字为三个字符的英雄按防御值升序排列
				select * from sanguo 
				where country in("蜀国","魏国") and sex="男" and name like "___" 
				order by fangyu ASC;
	3、limit(永远放在SQL语句的最后)
		1、作用 ：限制显示查询记录的个数
		2、用法
			1、limit n -->显示n条记录
			2、limit m,n
				m ：表示从 m+1 条记录开始显示
				n ：表示显示 n 条
				limit 2,4 ：显示第3、4、5、6四条记录
				limit 0,2 ：显示第1、2两条记录
		3、示例
			1、在蜀国英雄中查找攻击值前三名且名字不为NULL的英雄姓名、攻击值和国家
				select name,gongji,country from sanguo
				where
				country="蜀国" and name is not NULL
				order by gongji DESC
				limit 3;
			2、在蜀国英雄中,查找防御值倒数第2名至倒数第4名的英雄信息
				select * from sanguo 
				where country="蜀国" order by fangyu limit 1,3;
		4、分页
			每页显示5(n)条记录,显示第4(m)页
			
			第1页：limit 0,5  ## 1 2 3 4 5
			第2页：limit 5,5  ## 6 7 8 9 10    ## (2-1)*5
			第3页：limit 10,5 ## 11 12 13 14 15  ##(3-1)*5
			第4页：limit 15,5 ## 16 17 18 19 20  ##(4-1)*5
			
			分页公式：limit (m-1)*n,n  m:第几页 n:每页显示记录条数
	4、聚合函数
		1、分类
			avg(字段名) : 平均值
			max(字段名) : 最大值
			min(字段名) : 最小值
			sum(字段名) : 求和
			count(字段名) : 统计该字段记录的个数
		2、示例
			1、攻击力最强值
				select max(gongji) as zq from sanguo;
			2、统计一下表中id、name字段分别有多少条记录
				select count(id),count(name) from sanguo;
				## 空值NULL不会被统计
				select count(*) from sanguo;
	5、group by
		1、作用 ：给查询的结果进行分组
		2、示例
			1、计算所有国家的平均攻击力,显示国家名和平均攻击力
				select country,avg(gongji) from sanguo 
				group by country; 
	
				先分组-再聚合-去重
				蜀国    
				蜀国    400   蜀国
				蜀国
				魏国    300   魏国
				魏国
				吴国    200   吴国
			2、查找所有国家中,英雄数量最多的前2名,显示国家名称和英雄数量
				select country,count(*) as number from sanguo
				group by country 
				order by number DESC limit 2;
		3、注意
			1、group by之后的字段名必须要为select之后的字段名
			2、如果select后的字段名和group by之后的字段不一致,则必须对该字段进行聚合处理(聚合函数)
	6、having
		1、作用 ：对查询结果进一步筛选
		2、示例
			1、找出平均攻击力大于105的国家的前2名,显示国家名称和平均攻击力
				select country,avg(gongji) from sanguo
				group by country
				having avg(gongji)>105
				order by avg(gongji) DESC limit 2;
		3、注意
			1、having语句通常和group by语句联合使用,过滤由group by语句返回的记录集
			2、where只能操作表中实际存在的字段,having操作由聚合函数生成的显示列
	7、distinct
		1、作用 ：不显示字段的重复值
		2、示例
			1、sanguo表中有哪些国家
				select distinct country from sanguo;
			2、计算魏国一共有多少个英雄
				select count(distinct name) from sanguo 
				where country="魏国";
		3、注意
			1、处理distinct和from之间的所有字段,所有字段值必须全部相同才可以去重
7、约束
	1、作用
		保证数据完整性、一致性、有效性的规则
	2、约束分类
		1、默认约束(default)
			1、插入记录时,如果不给该字段赋值,则使用默认值
			2、字段名 数据类型 default 默认值,
		2、非空约束(not null)
			1、不允许该字段值有NULL记录
			2、字段名 数据类型 not null default 值,
8、索引
	1、索引优缺点
		1、优点
			加快数据的检索速度
		2、缺点
			1、当对表中数据进行增加、修改、删除时,索引需要动态维护,降低了数据的维护速度
			2、索引需要占用物理存储空间
	



# MYSQL_day03

MySQL-Day02回顾
1、日期时间类型
	1、date
	2、time
	3、datetime
	4、timestamp
2、日期时间函数
	1、NOW()
	2、CURDATE()
	3、CURTIME()
	4、日期时间运算
		select ... from 表名 
		where 字段名 运算符(时间 -interval 时间间隔单位);
		时间间隔单位：hour 、day、month、year、minute ...
3、表记录操作
	1、删除 ：delete from 表名 where 条件;
	2、更新 ：update 表名 set 字段名1=值1,... where 条件;
4、运算符
	1、数值、字符、逻辑比较
	2、范围内比较
		between 值1 and 值2
		in(...)
		not in(...)
	3、空、非空
		is null
		is not null
	4、模糊比较(字符)
		字段名 like 表达式
		_ : 单个 字符
		% : 0到多个 字符
5、SQL查询
	1、order by 字段名 ASC/DESC
	2、limit
		1、limit n
		2、limit m,n
		3、分页：limit (m-1)*n,n  第 m 页的记录
	3、聚合函数
		avg(...) max(...) min(...) sum(...) 
		count(...) #NULL值不会被统计
	4、group by
		select后字段名未在group by之后出现,必须对该字段聚合处理
	5、having
		group by ... having 聚合函数显示列 
	6、distinct
		seletct count(distinct 字段名1,字段名2,...) from 表名;
	7、执行顺序
		3、select ...聚合函数 from 表名 
		1、where ...
		2、group by ...
		4、having ...
		5、order by ...
		6、limit ...
6、约束
	1、默认约束(default)
	2、非空约束(not null)
		sex enum("M","F","S") not null default "S",
MySQL-Day03笔记
1、索引
	1、BTREE
	2、优点 ：加快数据的检索速度
	3、缺点
		1、需动态维护,占用系统资源,降低数据维护速度
		2、占用物理存储空间
	4、索引示例
		1、开启运行时间检测 ：set profiling=1;
			备注 ：show variables like "profiling";
		2、执行查询语句
			select name from t1 where name="lucy99999";
		3、查看执行时间
			show profiles;
		4、给name字段创建索引
			create index name on t1(name);
		5、执行查询语句
			select name from t1 where name="lucy88888";
		6、查看执行时间
			show profiles;
	5、索引类型
		1、普通索引(index)
			1、使用规则
				1、可设置多个字段
				2、约束 ：无
				3、KEY标志 ：MUL
			2、创建
				1、创建表时
					index(字段名),
					index(字段名),
				2、已有表
					create index 索引名 on 表名(字段名);
			3、查看
				1、desc 表名;
				2、show index from 表名\G;
			4、删除
				drop index 索引名 on 表名;
		2、唯一索引(unique)
			1、使用规则
				1、可设置多个字段
				2、约束 ：字段值不允许重复,允许为NULL
				3、KEY标志 ：UNI
			2、创建
				1、创建表
					unique(字段名),
					unique(字段名)
				2、已有表
					create unique index 索引名 on 表名(字段名);
			3、查看、删除同普通索引
				Non_unique: 0 --> 唯一索引
				Non_unique: 1 --> 普通索引
		3、主键(primary key)&&自增长属性(auto_increment)
			1、使用规则
				1、只能有一个主键字段
				2、约束 ：不允许重复,不能为NULL
				3、KEY标志 ：PRI
				4、通常设置记录编号字段 id 为主键,唯一锁定一条记录
			2、创建
				1、创建表时
					id int primary key auto_increment,
				2、已有表
					alter table 表名 add primary key(字段名);
			3、删除
				1、删除自增长属性
					alter table 表名 modify id int;
				2、删除主键
					alter table 表名 drop primary key;
			

					主键：primary key  
						添加、删除 ：add/drop primary key..
	
					自增长：auto_increment
						添加、删除 ：modify id int;
			4、指定自增长属性起始值
				1、创建表
					create table 表名(
					id int primary key auto_increment,
					... ...
					)auto_increment=10000;
				2、已有表
					alter table 表名 auto_increment=10000;
		4、外键(foreign key)
2、数据导入
	1、把文件系统内容导入到数据的表中
	2、命令格式
		load data infile "文件名"
		into table 表名
		fileds terminated by "分隔符"
		lines terminated by "\n"
	3、将scoretable.csv文件导入到db3库下的score表中
		1、先把scoretable.csv文件拷贝到数据库的默认搜索路径中
			1、查看搜索路径方法
				show variables like "secure_file_priv";
			2、执行复制命令
				sudo cp /home/tarena/scoretable.csv /var/lib/mysql-files/
		2、创建库、表(utf8字符集)
			1、create database db3 character set utf8;
			2、use db3;
			3、
				create table score(
				id int,
				name varchar(20),
				score decimal(5,2),
				phone char(11),
				class char(7)
				)character set utf8;
		3、执行导入语句
			load data infile "/var/lib/mysql-files/scoretable.csv"
			into table score
			fields terminated by ","
			lines terminated by "\n";

			注意：
				1、库、表必须都为utf8编码
				2、路径必须写绝对路径 /var/lib/mysql-files/..."
		4、文件权限问题
			rwx ：所有者对此文件权限
			--- ：所属组其他用户对此文件权限
			rw- ：其他组的用户对此文件权限
			root ：所有者    
			root ：所属组
			
			1、修改文件权限
				chmod +rw scoretable.csv
				chmod 666 scoretable.csv
				r:4
				w:2
				x:1
			步骤：
				1、sudo -i
				2、cd /var/lib/mysql-files
				3、chmod 666 scoretable.csv
	4、excel文件转为csv文件
		打开excel表格 -> 文件 -> 另存为 -> *.csv(逗号分隔)
	5、更改一个文件的字符编码
		用 记事本/编辑器 打开,文件 -> 另存为 -> 选择编码
3、数据导出
	1、将数据库中表记录保存到系统文件里
	2、语法格式
		select ... from 表名
		into outfile "文件名"
		fields terminated by "分隔符"
		lines terminated by "\n"
	3、示例
		1、把sanguo表中的姓名、攻击值、国家三个字段导出到文件 sanguo.csv中
			select name,gongji,country from MOSHOU.sanguo
			into outfile "/var/lib/mysql-files/sanguo.csv"
			fields terminated by ","
			lines terminated by "\n";
		2、把mysql库下的user表中 user、host两个字段的值导出到 user.txt中,字段之间用 三个空格 去分隔
			select user,host from mysql.user
			into outfile "/var/lib/mysql-files/user.txt"
			fields terminated by "   "
			lines terminated by "\n";
	4、注意
		1、导出的内容完全由SQL查询语句决定
		2、路径必须指定为数据库搜索的绝对路径
4、表的复制
	1、语法
		create table 表名 select ... from 表名;
	2、示例
		1、复制sanguo表,sanguo2
			create table MOSHOU.sanguo2 select * from MOSHOU.sanguo;
		2、复制sanguo表的前3条记录,sanguo3
			create table MOSHOU.sanguo3 select * from sanguo limit 3;
		3、复制sanguo表的id、name和country三个字段的前5条记录,sanguo4
			create table MOSHOU.sanguo4 select id,name,country from MOSHOU.sanguo limit 5;
	3、只复制表结构
		create table 表名 select * from 表名 where false;
5、嵌套查询(子查询)
	1、定义
		把内层的查询结果作为外层的查询条件
	2、select ... from 表名 where 字段名 运算符(select ....);
	3、示例
		1、把攻击值小于 平均攻击值 的名字和攻击值显示出来
			分两步
			select name,gongji from MOSHOU.sanguo 
			where gongji<(select avg(gongji) from MOSHOU.sanguo);
		2、找出每个国家攻击力最高的英雄名字和攻击值
			逻辑错误：
				select name,gongji from sanguo 
				where gongji in
				(select max(gongji) from sanguo group by country);
			正确：
				select name,gongji from sanguo
				where (country,gongji) in 
				(select country,max(gongji) from sanguo group by country);
6、多表查询
	1、两种方式
		1、select 字段名列表 from 表1,表2; 笛卡尔积(不加where)
	2、select 字段名列表 from 表1,表2 where 条件;
		1、显示 省、市详细信息
			select sheng.s_name,city.c_name from sheng,city
			where sheng.s_id=city.cfather_id;
		2、显示 省、市、县详细信息
			select sheng.s_name,city.c_name,xian.x_name from sheng,city,xian
			where sheng.s_id=city.cfather_id and city.c_id=xian.xfather_id;
7、连接查询
	1、内连接
		1、语法格式
			select ... from 表1 inner join 表2 on 条件;
		2、示例
			1、显示 省、市详细信息
				select sheng.s_name,city.c_name from sheng 
				inner join city on sheng.s_id=city.cfather_id;
			2、显示 省、市、县详细信息
				select sheng.s_name,city.c_name,xian.x_name from sheng inner join city 
				on sheng.s_id=city.cfather_id 
				inner join xian
				on city.c_id=xian.xfather_id;
	2、外连接
		1、左连接
			1、以左表为主显示查询结果
			2、语法格式
				select ... from 表1 left join 表2 on 条件;
			3、示例
				1、显示 省、市 详细信息,要求省全部显示
					select sheng.s_name,city.c_name from sheng
					left join city
					on sheng.s_id=city.cfather_id;
				2、显示 省、市、县 详细信息,要求 省 全部显示
					select sheng.s_name,city.c_name,xian.x_name from
					sheng left join city on sheng.s_id=city.cfather_id
					left join xian on city.c_id=xian.xfather_id;
				3、显示 省、市、县 详细信息,要求 市 全部显示(left、right)
					select sheng.s_name,city.c_name,xian.x_name from
					sheng right join city on sheng.s_id=city.cfather_id
					left join xian on city.c_id=xian.xfather_id;
		2、右连接
作业：
1、把 /ect/passwd 文件中内容导入到 db3库下的 userinfo表
	tarena:x:1000:1000:tarena,,,:/home/tarena:/bin/bash
	用户名:密码:UID号:GID号:用户描述:主目录:登录权限
		
​	



# MYSQL_day04

MySQL-Day03回顾
1、索引
  1、普通索引(MUL)、唯一索引(UNI,字段值不重复,可为NULL)
    1、创建
      index(字段名),index(字段名)
      unique(字段名),unique(字段名)
      create [unique] index 索引名 on 表名;
    2、查看
      desc 表名;
      show index from 表名;
    3、删除
      drop index 索引名 on 表名;
  2、主键、自增长(PRI,不能重复,不为NULL,只有1个字段)
    1、创建表 ：id int primary key auto_increment
    2、已有表 ：alter table 表名 add primary key(字段名);
    3、删除
      1、alter table 表名 modify id int;
      2、alter table 表名 drop primary key;
2、数据导入
  1、查看搜索路径 ：show varibles like "secure_file_priv";
  2、复制文件 ：sudo cp 文件名 搜索路径
  3、修改权限 ：chmod 权限 文件名
  4、创建表
  5、数据导入
3、数据导出
  1、查看搜索路径
  2、导出命令
4、表复制
  1、create table 表名 select ... from 表名 where false;
5、嵌套查询(子查询)
  1、把内层的查询结果作为外层查询的条件
6、多表查询
  1、不加where条件
    笛卡尔积：第一张表的所有记录和第二张表第一条记录去匹配...
7、连接查询
  内连接(inner join ... on) : 只显示匹配到的记录
  左连接(left join ... on) : 以左表为主显示查询结果
  右连接(right join ... on): 以右表为主显示查询结果
MySQL-Day04笔记
1、外键(foreign key)
  1、定义 ：当前表字段值从另一个表范围内选择
  2、语法格式
    foreign key(参考字段名)
    references 主表(被参考字段名)
    on delete 级联动作
    on update 级联动作
  3、使用规则
    1、主表、从表 字段数据类型要一致
    2、主表被参考字段 ：主键
  4、示例
    表1、缴费信息表(财务)
        学号  姓名     班级    金额
	  1   唐伯虎  AID1805  300
	  2   点秋香  AID1805  200

    表2、学生信息表(班主任)
        学号  姓名    金额
    
    表1、jftab
      create table jftab(
      id int primary key,
      name varchar(20),
      class char(7),
      money int
      )character set utf8;
      insert into jftab values
      (1,"唐伯虎","AID1805",300),
      (2,"点秋香","AID1805",200);
    表2、bjtab
      create table bjtab(
      stu_id int,
      name varchar(20),
      money int,
      foreign key(stu_id) references jftab(id)
      on delete cascade
      on update cascade)character set utf8;
      insert into bjtab values
      (1,"唐伯虎",300),
      (2,"点秋香",200);
  5、删除外键
    1、查看外键名 ：show create table 表名;
    2、删除外键 ：alter table 表名 drop foreign key 外键名;
  6、级联动作
    1、cascade
      数据级联删除、更新(参考字段)
    2、restrict(默认)
      从表有相关联记录,不允许主表操作
    3、set null
      主表更新,从表相关联记录字段值自动设置为 ：NULL
  8、已有表添加外键
    alter table 表名 add
    foreign key(参考字段名) references 主表(被参考字段)
    on delete ...
    on update ...
2、数据备份(mysqldump,在Linux终端中操作)
  1、命令格式
    mysqldump -u用户名 -p 源库名 > 路径/XXX.sql
  2、源库名的表示方式
    --all-databases   备份所有库
    库名              备份单个库
    -B 库1 库2 ...    备份多个库
    库名 表1 表2 ...  备份指定表
  3、练习
    1、备份所有库为 all.sql , /home/tarena/mydata/
      mysqldump -uroot -p --all-databases > all.sql
    2、备份MOSHOU库中 sheng、city、xian三张表 MOSHOUscx.sql
      mysqldump -uroot -p MOSHOU sheng city xian > MOSHOUscx.sql
    3、备份2个库
      mysqldump -uroot -p -B MOSHOU db4 > MSdb4.sql
3、数据恢复
  1、命令格式
    mysql -u用户名 -p 目标库名 < xxx.sql
    如何要恢复的库不存在则必须先创建空库
  2、示例
    1、恢复MOSHOU库,MOSHOU.sql
      mysql -uroot -p MOSHOU < MOSHOU.sql
    2、恢复MOSHOU库,all.sql
      ## --one-database
      mysql -uroot -p --one-database MOSHOU < all.sql
    3、在MOSHOU库中：
      1、新建一张表 t888 (id)
      2、sheng表中新增一条记录 : 台湾
    4、注意
      1、恢复库时,原库中表中记录会被覆盖,新增的表不会删除
4、事务和事务回滚
  1、一件事从开始发生到结束的整个过程
  2、作用 ：确保数据一致性
  3、事务应用
    1、开启事务
      mysql> begin;
      ## autocommit被禁用,SQL命令不会提交到数据库执行
    2、终止事务
      mysql> commit;  |  rollback;
  4、注意
    事务和事务回滚只针对表记录操作 ：增、删、改有效,对建库建表无效
  5、案例
    1、背景
      你 ：建行卡
      朋友 ：工商卡
      你在建行取款机给你朋友转5000元
    2、过程
      表1、CCB
        create table CCB(
	name varchar(20),
	money int
	);
	insert into CCB values("有钱人",10000);
      表2、ICBC
        create table ICBC(
	name varchar(20),
	money int
	);
	insert into ICBC values("没钱",0);
    3、开始转账
      mysql> begin;
      mysql> update CCB set money=money-5000 where name="有钱人";
      mysql> update ICBC set ;
      mysql> rollback;
6、MySQL存储引擎(处理表的处理器)
  1、基本操作
    1、查看所有存储引擎
      show engines;
    2、查看表存储引擎
      show create table 表名;
    3、指定存储引擎
      create table 表名(...)engine=innodb,character set utf8;
    4、修改表存储引擎
      alter table 表名 engine=myisam;
    5、工作中常用
      InnoDB  MyISAM
  2、修改表默认存储引擎
    1、sudo -i
    2、cd /etc/mysql/mysql.conf.d/
    3、cp mysqld.cnf mysqld.cnf.bak
    4、vi mysqld.cnf
       [mysqld]
       default-storage-engine=myisam
    5、/etc/init.d/mysql restart
7、锁
  1、目的 ：解决客户端的并发访问的冲突问题
  2、锁的分类
    1、锁类型
      读锁(select)共享锁 ：加读锁后其他用户只能查询,不能修改
      写锁(增删改)互斥锁、排他锁 ：其他用户不能做任何操作
    2、锁粒度
      表级锁 ：加读锁或者写锁
      行级锁 ：加读锁或者写锁
8、存储引擎特点
  1、MyISAM特点
    1、独享表空间
      表名.frm 表结构 
      表名.myd 表记录
      表名.myi 索引文件
    2、支持表级锁
  2、InnoDB特点
    1、共享表空间
      表名.frm 表结构和索引信息
      表名.ibd 表记录
    2、支持行级锁
  3、memory
    表结构存储在硬盘里,表记录存储在内存中
    表名.frm
    服务重启后表结构还在,表记录都消失
  4、如何决定表使用什么存储引擎
    1、主要用来查询的表用MyISAM
    2、写操作多的表用InnoDB
9、MySQL调优
  1、选择合适的存储引擎
  2、创建索引
    在SELECT、WHERE、ORDER BY常涉及的字段建立索引
  3、SQL语句优化
    1、where条件判断尽量不使用 != ,否则放弃索引全表扫描
    2、尽量避免NULL值判断,否则放弃索引全表扫描
      优化前：select id from t1 where id is null;
      优化后：在 id 字段上设置默认值0,确保id字段没有NULL值
              select id from t1 where id=0;
    3、尽量避免用 or 来连接条件,否则放弃索引全表扫描
      优化前：select id from t1 where id=10 or id=20;
      优化后：
        select id from t1 where id=10
	union all
	select id from t1 where id=20;
    4、模糊查询尽量避免使用前置%,否则放弃索引全表扫描
      select name from t1 where name like "c%";
    5、尽量避免使用in 和 not in,否则放弃索引全表扫描
      优化前：select id from t1 where id in(1,2,3,4);
      优化后：... where id between 1 and 4;
    6、尽量避免使用 * ,用具体的字段代替*,不要返回用不到的任何字段
10、与python交互
  1、交互类型
    python3 : pymysql  $ sudo pip3 install pymysql
    python2 : MySQLdb  $ sudo pip install mysql-python
  2、connect对象
    1、创建与数据库连接的对象(调用connect()方法)
      conn = pymysql.connect(参数列表)
      参数列表：
        1、host ：主机地址
	2、port ：端口3306
	3、db   ：数据库名
	4、passwd：密码
	5、charset：编码方式,推荐使用utf8
	6、user ：用户名
      示例：
        conn = pymysql.connect(host="localhost",user="root",passwd="123456",db="db4",charset="utf8")
    2、连接对象(conn)的方法
      1、close() 关闭连接
      2、commit() 提交到数据库执行
      3、rollback() 回滚
      4、cursor() 创建游标对象,用于执行sql语句
    3、游标对象
      1、作用 ：执行sql语句
      2、示例 ：
        cur = conn.cursor()
        cur.execute("delete from sheng;")
      3、常用方法
        1、execute(SQL命令,[SQL语句补位元素]) 执行SQL命令
	2、fetchone() 获取结果集第一条记录
	3、fetchmany(n) 获取n条记录
	4、fetchall() 获取所有记录    
    5、pymysql使用流程
      1、建立数据库连接 conn
      2、创建游标对象 cur = conn.cursor()
      3、cur.execute("...")
      4、提交：conn.commit()
      5、关闭游标：cur.close()
      6、断开连接: conn.close()
11、ER模型(Entry-Relationship)
  1、定义
    实体-关系模型,用于数据库设计
  2、三个概念
    1、实体 ：矩形框
    2、属性 ：椭圆形
    3、关系 ：实体之间的关系
      1、一对一关系(1:1) ：老公对老婆
      2、一对多关系(1:n) ：父亲对孩子
      3、多对多关系(m:n) ：兄弟姐妹对兄弟姐妹



			


			
​				






		





















			




