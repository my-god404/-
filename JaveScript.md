---

---

# day01



赵旭

zhaoxu@tedu.cn

1. JavaScript
2. Django
3. AJAX
4. PROJECT

---

---

1. JaveScript 概述

   1. 什么是JS

      是一种专门运行于JS解释器/

      引擎中的解释型脚本语言

   2. 发展史

      1. 1992年CMM （c--) , 更名为 ScriptEase

      2. 1995 年 LiveScript , 更名为 JaveScript

      3. 1996 年 JScript 

      4. 1997 年 网景 找到了 ECMA (欧洲计算机制造商联合会)

         网景将 JS 的核心模块交给了 ECMA ,从此 JS 的核心更名为 ECMA Script , 简称 ES

         JS 的组成：

         1. 核心 - ECMA Script

            包含了JS中最基本的语法规范

         2. 浏览器对象模型 - BOM 

            Browser  Object  Model

            允许JS操作浏览器

         3. 文档对象模型 - DOM

            Document Object Model

            允许 JS 操作 HTML 中的内容

2. JS 的使用方式 （重点）

   1. 浏览器控制台中输入代码并执行

      测试时使用

      console.log( "要输出的内容" );

   2. JS的使用方式

      1. 在元素事件中编写JS代码

         事件 ： 用户在元素上所激发的一些操作

         onclick: 当用户点击元素时要做的操作

         语法 ：

         ​	<ANY onclick="JS执行代码">

         ​	<button onclick="console.log('点你咋的');">点我试试</botton>

      2. 将代码嵌入在网页的<script></script>标记中

         在网页的任意位置处，都可以嵌入一个<script></script>标记

         语法： 

         ​	<script>

         ​		JS可执行代码

         ​	</script>

         注意：

          	1. 一个网页中允许有若干对 script
         		2. script 标记有顺序之分，先写的先被执行
         		3. 网页加载时就执行

         document.write("<h1>向网页中输出一句话</h1>");

      3. 在网页中，引入外部的JS文件

         1. 创建一个js 文件，xxx.js ,并编写js代码

         2. 在网页上对js 文件进行引入

            <script 	src="js文件路径"></script>

            ​	注意：1.  script 标记必须成对

            ​	2. 在引入的标记中不允许编写其他的 js 脚本

   3. JS 的基础语法

      1. JS都是由语句组成的

         1. 由运算符，关键字 或表达式组成

         2. JS 中严格区分大小写

            console.log ('xxx' ); 正确的

            Console.log ('xxx'); 错误的 c 不能大写

         3. 每条语句必须以 ； 表示结束

      2. 注释

         单行 ：//

         多行 : / * * /

   4. JS中的变量 和 常量 

      1. 声明变量

         声明：var 变量名；

         赋值：变量名=值；

         声明并赋值：var  变量名=值；

         e.g.:

         ​	var	uname="王小明";

         ​	console.log( uname );

         ​	同时声明多个变量

         ​	var uname="隔壁老王"，uage=35，ugender;

         注意：

           1. 声明变量时，尽量使用 var 关键字，如果省略，也可以，但容易出问题
              2. 声明变量如果未赋值的话，默认值为underfined
                3. 使用未声明过的变量的话，则为语法错误

                

      2. 变量名的命名规范

         1. 变量名不能是JS中的关键字或保留关键字

         2. 由字母，数字，下划线_ 以及$ 组成

            var $ = 35;

            var _age = 46;

         3. 不能以数字开头

         4. 尽量不要重复

         5. 尽量要见名知意

         6. 如无特殊需求的话，尽量使用小驼峰命名法

            强调：

            ​	不能使用 name 作为变量名

      3. 变量的使用

         1. 为变量赋值

            只要变量出现在赋值符号的左边，一律是赋值操作

         2. 获取变量的值

            只要变量没出现在赋值符号的左边一律是取值

            var 	age = 35;  // 赋值

            console.log( age ); // 取值

            var newAge = age; //

            newAge : 赋值 ， age : 取值

            age = age + 35;

      4. 常量

         1. 什么是常量

            一经声明就不允许被修改的数据就是常量

         2. 语法

            const 常量名=值；

            注意：

               	1. 常量声明好之后是不允许修改的，所以一定要赋初始值
                 2. 常量通常采用全大写形式

      5. 数据类型

         JS中的数据类型可以分为两大类

         1. 基本数据类型

            1. number   类型 

               数字类型，可以表示32位的整数以及64位的浮点数

               整数：

               ​	十进制：var num=30;

               ​	八进制 ： var num=010;

               ​	十六进制 ： var  num=0x21;

               ​	注意 ：以上数字在打印的时候都是按照十进制值打印输出的

               小数：

               ​	小数点计数法： var num=123.456;

               ​	指数计数法：var num=1.4e2;

            2. string 类型

               字符串类型

               注意：使用时，必须使用" " 或 ' ' 引起来

               JS中的字符串由Unicode 字符，数字，标点组成

               1. 查看字符 的 Unicode 码

                  var str="张"；

                  var uCode = str.charCodeAt().toString(16);

               2. 如何将 Unicode 码转换成对应的字符

                  已知Unicode 码 ：5f20

                  var str = "\u 5 f 2 0" ;

                  console.log(str); // ”张“

               3. 中文范围

                  "\u4e00" ~ "\u9fa5"

               4. 转义字符

                  \n: 换行

                  \t : 一个制表符

                  \":"    （\双引号 

                  \':'	（\单引号

                  \ \:\	（\

            3. boolean 类型

               布尔类型，只用于表示真 (true) 或假 (false)  注意 ： 都是小写

               注意 ： boolean 类型可以参与到数字运算，true 当成1运算，false 当成0去运算

               var r = true + 1 ; // 2

               var r = 3358 * false; //0

            4. 查看数据类型

               使用 typeof( ) 或 typeof     		typeof() 表示函数，没有区别

               查看变量的数据类型

         2. 引用数据类型

      6. 数据类型转换

         1. 隐式转换

            大部分加法运算时，如果数据类型不一致的话可以进行隐式转换

            1. 数字 + 字符串：将数字转换为字符串

               var  num = "15";  // number

               var  str  = "18"  // string

               var  r = num  + str ;  // 1518

               var r = "15" + 18 +15 ;  // 151815

               var r = 15 + 18 +"15";  //  3315

            2. 数字 + 布尔 ：将布尔类型转换为  number 

               var  r = 35 + true;  // 36

            3. 字符串  +  布尔 ：将布尔转换为字符串

               var  r = "你好"  + true;  //你好 true

            4. 布尔 + 布尔：

               两个 布尔

               在一起的任何运算都是 将布尔先转换为 number  再做数值的运算

               注意：

                	如果 - ， * ， +， % 两端都是数字格式的字符串的话，是可以按照数字的方式进行运算的

               ​	"35" - "48" :13

               ​	"35" - "你好" : NaN（Not A Number)

         2. 显示转换

            1. toString( ) 

               作用 ：将任意类型的数据转换成字符串，并返回转换后的结果

               var num =15 ;// number

               var r = num.toString();

                var  num = 15;

               var r = num + "";

            2. parseInt ()

               作用 ： 将任意类型的数据类型尽量转换成整数，如果实在无法转换的话，则返回 NaN

               e.g.

                1. var r = parseInt( " 13 ") ;

                   r = 13 (number)

                   2. var r = parseInt("13.5");

                   结果 ：13

                   3. var r = parseInt("13你好");

                   结果 ： 13

                   4. var r = parseInt("你好13");

                   结果 ：NaN

            3. parseFloat()

               作用：尽量将任意类型的数据转换为小数

               e.g.

                1. var r = parseFloat("35.7");

                   r : 35.7

               	2. var r = parseFloat("35.7你好")；

                   r : 35.7

               	3. var r = parseFloat ("你好35.7");

                   r : NaN

            4. Number()

               作用：将指定的数据转换为数字，只要包含非法字符的话，结果就为 NaN

               e.g.

                1. var r = Number("35.7");

                   r : 35.7

               	2. var r = Number("35.7你好")；

                   r : NaN

               练习：

                1. 创建网页 完成练习

                2. 在网页中弹出一个输入提示框

                   widdow.prompt ("提示文字")；

                   input 变量中，保存的就是用户输入的数据

               	3. 在输入框中输入一个数字

               	4. 将输入的数据 + 10， 打印计算后的结果

               	5. 根据步骤 4输出的结果，使用typeof 查看输入数据的数据类型

               	6. 将输入的数据转换为数字 再 + 10 查看结果

               注意 : 

               ​	只要是在网页中获取的数据，一律都是字符串类型

      7. 运算符

         1. 算术运算符

            +, -, *, /, %, ++(自增)，-- (自减)

            +:加法，拼接

            /: 5/2 结果 ：2.5

            % : 3%5 结果：3

            ​	场合：

              1. 倍数  或 奇偶性

              2. 获取某数字的最后几位

                 var num = 1234; 

            ++ ： 自增运算符，在自身数据基础上只做+1 操作

            -- ： 自减运算符，在自身数据基础上只做-1 操作

            语法：

            ​	变量 ++  或 ++ 变量

            ​	变量 -- 或 -- 变量

            ++ 做后缀： 变量 ++

            ​	要先使用变量的值，再对变量进行自增

            ​	var num =5;

            ​	//先输出num 的值，再对 num +1

            ​	console.log(num++); //5

            ​	console.log(num); //6

            ​	console.log(num++);  等同于 console.log(num) ; num ++ 1;

            ++ 做前缀  ：++ 变量

            ​	先对变量进行自增 ， 再使用变量的值

            ​	var num = 5;

            ​	// 先对num 进行+1 ，再打印输出

            ​	console.log(++num);  //6

            ​	console.log(++num);  等同于 num +=1;   console.log(num);

