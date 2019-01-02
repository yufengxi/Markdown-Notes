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

说明符清单如下:
类型        | 含义
:---------: | :-----------:
b           | 整数表示为二进制
c           | 整数解读为Unicode编码
e/E         | 科学记数法指数
f/F         | 定点数
g/G         | 定点数或科学计数
o           | 八进制
s           | 字符串格式
x/X         | 十六进制
%           | 百分比制

#### 4.2 字符串方法

> center: 在两端填充字符让字符串居中(默认空格),如:  
> `"Hello world".center(20)` `"Hello world".center(20,'*')`
> find: 查找子串,返回第一个字符索引,没有返回-1   `str.find(a)`
> 也可指定起点终点,如: `str.find(a,1,10)`
> join: 合并序列元素,如:
>> ```python
>>>>> seq = ['1', '2', '3', '4', '5']
>>>>> sep = '+'
>>>>> sep.join(seq)
>>'1+2+3+4+5'
>> ```
> lower: 返回小写版本: `str.lower()`
> replace: 将指定字串全部换为另一个 `str.replace('is','are')`
> split: 将字符串拆成序列(默认从空格拆分),如
>> ```python
>>>>> '1+2+3+4+5'.split('+')
>>['1', '2', '3', '4', '5']
>>>>> 'I am a long'.split()
>>['I', 'am', 'a', 'long']
>>```
>strip: 删除开头结尾的空白或指定字符,如:
>>```python
>>>>> "       fssffaa    ".strip()
>>'fssffaa'
>>>>> "    ! !!!  fssffaa **!!  ! ".strip(' !*')
>>'fssffaa'
>>```
>translate: 可替换多个单字符,但首先应对str类型建立转换表(maketrans)如:
>>```python
>>>>> table = str.maketrans('cs','kz')
>>>>> "tssj jjcm wws".translate(table)
>>'tzzj jjkm wwz'
>>>>> table = str.maketrans('cs','kz',' ')
>>>>> "tssj jjcm wws".translate(table)
>>'tzzjjjkmwwz'
>>#可定义第三个将被删除的参数
>>```

## 三、字典

Python中唯一内置的映射类型，其值不安顺序排列，而是存储在键下。

### 1. 创建字典

可通过如下几种方法创建：

#### 1.1 标准类型：

```python
phonebook = { 'A': '233', 'B': '424', 'C': '515'}
```

#### 1.2 函数dict：

```python
>>> item = [('name','Alice'), ('age', 42)]
>>> d= dict(item)
>>> d
{'name': 'Alice', 'age': 42}
>>> d['name']
'Alice'

>>> d = dict(name = 'Jack', age = '49')
>>> d
{'name': 'Jack', 'age': '49'}
```

### 2. 基本操作

> `len(d)` 返回字典键值对数
> `d[k]` 返回与键k关联的值，同样可直接给它赋值
> `del d[k]` 删除该键值对
> `k in d` 判断k是否为d的项 （k为d的键而非值）

### 3. 字典方法

> clear: 清空整个字典，返回值为空 `d.clear()`
> copy: 浅复制，替换值不受影响但修改影响原件 `y=x.copy` 深复制可利用copy模块中deepcopy `x = deepcopy(y)`
> fromkeys: 创造含指定值的空字典，也可自己赋默认值 `dict.fromkeys(['a','b'],'m')`
> get: 返回字典中键对应的值，对于空值也不会产生错误 `d.get('a')`或空值设为返回默认值 `d.get('a',0)`
> items: 返回字典视图，一个每个元素均为`(key, value)`的列表 `d.items`
> keys: 只返回键的字典视图 `d.keys`
> pop: 删除该键并返回其值 `d.pop('x')`
> popitems: 随机弹出一个字典项并返回其值 `d.popitems()`
> setfault: 与get相同，但当键无对应值时添加关联的值 `d.setfault('a','N/A)`
> update: 用一个字典的项更新另一个 `d.update(a)`
> values: 返回全部值 `d.values()`

## 四、语句

### 1. 赋值

```python
x, y, z = 1, 2, 3
#序列解包
x, y, *z = [1, 2, 3, 4]
#*可以手机多余的值，但包含的一定是一个列表
x = y = somefunction()
#链式赋值
x += 2
#增强赋值
```

### 2. 条件语句

布尔代数中， `False` `None` `0` `""` `()` `[]` `{}`被视为假

`True == 1`   `False == 0`

`if` `elif` `else`
不需要括号
条件表达式关键词： `==` `is` `in` `is not` `not in`

**断言：**assert语句，可预先规定某些条件，如果不满足条件则中断程序执行。

### 3. 循环

#### 3.1 while

```python
x = 1
while x <= 100:
#也可用while not
    print(x)
    x +=1
```

#### 3.2 for

利用迭代器进行循环，`for in`

```python
for number in range(1, 100)
    print(number)
#range为内置函数，range(10)代表0-9 10个自然数。，range(x,y)代表x开始n个自然数
```

