# Python学习笔记

## 一、基础

注释：`#`
整除：`//` &nbsp;  求余：`%` &nbsp; 求幂：`**`  
十六进制：`0x` &nbsp;  八进制：`0o` &nbsp; 二进制： `0b`

所有变量定义需先赋值

输入输出:

```python
x = input("the life is: ")
print("hello world")
```

类型转换，如：

 ```python
int(object)
float(object)
str(object)
 ```

字符串： `' str '` 或 `"str"`
长字符串： `'''strstrstr'''` 或 `"""strstrstr"""`

字符编码，如：

```python
"Hello,world".encode("ASCII")
"Hello,world".encode("UTF-8")
```

## 二、序列

### 1. 列表,元组和字符串

#### 1.1 列表：

**放在方括号中，可修改**的序列，如：

```python
edward = ['Edward Gaward', 42]
john = ['John Smith', 23]
database = [edward, john]
```

#### 1.2 元组：

**直接逗号分隔或加圆括号，不可变**的序列，如：

```python
x = 1, 2, 3
y = (4, 5, 6)
z = (42,)
```

可利用`tuple(a)`将序列转化为元组

（不可变指不可更改其中部分元素，但可以重新赋值）

#### 1.3 字符串：

**单引号或双引号包裹，不可变**的序列，如：

```python
str = "I'm a long"
```

### 2. 通用序列操作

#### 2.1 索引

0为元素第一位，-1为最后一位，可直接通过 `str[0]` 进行索引。如：

```python
>>> greeting = 'Hello'
>>> greeting[0]
'H'
>>> num = [1,4,577,333]
>>> num[2]
577
```

#### 2.2 切片

本质上是`:`隔开的两个索引，如`str[1:4]`
也可用`str[-3,]` `[,3]`，一直到结尾或开头

另外，可设置步长，如：

```python
>>>number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>>number[0:10:2]
[1, 3, 5, 7, 9]
>>>number[1::4]
[2, 6, 10]
>>>number[::-3]
[10, 7, 4, 1]
```

#### 2.3 相加

同类型可相加，如：

```python
>>> (1, 2, 3)+ (4,)
(1, 2, 3, 4)
>>> [1, 4, 5] + [4]
[1, 4, 5, 4]
>>> 'Hell' + "O"
'HellO'
```

#### 2.4 乘法

序列可与整数相乘：

```python
>>> 'python' * 5
'pythonpythonpythonpythonpython'
```

#### 2.5 成员资格

运算符`in`可检测元素是否在序列中，返回布尔类型，如：

```python
>>> str = "ate"
>>> "a" in str
True
>>> "m" in str
False
```

#### 2.6 其他

> `len(seq)`    : 返回序列长度
> `max(args)` `min(args`    :返回最大值最小值

### 3. 列表方法

#### 3.1 list

将字符串转化为列表的方法：

```python
>>> list('Hello')
['H', 'e', 'l', 'l', 'o']
```

#### 3.2 基本操作：

```python
>>> x = [1, 1, 1]
>>> x[1] = 2
>>> x
[1, 2, 1]
#赋值操作

>>> del x[1]
>>> x
[1, 1]
#删除元素

>>> x[1:] = [2, 3]
>>> x
[1, 2, 3]
>>> x[1:1] = [6, 6, 6]
>>> x
[1, 6, 6, 6, 2, 3]
#切片赋值与插入

```

#### 3.3 列表方法

> append:添加一个对象到列表末尾  `lst.append(4)`
> clear: 清除   `lst.clear()`
> copy: 复制    `b=a.copy`  (b = a则二者指向一个变量)
> count: 计算指定元素出现次数 `[1, 2, 1].count(1)`
> extend: 将多个值附到列表末尾 `[1, 2, 3].extend([4, 5])`
> index: 查找指定值第一次出现的索引 `lst.index(a)`
> insert: 插入  `lst.insert(2, 'a)`
> pop:  删除一个元素并返回 （唯一修改列表并返回非空的方法），如：
> ```python
>>>> x = [1, 2, 3]
>>>> x.pop()
>3
>>>> x
>[1, 2]
>>>> x.pop(0)
>1
>>>> x
>[2]
> ```
> remove:   删除第一个为指定值的元素： `x.remove('a')`
> reverse: 反转列表：   `x.reverse()`
> sort: 排序并更改列表顺序 `x.sort()`
>>高级排序：sort有两个科学参数key和reverse，如下：
>>```python
>>>>> x = ['aadad', '3ds', 'aadd', 'aaaa', 'ds']
>>>>> x.sort(key=len)
>>>>> x
>>['ds', '3ds', 'aadd', 'aaaa', 'aadad']
>>>>> x.sort(reverse=True)
>>>>> x
>>['ds', 'aadd', 'aadad', 'aaaa', '3ds']
>>#默认按首字符编码顺序排
>>```
> sorted: 排序但不更改列表内容，可用于任何序列，返回排序后的列表

### 4. 字符串操作

#### 4.1 设置格式

##### 4.1.1 设置运算符%，利用元组设置格式，如：

```python
>>> format = "Hello, %s. %s enough for ya?"
>>> values = ('world', 'Hot')
>>> format % values
'Hello, world. Hot enough for ya?'
```

##### 4.1.2 format方法赋值：

替换字号用花括号括起，其各部分包括：
> 字段名 ： 索引或标识符，指出哪个格式并使用结果替换该字段
> 转换标志： !后的单个字符，包括r（repr），s（str）和a（ascii）
> 格式说明符: 跟在:后的表达式.

###### 4.1.2.1 替换字段名

```python
>>> "{foo} {} {bar} {}".format(1, 2, bar=4 ,foo=3)
'3 1 4 2'
#参数指定名称

>>> "{foo} {1} {bar} {0}".format(1, 2, bar=4 ,foo=3)
'3 2 4 1'
#参数名称+标号
```

###### 4.1.2.2 基本转换

利用转换标志进行转换,如:

```python
>>> "{pi!s} {pi!r} {pi!a}".format(pi="π")
"π 'π' '\\u03c0'"
```

格式说明符转换如下:

```python
>>> "number is {num}".format(num=42)
'number is 42'
>>> "number is {num:f}".format(num=42)
'number is 42.000000'
>>> "number is {num:b}".format(num=42)
'number is 101010'
>>> "number is {num:o}".format(num=42)
'number is 52'
```

