# 第一部分 Python基础篇（80题）

## 1. 为什么学习Python？

1. Python在生物信息学分析中属于首选语言
2. 我之前学习过C，接触了Python以后发觉它更适合我这种生物出身的人
3. 人生苦短，我用Python

## 2. 通过什么途径学习的Python？

- 书籍：
  - 《Python核心编程》
  - 《Python cookbook》
- 视频
  - 教学视频很多的
- 博客
  - 廖雪峰的博客
  - 阮一峰的博客

## 3. Python和Java、PHP、C、C#、C++等其他语言的对比？

- 代码简洁，易懂
- 面向对象
- 性能慢

## 4. 简述解释型和编译型编程语言？

计算机是不能理解高级语言的，更不能直接执行高级语言，它只能直接理解机器语言，所以使用任何高级语言编写的程序若想被计算机运行，都必须将其转换成计算机语言，也就是机器码。而这种转换的方式有两种：编译、解释

由此高级语言也分为编译型语言和解释型语言。

### 编译型语言

使用专门的编译器，针对特定的平台，将高级语言源代码一次性的编译成可被该平台硬件执行的机器码，并包装成该平台所能识别的可执行性程序的格式。

**特点**
在编译型语言写的程序执行之前，需要一个专门的编译过程，把源代码编译成机器语言的文件，如exe格式的文件，以后要再运行时，直接使用编译结果即可，如直接运行exe文件。因为只需编译一次，以后运行时不需要编译，所以编译型语言执行效率高。

**总结**

- 一次性的编译成平台相关的机器语言文件，运行时脱离开发环境，运行效率高；
- 与特定平台相关，一般无法移植到其他平台；

- 现有的C、C++、Objective等都属于编译型语言。




### 解释型语言

使用专门的解释器对源程序逐行解释成特定平台的机器码并立即执行。

**特点**
解释型语言不需要事先编译，其直接将源代码解释成机器码并立即执行，所以只要某一平台提供了相应的解释器即可运行该程序。

**总结**

- 解释型语言每次运行都需要将源代码解释称机器码并执行，效率较低；
- 只要平台提供相应的解释器，就可以运行源代码，所以可以方便源程序移植；

- Python等属于解释型语言。





## 5. Python解释器种类以及特点？

**CPython**

当我们从Python官方网站下载并安装好Python 2.7后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。

> CPython是使用最广且被的Python解释器。教程的所有代码也都在CPython下执行。

**IPython**

IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了IE。

CPython用>>>作为提示符，而IPython用In [序号]:作为提示符。

**PyPy**

PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用JIT技术，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。

绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解PyPy和CPython的不同点。

**Jython**

Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

**IronPython**

IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。



## 6. 位和字节的关系？

#### 位

我们常说的bit，位就是传说中提到的计算机中的最小数据单位：说白了就是0或者1；计算机内存中的存储都是01这两个东西。

#### 字节

英文单词：（byte），byte是存储空间的基本计量单位。

1byte 存1个英文字母，2个byte存一个汉字。

规定上是**1个字节等于8个比特（1Byte = 8bit）。**

#### 字

字就是由一些字符组成的，是据算计处理数据时一次存取，加工和传送的数据长度。

字由若干字节构成，字的位数叫字长，一台8位机子：一个字等于1个字节，字长为8位，如果是16位的机子，一个字等于2个字节，字长为16，字是计算机处理数据和运算的单位。

由此可见，计算机的字长决定了其CPU一次操作处理实际位数的多少，即：计算机的字长越大，其性能越好。





## 7. 请至少列举5个 PEP8 规范（越多越好）

重点 

1. 缩进： 4个空格，配合冒号使用，使用缩进表示作用域
2. 注释：# ，字符串”“” “”” 、”’ ”’ 只有三引号支持多行注释
3. 常规变量命名、函数名、模块名：多个单词之间以下划线隔开 
   例：li_xiao_long = ‘abc’
4. 类  命名，使用大驼峰命名法
5. 模块导入的规范



## 8. 通过代码实现如下转换：

```
二进制转换成十进制：v = “0b1111011”
十进制转换成二进制：v = 18
八进制转换成十进制：v = “011” 
十进制转换成八进制：v = 30
十六进制转换成十进制：v = “0x12” 
十进制转换成十六进制：v = 87
```
``````python
int(“0b1111011”,base=2)
bin(18)
int(“011”,base=8)
oct(30)
int(“0x12”,base=16)
hex(87)
``````





## 9. 请编写一个函数实现将IP地址转换成一个整数。

如 10.3.9.12 转换规则为：
```
10            00001010
3            00000011
9            00001001
12            00001100
```
再将以上二进制拼接起来计算十进制结果：00001010 00000011 00001001 00001100 = ？

