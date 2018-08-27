# web_day01

# 

赵蒙蒙

g-zhaomm@tedu.cn

web前端课程HTML	CSS + JS

特点：简单 多 碎

1. 前端   web	

   1. 网页

      1. 网页的运转
      2. 服务器 ： 用于接收用户请求并响应，提供数据支撑
      3. 浏览器:电脑上的程序，客户端，帮用户发请求并且处理服务器端返回数据，图形化呈现给用户
      4. 通信协议 : 网络请求最常用的HTTP  HTTPS
      5. 服务器及浏览器产品
         1. 服务器：Tomcat  Apache   Nginx   iiS  （Internet  Information  Service)
         2. 浏览器：

      ```
      五大浏览器     按照浏览器内核进行划分
        
      ​				浏览器内核/引擎：
        
      ​					渲染引擎：对 HTML  CSS  进行处理
        
      ​						JS 引擎：  对JS  进行处理
        
      ​	1. Chrome		webkit   -- > bilnk
        
      ​	2. FireFox           Gecko
        
      ​	3. IE                     Trident
        
      ​	4. Safari              webkit
        
      ​	5. Opera              Presto
        
      4. 网页构成
        
      ​	静态页面 ：结构  HTML 和  样式 CSS
        
      ​	动态交互 ： JS
      ```

2. HTML

   1. 超文本标记语言 Hyper   Text   Markup   Language

   2. HTML 用来书写页面结构 文档类型都是 .html/.htm

   3. 特点：大量的标记确定页面结构和组成

   4. 浏览器页面中使用 F12 或者右键检查打开开发者工具

   5. 语法特点：

      1. 标签由 <标签名>组成 

      2. 分类 ：

         1. 双标签<html></html>

            成对出现，有开始和结束标签

         2. 单标签<meta>只有开始标签没有结束标签

      3. 标签语法：<title charset = "utf-8">标签内容</title>

         标签内容</title>

         ​	<标签名 属性名='属性值'>标签内容</标签名>

         ​	标签属性用来对标签本身做补充说明

         4.文档会忽略多余的空格，只显示一个空格

         

   6. 语法介绍

      1. 所有网页内容都需要放在<html>标签中
      2. <head>

      标签中存放网页文档的头部信息,例如 编码方式，

      链接的外部文件，网页关键字，用户不可见，浏览器选项卡上的信息，例如 网页标题，

      网页LOGO是用户可见

      1. HTML大小写不敏感，都可以识别，推荐统一小写
      2. <!doctyoe html> HTML5的文档声明方式
      3. w3c 国际组织，主要是制定和规范HTML  CSS语法

   7. 标签类型

      1. 块级元素

         1. 独占一行不与其他元素共行显示
         2. 默认宽度与父元素保持一致
         3. 可以手动设置宽高尺寸

      2. 行内元素

         1. 可以与其他元素共行显示
         2. 宽高由元素的内容决定，不能手动设置宽高

      3. 行内块元素

         既可以共行也可以手动设置宽高

3. 常用标签

   1. 标题标签 <hn></hn>

   2. 段落标签 <p></p>

   3. 文本标签

      1. <span>公式</span>
      2. <labe1>普通标签</label>
      3. <i>斜体</i>
      4. <b>加粗</b> <strong>标签同样加粗</strong>
      5. <u>下划线</u>
      6. <s>删除线</s> <del>删除文本</del>
      7. <sub></sub>

   4. 格式标签

      <br/>

      <hr/>

      字符实体 ： &nbsp: & yen; & copy; & lt; & gt;

      ​			空格 人民币 左尖括号 右尖括号

   5. 列表标签

      1. 无序列表

         设置type属性修改项目符号

         ​	disc(默认)

         ​	square

         ​	circle

         ​	none

         <ul type="">

         ​	<li></li>

         </ul>

      2. 有序列表

         设置type属性修改项目符号

         ​	1（默认）

         ​	a

         ​	A

         ​	i

         ​	I

         设置start 属性，决定从几开始排序，取值是数字

         <ol>

         ​	<li></li>

         </ol>

      3. 定义列表

         dt表示对数据分组

         dd表示具体数据

         <dt>

         ​	<dt></dt>

         ​		<dd></dd>

         ​		<dd></dd>

         ​	</dl>

         1. 图片标签
            <img src="C:/Users/%E5%90%B4%E8%83%9C%E5%86%9B/Desktop/Web/%E8%B7%AF%E5%BE%84">
            	url 组成 ： 协议 域名 目录路径 文件名
            	路径分为相对路径和绝对路径
            	绝对路径 ：
            		从根目录开始查找 
            		注意 ： 
            		1. 斜杠的问题 
            		2. 目录与文件名称
            		3. file：///协议是windows上打开本地文件的协议，类似于文件管理器
            	相对路径 ：
            	 	从当前文件所在的目录位置开始查找 	
            		../表示从当前文件夹返回上一级目录
            1. 超链接
               使用超链接标签 a href="url" 
               1. 指定网络URL进行跳转，一定要写协议
               2. 设置新网页的打开方式 是否在当前选项卡窗口打开 默认_self 在当前窗口打开，会覆盖当前文件， _blank表示新建窗口打开
               3. href 属性为空，表示链接到当前页，会进行页面刷新
               4. href 属性为 # 还是链接到当前页，不会进行页面刷新
               5. 文档内部锚点链接
                  在当前页设置锚点链接 跳转到当前文档的指定位置 
                  1. 在指定位置添加空标签，并且设置name 或者 id属性
                  2. 在超链接中设置 href = "#锚点值" 锚地值就是 name/id属性值



