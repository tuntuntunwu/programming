# Markdown?

1. markdown是什么？
    - html使用\<tag>内容\</tag>的方式将内容展现成不同的样子，比如：\<h1>内容\</h1>表示一级标题。markdown就是用更简洁的语法代替html这种\<tag>方式，比如：\#&nbsp;内容&nbsp;表示一级标题，代替了\<h1>内容\</h1>的方式。

2. 为什么要用markdown？
    - 相信你能理解markdown带来的快速样式化的好处。如果不能，亲自编写一段文档，你便能有所体会。

3. markdown怎么用？
    - 写作：markdown是纯文本的，你可以在任何地方编写它。
    - 阅读：你可直接阅读其纯文本的内容，markdown的简洁语法并不怎么会妨碍一个文本的可读性，但如果想看它样式化后（解析后）的内容，你需要一个支持markdown显示（具有md解析器）的东西。

4. markdown与html的关系？
    - markdown源于html，其语法只对应实现了html中的一部分\<tag>，但这些\<tag>都实用性极强。
    - 所有的html\<tag>都可被md解析器无差错地解析显示出来。如果你想要一些显示形式，而其难以用markdown语法实现，可直接使用html的\<tag>来实现。一些tips：
        - ***markdown语法中使用反斜杠\转义***
        - ***写作时的&nbsp;空一行，相当于包裹了html的\<p>标签***
        - ***想在解析结果中实现&nbsp;换行（也可使用此实现&nbsp;空一行），写作时应用&nbsp;2个空格（标准规定，但有些md解析器不支持）&nbsp;或&nbsp;\<br />&nbsp;或&nbsp;直接回车（有些md解析器支持）&nbsp;***
        - ***想在解析结果中实现&nbsp;空一格，写作时应用\&nbsp;或用全角的空格（推荐）***

5. 怎么学习、掌握markdown？
    - 以下为markdown的一些语法，是我自己根据“实用性”筛选过后的总结。我想，学习markdown的最佳方法，就是根据你自己的实际情况，用markdown写一个对你而言非常实用的markdown语法总结文档。



[TOC]



**1. 标题**
===========
1.1 一般形式
------------

写作：

```c++
// 1~6个#，必须空一格
# h1  // 有些md解析器会给 # h1（一级标题）添加分割线
## h2
### h3
#### h4
##### h5
###### h6
####### error  // 错误形式
```

解析：

# h1
## h2
### h3
#### h4
##### h5
###### h6
####### error


1.2 多级标题
------------

写作：

```c++
// 至少1个=、-，内容与=、-之间不能有空行
h1
=
h2
-
```

解析：

h1
=
h2
-

<br />



**2. 分割线**
=============
2.1 一般形式
------------

写作：

```c++
// 至少3个-、_
---
___
```

解析：

---
___

<br />



**3. 字体**
===========
3.1 一般形式
------------

写作：

```c++
*i*  // 斜体
**b**  // 粗体
***ib***  // 斜体+粗体
~~s/strike~~  // 删除线
```

解析：

*i*

**b**

***ib***

~~s/strike~~

<br />



**4. 引用**
===========
4.1 一般形式
------------

写作：

```c++
// 1个>
> blockquote  // 写多行时，需要换行操作
> cite
```

解析：

> blockquote  
> cite


4.2 嵌套
--------

写作：

```c++
// n个>
> blockquote
>>> cite
>>>> q
```

解析：

> blockquote
>>> cite
>>>> q

<br />



**5. 代码**
===========
5.1 一般形式
------------

写作：

```c++
// 使用` `包裹
`code`
`samp`
```

解析：

`code`
`samp`


5.2 代码块
----------

写作：

