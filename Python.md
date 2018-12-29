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

### 1. 列表和元组

#### 1.1 列表：

**放在方括号中，可修改**的序列，如：

```python
    edward = ['Edward Gaward', 42]
    john = ['John Smith', 23]
    database = [edward, john]
```

#### 1.2 元组：

**直接逗号分隔或加圆括号，不可修改**的序列，如：

```python
    x = 1, 2, 3
    y = (4, 5, 6)
    z = (42,)
```

### 2. 通用序列操作

#### 2.1 索引

0为元素第一位，-1为最后一位，可直接通过 `str[0]` 进行索引。如：

```python
    >>> greeting = 'Hello'
    >>> greeting[0]
    'H'
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