```
     	    MAC 截屏 command + shift + 3 / 4
     	    	取色 colorSnapper
     	    	文档查阅 Dash
     	    windows Zeal
```





# Web_day02



# 

## 表格

1. <table>
   <tr>
   			<td></td>
   		</tr>
      </table>

   ```
   创建行<tr></tr>
   
   在行中创建单元格<td></td>	
   ```

2. table 属性
   width  宽
   	height  高
   	border 默认以像素为单位
   	bgcolor 颜色值表示 ： 可以使用英文单词和十六进制
   	align 设置表格在窗口中的位置 left/center/right
   	cellspacing 设置单元格与边框之间的距离
   	cellpadding 设置单元格内容与单元格边框之间的距离

3. tr/td 属性

   width

   height

   bgcolor

   align 单元格内容的水平对齐方式

   valign  单元格垂直方向的对齐方式  top/middle / bottom

4. td 独有属性

   rowspan 

   设置单元格跨行合并，取值为数字，表示跨几行

   colspan

   设置单元格跨列合并，取值为数字，表示跨几列

5. 表格结构

   <table>

   ​	<thead>

   ​		<tr>

   ​			<td></td>

   ​		</tr>

   ​	</thead>

   ​	<tbody>

   ​		<tr>

   ​			<td></td>

   ​		</tr>

   ​	</tbody>

   ​	<tfoot>

   ​		<tr>

   ​			<td></td>

   ​		</tr>

   ​	</tfoot>

   </table>

   thead   tobdy   tfoot   可以省略，如果不写，

   表格中所有的内容会自动加入tbody中

   thead  tfoot  用来将一行或是若干行分组，作为表格的头部和尾部信息

6. 表格标题及首行文本特殊样式

   <table>

   ​	<caption>表格标题</caption>

   ​	<tr>
   		<th></th>
   	</tr>
   </table>
   <caption>可以用来设置表格标题，必须作为表格的第一个子元素使用
   		<th>用法与td 一样，自带文本居中和加粗效果

   

## 表单

1. 作用 ：向服务端发送数据

2. 基本语法

   <form action="" method="">

   </form>

   action

   属性指定表单数据提交到服务器中那个文件，属性值为文件路径

   method 属性指定数据提交的方式  常用 get/post

   注意 ： 

   get  请求 ： 数据会被拼接在URL后面，直接发送，安全性较低；数据大小受限，

   最大为2K。是默认的提交方式

   post  请求 ：数据会被打包单独发送，隐式提交给服务器，安全性高；数据大小不受限

   1. 表单控件  （重点）

      1. 文本输入框和密码框

         <input type="text" name="uname" placeholder="提示文本" maxlength="10"/>

         <input type="password" name="upwd"/>

         type : 属性用来指定控件类型

         name :  属性定义控件名称，缺少的话无法提交

         placeholder : 设置用户输入之前的提示文本

         maxlength :  设置最大可输入的字符数

      2. 单选和复选框

         <input type="radio" name="gender" value="male" checked>   

         <input type="checkbox" name="hobby" value="sing">    

         注意 ：radio : 单选 例如性别

         ​	checkbox :  复选  例如兴趣爱好

         ​	 name 属性用来分组，一组按钮的name 属性必须一致

         ​	value属性用来设置控件的值，最终会发送给服务器

         ​	checked 属性设置按钮默认选中状态

      3. 隐藏域

         隐式发送一些附加信息，用户不可见

         <input type="hidden" name="uid" value="101">

         <input type="hidden" name="other" value="用户隐私"

      4. 文件上传

         <input type="file" name="uimg">

      5. 文本域

         <textarea name="uinfo" cols="20" rows="5"></textarea>

         cols  指定文本默认显示的列数，一行能够显示的英文字符量，中文减半

         rows  指定文本域默认显示的行数

         注意：

         可以使用disabled属性禁用表单控件，适用于所有的表单控件

      6. 下拉菜单

         <select name="area">

         ​	<option value="bj">北京</option>

         </select>

         ​	下拉菜单分组

         ​	<select name="address">

         ​		<optgroup label="河北省">

         ​			<option value="sjz">石家庄</option>

         ​		</optgroup>

         ​		<optgroup label="河南省">

         ​			<option value="zz">郑州</option>

         ​	</select>

         注意：

         value 属性值是最终发送给服务器的数据

         optgroup 用来对选项分组，通过label属性设置组名

         option 用来设置具体的选项

      7. 提交 重置按钮  普通按钮

         1. 提交按钮 <input type="submit">  将表单数据发送给服务器

         2. 重置按钮 <input type="reset">

            ​	重置表单数据， 恢复到初始状态

         3. 普通按钮 <input type="button" value="点我"> 普通按钮需要通过value 属性显示文本

         4. <button type="submit">提交</button>   

            type 可以取值 submitreset  

            button,可以实现 input 按钮的功能，需要添加标签文本显示在按钮上

      8. label for ID

         

         <label for="male">男</label>

         <input type="radio" value="male" id="male" name="gender">

         使用label标签显示文本，将label 的标签属性 for 的属性值设置为将要绑定的表单控件 的id 的值，实现点击文本控件一样的效果

         

         补充 ： 

         maxlength  属性

         用来设置输入框可输入的最大字符数

      9. 取色板

         <input type="color" name="colorpick">