``````python
s = '10.3.9.12'
a = s.split('.')
sum_bin = ""
for k in a:
    sum_bin +=bin(int(k))
    print(sum_bin)
``````



## 10. python递归的最大层数？

1000



## 11. 求结果：

``````
v1 = 1 or 3              
v2 = 1 and 3
v3 = 0 and 2 and 1
v4 = 0 and 2 or 1
v5 = 0 and 2 or 1 or 4
v6 = 0 or Flase and 1
``````

``````
1
3
0
1
1
1
``````



## 12. ascii、unicode、utf-8、gbk 区别？

``````
ascii：
A：00000010 8位 一个字节

unicode：
A：00000000 00000001 00000010 00000100 32位 四个字节

中：00000000 00000001 00000010 00000100 32位 四个字节

utf-8：
A：00000110 8位 一个字节

中：00000010 00000110 16位 两个字节

gbk：
A：00000110 8位 一个字节

中：00000010 00000110 16位 两个字节

1，各个编码之间的二进制，是不能互相识别的，会产生乱码。

2，文件的存储，传输，不能是unicode （只能是utf-8 utf-16 gbk gbk2312 ascii等）

python3：
　　str  在内存中是Unicode编码。

　　　　bytes类型

　　　　对于英文：

　　　　　　str：表现形式：s = 'alex'

　　　　　　　　 编码方式：010101010 unicode

　　　　　bytes：表现形式：s = b'alex'

　　　　　　　　  编码方式：000101010 utf-8 gbk。。。。

　　　　对于中文：

　　　　　　 str：表现形式：s = '中国'

　　　　　　　　  编码方式：010101010 unicode

　　　　　bytes： 表现形式：s = b' x\e91\e91\e01\e21\e31\e32'

　　　　　　　　   编码方式：000101010 utf-8 gbk。。。。

　encode 编码，如何将 str ——> bytes

                 　　　　使用方法：  str.encode('utf-8')

　decode 解码，如何将 bytes——> str

                             使用方法：  bytes.decode('utf-8')
``````



## 13. 字节码和机器码的区别？

#### 机器码

**机器码(machine code)**，学名机器语言指令，有时也被称为原生码（Native Code），**是电脑的CPU可直接解读的数据。**

通常意义上来理解的话，机器码就是计算机可以直接执行，并且执行速度最快的代码。

用机器语言编写程序，编程人员要首先熟记所用计算机的全部指令代码和代码的涵义。手编程序时，程序员得自己处理每条指令和每一数据的存储分配和输入输出，还得记住编程过程中每步所使用的工作单元处在何种状态。这是一件十分繁琐的工作，编写程序花费的时间往往是实际运行时间的几十倍或几百倍。而且，编出的程序全是些0和1的指令代码，直观性差，还容易出错。现在，除了计算机生产厂家的专业人员外，绝大多数的程序员已经不再去学习机器语言了。

机器语言是微处理器理解和使用的，用于控制它的操作二进制代码。
8086到Pentium的机器语言指令长度可以从1字节到13字节。
尽管机器语言好像是很复杂的，然而它是有规律的。
存在着多至100000种机器语言的指令。这意味着不能把这些种类全部列出来。

#### 字节码

**字节码（Bytecode）**是一种包含执行程序、由一序列 op 代码/数据对 组成的二进制文件。**字节码是一种中间码，它比机器码更抽象，需要直译器转译后才能成为机器码的中间代码。**

通常情况下它是已经经过编译，但与特定机器码无关。字节码通常不像源码一样可以让人阅读，而是编码后的数值常量、引用、指令等构成的序列。

字节码主要为了实现特定软件运行和软件环境、与硬件环境无关。字节码的实现方式是通过编译器和虚拟机器。编译器将源码编译成字节码，特定平台上的虚拟机器将字节码转译为可以直接执行的指令。字节码的典型应用为Java bytecode。

字节码在运行时通过JVM（JAVA虚拟机）做一次转换生成机器指令，因此能够更好的跨平台运行。

#### 总结

> 1. 机器码是电脑CPU直接读取运行的机器指令，运行速度最快，但是非常晦涩难懂，也比较难编写，一般从业人员接触不到。
> 2. 字节码是一种中间状态（中间码）的二进制代码（文件）。需要直译器转译后才能成为机器码。

## 14. 三元运算规则以及应用场景？

``````
三元运算又称三目运算，是对简单的条件语句的简写，如：

简单条件语句：

if 条件成立:
    val = 1
else:
    val = 2
改成三元运算：

val = 1 if 条件成立 else 2
``````



## 15. 列举 Python2和Python3的区别？

