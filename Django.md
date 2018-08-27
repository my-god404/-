# day01

1.jQuery动画
	1.基本显示 / 隐藏
		$obj.show() / $obj.show(执行时长);
		$obj.hide() / $obj.hide(执行时长);
	2.滑动式显示 / 隐藏
		$obj.slideDown() / $obj.slideDown(执行时长);
		$obj.slideUp() / $obj.slideUp(执行时长);
	3.淡入淡出式显示 / 隐藏
		$obj.fadeIn() / $obj.fadeIn(执行时长);
		$obj.fadeOut() / $obj.fadeOut(执行时长);
2.jQuery插件
	1.下载插件并引入(jquery,插件文件,css文件)
	2.结合当前网页修改css

3.去插件中修改数据(替换图片/图片名称)

Django 框架
1.WEB 与 服务器
		1.WEB : 表示用户可以浏览的网页内容(HTML,CSS,JS)
		2.服务器 
			专门给用户提供服务的一台机器
			1.硬件与软件
				硬件范畴:一台机器
				软件范畴:一个能够接受用户请求并给出响应的程序
					1.APACHE
					2.TOMCAT
					3.IIS(Internet Information Service)
					4.Nginx
			2.服务器的作用
				1.存储WEB上所需要的信息(HTML,图片,js,css,音视频)
				2.处理用户的请求(request)并给出响应(response)
				3.执行服务器端的程序 : 查找数据库
			3.服务器 与 WEB之间的关系
				WEB需要放在服务器上才能够被用户访问
2.框架
	1.什么是框架
		框架是一个为了解决开放性问题而存在的一种结构.框架本身会提供一些最基本的功能.我们只需要在基本功能之上搭建属于自己的操作即可.
	2.PYTHON WEB 框架
		1.Django : 重量级的WEB框架
		2.Tornado : 异步框架
		3.Flask : 轻量级框架
3.Django 框架
	1.什么是Django
		是一个开源框架,2005年发布,采用Python语言编写的.早期是做新闻和内容管理的网站的.Django本身提供了强大的后台管理系统.
	2.Django的框架模式 - MTV
		M : Models 层
			模型层,负责数据库建模以及CRUD的操作
		T : Templates 层
			模板层,处理用户显示的内容的,比如:html
		V : Views 层
			视图层,处理与用户交互的部分内容


		MVC : 三层架构
			M:Models,模型层,与数据库打交道
			V:Views,视图层,处理用户显示的内容的
			C:Controller,控制器层,处理与用户交互的部分内容
		MTV            MVC
		M    ....      M
		T    ....      V
		V    ....      C
	3.Django的官方介绍
		官网:http://www.djangoproject.com
		中文文档:http://djangobook.py3k.cn/2.0/