# CSS_day01

# 

1. 容器标签  -  块级元素

   <div></div>常用于页面的模块划分

   类似 ： <span></span> 用于行内分区

2. CSS介绍

   Cascading  Style  Sheets  层叠样式表

   样式的重用、样式的分类

   1. 作用 ： 为元素设置样式，美化页面

   2. 使用方式 ：

      1. 内联样式(行内样式)	

         语法  <标签 style="CSS样式规则" >

         样式规则  width  :  200px;

         1. 常用属性 ：

            width  :    取数值，单位为像素px

            ```
            height :    取数值，单位为像素px
            
            background-color  : 背景颜色
            
            color :  取颜色值，设置文本颜色
            
            font-size  :   字体大小，取数值，单位为px
            
            font-weight  :   设置字体为粗体   取值 bold 
            ```

         2. 练习  ：

            1. 创建页面 01work.html

            2. 创建<div>,内容不限

            3. 使用行内样式设置div

               ​	500  *  500  尺寸

               ​	橘色  背景色

               ​	红色  文本色

               ​	字体大小为   24 px

               ​	字体加粗

   3. 文档内嵌方式

      使用<style>样式</style> 来引入CSS 样式，常写在<head></head>

      标签中   标签内容就是样式规则

      语法 ：

      ​	<style>

      ​		div{

      ​			width: 300px;

      ​			height: 300px;

      ​			...

      ​		}

      ​	</style>

      ​	选择文档中的div元素为其设置样式

      CSS	选择器 ：

      ​	由选择符/器 和 样式规则组成

      ​	选择符用来

      ​				规范页面中那些元素需要设置样式

      ​	样式规则   具体的样式声明

   4. 外链方式引入CSS代码

      1. 创建外部的CSS文件  index.css
      2. 使用 <link rel="stylesheet" href="url">,书写在<head>标签中
      3. 样式表中采用选择器去声明样式

## 补充元素

5. 补充元素分类
   1. 块级元素：

      独占一行，不与其他元素共行，可以设置宽高

      代表元素 ： div  hn  p  ul  ol  li  table  form ..

   2. 行内元素：

      可以与其他元素共行，不可以设置宽高

      代表元素 ： span  label  a  strong  i  b  sub  sup

   3. 行内块元素:

      既可以与其他元素共行，又可以设置宽高

      代表元素 ： img  input

   4. CSS样式表的特点：

      1. 层叠性

         可以对同一个元素设置多个不同的样式规则，共同起作用

      2. 继承性

         字元素可以继承父程序中设置的样式

         例如 ： 块元素  默认   宽度与父元素保持一致，

         文本属性都可以被继承

      3. 优先级

         在样式声明发生冲突的时候，需要考虑优先级

         从低到高  ： 浏览器样式	低

         ​			文档内嵌/外链形式引入		中  （这两种样式冲突时，

         ​					根据代码的书写顺序决定最终样式，后来者居上）

         ​			行内样式		高

## CSS选择器



6. CSS选择器 （重点）
   1. 作用：规范页面中那些元素可以设置样式

   2. 分类 ：

      1. 标签选择器/元素选择器

         标签名{

         ​	属性：值；

         ​	属性：值；

         }

         作用 ：根据标签名在文档中匹配所有的该元素，并为其添加样式

      2. ### id 选择器

         作用：根据元素id 属性值进行匹配

         语法：

         ​	<h1 id="redText"></h1>

         ​	.#redText_1{

         ​		属性：值；

         ​	}

         特点：

         1. 命名规范  ID  值不能以数字和下划线开头，推荐以字母开头，可以出现下划线和数字
         2. 选择符 以 # 开头，跟上 ID 属性值
         3. id 属性具有唯一性， id 值不能出现重复
         4. 常用来划分外围结构

      3. ### 类选择器

         作用：根据元素的class 属性值进行匹配，可以实现样式复用

         语法： <h1class="redText2"></h1>

         ​		.redText2{

         ​			属性：值；

         ​			}

         特点 ：

         1. 命名规范 不允许以数字和下划线开头，推荐小写字母开头，由

            数字下划线组成，大小写敏感

            1. 以 . 开头跟上class 属性值作为选择符
            2. 允许重复使用class值，实现样式复用

         特殊用法 ：

         1. class 的属性值可以出现多个，使用空格分隔

            <h1 class="redText Green"></h1>

         2. 组合使用，缩小匹配元素范围

         p.orangeText  表示在p 元素中查找类名为orangeText 的元素

         注意 ： 标签选择器与其他选择器结合，标签名一定要写在前面

      4. ### 群组选择器

         为一组元素共同设置样式

         div , h1, p{

         ​	width : 200px;

         }

         body, h1, p{

         ​	margin :0;

         ​	}

      5. ### 后代选择器

         为后代元素设置样式

         语法： 父元素 子元素{

         ​					属性：值；

         ​				}

         注意：

         1. 父元素与字元素之间使用空格隔开

            1. 后代元素包含直接字元素和间接子元素

             <ul>

             ​	<li>

             ​		<a></a>

             ​	</li>

             ​	<li>

             ​		<ol>

             ​			<li></li>

             ​		</ol>

             ​	</li>

             </ul>

             ul li{

             ​	color:red;

             }

      6. ### 子代选择器

         ​	用来匹配父元素中指定的直接元素

         ​	语法 ：父元素>字元素 {

         ​						属性 ： 值；

         ​						}

         注意 ： 只会匹配直接后代元素

      7. ### 通配符选择器

         ​	*表示匹配文档中所有元素

         ​	*{

         ​		margin : 0;

         ​		padding : 0;

         ​	}

         设置文档中所有元素的内外边距为0

      8. ### 伪类选择器

         为元素的不同状态设置样式

         以 ： 开头

         1. 分类：

            超链接伪类选择器

            动态伪类选择器

         2. 超链接伪类：

            ：link  表示超链接未被访问时的状态

            ：visited  表示超链接被访问后的样式

         3. 动态伪类：

            ：hover  鼠标悬停时的状态

            ：active  鼠标点按时的状态

            ：focus  元素获取到焦点时的样式，常用于输入框

         4. 注意：

            ​	如果给超链接设置四种状态的样式，必须按照以下顺序书写伪类

            ​	a:link

            ​	a:visited

            ​	a:hover

            ​	a:active

            ​	简称 LVHA 爱恨原则