```
练习:
				1.
					var num = 5;
					console.log(num++);//输出5 变为6
					console.log(++num);//变为7 输出7
					console.log(++num);//变为8 输出8
					console.log(num++);//输出8 变为9
					console.log(num); //输出 9
2.
var num = 5;
             5     (6)6    6(7)    7(8)    (9)9
var result = num + ++num + num++ + num++ + ++num;

结果4:33
```

#  day02



1. 运算符

   1. 算术运算符

      +, -, *, /, %, ++, --

   2. 关系运算符（比较运算符）

      只要是使用关系运算符比较出来的结果一定是Bollean

      : > ,<, <=, >=, == , !=, === , ! ==

      1. 10>5  :true

      2. "3" > 5   :true

      3. :"10" > 5    : false

      4. "10a" > 5 : false

         1. 先将10a 通过 Number () 转换，结果为 NaN

         2. 使用 NaN 与 5 进行比较

            NaN 与任何数据做 != , 结果都为 true

            NaN 与 任何数据除了 !=, 结果都为 false

      5. "10a"  < 5 : false

      6. " 张三丰 "  > " 张无忌 "  ： false 

         比较每位字符 的 Unicode 码

         最终比较的是 "三" 和 " 无 " 的大小关系

         "三" ：19977

         "无" ：26080

      7. "10" > "5"  : false

      8. "10"  < "5"  :true

      9. "50" > "5" : true

      10. "49" > "5" :false

      ===  ,  ! ==

      "3" == 3 : true

      === : 比较的数据和数据类型必须都相等的情况下，整个结果才为真

      "3" === 3  : false

      !== : 比较的数据和数据类型只要一个不相等，结果就为true

      "3" !== 3 : true

   3. 逻辑运算符

      判断数字 n , 是否大于3 小于5

      运算符 ： ! ,  &&,  || 

      !  :  等同于 python  中的 not 对现有条件取反   非真即假，非假既真

      && : 等同于 python  中的 and 关联两个条件 ，起到并且 的作用

      ​	关联的两个条件必须同时都为真的时候，整个结果才为真，否则结果为假

      || :  等同于 python 中的 or 关联两个条件，起到 或者 的作用

      ​		关联的两个条件中，只要有一个为 true 的话， 整个结果就为true, 只要两个条件同时都为 false 的时候 ，整个表达式的结果才为 false 

      练习1 :

       1. 创建一个网页

       2. 从弹框中录入一个数字，表示年份

       3. 判断该年份是否为闰年并输出结果 ( true 或 false)

          闰年 ： 能被4整除但不能被100整除或能被400整除的年份都是闰年

      练习2

      ​	从弹框中录入1 个字符，判断该字符是英文? 中文 ? 数字 ?

      从弹框中录入 ： k

      是数字吗 ? false

      是英文吗 ? true

      是中文吗? false 

   4.  位运算符

      1. 按位与 ： &

         3  &  5

         二进制  3  : 11

         ​	     5 : 101

         ---

         ​		 001

         ​	使用场合 ： 判断一个数字的奇偶性

         任意数字与1做按位与操作，结果为1是奇数，结果为0是偶数

      2. 按位或：｜

         ５｜３：

         ５：１０１

         ３：０１１

         ---

         ​	1  1   1

         使用场合：任意小数与0做按位或操作，快速取整（抛弃小数位，保留整数位）

      3. 按位异或 ： ^

         3 ^ 5:

         3 : 011

         5 : 101

         ---

         ​    110 

         var a  = 3 ;

         var b = 5;

         a = a ^ b;

         b = a ^ b;

         a = a ^ b;

         a = 5;

         b = 3;

         使用场合 ：在不借助第三方的场合下，交换两个变量

   5. 条件运算符

      单目运算符 / 一元运算符 ： 只有一个操作数的运算符

      ​	如 ： ++ ， --， !,   typeof , -

      双目运算符  /   二元运算符 ： 有两个操作数的运算符

      ​	如 ： +, -, *, /, %, &&, ||, &, |, ^, >, <, ....

      三目运算符 /  三目运算符 ： 有三个操作数的运算符

      ​	如 ： 条件运算符 ？： 

      语法 ： 

      ​	条件表达式 ？ 表达式1 ：　表达式２；

      先判断条件表达式得结果，如果为　ｔｒｕｅ　，则执行表达式１的内容，否则，执行表达式２的内容

      ｉｆ　条件表达式：　

      ​	表达式１

      ｅｌｓｅ：

      ​	表达式２

      练习：BMI 指数计算

      ​	要求从弹框中录入身高(m)

      ​	要求从弹框中录入体重(kg)

      ​	BMI = 体重 /  (身高*身高)

      ​	如果 BMI 小于 18.5 属于 偏瘦

      ​	如果 BMI 大于 23.9 属于 偏胖

      否则 ： 正常