4.Django 框架的使用
	1.安装Django框架	
		1.查看已安装的Django版本
			1.进入到终端以及python交互模式
				python3 / ipython3
			2.交互模式中 输入 import django
				如果未报错:当前环境下已经安装好Django
				如果报错:当前环境未安装过Django
			3.查看已安装的版本
				交互模式中:django.VERSION
		2.安装
			1.在线安装 - 使用 pip / pip3
				sudo pip3 install django
				(安装Django的最新版本)

				sudo pip3 install django==1.11.8
				(安装Django的指定版本)
			2.离线安装
				1.下载Django包
				2.在环境下解压Django包
					tar -xvf Django-1.11.8.tar.gz
				3.进入到目录中,找到 setup.py 文件
					sudo python3 setup.py install
	2.使用Django
		1.创建目录
			用于保存所有的Django项目
			mkdir Django
	
			使用 django-admin 指令创建Django项目
			语法:django-admin startproject 项目名
		2.启动服务,访问网站
			在项目中找到 manage.py
			通过manage.py启动项目(服务)
			python3 manage.py runserver
		3.访问网站
			启动服务之后,浏览器访问
			http://localhost:8000
			http://127.0.0.1:8000
	3.Django 项目结构介绍
		1.manage.py
			负责执行Django中的各项操作
			如:
				启动服务:runserver
				创建应用:startapp
				... ...
		2.主目录(目录名称与项目名称一致)
			1.__init__.py
				项目的初始化文件,服务被启动时,该文件自动被执行
			2.urls.py
				项目的基础url配置文件(路由配置文件)
			3.wsgi.py
				应用服务器配置文件
			4.settings.py
				项目的配置文件
				1.BASE_DIR:获取当前项目的绝对路径
				2.DEBUG : 调试模式
					开发过程:推荐使用 True
					上线运行:必须改为 False
				3.ALLOWD_HOSTS
					设置允许访问本项目的地址列表
					如果为空,只有本机能访问(localhost/127.0.0.1)
					推荐写 ['*'],任何表示该机器的地址都可以访问当前项目
	
					如果允许被其他机器访问的话,启动服务时,必须使用以下方式:
						./manage.py runserver 0.0.0.0:端口号
				4.INSTALLED_APPS
					指定已安装的应用,如果有自定义应用的话,需要在此注册
				5.MIDDLEWARE
					注册中间件
				6.ROOT_URLCONF
					指定项目的基础路由配置文件
				7.TEMPLATES
					指定模板的信息
				8.DATABASES
					指定数据库的信息
				9.LANGUAGE_CODE
					语言设置,如果需要中文的话,允许将值更改为 "zh-Hans"
	
				10.TIME_ZONE
					指定时区,建议修改为 "Asia/Shanghai"
	4.URL的使用
		1.urls.py
			默认在主目录中,主路由配置文件,包含所有的地址映射
		2.测试
			1.在主目录中,创建 views.py
				作用:包含所有定义好的视图(处理程序)
	
		3.url 函数
			作用:为了匹配用户的访问路径
			语法:
				url(regex,views,kwargs=None,name=None)		
					1.regex:允许是正则表达式,匹配请求的url的
					2.views:对应的视图处理函数
					3.kwargs:字典,用来向views传参的,如果没有参数的话则可以省略
					4.name:字符串类型,为url起别名,在地址反向查询时使用
		4.通过url向视图传参
			http://localhost:8000/run/15
			http://localhost:8000/run/26
			http://localhost:8000/run/78
			1.使用正则表达式传参
				使用子组传参,一个子组是一个参数,要传递多个参数的话使用多个子组
				子组 - ()
	
				urlpatterns = [
					# 访问路径是run/的时候,交给run_views去处理
					url(r'^run/$',run_views),
					# 访问路径是run/两位数字的时候,交给run1_views去处理
					url(r'^run/(\d{2})/$',run1_views),
					# 访问路径是run/四位数字/两位数字的时候,交给run2_views去处理
					url(r'^run/(\d{4})/(\d{2})/$',run2_views),
				]
	注意:
	1.url()中,一个子组表示一个参数
	2.在views中,对应的处理函数要根据url()中子组的个数,相应的定义参数.定义的参数要位于request之后







# day02



1. url ()

   1. 注意

      如果一个访问路径能够匹配到多个url( )的时候，那么只能匹配的第一个url ( )去执行

   2. url 传参

      1. 通过正则的子组传参

      2. 使用 url ( )第三个参数 - 字典传参

      3. dic = {

         	'name' : 'sa.zh',

         	'age': '25'

         }

         url(r'^show/$', show_views,dic)

      views.py

      def  show_views(request, name, age):

      	pass

2. Django 中的应用

   1. 什么是应用

      应用就是网站中一个独立的模块程序

      在Django中，主目录一般不处理用户的具体请求，主目录主要做的是项目的初始化以及请求的分支，而具体的请求由各个应用去处理

   2. 创建应用

      1. 指令

         ./manage.py  startapp   应用名称

         ex:

         ```
         ./manage.py startapp news
         ```

      2. 在settings.py 中进行注册

         在 INSTALLED_APPS 中追加应用名称

         INSTALLED_APPS = [

         	'django.contrib.admin',
      		
         	...  ...,
      		
         	'自定义应用名称'

         ]

      3. 练习

         1. 创建新项目  - netease
         2. 创建 index 应用,并注册
         3. 创建 sport 应用,并注册
         4. 创建 music 应用，并注册
         5. 创建 news 应用，并注册

   3. 应用的结构组成

      1. migrations 目录

         存放的是数据库的中间文件

      2. `__init__`.py

         应用的初始化文件

      3. admin.py

         应用的后台管理配置文件

      4. app.py

         应用的属性配置文件

      5. models.py

         Models 与模型相关的配置文件

      6. tests.py

         测试模块

      7. views.py

         定义视图的文件

      #交给music 应用去处理（转交给music 的 urls)

      from dango.conf.urls import include

      #url(r'^music/', include('music.urls')),

      http://localhost:8000/music/****

      #交给music 应用中的 index_views 视图去处理

      http://localhost:8000/sport/****

      #交给 sport 应用去处理(转交给sport的urls)

      http://localhost:8000/sport/****

      练习：

       1. 访问路径 localhost:8000/news/index

          转交给 new 的 urls 再找到 index_views 处理

          2. 访问路径 localhost:8000/sport/index

          转交给sport 的urls再找到index_viewss处理

          3. 访问路径 localhost:8000/index/index

          转交给 index 的 urls 再找到index_views处理