# CSS_day02



# 

1. 选择器的优先级

   根据选择器的权重（值）进行优先级判断

   id  选择器  				100

   class 选择器/伪类选择器	10

   标签选择器				1

   注意 ： 

   1. 组合选择器的权重，由各个选择器的权重相加得到

   2. 选择器的优先级与书写顺序无关，只看权重

   3. 行内样式的优先级最高

      。#h1{

      color = blue;

      ​	}

      <h1 style="color:red;">

## 尺寸

1. 

2. 尺寸与边框

   1. 尺寸单位：

      1. px  像素，最常用的单位，也是浏览器默认单位
      2. % 百分比  占据父元素对应属性的占比

      ---------------以下为绝对单位，不常用-----

      1. In  英寸 1 in  = 2.54 cm 
      2. pt  磅   1  pt  =  1/72  in 
      3. cm 厘米
      4. mm  毫米

      注意 ： CSS中的尺寸单位是不能省略的，0 除外。

   2. 颜色单位 :

      1. 取值英文单词 red green blue ...

      2. 取值十六进制 # aabbcc

         每两位一组代表一种三原色，

         三组分别对应红绿蓝

         每一位取值范围 0-9  a-f

      3. 短十六进制#abc

         由三位组成，每一位就代表了一种三原色

         浏览器在渲染时会自动对每一位进行重复，补全

         成六位的十六进制

         。#abc = #aabbcc

      4. CSS  提供的颜色表示法

         rgb( r,g,b )  每个值取值 0 - 255

         红色 rgb(255,0,0) # f 0 0

      5. CSS 提供的颜色表示法

         rgba(r,g,b,alpha)  颜色取值  0 -255

         alpha  表示透明度  取值 0- 1（透明 - 不透明）

   3. 尺寸属性

      1. 作用：

         改变元素的宽度和高度

         属性 width height

         取值为数值，单位为 px  或  %

      2. 使用  ：

         所有的块级元素可以设置宽高，默认情况宽度与

         父元素保持一致，高度由内容决定；

         所有的行内元素不可以设置宽高，大小由内容决定

      3. 内容溢出处理：

         属性 ： overflow

         取值 ：

         1. visible  默认值，溢出部分可见

         2. hidden  溢出部分隐藏不可见

            . scroll	设置内容滚动条

         3. auto  自动当内容溢出时，自动添加滚动条并且可用

            注意 ： scroll  表示显示水平和垂直方向的滚动条，不管是否真的需要

            ​		auto  根据内容需要，添加水平或者垂直方向的滚动条

## 边框

1. 

2. 

3. 