`````
在Python2和Python3中都提供print()方法来打印信息,但两个版本间的print稍微有差异

主要体现在以下几个方面：

1.python3中print是一个内置函数，有多个参数，而python2中print是一个语法结构；

2.Python2打印时可以不加括号：print 'hello world'， Python3则需要加括号   print("hello world")

3.Python2中，input要求输入的字符串必须要加引号，为了避免读取非字符串类型发生的一些行为，不得不使用raw_input()代替input()

下面通过以下几点给大家介绍Python2与Python3的不同点，具体内容如下所述：

1、规范性

1）、在大的环境下，Python2含有PHP、Java、C等语言的规范陋习。（Python是一门开源的语言，任何人都可以贡献代码，但是每个人上传的代码规范都不相同。）

2）、Python2里面重复的代码特别多。

3）、Python3编码规范、清晰、简单，符合Python的宗旨。

2、编码

1）、Python2默认编码是ASCII，只能显示英文，显示中文会报错。想让Python2显示中文，就需在首行添加“# -*- encoding：utf-8 -*-”。

2）、Python3的默认编码就是utf-8，中文和英文都能支持。

3、语法

1）、用户交互：Python2的语法是“ raw_input”，而Python3的语法是“input”。

4、数据类型

1）、Python2里既有 int 类型又有 long int 类型，而Python3里只有 int 类型。
Python2中input的坑

print ("what do you like")
a = input("Enter any content:")
print ("i like",a)
输入字符串时会报错，而在python3中很好地解决了这个问题。
`````



## 16.用一行代码实现数值交换：

``````
a = 1
b = 2
``````

``````
a,b=b,a
``````



## 17. Python3和Python2中 int 和 long的区别？

``````
Python2里既有 int 类型又有 long int 类型，而Python3里只有 int 类型。
``````



## 18.xrange和range的区别？

``````
首先我们看看range: range([start,] stop[, step])，根据start与stop指定的范围以及step设定的步长，生成一个序列。注意这里是生成一个序列。

xrange的用法与range相同，即xrange([start,] stop[, step])根据start与stop指定的范围以及step设定的步长,他所不同的是xrange并不是生成序列，而是作为一个生成器。即他的数据生成一个取出一个。

所以相对来说，xrange比range性能优化很多，因为他不需要一下子开辟一块很大的内存，特别是数据量比较大的时候。

注意：1、xrange和range这两个基本是使用在循环的时候。

     2、 当需要输出一个列表的时候，就必须要使用range了。

``````



## 19.文件操作时：xreadlines和readlines的区别？

``````
file.xreadlines()则直接返回一个iter(file)迭代器，在Python 2.3之后已经不推荐这种表示方法了
``````

## 20.列举布尔值为False的常见值？

``````
0（整型）
0.0（浮点型）
0L(长整型)
0.0+0.0j(复数)
(空字符串)""
(空列表)[]
(空元组)()
(空字典){}
``````

## 21.字符串、列表、元组、字典每个常用的5个方法？

**字符串**