3. Django 中的模板 (Templates)

   1. 什么是模板

      1. 模板就是要动态呈现给用户的网页内容
      2. 模板的本质就是网页 - 前后端结合的网页

   2. 模板的设置

      在 setting.py 中,TEMPLATES 变量

      1. BACKEND：指定模板的存放目录们

         如果DIR中为空的话，那么Django会自动的到每一个应用中搜索一个叫

         templates 的目录作为模板存放目录

      2. APP_DIRS

         True: 优先从DIRS指定的目录中查找模板，如果没找到的话，再搜索应用中的、templates 目录

   3. 模板的加载方式

      1. 使用 loader 获取模板， 通过HttpResponse 进行响应 

         from django.template import loader

         def index_views(request):

          1. 通过loader 加载模板

             t = loader.get_template("模板名称")

          2. 将模板渲染成字符串

             html = t.render( )

          3. 通过 HttpResponse 响应给客户端

             return  HttpResponse(html)

      2. 使用 render 直接加载并返回模板

         ```
         def index_views(request):
         	return render(re)
         
         ```

   4. 模板的语法

      1. 变量

         1. 作用：允许将后端的数据传递给模板在模板中进行显示

         2. Django中允许作为变量传递给模板的数据类型

            字符串，数字，列表，元组，字典，函数，对象

         3. 变量的语法

            变量们必须封装到字典中才能传递给模板

            1. 使用 loader 加载模板

               dic = {

               	'变量1' ：'值1'，
			
               	'变量2' ：'值2'，
			
               	...         ...

               }

               t = loader.get_template('模块名称')

               #渲染成字符串时需要传递变量字典到模板中

               t.render(dic)

            2. 使用render 加载并返回模板

               dic = {

               	'变量1' :  '值1'，
			
               	'变量2' :  '值2'，

               }

               return render(request,"模板名称",dic)

         4. 在模板中使用变量

            {{变量名}}

      2. 标签

         1. 作用：

            将服务器端的功能嵌入到模板中

         2. 语法

            {% 标签内容 %}

         3. 标签详解

            1. comment标签

               {% comment %}



               {% endcomment %}
    
               作用：在服务器就被注释的内容，不会被渲染到客户端
    
            2. for 标签
    
               1. 作用：循环遍历 列表，字典，元组
    
               2. 语法：
    
                  {% for 变量,}





# day03

1. 模板

   1. 过滤器

      在显示变量数据之前，对数据进行过滤筛选

   2. 过滤器的语法

      {{变量 | 过滤器}}

      1{{value | upper}}

      	将value变为大写

      2. {{value | lower}}

         将value 变为小写

      3. {{value | add:num}}

         将num累加到value后

      4. {{value | floatformat :n}}

         将value四舍五入到n位小数

      5. {{value | truncatechars:n}}

         将value截取保留至n位字符(包含...)

   3. 静态文件

      1. 什么是静态文件

         在Django中，不被解释器动态解析的文件

         如:图片, js , css, 静态的html

         在Django中，物理路径是无法找到静态文件的

      2. Django中静态文件的处理

         需要在 settings.py中设置有关静态文件的信息:

          1. 设置静态文件的访问路径

             SRATIC_URL=' /static/ '

             ex : 

             	http://localhost:8000/static/xxx

          2. 设置静态文件的存储路径

             STATICFILES_DIRS = (os.path.join(BASE_DIR,'静态文件目录名'))

             STATICFILES_DIRS=(os.path.join(BASE_DIR,'static'))

             静态文件目录存放位置:

             1. 所有应用中创建一个  [同名目录]('静态文件目录名')
             2. 项目的根目录处创建一个  [同名目录]('静态文件目录名')

         	3. 访问静态文件

             	1. 直接使用 静态文件访问路径 进行访问

                 ```
                 http://localhost:8000/static/...
                 <img src="/static/...">
                 	<img src="/static/images/admin.png">
                 	<img src="http://localhost:8000/static/images/admin.png">
                 ```

             	2. 使用 {% static %}访问静态资源

                		{% static %}表示的就是静态资源的访问路径

                  1. 在模板的最顶层增加

                     {% load static %}

                		2. 在使用静态资源时

                     <img src="{% static 'images/list_filter.png'%}"

                 练习:

                  1. 创建一个项目 - fruitday

                  2. 创建一个应用 - index

                  3. 配置主路由 和 应用路由

                  4. 在 index 中配置首页的 url 和模板

                     url : /

                     模板 : index.html (配置好所有的静态文件)

                     	静态文件:图片,css