#### 3.3 迭代工具

##### 3.3.1 并行迭代

内置函数 `zip` 可将两个序列缝合，返回元组组成的序列。如下：

```python
>>> names = ['Jack', 'Beth', 'Mike']
>>> ages = [20, 19, 24, 92]
>>> list(zip(names, ages))
[('Jack', 20), ('Beth', 19), ('Mike', 24)]
>>> for name, age in zip(names, ages):
...     print(name, 'is', age, 'years old')
Jack is 20 years old
Beth is 19 years old
Mike is 24 years old
```

>对于长度不同的两个序列，`zip`将在较短序列完成后停止"缝合"

##### 3.3.2 迭代时索引

可利用内置函数 `enumerate`在迭代时获取对象索引，如：

```python
>>> strings = ['xxx', 'fswfwfxxx', 'wrwx']
>>> for index, string in enumerate(strings):
...     if 'xxx' in string:
...             strings[index] = '[censored]'
...
>>> strings
['[censored]', '[censored]', 'wrwx']
```

##### 3.3.3 反向迭代和排序后迭代

可利用`reversed`和`sorted`两个函数直接返回修改排序后的版本，而不对对象本身进行更改

#### 3.4 跳出循环

> break: 直接跳出循环
> continue: 结束当前迭代，跳到下一次迭代开始
> while 和 break

#### 3.5 循环与else

如果循环中未执行break，则可以在其后加上一个else让程序执行else中的内容，如：

```python
>>> from math import sqrt
>>> for n in range(99, 81, -1):
...     root = sqrt(n)
...     if root == int(root):
...             print(n)
...             break
... else:
...     print("No")
...
No
```

### 4. 其他语句

>del: 删除对象，但只删除名称，例如`x=y=1`,`del x`后y仍然存在
>exec：将字符作为代码执行，如： `exec("print('Hello,world')")`，但需要传递命名空间
>eval: 类似exec并返回结果

## 五、抽象和类

### 1. 函数

**def**为函数定义关键字，如:

```python
def test():
    return 5
test()

def init(data):
    data['first'] = {}
    data['middle'] = {}
    data['last'] = {}
```

默认参数为位置参数，也可以直接指定参数名称，这样的参数称为关键字参数

```py
hello(greeting = 'Hello', name = 'world')
```

同样也可以用*来收集参数

```py
>>> def prints(title, *params):
...     print(title)
...     print(params)
>>> prints('Params:', 1,2,3)
Params:
(1, 2, 3)
#*吸收剩余的值，返回一个元组

>>> def Prints(**p):
...     print(p)
>>> Prints(x=1, y=2, z=3)
{'x': 1, 'y': 2, 'z': 3}
#多参数用**，返回一个字典
```

函数中定义的只是局部变量，是在**命名空间**或**作用域**中定义的。除全局作用域外，每个函数都将创建一个。

### 2. 对象

指一些列数据及访问操作它们的方法。其优点包括：

>多态：可对不同类型数据执行相同操作
>封装：对外隐藏工作原理细节
>继承：基于通用类创建专用类

### 3. 类

#### 3.1 定义类

关键字：class，self

```py
class person:

    name = None

    def set_name(self, name):
        self.name = name;

    def get_name(self):
        return self.name;

    def greet(self):
        print("Hello, world! I'm {}.".format(self.name))
#需要注意类中所有函数都需要含self参数，但使用时不需要写出，如下：

foo = person()
#定义对象的方法
foo.set_name('Jack')
foo.greet()
```

另外可以将类内函数关联到一个普通函数中。

```py
def Greet():
    print('Hello!)

foo.greet = Greet
```

同理，类外函数也可关联到类内

私有：只需要在名称加上__即可，如`def __a(self)`

#### 3.2 继承

可以通过`class b(a):`定义a的子类b，a即为b的超类

子类也可以重新定义重写超类方法

```py
class Filter:
    def init(self):
        self.blocked = []
    def fileter(self, sequence):
        return [x for x in sequence if x not in self.blocked]

class SPAMFilter(Filter):
    def init(self):     #重写方法
        self.blocked = ['SPAM']

```

>判断是否为子类的方法：`issubclass(a,b)`，若a为b子类返回`True`  
>确定类的基类： `a.__bases__`
>判断对象是否为类的实例: `isinstance(a,b)`，a为实例返回`True`

多继承：`class A(B, C)`如果BC含相同方法，则C中的会覆盖掉B中的

抽象基类：定义子类需要实例化的方法，具体实现如下：

```py
from abc import ABC, abstractmethod

class Talker(ABC):
    @abstractmethod     #装饰器，用于标记抽象的方法
    def talk(self):
        pass
```

## 六、异常

出现异常时，python会返回错误消息并终止程序

>raise: 可将类或实例作为参数，用于引发异常的语句 `raise Exceprion`  
>Exception: 内置异常类，所有异常类都由其派生
>try/except： 用于捕获异常的语句