2. 流程控制

   1. 程序的流程结构

      1. 顺序结构
      2. 分支结构（选择结构)
      3. 循环结构

   2. 分支结构

      1. if 结构

         1. if (条件){

            ​	语句块；

            }

            注意： 

            1. 条件不是bollean 的话，以下情况视为  false 

               if (0.0) {}

               if (0) {}

               if ("") {}

               if (underfined) {}

               if (null) {}

               ---

               if (35.5) {真}

            2. if结构可以省略 {}

               如果省略的话，if则只能控制它下面的第一条语句

         2. if (条件){

            ​	语句块1

            }else{

            ​	语句块2

            }

         3. if(条件){

            ​	语句块

            }else if(条件n){

            ​	语句块n

            }else{

            ​	语句块n+1

            }

            练习：

            ​	分三次从弹框中录入年，月， 日计算该日是该年的第?天

      2. switch 结构

         特点： 只能用在等值判断的场合

         语法 :

         ​	switch( 变量 ){

         ​		case 值1：

         ​		语句块1

         ​		break;//可选，跳出switch 结构

         ​		case 值2 ：

         ​			语句块2

         ​			break;//同上

         ​			....

         ​		default :

         ​			语句块n

         ​			// 当所有的switch 都未匹配上的时候才会执行 default

         ​			//default  块是可选的

         ​	}

         ​	注意：

           		1. 变量和 各个case 块后面的值， 是采用 == 的方式来匹配的
           		2. 如果case 后面不增加break 的话，则从匹配的case 

      3. 循环结构

         1. 循环作用

            重复的执行相同或相似的代码

         2. 循环二要素

            1. 循环条件
            2. 循环操作

            e.g. :

             1. 想打印100遍Hello World

                条件：从1开始，到 100 结束

                操作 ： 打印 Hello  World

            	2. 想打印1 - 100 之间所有的数字

                条件：从1 开始，到 100 结束

                操作：打印 条件 的值

         3.  while  循环

            1. 语法

               while(条件){

               ​	循环操作

               }

            2. ex

               1. 打印100遍的Hello World

               练习：

                1. 打印1-100之间所有3的倍数的数字

                2. 打印  九九乘法表中的某一行

                   从弹框中录入一个数字，录入的是几，就打印第几行

         4. do ... while 循环

            1. ex 

               循环的从弹框中录入数据，并将录入的数据打印在控制台上，直到输入exit 为止

            2. 语法

               do {

               ​	循环操作

               }while(条件);

            3. 流程

               1. 先执行循环操作
               2. 再判断循环条件
               3. 如果条件为真，则继续执行循环操作，否则退出循环

         作业：分三次输入年，月，日

         ​	判断该日是星期？

         ​	前提 ：1900.1.1 是星期一

         ​	附加：将该月的日历，打印输出

         ​	日  一  二  三  四  五  六

         ​		     1    2   3     4   5



# day03

1. 循环

   1. 循环的流程控制

      1. break 

         在循环体内使用

      2. continue

         在循环体内使用

         ex:

          1. switch(i){

             ​	case 1:

             ​		console.log(11111);

             ​		break;

             ​	case 2:

             ​		console.log(22222);

             ​		break;

             ​	}

         	2.  var i = 1:

             		while (i < 10 ){

             			swith( i ){
						
             			case 1:
						
             				console.log(1111111);
						
             				break;
						
             			case 2:
						
             				console.log(222222);
						
             				continue; // 作用在while 上
						
             		}
						
             		i ++;

             }

   2. for 循环

      1. while

         打印1-100 之间所有的数字

         var i= 0；//循环条件的初始化

         while (i < 100) { // 循环条件

         ​	console.log(i); // 循环的操作

         ​	i ++ ; // 更新循环条件

         }

      2. for 

         1. 语法

            for (表达式1；表达式2；表达式3) {

            ​	循环操作

            }

            表达式1 ：循环条件的初始化

            表达式2 ： 循环条件的判断

            表达式3 : 更新循环条件

            

            打印 1- 100 之间所有的数字

            for (var i=1;i<=100;i++) {

            ​	console.log(i);

            }

            流程 ：

             1. 先执行表达式1，声明条件(执行1次)

             2. 再判断表达式2的值，true 或false

             3. 如果条件为true,则执行循环操作

                如果条件为 false , 就退出循环

            	4. 执行完循环操作后，再执行表达式3

            	5. 再判断表达式2的值，同步骤2

         2. for  VS  while 

            1. 相同

               先判断条件，再执行循环操作

            2. 不同

               while : 优先使用在不确定循环次数的场合下

               for : 优先使用在确定循环次数的场合下

            while (true) {

            ​	console.log();

            ​	if( xxxx)

            ​	if( xxx)

            ​		break;

            }

            for (var i=1; i <= 100; i++){

            }

         3. 练习

            1. 修改 日期计算器， 将while 循环更改为for 循环

            2. 判断素数(质数)

               1. 从弹框中随意录入一个数字，判断其是否为素数

                  素数：只能被1和自己整除的数字

         4. 循环的嵌套

            允许在一个循环的内部再出现一个循环

            //外层循环

            for (var i = 1; i <= 10; i++ ){

            ​	//内层循环

            ​	for (var j=1;j<=10;j++){

            ​	}

            }

            外层循环走一次，内层循环走一轮

            练习：在控制台中打印以下图案

            ```
            
            			    *      4个空格1个* 
            			   ***     3个空格3个*
            			  *****    2个空格5个*
            			 *******   1个空格7个*
            			*********  0个空格9个*
            
            			空格条件:从1开始到总行数-当前行为止
            			星星条件:从1开始到当前行数*2-1为止
            ```