# day04

### 模型 - Models

1. 什么是模型

   模型，是根据数据库中数据表的结构来创建出来的class,每一张表对应到编程语言中就是一个class。表中的每一个列，到编程语言中就是class中的一个属性。

2. 创建 和 使用模型 ORM

   1. 什么是ORM

      ORM : Object  Relational  Mapping

      简称: ORM, O/RM, Mapping

      中文: 对象关系映射

      三大特征:

      1. 数据表 到 类(class)的映射

         允许将数据表 (Table) z=自动生成一个类(class)

         允许将类(class)自动生成一个数据表(Table)

      2. 数据类型的映射

         允许将表中字段类型 自动 映射成编程语言中对应的数据类型

         允许将编程语言中的数据类型自动 映射成表中字段对应的数据类型

      3. 关系映射

         允许将表与表之间的关系 自动 映射成类与类之间的关系

         允许将类与类之间的关系 自动 映射成表与表之间的关系

   2. ORM的优点

      1. 提高了开发效率，能够自动完成表与类之间的映射
      2. 可以省略庞大的数据访问层，即便不用SQL编码，也能完成对数据库的CRUD操作

   3. 创建 和 配置 数据库

      1. 创建数据库 (支持中文)

         create  database  数据库名 default

         charset  utf8  collate  utf8_general_ci;

      2. Django 中数据库的配置

         在 settings.py 中配置数据库的信息

         DATABASES = {

         	'default' :{

         		'ENGINE' : '...',

         		'NAME' : '...',

         	}

         }

         连接MySQL数据库的配置：

          1. ENGINE ： 连接到数据库的引擎(驱动程序)

             ```
             django.db.backends.mysql
             ```

         	2. NAME : 要连接的数据库名称

         	3. USER : 用户名称，通常为 root 

         	4. PASSWORD : 密码，

         	5. HOST : 要连接的主机

             主机:localhost 或 127.0.0.1

         	6. POST :指定端口号

             MYSQL:3306

         注意：

         	Django 中要连接 MySql 数据库的话依赖于 MySQLdb

         	通过 pymysql 解决该问题

         		sudo pip3  install  pymysql == (版本号)

         		在项目的主目录中的 __ init __.py:

         			import  pymysql

         			pymysql.install_as_MySQLdb()

   4. 数据库的同步操作

      1.  ./manage.py  makemigrations

         作用：将每个应用下的 models.py 文件生成一个数据库的中间文件，并将中间文件保存在migrations 的目录中

      2.  ./manage.py migrate

         作用：将每个应用下的 migrations 目录中的中间文件同步到数据库中

         编写Models(重难点)

   #### 1.注意

   Models 中的每个class都称为 模型类(Model) 或 实体类(Entry)

   	实体：表示的就是数据库中表中的一条记录

   	实体完整性:约束表中的记录不完全重复

   Models中的每个类都必须继承自 models.Model

   #### 例题

   在 index 应用中 的 models.py 中

   ```
   from django.db import models
   # 创建 Publisher 实体类
   # 表示 出版社 的信息，属性如下:
   # 1. name:出版社的名称(varchar)
   # 2. address: 出版社的地址
   # 3. city:出版社所在城市
   # 4.country:出版社所在国家
   # 5.website:出版社的网址
   class Publish(models.Model):
   		# 1. name: 出版社的名称(varchar,string)
   	name = models.CharField(max_length=30) 名字长度最大30
   		# 2. address:出版社的地址(字符串，长度50)
   	address = models.CharField(max_length=50)
   		# 3. city:出版社所在城市(字符串，长度20)
   	city = models.CharField(max_length=20)
   		# 4. country:出版社所在国家(字符串，长度20)
   	country = models.CharField(max_length=20)
   		# 5. website:出版社的网址
   	website = models.URLField()
   ```