| **方法**                                                     | **描述**                                                     |      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| [string.capitalize()](http://www.runoob.com/python/att-string-capitalize.html) | 把字符串的第一个字符大写                                     |      |
| [string.center(width)](http://www.runoob.com/python/att-string-center.html) | 返回一个原字符串居中,并使用空格填充至长度 width 的新字符串   |      |
| **string.count(str, beg=0, end=len(string))**                | 返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数 |      |
| [string.decode(encoding='UTF-8', errors='strict')](http://www.runoob.com/python/att-string-decode.html) | 以 encoding 指定的编码格式解码 string，如果出错默认报一个 ValueError 的 异 常 ， 除非 errors 指 定 的 是 'ignore' 或 者'replace' | 常用 |
| [string.encode(encoding='UTF-8', errors='strict')](http://www.runoob.com/python/att-string-encode.html) | 以 encoding 指定的编码格式编码 string，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace' | 常用 |
| **string.endswith(obj, beg=0, end=len(string))**             | 检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False. |      |
| [string.expandtabs(tabsize=8)](http://www.runoob.com/python/att-string-expandtabs.html) | 把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8。 |      |
| **string.find(str, beg=0, end=len(string))**                 | 检测 str 是否包含在 string 中，如果 beg 和 end 指定范围，则检查是否包含在指定范围内，如果是返回开始的索引值，否则返回-1 |      |
| **string.format()**                                          | 格式化字符串                                                 |      |
| **string.index(str, beg=0, end=len(string))**                | 跟find()方法一样，只不过如果str不在 string中会报一个异常.    |      |
| [string.isalnum()](http://www.runoob.com/python/att-string-isalnum.html) | 如果 string 至少有一个字符并且所有字符都是字母或数字则返回 True,否则返回 False |      |
| [string.isalpha()](http://www.runoob.com/python/att-string-isalpha.html) | 如果 string 至少有一个字符并且所有字符都是字母则返回 True,否则返回 False |      |
| [string.isdecimal()](http://www.runoob.com/python/att-string-isdecimal.html) | 如果 string 只包含十进制数字则返回 True 否则返回 False.      |      |
| [string.isdigit()](http://www.runoob.com/python/att-string-isdigit.html) | 如果 string 只包含数字则返回 True 否则返回 False.            |      |
| [string.islower()](http://www.runoob.com/python/att-string-islower.html) | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False |      |
| [string.isnumeric()](http://www.runoob.com/python/att-string-isnumeric.html) | 如果 string 中只包含数字字符，则返回 True，否则返回 False    |      |
| [string.isspace()](http://www.runoob.com/python/att-string-isspace.html) | 如果 string 中只包含空格，则返回 True，否则返回 False.       |      |
| [string.istitle()](http://www.runoob.com/python/att-string-istitle.html) | 如果 string 是标题化的(见 title())则返回 True，否则返回 False |      |
| [string.isupper()](http://www.runoob.com/python/att-string-isupper.html) | 如果 string 中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False |      |
| **string.join(seq)**                                         | 以 string 作为分隔符，将 seq 中所有的元素(的字符串表示)合并为一个新的字符串 |      |
| [string.ljust(width)](http://www.runoob.com/python/att-string-ljust.html) | 返回一个原字符串左对齐,并使用空格填充至长度 width 的新字符串 |      |
| [string.lower()](http://www.runoob.com/python/att-string-lower.html) | 转换 string 中所有大写字符为小写.                            |      |
| [string.lstrip()](http://www.runoob.com/python/att-string-lstrip.html) | 截掉 string 左边的空格                                       |      |
| [string.maketrans(intab, outtab\])](http://www.runoob.com/python/att-string-maketrans.html) | maketrans() 方法用于创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。 |      |
| [max(str)](http://www.runoob.com/python/att-string-max.html) | 返回字符串 *str* 中最大的字母。                              |      |
| [min(str)](http://www.runoob.com/python/att-string-min.html) | 返回字符串 *str* 中最小的字母。                              |      |
| **string.partition(str)**                                    | 有点像 find()和 split()的结合体,从 str 出现的第一个位置起,把 字 符 串 string 分 成 一 个 3 元 素 的 元 组 (string_pre_str,str,string_post_str),如果 string 中不包含str 则 string_pre_str == string. |      |
| **string.replace(str1, str2,  num=string.count(str1))**      | 把 string 中的 str1 替换成 str2,如果 num 指定，则替换不超过 num 次. |      |
| [string.rfind(str, beg=0,end=len(string) )](http://www.runoob.com/python/att-string-rfind.html) | 类似于 find()函数，不过是从右边开始查找.                     |      |
| [string.rindex( str, beg=0,end=len(string))](http://www.runoob.com/python/att-string-rindex.html) | 类似于 index()，不过是从右边开始.                            |      |
| [string.rjust(width)](http://www.runoob.com/python/att-string-rjust.html) | 返回一个原字符串右对齐,并使用空格填充至长度 width 的新字符串 |      |
| [string.rpartition(str)](http://www.runoob.com/python/att-string-rpartition.html) | 类似于 partition()函数,不过是从右边开始查找                  |      |
| [string.rstrip()](http://www.runoob.com/python/att-string-rstrip.html) | 删除 string 字符串末尾的空格.                                |      |
| **string.split(str="", num=string.count(str))**              | 以 str 为分隔符切片 string，如果 num有指定值，则仅分隔 num 个子字符串 |      |
| [string.splitlines([keepends\])](http://www.runoob.com/python/att-string-splitlines.html) | 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。 |      |
| [string.startswith(obj, beg=0,end=len(string))](http://www.runoob.com/python/att-string-startswith.html) | 检查字符串是否是以 obj 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查. |      |
| **string.strip([obj])**                                      | 在 string 上执行 lstrip()和 rstrip()                         |      |
| [string.swapcase()](http://www.runoob.com/python/att-string-swapcase.html) | 翻转 string 中的大小写                                       |      |
| [string.title()](http://www.runoob.com/python/att-string-title.html) | 返回"标题化"的 string,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle()) |      |
| **string.translate(str, del="")**                            | 根据 str 给出的表(包含 256 个字符)转换 string 的字符,要过滤掉的字符放到 del 参数中 |      |
| [string.upper()](http://www.runoob.com/python/att-string-upper.html) | 转换 string 中的小写字母为大写                               |      |
| [string.zfill(width)](http://www.runoob.com/python/att-string-zfill.html) | 返回长度为 width 的字符串，原字符串 string 右对齐，前面填充0 |      |

**列表**

| 序号 | 方法                                                         |      |
| :--: | ------------------------------------------------------------ | :--: |
|  1   | [list.append(obj)](http://www.runoob.com/python/att-list-append.html) 在列表末尾添加新的对象 | 常用 |
|  2   | [list.count(obj)](http://www.runoob.com/python/att-list-count.html) 统计某个元素在列表中出现的次数 |      |
|  3   | [list.extend(seq)](http://www.runoob.com/python/att-list-extend.html) 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表） | 常用 |
|  4   | [list.index(obj)](http://www.runoob.com/python/att-list-index.html) 从列表中找出某个值第一个匹配项的索引位置 | 常用 |
|  5   | [list.insert(index, obj)](http://www.runoob.com/python/att-list-insert.html) 将对象插入列表 | 常用 |
|  6   | [list.pop([index=-1\])](http://www.runoob.com/python/att-list-pop.html) 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值 | 常用 |
|  7   | [list.remove(obj)](http://www.runoob.com/python/att-list-remove.html) 移除列表中某个值的第一个匹配项 | 常用 |
|  8   | [list.reverse()](http://www.runoob.com/python/att-list-reverse.html) 反向列表中元素 | 常用 |
|  9   | [list.sort(cmp=None, key=None, reverse=False)](http://www.runoob.com/python/att-list-sort.html) 对原列表进行排序 | 常用 |

元祖

| 序号 | 方法及描述                                                   |
| :--: | ------------------------------------------------------------ |
|  1   | [cmp(tuple1, tuple2)](http://www.runoob.com/python/att-tuple-cmp.html) 比较两个元组元素。 |
|  2   | [len(tuple)](http://www.runoob.com/python/att-tuple-len.html) 计算元组元素个数。 |
|  3   | [max(tuple)](http://www.runoob.com/python/att-tuple-max.html) 返回元组中元素最大值。 |
|  4   | [min(tuple)](http://www.runoob.com/python/att-tuple-min.html) 返回元组中元素最小值。 |
|  5   | [tuple(seq)](http://www.runoob.com/python/att-tuple-tuple.html) 将列表转换为元组。 |

字典

| 序号 | 函数及描述                                                   | 备注 |
| :--: | ------------------------------------------------------------ | ---- |
|  1   | [dict.clear()](http://www.runoob.com/python/att-dictionary-clear.html) 删除字典内所有元素 |      |
|  2   | [dict.copy()](http://www.runoob.com/python/att-dictionary-copy.html) 返回一个字典的浅复制 |      |
|  3   | [dict.fromkeys(seq[, val\])](http://www.runoob.com/python/att-dictionary-fromkeys.html) 创建一个新字典，以序列 seq 中元素做字典的键，val 为字典所有键对应的初始值 |      |
|  4   | [dict.get(key, default=None)](http://www.runoob.com/python/att-dictionary-get.html) 返回指定键的值，如果值不在字典中返回default值 | 常用 |
|  5   | [dict.has_key(key)](http://www.runoob.com/python/att-dictionary-has_key.html) 如果键在字典dict里返回true，否则返回false |      |
|  6   | [dict.items()](http://www.runoob.com/python/att-dictionary-items.html) 以列表返回可遍历的(键, 值) 元组数组 | 常用 |
|  7   | [dict.keys()](http://www.runoob.com/python/att-dictionary-keys.html) 以列表返回一个字典所有的键 | 常用 |
|  8   | [dict.setdefault(key, default=None)](http://www.runoob.com/python/att-dictionary-setdefault.html) 和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default |      |
|  9   | [dict.update(dict2)](http://www.runoob.com/python/att-dictionary-update.html) 把字典dict2的键/值对更新到dict里 | 常用 |
|  10  | [dict.values()](http://www.runoob.com/python/att-dictionary-values.html) 以列表返回字典中的所有值 | 常用 |
|  11  | [pop(key[,default\])](http://www.runoob.com/python/python-att-dictionary-pop.html) 删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。 |      |
|  12  | [popitem()](http://www.runoob.com/python/python-att-dictionary-popitem.html) 随机返回并删除字典中的一对键和值。 |      |



## 22.lambda表达式格式以及应用场景？

Lambda 函数又称匿名函数，匿名函数就是没有名字的函数

``````python
>>> lambda x, y : x+y
<function <lambda> at 0x102bc1c80>
``````

应用场景:

1. 函数式编程
2. 闭包



## 23. pass的作用？

Python pass 是空语句，是为了保持程序结构的完整性。pass 不做任何事情，一般用做占位语句 

1. 空语句 do nothing
2. 保证格式完整
3. 保证语义完整

## 24. *arg和**kwarg作用

用`*args`和`**kwargs`只是为了方便并没有强制使用它们.

当你不确定你的函数里将要传递多少参数时你可以用`*args`.例如,它可以传递任意数量的参数:

```python
>>> def print_everything(*args):
        for count, thing in enumerate(args):
...         print '{0}. {1}'.format(count, thing)
...
>>> print_everything('apple', 'banana', 'cabbage')
0. apple
1. banana
2. cabbage
```

相似的,`**kwargs`允许你使用没有事先定义的参数名:

```python
>>> def table_things(**kwargs):
...     for name, value in kwargs.items():
...         print '{0} = {1}'.format(name, value)
...
>>> table_things(apple = 'fruit', cabbage = 'vegetable')
cabbage = vegetable
apple = fruit
```

你也可以混着用.命名参数首先获得参数值然后所有的其他参数都传递给`*args`和`**kwargs`.命名参数在列表的最前端.例如:

```python
def table_things(titlestring, **kwargs)
```

`*args`和`**kwargs`可以同时在函数的定义中,但是`*args`必须在`**kwargs`前面.

当调用函数时你也可以用`*`和`**`语法.例如:

```python
>>> def print_three_things(a, b, c):
...     print 'a = {0}, b = {1}, c = {2}'.format(a,b,c)
...
>>> mylist = ['aardvark', 'baboon', 'cat']
>>> print_three_things(*mylist)

a = aardvark, b = baboon, c = cat
```

就像你看到的一样,它可以传递列表(或者元组)的每一项并把它们解包.注意必须与它们在函数里的参数相吻合.当然,你也可以在函数定义或者函数调用时用*.

<http://stackoverflow.com/questions/3394835/args-and-kwargs>

## 25. is和==的区别

### 简述Python的深浅拷贝以及应用场景？

``````
首先直接上结论：

—–深复制，即将被复制对象完全再复制一遍作为独立的新个体单独存在。所以改变原有被复制对象不会对已经复制出来的新对象产生影响。 

—–而等于赋值，并不会产生一个独立的对象单独存在，他只是将原有的数据块打上一个新标签，所以当其中一个标签被改变的时候，数据块就会发生变化，另一个标签也会随之改变。

—–而浅复制要分两种情况进行讨论：

1）当浅复制的值是不可变对象（数值，字符串，元组）时和“等于赋值”的情况一样，对象的id值与浅复制原来的值相同。

2）当浅复制的值是可变对象（列表和元组）时会产生一个“不是那么独立的对象”存在。有两种情况：

第一种情况：复制的 对象中无 复杂 子对象，原来值的改变并不会影响浅复制的值，同时浅复制的值改变也并不会影响原来的值。原来值的id值与浅复制原来的值不同。

第二种情况：复制的对象中有 复杂 子对象 （例如列表中的一个子元素是一个列表），如果不改变其中复杂子对象，浅复制的值改变并不会影响原来的值。 但是改变原来的值 中的复杂子对象的值  会影响浅复制的值。

对于简单的 object，例如不可变对象（数值，字符串，元组），用 shallow copy 和 deep copy 没区别

复杂的 object， 如 list 中套着 list 的情况，shallow copy 中的 子list，并未从原 object 真的「独立」出来。也就是说，如果你改变原 object 的子 list 中的一个元素，你的 copy 就会跟着一起变。这跟我们直觉上对「复制」的理解不同。
``````



## 26. Python垃圾回收机制？

Python的GC模块主要运用了“引用计数”（reference counting）来跟踪和回收垃圾。在引用计数的基础上，还可以通过“标记-清除”（mark and sweep）解决容器对象可能产生的循环引用的问题。通过“分代回收”（generation collection）以空间换取时间来进一步提高垃圾回收的效率。

[具体的资料在这里](<http://python.jobbole.com/82061/>)

## 27. Python的可变类型和不可变类型？

可变类型（mutable）：**列表，字典**

不可变类型（unmutable）：**数字，字符串，元组**

**这里的可变不可变，是指内存中的那块内容（value）是否可以被改变**

## 28.求结果：

``````python
v = dict.fromkeys(['k1','k2'],[])
v[‘k1’].append(666)
print(v)
v[‘k1’] = 777
print(v)
``````

``````python
# 输出 
{'k1': [666], 'k2': [666]}
{'k1': 777, 'k2': [666]}
``````



### 29.求结果：

``````python
def num():
    return [lambda x:i*x for i in range(4)]
print([m(2) for m in num()])
``````

输出：

`[6,6,6,6]`

### 30. 列举常见的内置函数？

#### 数学相关

- abs(a) : 求取绝对值。abs(-1)
- max(list) : 求取list最大值。max([1,2,3])
- min(list) : 求取list最小值。min([1,2,3])
- sum(list) : 求取list元素的和。 sum([1,2,3]) >>> 6
- sorted(list) : 排序，返回排序后的list。
- len(list) : list长度,len([1,2,3])
- divmod(a,b): 获取商和余数。 divmod(5,2) >>> (2,1)
- pow(a,b) : 获取乘方数。pow(2,3) >>> 8
- round(a,b) : 获取指定位数的小数。a代表浮点数，b代表要保留的位数。round(3.1415926,2) >>> 3.14
- range(a[,b]) : 生成一个a到b的数组,左闭右开。 range(1,10) >>> [1,2,3,4,5,6,7,8,9]

#### 类型转换

- int(str) : 转换为int型。int('1') >>> 1
- float(int/str) : 将int型或字符型转换为浮点型。float('1') >>> 1.0
- str(int) : 转换为字符型。str(1) >>> '1'
- bool(int) : 转换为布尔类型。 str(0) >>> False str(None) >>> False
- bytes(str,code) : 接收一个字符串，与所要编码的格式，返回一个字节流类型。bytes('abc', 'utf-8') >>> b'abc' bytes(u'爬虫', 'utf-8') >>> b'\xe7\x88\xac\xe8\x99\xab'
- list(iterable) : 转换为list。 list((1,2,3)) >>> [1,2,3]
- iter(iterable)： 返回一个可迭代的对象。 iter([1,2,3]) >>> <list_iterator object at 0x0000000003813B00>
- dict(iterable) : 转换为dict。 dict([('a', 1), ('b', 2), ('c', 3)]) >>> {'a':1, 'b':2, 'c':3}
- enumerate(iterable) : 返回一个枚举对象。
- tuple(iterable) : 转换为tuple。 tuple([1,2,3]) >>>(1,2,3)
- set(iterable) : 转换为set。 set([1,4,2,4,3,5]) >>> {1,2,3,4,5} set({1:'a',2:'b',3:'c'}) >>> {1,2,3}
- hex(int) : 转换为16进制。hex(1024) >>> '0x400'
- oct(int) : 转换为8进制。 oct(1024) >>> '0o2000'
- bin(int) : 转换为2进制。 bin(1024) >>> '0b10000000000'
- chr(int) : 转换数字为相应ASCI码字符。 chr(65) >>> 'A'
- ord(str) : 转换ASCI字符为相应的数字。 ord('A') >>> 65

#### 相关操作

- eval() : 执行一个表达式，或字符串作为运算。 eval('1+1') >>> 2
- exec() : 执行python语句。 exec('print("Python")') >>> Python
- filter(func, iterable) : 通过判断函数fun，筛选符合条件的元素。 filter(lambda x: x>3, [1,2,3,4,5,6]) >>> <filter object at 0x0000000003813828>
- map(func, *iterable) : 将func用于每个iterable对象。 map(lambda a,b: a+b, [1,2,3,4], [5,6,7]) >>> [6,8,10]
- zip(*iterable) : 将iterable分组合并。返回一个zip对象。 list(zip([1,2,3],[4,5,6])) >>> [(1, 4), (2, 5), (3, 6)]
- type()：返回一个对象的类型。
- id()： 返回一个对象的唯一标识值。
- hash(object)：返回一个对象的hash值，具有相同值的object具有相同的hash值。 hash('python') >>> 7070808359261009780
- help()：调用系统内置的帮助系统。
- isinstance()：判断一个对象是否为该类的一个实例。
- issubclass()：判断一个类是否为另一个类的子类。
- globals() : 返回当前全局变量的字典。
- next(iterator[, default]) : 接收一个迭代器，返回迭代器中的数值，如果设置了default，则当迭代器中的元素遍历后，输出default内容。
- reversed(sequence) ： 生成一个反转序列的迭代器。 reversed('abc') >>> ['c','b','a']

### 31. filter、map、reduce的作用？

![VDNrdS.jpg](https://s2.ax1x.com/2019/06/08/VDNrdS.jpg)

一图胜千言

## 32. 一行代码实现9*9乘法表

如何安装第三方模块？以及用过哪些第三方模块？

至少列举8个常用模块都有那些？

re的match和search区别？

什么是正则的贪婪匹配？

求结果：  a. [ i % 2 for i in range(10) ]  b. ( i % 2 for i in range(10) )

求结果：  a. 1 or 2  b. 1 and 2  c. 1 < (2==2)  d. 1 < 2 == 2

def func(a,b=[]) 这种写法有什么坑？

如何实现 “1,2,3” 变成 [‘1’,’2’,’3’] ?

### 如何实现[‘1’,’2’,’3’]变成[1,2,3] ?

``````python
In [8]: a = ['1','2','3']

In [9]: b = [int(i) for i in a]

In [10]: b
Out[10]: [1, 2, 3]
``````



比较： a = [1,2,3] 和 b = [(1),(2),(3) ] 以及 b = [(1,),(2,),(3,) ] 的区别？

### 如何用一行代码生成[1,4,9,16,25,36,49,64,81,100] ?

``````python
In [3]: [x*x for x in range(1,11)]
Out[3]: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
``````



### 一行代码实现删除列表中重复的值 ?

集合去重

``````python
In [6]: list(set([1,4,2,2,4,5,2,4,6,1]))
Out[6]: [1, 2, 4, 5, 6]
``````

分布式，



### 如何在函数中设置一个全局变量 ?

利用global声明即可

### logging模块的作用？以及应用场景？

在开发过程中，如果程序运行出现了问题，我们是可以使用我们自己的 Debug 工具来检测到到底是哪一步出现了问题，如果出现了问题的话，是很容易排查的。但程序开发完成之后，我们会将它部署到生产环境中去，这时候代码相当于是在一个黑盒环境下运行的，我们只能看到其运行的效果，是不能直接看到代码运行过程中每一步的状态的。在这个环境下，运行过程中难免会在某个地方出现问题，甚至这个问题可能是我们开发过程中未曾遇到的问题，碰到这种情况应该怎么办？

如果我们现在只能得知当前问题的现象，而没有其他任何信息的话，如果我们想要解决掉这个问题的话，那么只能根据问题的现象来试图复现一下，然后再一步步去调试，这恐怕是很难的，很大的概率上我们是无法精准地复现这个问题的，而且 Debug 的过程也会耗费巨多的时间，这样一旦生产环境上出现了问题，修复就会变得非常棘手。但这如果我们当时有做日志记录的话，不论是正常运行还是出现报错，都有相关的时间记录，状态记录，错误记录等，那么这样我们就可以方便地追踪到在当时的运行过程中出现了怎样的状况，从而可以快速排查问题。

因此，日志记录是非常有必要的，任何一款软件如果没有标准的日志记录，都不能算作一个合格的软件。作为开发者，我们需要重视并做好日志记录过程。





### 请用代码简单实现stack 。

``````python
class Stack(object):
    # 初始化栈为空列表
    def __init__(self):
        self.items = []
 
    # 判断栈是否为空，返回布尔值
    def is_empty(self):
        return self.items == []
 
    # 返回栈顶元素
    def peek(self):
        return self.items[len(self.items) - 1]
 
    # 返回栈的大小
    def size(self):
        return len(self.items)
 
    # 压栈，入栈，进栈
    def push(self, item):
        self.items.append(item)
 
    # 出栈
    def pop(self):
        return self.items.pop()

``````



### 常用字符串格式化哪几种？

　　**第一种**：**最方便的**

　　**缺点：需一个个的格式化**

```
print(‘hello %s and %s‘%(‘df‘,‘another df‘))
```

 

**第二种**：**最好用的**

**优点：不需要一个个的格式化，可以利用字典的方式，缩短时间**

```
print(‘hello %(first)s and %(second)s‘%{‘first‘:‘df‘ , ‘second‘:‘another df‘})
```

**第三种**：**最先进的**

　   **优点：可读性强**

```
print(‘hello {first} and {second}‘.format(first=‘df‘,second=‘another df‘))
```

### 简述 生成器、迭代器、可迭代对象 以及应用场景？

用Python实现一个二分查找的函数。

谈谈你对闭包的理解？

os和sys模块的作用？

如何生成一个随机数？

如何使用python删除一个文件？

谈谈你对面向对象的理解？

Python面向对象中的继承有什么特点？

面向对象深度优先和广度优先是什么？

面向对象中super的作用？

是否使用过functools中的函数？其作用是什么？

列举面向对象中带爽下划线的特殊方法，如：__new__、__init__

如何判断是函数还是方法？

静态方法和类方法区别？

列举面向对象中的特殊成员以及应用场景

1、2、3、4、5 能组成多少个互不相同且无重复的三位数

什么是反射？以及应用场景？

metaclass作用？以及应用场景？

用尽量多的方法实现单例模式。

装饰器的写法以及应用场景。

异常处理写法以及如何主动跑出异常（应用场景）

什么是面向对象的mro

isinstance作用以及应用场景？

写代码并实现：
Given an array of integers, return indices of the two numbers such that they add up to a specific target.You may assume that each input would 
have exactly one solution, and you may not use the same element twice.
Example: 
​          Given nums = [2, 7, 11, 15], target = 9,
​            Because nums[0] + nums[1] = 2 + 7 = 9, 
​           return [0, 1]

json序列化时，可以处理的数据类型有哪些？如何定制支持datetime类型？

json序列化时，默认遇到中文会转换成unicode，如果想要保留中文怎么办？

什么是断言？应用场景？

有用过with statement吗？它的好处是什么？

使用代码实现查看列举目录下的所有文件。

简述 yield和yield from关键字。