2. 函数

   1. 什么是函数

      函数，又称为 function , 是一段被预定义好，并可以独立反复执行并包含多条执行语句的代码块

   2. 在 JS 中创建函数

      function 函数名 (参数){

      ​	函数体

      ​	[返回值]

      }

      参数列表：

      ​	如果没有参数，此处为空

      ​	如果没有参数，则编写参数列表，如果有个参数的话，各个参数之间使用"," 隔开

      ​	有参数的函数在调用时，就要传参，如果未传参的话，那么参数的值就是 undefined

      返回值：

      ​	在函数体内，经过运算后，需要传递给函数调用者的一个值，就是返回值

      ​	返回值是可选的，有返回值

   3. 函数的调用

      在任意的JS 的合法位置处，都允许做函数的调用

      ​	var ret = 函数名(参数列表)

      有参数，则传递参数，否则参数列表为空

      有返回值，则可以没有返回值的话，返回值为 undefined 

      练习：

      ​	修改作业内容：

      1. 将作业中的所有内容提炼成一个函数，通过一个按钮调用执行

      2. 将闰年判断的逻辑提炼成一个函数

         参数：要判断的年份

         返回值：是否为闰年的结果(boolean)

         将日期计算器作业中所有闰年判断的逻辑改为函数调用

      

   4. 匿名函数

      1. 什么是匿名函数

         匿名函数是一个没有名称的函数，该类函数会针对某一个功能而存在，不能独立声明

      2. 语法

         function (参数列表) {

         ​	函数体

         }

         window.onload = function ( ){

         ​	console.log(...);

         }

   5. 变量的作用域

      1. 什么是变量的作用域

         变量的作用域指的是变量的可访问范围

      2. 作用的分类

         1. 局部变量

            使用var 关键字声明在某个函数内的变量，就是局部变量

            局部变量只能在声明的函数内使用

         2. 全部变量

            1. 在function 之外声明的变量全部是全局变量

            2. 声明变量只要不使用var 关键字，全部都是全局变量

               全局变量可以应用在各个函数中，

               注意: 全局变量，推荐在所有的function 之外使用 var 关键字去声明

   6. 声明提前

      在js中使用var 声明的变量，在程序执行之前都会被预读到所在作用域的顶端，但赋值还保留在原位

   7. 数组 - Array

      1. 什么是数组

         数组(Array),是一个用于保存批量数据的数据结构

         数组是按照线性结构来保存数据的

      2. 创建数组

         1. 创建一个空数组

            var 数组名 = [];

         2. 创建数组并初始化数据

            var 数组名 = [ 元素1， 元素2， 元素3，...  ...];

         3. 创建一个空数组

            var  数组名 = new Array( );

         4. 创建数组并初始化数据

            var  数组名 = new Array (元素1, 元素2, 元素3)；

      3. 数组的使用

         获取 或 设置数组的元素的值，一律使用下标

         下标是从0开始，到数组元素个数-1结束

         var arr1 = ["罚款","阀门","法克"];

         1. 将数组中的第一个元素更改为 佐助

            arr1[0] = "佐助";

         2. 打印输出 arr1 数组中的第2 个元素

            console.log(arr1[1]);

         3. 为arr1 数组中的第10 个元素赋值为 "李洛克"

            arr1[9] = '李洛克';

      4. 获取数组的长度

         属性:length 

         用法 : 数组名.length

         使用场合 :

          	1. 能够找到数组中，要最新插入的位置(向数组尾部增加新元素时使用)
         		2. 配合循环，遍历数组中的每个元素

         练习：

          1. 让用户循环的从弹框中录入数据，并将录入的数据保存在一个数组中，直到输入 exit 为止，最后打印数组中所有的数据

          2. 声明一个数据，存放若干人的姓名

             要求 从弹框中录入一个人的姓名，并判断该人的姓名在数组中的下标是多少

             如果存在：则显示下标的值

             如果不存在：提示 输入的数据不存在

      作业：

       1. 、解决 练习2

          如果输入的姓名在数组中存在多个怎么办？

      	2. 声明一个数组保存三个数字，将三个数字按照从小到大的方式排列

          nums = [76,12,51]

          ... ...

          nums = [12, 51, 76]




# day04

1. 数组

   1. 常用API

      1. toString()

         作用：将数组转换为字符串，默认是将数组的元数使用，连接成字符串再进行返回

         e.x.

         ​	var  arr = ['三国演义','水浒传','西游记'];

         ​	console.log(arr.toString());

         ​	结果:三国演义,水浒传,西游记

      2. join (seperator)

         作用：将数组的元素使用seperator 字符串拼接并返回

         ```
         	var arr = ['三国演义','水浒传','西游记'];
         	//var ret = arr.join('-');
         	//ret:三国演义-水浒传-西游记
         	var ret = arr.join('');
         	ret:三国演义水浒传西游记
         ```

      3. reverse（）

         作用：将数组进行反转

         注意：该函数会改变现有数组的结构

         练习：

         1. 随意从弹框中录入一个数字
         2. 将该数转换为二进制,并输出

      4. sort()

         1. 作用

            对现有数组的内容进行排序

            默认是按照元素的Unicode码进行排序的

         2. 注意

            该函数会改变现有数组的内容

         3. 允许通过自定义的排序规则(排序函数)

            来指定数字的排序方式

            ​	语法：arr.sort( );

            1. 升序的排序函数

               function  sortAsc(a,b){

               ​	通过 返回值 表示a,b的大小关系

               ​	返回值为正数，说明a>b

               ​			要交换 a 和 b 的位置

               ​	返回值为0，说明a=b

               ​	返回值为负值，说明a<b

               ​	return a - b;

               }

               arr.sort(sortAsc);

               练习 :

                	1. 声明一个全局数组
               		2. 网页中创建两按钮
                    		1. 升序：点击时，数组升序并打印输出
                    		2. 降序 :  点击时，数组降序并打印输出

      5. 进出栈操作

         1. push( )

            入栈(压栈),向数组的尾部添加新元素，并返回新数组的 长度

            等同于: arr[arr.length] = "";

         2. pop ( )

            出栈(弹栈)，删除 并返回数组尾部的元素

         3. unshift ()

            向数组头部添加新元素并返回新数组的长度

         4. shift ()

            删除并返回数组头部的元素

   2. 二维数组

      1. 声明二位数组

         ```
         			var names = [
         				["孙悟空","猪八戒","沙师弟"],
         				["潘金莲","马蓉","李小璐"]
         			];
         
         			获取 马蓉:
         				var sub_names = names[1];
         				var uname = sub_names[1];
         
         				var uname = names[1][1];
         ```

2. 字符串 - string

   1. 声明字符串

      var  str1 = ' 字符串1 ';

      var  str2 = String(" 字符串2 ");

      var  str3 = new String(" 字符串3 "); 

   2. length  属性

      作用 ： 返回当前字符串的长度

   3. String  API

      1. 大小写转换函数

         1. toUpperCase()

            返回字符串的完全大写形式

         2. toLowerCase()

            返回字符串的完全小写形式

            练习：模拟验证码的生成和验证

            1. 创建一个数组，初始化若干数据( 英文大小写，数字)

            2. 生成一个四位的随机验证码

               验证码需要从数组中获取  math.random()  生成一个 0-1(取不到) 之间的随机小数

            3. 将随机生成的验证码字符串通过prompt() 展示给用户

            4. 比较用户输入的字符与生成的验证码是否一致并给出提示 (忽略大小写)

      2. 去掉字符串两端空格

         方法: trim( )

         注意: 该方法不会改变现有字符串，是将去掉空格后的字符串进行返回

      3. 获取指定位置的字符

         1. 获取指定位置的字符

            方式 : charAt (index)

            ex : 

            ​	var  str = "Hellp World";

            ​	var  s = str . charAt(3);

            ​	console.log( s );   //1

         2. 获取指定位置字符的 Unicode 码

            方法 ：charCodeAt (index)

            ex :

            ​	var  str  =  "Hello  World";

            ​	var  code = str . char CodeAt(6);

            ​	输出的是 W 的 Unicode 码

      4. 检索字符串

         1. indexOf( )

            value : 查找的字符串

            fromIndex：从哪个位置处开始查找，如果省略，则从第一个字符开始查找

            返回值： 返回字符串第一次出现的下标，如果没有查询到子字符串的话，则返回 -1 

            var  str = "Hello  World"

         2. lastIndexOf(value,fromIndex) 

            作用：查找value 最后一次出现的下标

            注意 ： 该函数的查找方式是从后往前找

            ex :

            ​	var  str = "Hello World";

            ​	var  r = str.lastIndexOf("l");

            ​	console.log(r);/9

            ​	var  r = str.lastIndexOf("l" , 7);

            ​	console.log(r);/3

            练习：判断一个字符是否满足邮箱的格式

            1. 字符串必须包含 @符号
            2. 字符串必粗包含. 符号
            3. 最后一个 . 必须在 @ 之后

      5. 截取子字符串

         函数 substring(start, end)

         作用： 返回从 start 到 end -1 之间的字符串，如果省略 end 的话，则截取到整个字符串的尾部

         ex : 

         ​	

         练习：

          1. 从指定邮箱中截取用户名

             sanfeng.zhang@tedu.cn

             2. 从指定邮箱中截取邮箱服务商

             sanfeng.zhang@tedu.cn

             3. 从身份证号中提取生日

                ```
                220101199912056621
                生日:1999年12月05日
                ```

      6. 分割字符串

         作用：将具备特殊连接符的字符串拆成字符串数组

         函数：split (seperator)

         ex : 

         ```
         	var str = "1001_5&1002_4&1053_1";
         
         				商品ID:1001
         				购买数量:5
         				商品ID:1002
         				购买数量:4
         				商品ID:1053
         				购买数量:1
         ```

      7. 模式匹配

         1. 作用：

            配合 子字符和正则表达式完成字符串的查找，替换

         2. 正则表达式

            语法：

            ​	/正则表达式/ 修饰符

            ​	修饰符:

            ​		i  :  ignorecase (忽略大小写)

            ​		g : global(全局匹配)

            ​		m: multiple (允许多行匹配)

            ​	ex : 

              		1. /\d{2,6}/g
              		2. /你大爷/g

         3. 函数

            1. replace (substr / regexp,replacement) 在一个字符串中，将 substr 或满足 regexp 格式的字符串替换成 replacement

            2. match (substr / regexp)

               按照指定的字符串或正则表达式进行匹配，并返回满足格式的子字符串数组

               ```
               			4.练习
               				Microsoft is a big company,microsoft's color is red and has MICROSOFT logo like Microsoft
               				1.将所有的 microsoft(大小写) 都替换成微软
               				2.统计 共替换了多少出 microsoft
               ```