4. 边框  

   1. 属性  border  

   2. 取值   border-width   border - style

      border - color  三个取值缺一不可

      ```
      eg :  border :  spx   solid   red;
      
      		边框
      
      	border - width :  设置边框线的宽度
      
      	border - style :  设置边框的样式 ，取值
      
      		1. solid  实线
      
      		2. dashed 虚线
      
      		3. dotted 点线
      
      		4. double  双线 （不常用）
      
      	border - color  :  颜色值， 可以使用 transparent    表示透明色
      ```

   3. 特殊用法

      取消边框  border :  none;

   4. 单边框设置 ：

   border  属性用来设置上右下左四个方向的边框

   四个方向单独设置边框 ：

   border - top  :  5px  solid   red;

   border - right  :  10px solid  green;

   border - bottom :  4px solid  gray;

   border - left : 1px solid blue;

   1. 网页三角标制作

      1. 元素尺寸为0
      2. 为元素添加四个方向的边框
      3. 设置其中三条边框颜色为透明 transparent 

   2. 圆角边框

      属性 ： border - radius

      取值 ： px或 %

      作用：将边框的值变成圆角

      ```
      eg :
      				border-radius : 10px; 表示四个角都按照10px的半径去生成圆角
      				border-radius : 5px 10px 15px 20px; 四个值代表了上右下左四个角
      				border-radius : 10px 20px; 第一个值表示上下,第二个值表示左右
      				border-radius : 5px 10px 15px; 第四个值默认跟第二个值一致
      				注意 : 
      				边框圆角在元素不设置边框的情况下依然有效,可以通过设置 50% 呈现圆形或椭圆形,修改元素显示形状
      ```

   3. 边框阴影

      属性 box - shadow  :   h - offset v- offset  blur

      ​	spread  color;

      h - offset  :  阴影的水平偏移距离取值为数字    取值为正，阴影向右偏移

      ​			取值为负， 阴影向左偏移

      v - offset :  阴影的垂直偏移距离  取值为数字  取值为正 ， 阴影向下偏移

      ​									取值为负， 阴影向上偏移

      blur :  阴影的模糊程度   取值为数字   值越大， 越模糊

      spread : 阴影扩大或是缩小的距离  取值为数字   取值为正  阴影会扩大   取值为负 阴影会收缩

      color : 设置阴影颜色

   4. 浏览器坐标系

      浏览器左上角为原点，向右向下为x轴和Y轴正方向，向左向上为负方向

## 盒模型/框模型

1. 

2. 

3. 

4. 

5. 盒模型/框模型

   1. 元素皆为框

      ​	盒模型 ：元素在文档中占据尺寸的计算方式

      ​	组成： 外边距 margin 边框 border  内边距 padding  内容尺寸

      ​		计算方式  ： 标准盒模型 ： 最终width = 左右外边距 + 左右内边距 + 内容宽度

      ​			最终height = 上下外边距 + 上下内边距 + 内容高度

      ​	（了解） 怪异盒模型 :

      ​			元素内容宽度 = 左右内边距 + 边框 + 内容

      ​	e.g:

      ​		div{

      ​			width : 200px;

      ​			height : 200px;

      ​			border : 10px solid red;

      ​			margin : 10px;

      ​			padding : 10px;

      ​		}

      ​	标准盒模型下：

      ​		占据宽度 （260） = 200+10*2+ 10 * 2 + 10 * 2 

      ​	怪异盒模型下 ：

      ​		占据宽度 （220）= 200 +10*2

   2. 外边框 margin 

      1. 元素边框与边框之间的距离

      2. 语法

         1. 属性 margin

         2. 取值 ：

            margin : 10px; 表示上右下左四个方向设置10px的外边距

            margin : 10px 20px;  上下为10  左右为 20

            margin :10px 20px 30;  上下分别为 10  30 ,左右为20

            margin : 10px 20px 30px 40;  设置上右下左四个方向的外边距

         3. 特殊值

            margin : 0  auto;

            表示自动，可以用来设置元素居中

         4. margin 取值可以分正负

            正值  就代表正方向

            负值  就代表负方向

            margin  设置为负值  元素将进行偏移

         5. 四个方向单独设置外边距

            margin - top  设置上方的外边距

            margin - right  设置右边的外边距

            margin - bottom  设置底部外边距

            margin - left  设置左边外边距

            取值同样是数值，取一个值

         6. 具有默认外边距的元素 ：

            nody,h1,h2,h3,h4,h5,h6,p,ul,ol{

            ​		margin:0;

            }

      3. 内边距 padding 

         1. 元素内容与元素边框之间的距离

            通过设置width  height  属性，实际上设置的是元素内容框的大小 

         2. 使用

            1. 属性 padding

            2. 取值   数值，  可以给定 1 /  2/  /3   /4 个值

               ​			padding : 2px;

               ​			上右下左四个方向都为2px 的内边距

               ​			padding  :   10px  20px;

               ​			padding  :   10px  20px  30px;

               ​			padding  :   10px  20px  30px  40px;

         3. 具有默认内边距的元素

            ol., ul,  input ( 文本框，密码框，按钮会存在)

            ol, ul, input {

            ​	padding:0;

            }

            页面开发时，清除浏览器的默认边距

            body, ul, ol, h1, h2, h3, h4, h5,h6, p{

            ​	margin : 0;	

            ​	padding : 0;

            }

            input  可以根据需求单独设置

         4. 盒模型属性的支持度

            1. 盒模型属性 ： margin border padding  width  height

            2. 块元素对盒模型属性完全支持

            3. 行内元素对盒模型属性部分支持：

               ​	行内元素可以设置  左右的内外边距 不可以设置  宽高 及上下内外边距

         5. 元素类型转换

            属性 display

            取值 ： 

            ​	inline  行内元素

            ​	block 块元素哦

            ​	none  元素隐藏

         6. 文本居中显示

            水平居中 ： text - align : center;

            垂直居中 ： 设置元素 高度height

            与行高line-height  保持一致



# CSS_day03







1. 边框尺寸

   1. 轮廓线

      outline

      默认情况下文本框密码框都带有轮廓线

      取消轮廓线 outline :  none;

   2. box-sizing

      改变元素尺寸的计算方式

      1. 默认值尺寸的计算方式

         元素实际尺寸 由margin + border + padding + width/height  计算得到

      2. 取值 border-box

         元素实际尺寸 width = margin + border + padding + 内容；

         一旦为元素设置边距和边框，会压缩内容区域