```c++
// 使用``` ```包裹，```必须独占1行
```c++  // 指定语言，可语法高亮
code
samp
int a = 1;
```  //
```

解析：

```c++
code
samp
int a = 1;
```

<br />



**6. 超链接**
=============
6.1 一般形式
------------

写作：

```c++
// [超链接名](超链接地址 "超链接title")
[a](https://www.baidu.com/ "baidu")
```

解析：

[a](https://www.baidu.com/ "baidu")


6.2 引用式
----------

写作：

```c++
// [超链接名][引用标识]
// [引用标识]: 超链接地址 "超链接title"
[a][anyword]
  // 有些md解析器需空行，有些不需要
[anyword]: https://www.baidu.com/ "baidu"  // 不要()
```

解析：

[a][anyword]

[anyword]: https://www.baidu.com/ "baidu"


6.3 快速超链接
----------

写作：

```c++
// 使用< >包裹
<https://www.baidu.com/>
```

解析：

<https://www.baidu.com/>

<br />



**7. 图片**
===========
7.1 一般形式
------------

写作：

```c++
// ![图片名](图片地址 "图片title")
![](https://www.baidu.com/img/bd_logo1.png "baidu")  // 图片名没什么用，可缺省
```

解析：

![](https://www.baidu.com/img/bd_logo1.png "baidu")


7.2 引用式
----------

写作：

```c++
// ![图片名][引用标识]
// [引用标识]: 图片地址 "图片title"
![][anyword0]

[anyword0]: https://www.baidu.com/img/bd_logo1.png "baidu"
```

解析：

![][anyword0]

[anyword0]: https://www.baidu.com/img/bd_logo1.png "baidu"


7.3 带有超链接的图片
--------------------

写作：

```c++
// 将超链接名替换为图片表示
// 一般形式（内链式）
// [![图片名](图片地址 "图片title")](超链接地址 “超链接title”)
// 引用式
// [![图片名](图片地址 "图片title")][引用标识]
// [引用标识]: 超链接地址 "超链接title"
[![](https://www.baidu.com/img/bd_logo1.png "baidu")][anyword]

[anyword]: https://www.baidu.com/  // 图片title会覆盖超链接title，请缺省
```

解析：

[![](https://www.baidu.com/img/bd_logo1.png "baidu")][anyword]

[anyword]: https://www.baidu.com/

<br />



**8. 列表**
===========
8.1 有序列表
------------

写作：

```c++
1. olli  // 必须空一格
2. olli
3. olli
```

解析：

1. olli
2. olli
3. olli


8.2 无序列表
------------

写作：

```c++
- ulli  // 必须空一格
- ulli
- ulli
```

解析：

- ulli
- ulli
- ulli


8.3 任务列表
------------

写作：

```c++
// 支持此语法的md解析器较少
- [x] li
- [ ] li
- [ ] li
```

解析：

- [x] li
- [ ] li
- [ ] li


8.4 嵌套
--------

写作：

```c++
- ulli
    1. olli  // 4个空格
    2. olli
    3. olli
- ulli
    - ullii
    - ullii
    - ullii
- **ulli**
    - ```c++
      // 
      ```
    
    - <https://www.baidu.com/>
    
    - ![](https://www.baidu.com/img/bd_logo1.png "baidu")
```

解析：

- ulli
    1. olli
    2. olli
    3. olli
- ulli
    - ullii
    - ullii
    - ullii
- **ulli**
    - ```c++
      // 
      ```
    
    - <https://www.baidu.com/>
    
    - ![](https://www.baidu.com/img/bd_logo1.png "baidu")

<br />



**9. 表格**
===========
9.1 一般形式
------------

写作：

```c++
|th  | th |  th|
|:---|:---:|---:|  // 至少3个-，:指定文本对齐方式
|  td|td  | td |
| td |  td|td  |
```

解析：

|th  | th |  th|
|:---|:---:|---:|
|  td|td  | td |
| td |  td|td  |


9.2 复杂表格
------------

markdown可实现复杂表格，不过过程繁复且无趣。

请通过[在线表格生成器](http://www.tablesgenerator.com/markdown_tables)生成对应的markdown代码，再贴回你的写作中。

<br />



***1\~9的语法较为常用，md解析器多数都会支持，而对10\~15的语法支持便不是很确定了***

***以下的解析如果不正确，则说明该md解析器不支持相应语法***

**10. 目录**
=====================
10.1 一般形式
-------------

写作：

```c++
[TOC]  // 仅支持标题的一般形式
```

解析：

一个解析的例子在此文章开头处

<br />



# 11. ID与锚点 {#idword}

11.1 ID
-------

写作：

```c++
# 11. ID与锚点 {#idword}  // 只能用在标题上,必须空一格
```

解析：

一个解析的例子在此标题处


11.2 锚点
---------

写作：

```c++
[anchor](#1-标题)  // 没有对应html标签,不能空格
// 有些md解析器会自动为所有标题设置锚点
```

解析：

[anchor](#1-标题)

<br />



**12. 脚注**
============
12.1 一般形式
-------------

写作：

```c++
footnotes[^1]  // 没有对应html标签
  // 有些md解析器需空行，有些不需要
[^1]: 脚注1  // 在文章的最后显示脚注
```

解析：

footnotes[^1]

[^1]: 脚注1

<br />



**13. 定义**
============
13.1 一般形式
-------------

写作：

```c++
dt
: dd  // 空1个或n个格
```

解析：

dt
: dd

<br />



**14. 公式**
============
14.1 一般形式
-------------

写作：

```c++
// markdown全公式 https://blog.csdn.net/jyfu2_12/article/details/79207643
$$ x^{y^z}=(1+{\rm e}^x)^{-2xy^w} $$  // 1个$左对齐，2个$居中
```

解析：

$$ x^{y^z}=(1+{\rm e}^x)^{-2xy^w} $$

<br />