3. RegExp 对象

   1. 创建 RegExp 对象

      1. var reg = /正则表达式/ 修饰符;

         var reg = / 你大爷 / gim ;

      2. var reg = new RegExp( "匹配模式","修饰符" );

         var reg = new RegExp("^\d{6}$");

   2. RegExp 常用方法

      1. test (string)

         string : 要验证的字符串

         如果string 满足reg 对象的格式的话，则返回 true ,否则返回 false

4. Math 对象

   1. 属性

      Math.PI

      Math.E

   2. 方法

      1. 三角函数

         Math.sin( )

         Math.cos( )

         Math.tan( )

      2. 计算函数

         Math.sqrt(x) : 开平方

         Math.log(x): 求对数

         Math.pow(x,y) : 求 x 的 y 次方

      3. 数值函数

         Math.abs(x) : 获取x 的绝对值

         Math.max(a,b,c,d) : 获取最大值

         Math.min (a,b,c,d ): 获取最小值

         Math.random( ) : 生成随机数(0-1)

         Math.round(x): 将 x 四舍五入到整数

5. Date 对象

   1. 作用：

      获取客户端的日期时间

   2. 创建Date对象

      1. 获取当前日期对象

         var  date = new Date();

      2. 初始化自定义日期时间对象

         var  date = new Date("2018/08/14 17:29:35");

   3. 方法

      1. 读取 或 设置 当前时间的毫秒数

         1. getTime( )

            返回自 1970-1-1 00:00:00 到 date 所经过的毫秒数

         2. setTime( )

            根据给定的毫秒数，结合 1970-1-1  计算日期时间

      2. 读取时间分量

         1. getFullYear( )

            获取当前时间对象的年份

         2. getYear( )

            返回自1900年以来到当前日期对象所经过的年数

         3. getMonth ( )

            返回0-11的数字来表示 1-12 月

         4. getDate( )

            返回date 对象所对应的日

         5. getDay()

            返回date 对象所对应的是星期?

            返回 0-6 表示 星期日 - 星期六

         6. 获取时间

            getHours () : 获取小时

            getMinutes( ) : 获取分钟

            getSeconds( ) : 获取秒

            getMilliseconds( ) : 获取毫秒

         7. 转换为字符串

            1. toString( )

            2. toLocaleString( )

               将日期对象转换成本地字符串

            3. toLocalTimeString( )

               转换成时间日期字符串(年月日)

      作业：

       1. 获取当前的系统日期时间

       2. 按照以下格式输出

          xxxx 年 xx 月 xx 日  xx 时 xx 分 xx 秒 星期[二]





# day05

1. 外部对象

   1. BOM 和 DOM

      BOM: Brower  Object  Model

      ​	浏览器对象模型

      ​	将浏览器比喻成一个对象 - window(网页初始化时自动创建的),可以通过window 对象操作浏览器中的内容

      DOM: Document  Object  Model

      ​	文档对象模型

      ​	将HTML 文档比喻成一个对象  -  document (属于window的一个属性)，可以灵活的操作网页上的内容

   2. window 对象 (BOM模型)

      1. 作用

         表示浏览器

         window 对象下的属性和方法在使用时，可以省略window.直接去调用

         ex : 

         ​	window.alert ()     --> alert ( )

         ​	window.prompt( )  -- > prompt( )

         ​	window.document -- > document

         ​	window. history  -- > history

      2. window中的对话框

         1. 警告框

            window .alert ( )   / alert ( )

         2. 输入框

            window.prompt( ) / prompt ( )

         3. 确认框

            window.confirm(" ")  / confirm(" ")

            点击"确定"按钮的话，返回true

            其余所有操作，都返回 false

         练习：

          1. 网页中创建一个 按钮，显示 “关闭”

          2. 点击按钮时，弹出确认框

             “确认关闭网页吗”

         	3. 如果点击确认的话，则关闭网页

             关闭网页：window.close();

         	4. 否则什么都不操作即可

      3. window 中的定时器

         1. 定时器的分类

            1. 周期性定时器

               每间隔一段时间后，就执行一段程序，反复执行

            2. 一次性定时器

               在指定的时间间隔后，只执行一次操作

         2. 周期性定时器

            1. 声明定时器

               var ret = window.setInterval(fun,time);

               ​	fun : 函数，要周期执行的操作，可以是匿名函数

               ​	time : 要间隔的时间周期，以毫秒为单位的数字

               ​	ret  :  返回已创建好的定时器对象

               1. 清除定时器

                  window . clearInterval (timer)

                  timer : 要停止的定时器对象

            2. 一次性定时器

               1. 声明定时器

                  var ret = setTimeout (fun, time);

                  ​	fun : 等待一定的时间后要执行的操作

                  ​	time : 要等待的时长，以 ms 为单位

                  ​	ret : 创建好的定时器对象

               2. 清除定时器

                  clearTimeout(timer);

                  timer : 一经创建好的一次性定时器对象

                  练习

                   1. 创建一个按钮

                   2. 点击按钮，弹出一个确认框

                      确认一下是否要关闭网页??

                  	3. 如果用户点击确定的话，5s 钟后再关闭网页

      4. window 中的属性

         1. screen 属性

            作用：获取客户端显示器的相关信息

            属性: 

             1. width  /  height

                获取屏幕分辨率

            	2. availWidth  /  availHeight

                可用宽度和可用高度

         2. history  属性

            作用：处理当前窗口所访问过的 url 地址们

            属性 & 方法：

             1. 属性： length, 表示当前窗口所访问过的url 数量

             2. 方法：

                 1. back (): 后退

                 2. forward (): 前进

                 3. go (num)  在当前页面的基础上前进或后退 num 步

                    num : 

                    ​	取值为正数，前进

                    ​	取值为负数， 后退

         3. location 属性

            	1. 作用

                表示浏览器上地址栏的信息

            	2. 属性 & 方法

                	1. 属性 ： href 

                    表示当前窗口中正在浏览器的网页地址

                    如果为href 属性设置值的话，相当于实现了浏览器跳转的功能

                	2. 方法 : reload( )

                    重新加载当前网页，等同于刷新操作

         4. navigator 属性

            	1. 作用

                封装了浏览器的相关信息

            	2. 属性

                userAgent : 显示浏览器相关信息

         5. document 属性 (重点)