## 背景属性

1. 

2. 背景属性

   1. 背景颜色

      属性 background-color

      取值 颜色值

   2. 背景图片

      属性 background-image

      取值 url (路径)

   3. 背景图片相关属性

      1. 背景图片重复平铺显示

         属性 background-repeat

         取值 ：

         1. repeat  默认值，图片尺寸不够时，沿水平和垂直方向重复平铺
            1. repeat-x 沿水平方向平铺
            2. repeat-y 沿垂直方向平铺
            3. no-repeat  不平铺

      2. 背景图片尺寸

         1. 属性 background-size

         2. 取值 ：

            1. px  分别设置背景图片宽高

            2. % 采用当前元素的尺寸比作为背景图片的尺寸

               ------了解

            3. cover  表示对图片等比缩放至完全覆盖元素，多出则裁剪掉

            4. contain  对图片等比缩放至刚好容纳图片，不足部分不管

            5. suto 自动

      3. 背景图片位置

         1. 属性  background-postition

         2. 取值 ：

            1. 数值 px ：x  y  设置水平和垂直方向的偏移距离

            2. x%  y%

               0% 0% 表示图片在左上角显示

               100% 100%  图片在右下角显示

               50% 50% 背景图片居中

            3. 方位值表示  

               top  center  bottom

               left center right

               设置背景图片水平和垂直方向的显示位置，某一个方向缺省的话，

               默认为center

      4. 背景图片是否固定

         属性 background -attachment

         设置背景图片是否跟随页面滚动

         取值 ：

         1. scroll 默认值  跟随滚动
         2. fixed  固定背景图片位置
            1. 给任何元素添加背景图片固定，

         ```
         当前背景图片是相对于视口viewport 和当期容器元素几乎没有关系
          
         2. 当容器元素不可见时，背景图片也不可见
         ```

   4. 背景属性简写

      属性 background 

      取值 color url  position repeat  size  attachment

      eg. :

      ​	background: red  url ("")  right

      ​	no - repeat scroll

      background-size 是css3 属性，需要单独设置

## 字体/文本属性

1. 

2. 

3. 字体/文本属性

   1. 指定字体

      font - family  ： "微软雅黑","黑体"，Ａｒｉａｌ；

      注意 ：当字体名称是中文，或者是由多个英文单词组成的，都需要添加引号

   2. 字体粗细

      font - weight:

      取值：

      1. lighter (100) / normal (400) / bold(700)
      2. 采用数字，无单位，取值100-900，值越大，字体越粗

   3. 字体大小

      font - size

      取值  16px

   4. 字体样式 (斜体)

      font - style

      取值 ： 

      1. normal
         1. italic  斜体
            1. oblique  字体倾斜  显示效果与斜体一致

   5. 行高

      line - height

      常用于设置文本垂直居中

   6. 字体属性简写

      使用简写，有必填的属性值 family

      font : style weight size family;

      font : family size/line - height;

      注意：

      font-weight  font-style 必须设置在 font - size  之前

      同时设置字体大小和行高，必须写成一个属性值存在， size/line-height

   7. 文本颜色

      color

   8. 文本装饰线

      text-decoration

      取值  ：

      1. underline 下划线
         1. none 取消装饰线
         2. overline 上下划线
         3. line-through  删除线

   9. 首行缩进

      text-indent

      取值 像素值  或者以 em 为单位  lem = 元素字体大小



## 表格属性

1. 

2. 

3. 

4. 表格属性

   1. 表格添加边框

      border: 1px solid black;

   2. 表格边框合并

      属性  border - collapse

      取值 ：

   ```
   1. separate  (默认边框分离)
   ```

   1. Collapse  （边框合并）

   2. 边框边距

      设置单元格之间的距离

      ```
      属性 ： border - spacing
      
      取值 ：
      
      1. 指定一个数值水平与垂直方向上间距相等
      ```

      1. 指定两个数值分别设置水平方向与垂直方向上单元格之间的距离

   注意 ：属性必须在边框分离的情况下使用



## 列表属性

1. 

2. 

3. 

4. 

5. 列表属性

   1. 列表特征：

      1. 无序列表和有序列表  存在上下外边距
      2. 存在左边的内边距
      3. 具备项目符号
      4. 列表项垂直

   2. 列表属性

      属性 

      1. list - style-type  设置项目符号

      2. list - style - position :

         设置项目符号的位置  默认 outside 项目符号与内容框分离，设置inside 可以将项目符号调整到内容框中。不常用

      3. list - style - inage  ：url()自定义项目符号

         属性简写：

         ```
         list - style : type image postition;
         
         常用的取消列表项目样式；
         
         list - style : none;
         ```



## 过渡效果

1. 

2. 

3. 

4. 

5. 

