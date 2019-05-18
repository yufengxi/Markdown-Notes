# R

## 1. 数据集及基本数据结构

1. 向量
    用于存储数值型，字符型或逻辑型数据的一维数组，但仅能存储同一类型变量

    ```r
    a <- c(2, 5, -2)
    b <- c("d", "a")
    ```

2. 矩阵
    二维数组

    ```r
    > y <- matrix(1:20, nrow =5, ncol = 4, byrow = TRUE)
    > y
        [,1] [,2] [,3] [,4]
    [1,]    1    2    3    4
    [2,]    5    6    7    8
    [3,]    9   10   11   12
    [4,]   13   14   15   16
    [5,]   17   18   19   20

    ##行列命名
    rownames(y) <- c("Row 1", "Row 2")
    colnames(y) <- c("Col 1", "Col 2", "Col 3")

    is.matrix(y)
    > TRUE
    as.vector(y)
    > 1 5 9 13...
    ```

3. 数组
    维度可大于二的矩阵，形式为`myarray <- array(vector, dimensions, dimnames)`，`vector`成员变量；`dimensions`维度，可用向量表示；`dimnames`为维度坐标名（列表），可选

    ```r
    x1 <-c("a1","a2")
    x2 <- c("b1","b2","b3")
    x3 <- c("c1", "c2", "c3", "c4", "c5")
    z <- array(1:24, c(2,3,5), list(x1, x2, x3))
    ```

4. 数据框
    可以包含不同类型数据，成员变量用$，形式如`mydata <- data.frame(col1, col2, col3)`

    ```r
    patientID = c(1,2,3,4)
    age <- c(2,55,23,441)
    status <- c("poor", "rich")
    health <- 10
    Pdata <- data.frame(patientID, age, health, status)
        patientID age health status
    1         1   2     10   poor
    2         2  55     10   rich
    3         3  23     10   poor
    4         4  441    10   rich
    ```

    选取数据框中元素：

    ```r
    Pdata[3:4]
    Pdata[c(patientID, health)]
    #两个变量列联表：
    table (Pdata$age, Pdata$health)
    ```

    > `attach` 可定位到某个数据框中，之后可直接操作其成员；`detach` 可解除定位
    > `with()`结构内处理数据框变量，如`with(dataframe, {ele1-ele2})`

5. 因子
    分为无序和有序因子，统计时会计算频数

6. 列表

`list`可整合多种结构，如

```r
> g <- "My Title"
> h <- c(2, 51, 24, 1)
> j <-matrix(1:10, nrow = 5)
> k <- c("one", "two", "three")
> mylist <- list(title=g, ages=h ,j, k)
> mylist
$title
[1] "My Title"

$ages
[1]  2 51 24  1

[[3]]
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10

[[4]]
[1] "one"   "two"   "three"
```

## 2. 数据管理

1. 获取数据子集

    ```r
    ## 前3列数据：
    newdata <- Data[1:3]

    ## 前3行数据：
    newdata <- Data[1:3,]

    ## 挑选特定属性的行:
    attach(Data)
    newdata <- Data[gender == "M"& age >30 ]

    ##subset,保留q1-q4:
    newdata <- subset (leadership, age > 30 & age < 24 ,
                    select = c(q1, q2, q3, q4))

    ## 保留gender到q2所有列的数据
    newdata <- subset (leadership, age > 30 & age < 24 ,
                    select = gender:q2)

    ## 随机抽样

    mysample <- leadership[sample(1:nrow(leadership), 3 ,        replace=FALSE),]
    ```

2. 数值处理

    * 数学函数：

    > `abs(x)`绝对值
    > `sqrt(x)`平方根
    > `ceiling(x)` 不小于x的最小整数
    > `floor(x)` 不大于x的最大整数
    > `trunc(x)` x整数部分
    > `round(x, digits=n)` x舍为n为小数
    > `signif(x, digits=n)` x舍入为有效位数字
    > `exp(x)` e^x

    * 统计函数

    > `mean(x)`算术平均数;`mean(x, trim = 0.05, na.rm =T`)派出最大最小5%数据以及缺失值
    > `median(x)`

3. 分组

    * aggregate()

    ```r
     aggregate(data, list(), FUN)
    ```

## 3. 作图

## 实战

1. [O3]MDA8

```r
library(dplyr)

attach(Data)
newGroup = Data %>%
  mutate(Station = as.factor(jczname),
         Date = as.factor(day(time_point)),
         Month = as.factor(month(time_point)),
         rolling = rollmean(o3, k = 8, fill = NA, na.rm =T))%>%
  group_by(Month, Date, Station)%>%
  summarise(Maxrolling = round(max(rolling, na.rm = T), 3))
detach(Data)
```

## 机器学习与深度学习

1. 决策树：基于基尼不纯度（一个随机事件变成对立面的概率）

2. 随机森林：集成思想

## Package

zoo