2. document 对象 (DOM模型)

   1. document 的概述

      document 对象，是 DOM模型中的顶层对象，封装了所有和 HTML元素相关的属性，方法以及事件，由于 document 是属于window 对象的核心属性之一，所以不用声明在网页中就可以直接使用

      网页加载的时候，会在内存中形成一颗节点数(DOM树).DOM树会封装网页上的所有的内容，网页上的每一个元素，每一个属性，都是DOM树上的一个独立“节点”

      DOM 所提供的操作：

       	1. 查找节点的操作方法
      		2. 读取节点的信息
      		3. 修改节点的信息
      		4. 删除节点
      		5. 创建节点

      注意：只要DOM 树上的内容产生变化的话，网页也会一同变化

      DOM 树上的节点的类型:

       1. 元素节点 - 表示的是网页中的一个元素
       2. 属性节点 - 表示的是元素中的一个属性
       3. 文本节点 - 表示的是元素中的文本内容
       4. 注释节点 - 表示网页中的一个注释
       5. 文档节点 - 表示整个HTML文档

   2. 查找元素节点

      1. 通过元素id 查找元素节点

         前提：元素一定要具备id 属性，否则无法查找 

         var elem = document.getElementById( "元素ID");

         elem : 对应的ID 的元素在 Js 中的表现形式 - DOM元素 / DOM对象

      DOM对象属性

      1. inner HTML

         修改 或 获取当前 DOM 对象的 HTML文本

      2. innerText

         ​	修改 或 获取当前 DOM 对象的普通对象

         注意：以上两个属性只针对双标记有效

      3. value 

         该属性只针对表单控件，允许获取或设置表单控件的值

   3. 读取节点的信息

      1. 节点的类型

         属性 ： node Type

         值：

         ​	返回1 ： 元素节点

         ​	返回2 ： 属性节点

         ​	返回3 ：文本节点

         ​	返回8 ：注释节点

         ​	返回9 ： 文档节点

      2. 节点名称

         属性 : nodeName 

         ​	元素节点 或 属性节点： 返回标签名或属性名

         ​	文本节点 : 返回 #text

         ​	文档节点 ：返回 #document

         ​	注释节点 ： 返回 #comment

   4. 获取 或设置元素节点的属性

      所有元素节点都具备以下方法，用于操作属性：

      1. getAttribute( "attrName")

         作用：获取指定属性的值

         attrName: 要获取的属性名称

         返回值 ：attrName 属性对应的值

      2. setAttribute(attrName,attrValue)

         作用：设置指定属性的值

         attrName:要设置的属性名

         attrValue:要设置的属性值

      3. removeAttribute("attrName")

         作用：将attrName 属性从节点中删除出去

      练习：

      1. 创建一个网页

      2. 创建一个a标记

         链接地址为 : http://www.baidu.com

         文本：百度

      3. 创建一个按钮，文本为修改

      4. 点击按钮时，将a标记修改为

         链接地址为： http://www.tmooc.cn

         文本：TMOOC

   5. 元素节点的样式

      1. 使用 setAttribute ( ) 设置 class 属性值

         相当于动态的为元素绑定类选择器

         elem.setAttribute("class","类选择器");

      2. 使用元素的 className 属性修改 class 的值

         elem.className = "类选择器"；

      3. 变相的使用内联方式设置样式属性

         elem.style.css 属性名 = 值；

         elem.style.color = "red";

         注意： 

         ​	如果css属性名中包含 "-" 的话，"-" 要取消，并且后面单词的首字符变大写

         ​	elem.style.fontSize="18px";

         ​	//设置 elem 元素的右边框的颜色为红色

         ​	border - right - color

         ​	elem.style.borderRightColor="red";

3. 查询节点的方式

   1. 根据id 查询

      document.getElementById( );

   2. 根据节点的层级关系查询节点

      1. parentNode属性

         返回当前节点的父节点元素

      2. childNodes属性

         返回当前节点的所有子元素数组

      3. children 属性

         返回当前节点的所有子元素数组（元素节点）

      4. nextSibling

         获取当前节点的下一个兄弟节点

      5. nextElementSibling

         获取当前节点的下一个元素兄弟节点

      6. previousSibling

         获取当前节点的上一个兄弟节点

      7. previous ElementSibling

         获取当前节点的上一个兄弟元素节点



# day06

1. 查询节点

   1. 根据节点的层级查询节点

      1. childNodes

         元素节点，文本节点

      2. children

         元素节点

      3. parentNode

         获取父节点

      4. nextSibling

         获取下一个兄弟节点

         有可能是文本节点

      5. nextElementSibling

         获取下一个兄弟元素节点

      6. previusSibling

         获取上一个兄弟节点

         有可能是文本节点

      7. previousElementSibling

         获取上一个兄弟元素节点

   2. 通过标签名查询节点 - 返回数组

      document |  elem.getElementsByTagName("标签名");

      ​	document : 整个文档内查找

      ​	elem : 某个元素内查找

   3. 通过元素的 name 属性值查询节点

      语法: document.getElementsByName("name属性值")；

      返回值:包含指定name 属性值得元素的数组

      练习：

       1. 创建一个网页，包含多个单选按钮

       2. 创建一个普通按钮

       3. 单机普通按钮的时候

          多个单选按钮中必须有一个被选中

          ```
          <input type = "radio' checked>
          ```

      	4. 通过元素的class 值查询节点

          语法: document | elem.getElementsByClassName("class");

          返回 ：返回所有包含指定class 属性值的所有元素