6. 过渡效果

   1. 过渡效果指的是CSS 属性在一段时间内平缓变换的效果

   2. 语法

      1. 指定过渡属性

         指定哪个属性在变化的时候使用过渡效果

         transition - property  :

         取值  ：

         1. all  但凡能够使用过渡效果的属性值在变化时一律使用过渡效果来体现

         2. 单独设置属性，指定某一个属性在变化时使用过渡效果

            ​	允许使用过渡效果的属性

            1. 颜色相关的设置
            2. 取值为数字的属性

      2. 指定过渡时长

         transtion - duration 

         指定在多长时间内完成过渡效果

         取值 ： 以 s  或者 ms  为单位的数值  1s  =  1000ms

         ​			500ms  =  0.5s  = .5s

      3. 指定过渡的速度时间曲线函数

         transition - timing - function 

         取值 ： 

         1. ease 默认值  慢速   慢速开始，快速变快，缓慢结束
            1. linear   匀速变换
            2. ease - in 慢速开始， 加速结束
            3. ease - out  快速开始， 慢速结束
            4. ease - in - out 慢速开始和结束，中间先加速后减速的过程

      4. 指定过渡效果的延迟时间

         等激发过渡效果之后，等待多久开始执行

         transition - delay

         取值 以 s 或者 ms 为单位的数值

      5. 属性简写

         transition : property  duration

         timing - fun  delay;

      6. 练习

         创建 200 *200 的元素， 背景为红色

         鼠标悬停时：

         1. 尺寸变为400*400
            1. 背景颜色变成橘色
            2. 变成圆形

      属性值的变换需要在5s 内完成



## 布局方式 （重点掌握）

1. 

2. 

3. 

4. 

5. 

6. 

7. 布局方式（重点掌握）

   1. 布局方式影响页面整体结构划分和元素的显示样式

   2. 布局方式分类

      1. 文档流布局/普通流/静态流 

         默认的布局方式

         元素按照书写顺序 及元素类型，从上到下，从左到右排列

      2. 浮动布局（重难点）

      3. 定位布局

         1. 绝对定位
         2. 相对定位
         3. 固定定位

   3. 浮动布局

      最常用的布局方式

      1. 将元素设置浮动你之后，元素会具备以下特点：

         1. 元素会脱离文档流，不会占据文档空间
         2. 剩余未浮动元素会上前占位
         3. 元素浮动时，会停靠在父元素的左边或右边，或者是其他的浮动元素边缘上
         4. 元素浮动只能在当前行浮动
         5. 浮动可以解决共行问题，也可以解决行内块元素水平间隙的问题

      2. 语法

         属性 float

         取值 ：

         1. left  元素向左浮动，碰到其他元素的边框时停止
            1. right 元素向右浮动，碰到其他元素的边框停止
               1. none 默认值，元素未浮动

      3. 浮动引发的效果

         1. 如果父元素中无法容纳浮动元素，浮动元素会自动换行显示
         2. 元素一旦设置浮动，便可以设置宽高，主要针对行内元素
         3. 元素一旦浮动，默认尺寸由内容决定
         4. 文字环绕效果如果前一个元素设置浮动，后面元素会上前占位，并且后面元素的文本会环绕浮动元素显示



# CSS_day04

# 

1. 浮动元素带来的影响及解决

   1. 由于浮动元素脱离文档流，在文档中不占位，所以在父元素中也相当于不存在，而父元素的高度是以未浮动元素的高度为准的，所以一旦所有子元素浮动，会造成父元素高度塌陷。

   2. 解决方式 ：

      1. 针对父元素高度塌陷可以采用

         1. 直接给父元素设置高度

            弊端 ：不一定每次都清楚的知道父元素的高度

         2. 给父元素设置浮动 

            弊端 ：影响后面其他元素的布局（不推荐）

         3. 直接给父元素添加 overflow为 hidden 或 auto  

            弊端 ：hidden 如果出现内容溢出，会被隐藏不显示

         4. 清除浮动带来的影响（标准）

            1. 属性 clear 

               在正常元素中使用

            2. 解决父元素高度塌陷，还可以解决浮动元素遮挡正常元素的问题

            3. 取值 ：

               1. none  默认不做任何操作
               2. left  清除当前元素前面元素左浮动带来的影响，不会被前面左浮动的元素压在底下
               3. right  清除当前元素前面元素右浮动带来的影响，不会被前面右浮动的元素压在底下
               4. both 清除当前元素前面元素任何一种浮动方式带来的影响

            4. 解决父元素高度塌陷

               在父元素中添加空的子元素，设置子元素清除浮动

               clear : both

               要求必须使用块元素做子元素

## 定位布局

1. 

2. 定位布局

   1. 属性  ：position

   2. 取值 ：

      1. relative  相对定位
      2. absolute  绝对定位
      3. fixed       固定定位
      4. static  静态布局 (默认值)

   3. 偏移属性

      作用 ：配合已定位元素实现位置移动

      元素设置position 属性为 relative / absolute / fixed 都被成为已定位元素

      属性 ：top / right  / bottom  / left  

      取值 ：像素值

      ​	top  :  以元素上边为基准进行偏移

      ​	right : 以元素右边为基准进行偏移

      ​	bottom: 以元素下边为基准进行偏移

      ​	left : 以元素左边为基准进行偏移

   4. 相对定位

      1. 元素会相对于它在文档中的原来进行偏移

      2. 练习

         创建一个页面

         创建 ul 及 四个列表项 li 

         ​	每个li 100 *30 ,设置背景颜色，左浮动， 10px 的右外边距

         使用相对定位实现 ：

         ​	当鼠标悬停在li上li 元素实现向左上偏移10px

         同样效果，使用外边距实现

      3. 元素使用相对定位进行偏移，在文档中始终占据原本的位置，一经偏移，会遮挡其他元素

#### 绝对定位 （重点)



5. 绝对定位 （重点）

1. 特点：

   1. 元素使用绝对定位，会脱离文档流，在文档中不再占位
   2. 绝对定位的元素会参照距它最近的一个已经定位的祖先元素进行偏移
   3. 如果没有已经定位的祖先元素，元素会参照body 进行定位

2. 语法：

   属性 position

   取值 absolute

   配合偏移属性实现定位

3. 注意

   1. 由于绝对定位元素会脱离文档流，所以在使用绝对定位时，一般按照 父元素相对定位，

      子元素绝对定位的原则进行布局 --- 父相子绝

   2. 元素脱离文档流之后，都可以设置宽高（针对行内元素）

1. 固定定位

   1. 元素一旦设置固定定位，会被固定在浏览器窗口的某个位置，不会跟随网页滚动而发生位置的改变

   2. 语法

      属性  position

      取值 fixed

      配合偏移属性进行定位布局

   3. 注意

      1. 固定定位的元素永远都是相对于body 实现位置初始化
      2. 元素位置固定定位，就会变成块级元素

2. 元素堆叠次序

   1. 已定位的元素们堆叠在一起的排列顺序

   2. 语法

      属性 z - index

      取值 数字，无单位，值越大，元素越靠上

   3. 注意 ：

      1. 只有已经定位的元素 position : relative / absolute / fixed , 才能设置 z- index ,否则不起作用
      2. 父子元素之间，无论如何修改 z - index ,永远都是子元素在上，父元素在下
      3. 如果 z - index 取值相同，后来者居上

3. 元素隐藏与显示

   1. 元素的显示方式

      1. 元素以什么形式显示在页面中（行内/行内块/块）

      2. 语法 ：

         display : none / inline / block/ inline-block

         取值 : 

         1. none  

            元素隐藏不显示，在文档中不占位

            1. inline 显示为行内元素

            2. block 显示为块内元素

            3. inline - block 显示为行内块元素

               行内块元素兼具行内元素与块元素的特征，既可以共行，也可以设置宽高 img input

   2. 元素显示效果

      1. 可见性设置

         属性  visibility

         取值 ：

         1. visible 默认值 可见的

         2. hidden  隐藏，元素隐藏仍然在文档中占位 

            对比 display : none 与 visiblity : hidden  : 

            同样设置元素隐藏，前者不占位，后者依旧在文档中占位

      2. 透明度设置

         属性 opacity 透明度

         取值 0 (完全透明 )  ~  1 ( 不透明 )

         对比 rgba () 与 opacity 设置透明度， 二者的区别：

         rgba () 设置的半透明效果不会被子元素继承；

         opacity 设置的半透明效果会被子元素继承下来，如果子元素也使用opacity 设置了透明度，最终子元素的透明度由两个值相乘得到

      3. 元素的垂直对齐方式

         属性 vertical - clign

         取值 top / middle / bottom/ baseline(默认值，基线对齐)

         使用场景 ：

         ​	添加在行内块元素上 img  input ,  用来设置元素两端的文本与当前元素的对齐方式

   3. 光标外观

      属性  cursor 

      取值  

      1. default
         1. pointer  小手形状
            1. text   显示为   I  样式



# CSS_day05

## 转换

1. CSS转换属性

   属性  transform 

   取值  转换函数，如果出现多个转换函数，使用空格隔开

2. 转换原点

   属性 transform - origin

   取值

   1. 关键字 top / bottom / left / right /center
      1. 使用 px 或者 % 指定转换原点
         1. 默认转换原点在元素的中心位置

3. 转换函数

   1. 平移转换

      1. 转换函数   translate ()

      2. 取值

         1. translate (x)

            元素沿x轴水平方向进行移动

            等价于 translatex()

         2. translate (x,y)

            元素沿水平方向移动x,沿垂直方向移动y 

         3. 元素沿垂直方向平移

            reanlateY()

## 缩放

1. 

2. 缩放

   1. 根据比例改变元素大小

   2. 语法

      1. 转换函数   scale ( x ) 表示元素 x 轴 和 y 轴都按照指定比例缩放

      2. scaleX ( x ) 取值为无单位的数字，默认值是1，表示原始尺寸，元素沿 X 轴缩放

         取值 >  1  元素放大的比例

         ​	  取值 在0～1之间， 元素会按照比例缩小

         取值为负值  元素会反转

      3. scaleY （x)  元素沿 Y 轴缩放

## 旋转

1. 

2. 

3. 旋转

   1. 改变元素在文档中的显示角度

   2. 属性 rotate( n  deg )

   3. 取值为带角度单位的数值，eg : 45 deg

      取值为正  表示顺时针旋转

      取值为负 表示逆时针旋转

   4. 注意 ：

      1. 转换原点一旦改变，会影响转换效果
      2. 旋转操作会连带坐标轴一起旋转，会影响其后其他的转换操作