2. 增加节点

   1. 创建元素节点

      语法：

      ```
      	var  elem = document.createElement("元素名");
      
      ex : 
      
      	var  div =  document.createElement("div");
      
      	div.setAttribute("id","container");
      
      	div.innerHTML = "动态创建的文本";
      
      ```

   2. 增加节点到网页上

      1. document.body.appendChild( elem );

         向body中追加elem的新元素

      2. parentNode.appendChild(elem);

         向parentNode内部追加elem新元素

      3. parentNode.insertBefore( newElem,oldElem)

         将newElem元素插入到 parentNode 中 oldElem元素之前

      ```练习
      练习步骤：
      	点击按钮时
      	1.先获取三个文本框的值
      	2.创建两个按钮 - 删除按钮，修改按钮
      	3.先创建四个td
      		将三个文本框的值追加到前三个td
      		将两个按钮追加到第四个td中
      	4.创建一个tr
      		将四个td追加到tr中
      	5.将 tr 追加到 table 中
      ```

   3. 删除节点

      在DOM中，删除节点的行为只能由父元素发起

      语法：parentNode.removeChild (elem);

      ​	删除 parentNode 中的 elem 元素

   4. 事件

      1. 什么是事件

         通常都是由用户的行为来激发的操作

      2. 触发事件的行为

         所有的事件在绑定时，必须加 on 

         1. 鼠标事件

            [1.click事件](onclick)

            当鼠标单击元素时触发该事件

            2. mouseover 事件

               当鼠标移入元素时的事件

            3. mouseout 事件

               当鼠标移出元素时的事件

            4. mousemove 事件

               当鼠标在元素内移动时的事件·

         2. 键盘事件

            1. keydown 事件

               当键位按下时所激发的事件

            2. keypress 事件

               当键位按下时所激发的事件

            3. keyup 事件

               当键位抬起时所激发的事件

         3. 状态改变事件

            1. load 事件

               当元素加载完全时所触发的事件(body)

            2. change 事件

               当选项发生改变时所触发的事件 (select)

            3. focus 事件

               当元素获取焦点时所触发的事件(文本框类)

            4. blur 事件

               当元素失去焦点时所触发的事件 (文本框类)

            5. submit 事件

               当表单被提交时所提交时所触发的事件 (表单)

      3. 绑定的方式

         1. 在元素中绑定事件

            <元素 on 元素事件名="on..."> </元素>

         2. 在 js 动态的为元素绑定事件

            DOM 对象. on 事件名 = function(){

            ​	

            }

            ex :

            ```
            	var mian = document.getElementBuId("main");
            	main.onclick = function(){
            	}
            ```

            注意：在js 动态绑定事件中，允许使用this 来表示触发当前事件的DOM事件

      4. 事件行为

         1. 状态改变事件

            1. load 事件

               通常为 body 绑定 load 

               事件，目的是为了在所有内容都加载完成之后再实现一些初始化的操作

               1. ```
                  <body onload ="函数()">
                  ```

               2. js 中动态绑定

                  windows.onload = function(){

                  ​	网页加载完成后，要执行的操作

                  }

            2. submit 事件

               只有表单被提交时才会被触发

               注意：该事件需要一个 boolean 返回值来通知表单是否要继续被提交，如果返回true,则可以提交表单，否则，阻止表单提交

               js 中动态绑定：

               表单对象 . onsubmit = function(){

               ​	return  true/false;

               }



# day07

1. 事件

   1. 状态事件

      1. change 事件

         主要场合：使用在select 中的，每当选项发生改变时，就会激发一次该事件

   2. 事件对象 - event 

      1. 什么是事件对象

         全称：事件参数对象，简称为事件对象

         任何一个事件对象被触发后，都会自动产生一个 event

         对象 . event 对象中会包含与当前事件相关的一些属性和方法

      2. 获取 event 对象

         1. html 元素中绑定事件

            ```
            <ANY on事件名 = "btnClick(event)>
            
            <script>
            	function btnClick(event){
                    event 表示的就是事件对象
            	}
            </script>
            ```

         2. 在 js 中动态为元素绑定事件

            var d1 = document.getElementById("d1");

            d1.onclick = function(){

            ​	event 表示的就是事件对象

            }

      3. 事件对象的常用属性

         1. 事件源

            1. 什么是事件源	

               触发当前事件的元素是谁

            2. 获取事件源

               通过 event.tarent 获取事件源

               得到的是一个DOM对象

         2. 鼠标事件的属性

            鼠标事件: mouseover,  mouseout, mousemove ,click

            1. offsetX,offsetY

               获取鼠标在元素上的坐标点

               以元素在左上角为(0,0)进行计算的

         3. 键盘事件的属性

            键盘事件：keydown,keypress,keyup

            keydown , keypress 事件中允许增加一个返回值，通知浏览器是否要正常处理按下的字符，返回值为 true,则正常显示字符，返回值为 false,则不显示字符

            1. keydown 事件

               只要按下键位，就会触发 keydown

               属性：

                1. which

                   按下的键位码

            2. keypress 事件

               只有字符输出时才会触发该事件

               属性：

                1. which

                   要输出的字符的ASCII码

   3. 事件冒泡

      阻止事件冒泡

      ​	event.stopPropageation( )

      ---

      jQuery

      1. jQuery 介绍

         jQuery 是一个轻量级的JS 库 - 是一个封装好的 JS文件，提供了更为简便的元素操作方式

         核心理念 ：write Less Do More

         

      2. 使用jQuery

         1. 引入jQuery文件

            ```
            <script src="jquery-1.11.3.js"></script>
            ```

            注意：jQuery文件引入操作必须要放在其他jQuery操作之前

      3. jQuery对象

         1. 什么是jQuery对象

            jQuery对象是由jQuery对页面元素进行封装后的一种体现

            **jQuery中所提供的所有操作都只针对jQuery对象，DOM对象不能用**

         2. 工厂函数  -  $ ( )

            作用:

             	1. 能够获取jquery对象
            		2. 能够将DOM对象转换为jquery对象

            语法：

            ​	$(选择器 / DOM对象)；

            ​	$( ) 能够将选择器 和 DOM 对象封装成 jquery 对象进行返回

         3. DOM对象和 jQuery 对象之间的转换

            DOM对象：只能使用DOM提供的操作，不能使用jQuery操作

            jQuery对象：只能使用jQuery操作，不能使用 DOM 操作

            1. 将DOM对象转换为jQuery对象

               语法：

               ​	var 变量 = $ (DOM对象)；

               注意：所有的JQuery对象在起名的时候，最好在变量名称+$ ,用于区分与 DOM对象的区别

            2. 将jQuery对象转换为DOM对象

               1. var dom 对象 = jQuery对象.get ( 0 )
               2. var  dom 对象 jQuery 对象[0]

   4. jQuery选择器

      1. 作用

         获取页面上的元素们，返回值都是由JQ对象所组成的数组。

         	语法: $("选择器"); 

      2. 选择器详解

         1. 基本选择器(略)

         2. 层级选择器

            1. $("selector1 + selector2")

               名称 ：相邻兄弟选择器

               作用：匹配紧紧跟在selector1 后面且满足selector2选择器的元素

            2. $("selector1~selector2")

               名称：通用兄弟选择器

               作用：匹配selsctor 后面所有满足于

         3. 基本过滤选择器

            1.  :first 

               只匹配到第一个元素

            2.  : last

               只匹配到最后一个元素

            3.  : not( selector )

               将满足 selector 选择器的元素排除出去

            4.  :odd

               匹配 偶数行元素 (奇数下标)

            5.  :even 

               匹配奇数行元素（偶数下标）

            6.  :eq(index)

               匹配下标等于index 的元素

            7.  :gt(index)

               匹配下标大于index 的元素

            8.  : lt(index)

               匹配下标小于index 的元素

         4. 属性选择器

            1. [attribute]

               作用：匹配包含指定属性的元素

               ex : $("div[id]");

            2. [attribute = value]

               作用：匹配属性值为value的元素

               ex : 

               ```
               $("div[id=main]")  ->  $("main")
               $("[type=text]");
               ```

            3. [attribute != value]

               作用：匹配属性值不是 value 的所有元素

            4.  [attribute ^= value]

               作用：匹配属性值以value 字符作为开始的元素

            5. [attribute $= value]

               作用： 匹配属性值以 value 字符作为结尾的元素

            6.  [attribute *=value]

               作用：匹配属性值中包含 value 字符的元素

         5. 子元素过滤选择器

            1. : first - child

               匹配属于其父元素中的首个子元素

            2. : last - child

               匹配属于其父元素中的最后一个子元素

            3. :nth - child (n)

               匹配属于其父元素中的第n个子元素

               ：nth - child(1)  -->  : first -child



# day08

1. jQuery操作DOM

   1. 基本操作

      1. html ( )

         作用：获取 或设置 jQuery 对象的 html 内容

         等同于 inner HTML

         ex.:

         ``` 
         	var $div= $("#main");
         	console.log($div.html());
         	$div.html('动态设置的文本');
         ```

      2. text( )

         作用：纯文本内容

         等同于：innerText

      3. val( )

         作用：获取 或 设置 表单控件的value 值

         等同于 : value

   2. 属性操作

      1. attr ( )

         作用：读取 或 设置 jQuery 对象的 属性值

         ex : 

          1. $obj.attr("id");

             获取 $obj 对象的 id 属性值

         	2. $obj.attr("id", 'container')

             设置 $obj对象的 id 属性值为 container

      2. removeAttr("attrName")

         作用：删除 jquery 对象的 attrName 属性

         ex : 

          	$ obj.removeAttr("class");

   3. 样式操作

      1. attr ("class" , "className")

         使用 attr( ) 绑定className 值到jq 对象的 class 属性上

      2. addClass ("className")

         作用：追加className 选择器到 jq对象的class 属性后

         返回值:jq 对象

         ```
         <div id="obj"></div>
         var $obj = $("#obj");
         ex:
         	$obj = $obj.addClass("c1);
         	结果:<div id="obj" class="c1"></div>
         	
         	$obj = $obj.addClass("c2");
         	结果:<div id="obj" class="c1 c2"></div>
         以上两个操作,可以简化为:
         				(连缀调用)
         				$obj.addClass("c1").addClass("c2").html();
         ```

         

      3. removeClass("className")

         作用：将className属性值从 class 属性中移除

      4. removeClass( )

         作用：清空class 属性值

      5. toggleClass("className")

         切换样式:

         ​	元素如果具备className属性值，则删除

         ​	元素如果没有className属性值，则添加

      6. css( 'css属性名')

         作用：获取对应css 属性的值

         ex:

         ​	$obj.css ('id')

         ​	作用：获取$obj对象的 id 属性值

      7. css("css属性名","css属性值")

         作用：为元素设置css 属性值

      8. css (JSON对象)

         JSON 对象 类似于 PYTHON 中字典的写法

         ex :

         ```
         $obj.css({
         	"color":"red",
         	"background-color":"orange"
         });
         
         ```

   4. 遍历节点

      1. children( ) / children(selector)

         作用：获取jq对象的所有子元素或带有指定选择器的子元素

         注意：只考虑子代元素，不考虑后代元素

      2. .next() / next(slector)

         作用：获取jq 对象的下一个兄弟元素 / 满足delector 的下一个兄弟元素

      3. prev( ) / prev(selector)

         作用：获取jq对象 的上一个兄弟元素 / 满足selsctor 的上一个兄弟元素

      4. siblings( ) / siblings(selector)

         作用：获取jq对象的所有兄弟节点 / 

         满足 selector 的所有兄弟

      5.  find (selector)

         作用：获取满足 selector 选择器的所有后代元素

      6. parent()

         作用：查找jq对象的父元素

   5.创建元素 & 插入元素

    1. 创建元素

       语法:var `$`obj = $("创建的内容");

       注意：创建的内容必须是标记

       ex: 

       ​	1.创建一对div

       ​		var `$`div  =  $("<div id = 'xxx'>xxxxx</div>");

       ​	2.创建一对button

       ```
       var $btn = $("<button></button>");    			$btn.attr("id","btnDelete");
       $btn.html("删除");
       ```

       ​	

       2. 插入元素

         1. 内部插入

            1. ```
               $obj.append($now)
               ```

               将`$`now 元素插入到 $obj中最后一个子元素位置处

               ```
               $obj.prepend($new);
               
               ```

            	2. 将 `$` new元素插入到 $ obj中第一个子元素的位置处

         2. 外部插入

           作为兄弟元素插入到网页中

           1. `$`obj.after($new);

              将`$new元素作为`$obj 的下一个兄弟节点插入到网页中

           2. `$obj.before(`$new);

              将`$new作为`$obj 的上一个兄弟节点插入到网页中

2. jQuery 中的事件处理

   1. DOM 加载完成后的操作

   2. ```
      $(document).ready(function(){
          //DOM数加载完毕后要执行的操作
          //相当于是网页初始化
      });
      ```

      ```
      $().ready(function(){
      
      	//效果同上
      
      });
      
      ```

   3. ```
      $(function(){
         	//效果同上
      })；
      
      ```
      jQuery 事件绑定
       1. 方式1

          $obj.bind("事件名称",事件处理函数);

          ex:

          ​	$obj.bind("click");

          2.  

          $obj.事件名称(function(){

          });

          ```
          ex:
          $obj.click(function(){
              xxxxx
          });
          ```

      常用事件

      ```
      $obj.click(fn);
      $obj.mouscove(fn);
      $obj.mousemove(fn);
      $obj.mouseout(fn);
      $obj.keydown(fn);
      $obj.keypress(fn);
      $obj.keyup(fn);
      $obj.focus(fn);
      $obj.blur(fn);
      $obj.change(fn);
      $obj.submit(fn);
      ```

   1. 事件中的this

      在jquery 事件中，this 表示的就是触发当前事件的DOM事件

   2. 事件对象 - event

      在绑定事件的时候，允许传递event 参数来表示事件对象

      1. $obj.bind("事件名称",function(event){

         ​	event 表示的就是事件对象

         })

      2. $obj.事件名称(function(event){

         ​	event 表示的就是事件对象

         });

      event的使用方式 与 原生 JS 事件中的事件对象一致

      1. 事件源

         event.target

      2. 鼠标事件

         event.offsetX : 在元素上的横坐标

         event.offsetY:在元素上的纵坐标

      3. 键盘事件

         event.which : 键位码或 ASCII码

    3. 激发事件操作

       $obj.事件名称();

       ex:

       ```
       $obj.click(); //触发$obj的click事件
       $obj.click(function(){}); //为$obj绑定click事件
       ```

3. jQuery 删除节点

   1. remove( )

      语法:$obj.remove( );

      作用：删除$obj 元素

   2. remove("slector")

      语法:$obj.remove("selector");

      作用:将满足selector 选择器的元素删除

   3. empty ( )

      语法: $obj.empty( );

      作用: 清空 $obj 内容

4. jQuery 遍历操作

   方法:each( )

   1. 循环遍历 jQuery 数组

      ```
      $obj.each(function(i,obj){
          i:循环出来的元素的下标
          obj:循环出来的元素(DOM元素)
      });
      ```

      

   2. 循环遍历 JS 数组(原生)

      1. 将原生数组通过$() 装换成 jQuery 数组

      2. $.each(原生数组,function(i,obj)){

         ​	i : 遍历出来的下标

         ​	obj:遍历出来的元素

         }

      作业:

      ```
      		在 07-jquery-each.html 的基础上
      		完成下列操作
      		1.点击哪个 p 元素,哪个p元素的背景变为 orange
      		2.其他的 p 元素背景再变回默认效果(无背景)
      			background-color:transparent
      ```

       

      

      

      

# day09

1. jQuery 动画

   1. 基本显示 / 隐藏

      `$`obj.show() / $obj.show(执行时长)

      `$`obj.hide() / $obj.hide(执行时长)

   2. 滑动式显示 / 隐藏

      $

2. Dango

   1. WEB : 表示用户可以

   2. 服务器

      1. APACHE

      服务器的作用

       	1. 存储WEB上所需要的信息(HTML,图片,js,css,音视频)
       	2. 处理用户的请求(request)并给出
