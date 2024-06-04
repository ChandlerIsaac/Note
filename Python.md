# Python 基础语法



## 字面量



| 类型               | 描述                                                         | 说明                                       |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------ |
| 数字（Number）     | 整数（int）、 浮点数（float）、复数（complex）、布尔（bool） | 复数（conplex）：如4+3j，以j结尾表示复数。 |
| 字符串（String）   | 用双引号                                                     | String由任意数量的字符组成                 |
| 列表（List）       | 有序可变序列                                                 | 有序记录一堆数据                           |
| 元组（Tuple）      | 有序不可变序列                                               |                                            |
| 集合（Set）        | 无序不重复集合                                               |                                            |
| 字典（Dictionary） | 无序Key-Value集合                                            |                                            |



## 注释

单行注释：# 注释内容（#与注释内容中间有一个空格）

多行注释："""注释内容 """ (一对三引号)



## 变量

变量名称 = 变量值



## 数据类型和数据类型的转换

查看类型信息可用type()函数 

常见转换函数：

| 语句     | 说明            |
| -------- | --------------- |
| int(x)   | 将x转换成整型   |
| float(x) | 将x转换成浮点型 |
| str(x)   | 将x转换成字符串 |

## 标识符和运算符	

Python大小写敏感。

运算符：//取整除，**指数, is 判断两个变量引用对象是否为同一个，is not  判断两个变量引用对象是否不同。

逻辑运算：and ，or，not 

三元运算符：max = a if a>b else b

## 字符串

字符串定义：

1. 单引号定义法： name = 'name'
2. 双引号定义法 ：name = "name"
3. 三引号定义法：name = """name"""

## 格式化输出

1. 用%操作符

   ```python
   print("输出信息 %s %d" % ("information", 16))
   ```

2. format()函数

   ```python
   print("输出信息{} {} {}".format("name", "information", 10))
   ```

3. f-strings

   ```python
   name = "bob"
   age = 16
   gender = "male"
   print(f"输出信息为： {name} {age} {gender}")
   ```



## 顺序控制

### 单分支（if）

```python
if 2 > 1:
    print("yes")
print("no")
```

最短的缩进对较长的缩进有包含关系

### 双分支

```python
if 2 > 1:
    print("yes")
else:
    print("no")
```

### 多分支

```python
if 2 > 1:
    print("yes")
elif 2 > 1:
    print(" ")
elif 3 > 2:
    print(" ")
else:
    print(" ")
```



### for循环控制

```python
# for <变量> in <范围/序列>：
#	<循环操作语句>
num = [10, 50, 52, 63]
for i in num:
    print(i)
```

range（）函数：前闭后开。# range还有第三个参数，步长。

```python
for i in range(1, 6):
    print(i)

```



### while循环

```python
i = 1
while i < 10:
    print(i)
    i += 2
```





## 键盘输入

input（）函数 ``` 返回类型默认为string类型```

```python
name = input("name = ")
age = input("age = ")

print("\nname = ", name)
print("age = ", age)

```



# 函数

函数定义

```python
def max_a_b(a, b):
    if a > b:
        return a
    else:
        return b


i = max_a_b(10, 49)
print(i)
```

函数作为参数传递：

```python
def max_a_b(a, b):
    if a > b:
        return a
    else:
        return b


def f1(fun, a, b):
    return fun(a, b)


def f2(fun, a, b):
    return a + b, fun(a, b)


i = f1(max_a_b, 10, 19)
x, y = f2(max_a_b, 10, 19)
print(f"i = {i} x = {x} y = {y}")
```



## Lambda匿名函数

需要将函数作为参数进行传递，但是这个**函数只使用一次**，这时可以考虑lambda匿名函数。

---

lambda关键字可以定义匿名函数**（没有名称）**，但是匿名函数**只能使用一次。**

举例：

```python
# 编写一个函数，可以接收一个匿名内部类函数和两个参数值，计算最大值
def f1(fun, a, b):
    return fun(a, b)


i = f1(lambda a, b: a if a > b else b, 12, 18)
print(i)

```



# 容器

## 列表(List)

创建一个列表，只要用逗号分隔的**不同的数据项**使用方括号括起来即可。可以**用下标访问**，**还可以反向缩影**。可以有**重复数据**。列表是可变序列。

---

```python
# list的创建
list1 = []
list2 = list()
```

**列表常用操作：**

| 函数                                  | 说明             |
| ------------------------------------- | ---------------- |
| len（list）                           | 返回列表的长度   |
| max（list）                           |                  |
| min（list）                           |                  |
| list（seq）                           | 将元组转换成列表 |
| list.append(obj)                      | 在列表末尾加元素 |
| list.count(obj)                       |                  |
| list.extend(seq)                      |                  |
| list.index(obj)                       |                  |
| list.intsert(index,obj)               |                  |
| list.pop([index = -1])                |                  |
| list.remove(obj)                      |                  |
| list.reverse()                        |                  |
| list.sort(key = None,reverse = false) |                  |
| list.clear()                          |                  |
| list.copy                             |                  |

**列表生成式：**```生成列表的公式```

基本语法:[列表元素的表达式for自定义对象in可迭代对象]

```python
list1 = [ele * 2 for ele in range(1, 5)]
print(list1)  # 输出结果为 [2, 4, 6, 8]
```



## 元组（tuple）

元组是**不可变序列**，可以存放**多个不同类型的数据。****不能重新赋值**

创建一个元组，只要把逗号分隔的不同数据项，用**圆括号**括起来即可。

---





## 切片

从一个序列中，取出一个子序列。

---

语法：序列[起始索引：结束索引：步长]

## 集合（set）

集合是由**不重复元素**组成的**无序**容器。

创建一个几个，只要把逗号分隔的不同数据项，用**大括号**括起来即可。

## 字典（dict）

key-value

创建一个几个，只要把逗号分隔的不同数据项，用**大括号**括起来即可,存储的元素是一个个的：**键值对**。

dict_a = {key:value, key:value, key:value, ...}

通过key取出对应的value ： 字典名[key]



# 模块

一个Python文件就是一个模块

 **导入模块：**

1. ```python
   import math
   ```

2. ```python
   from math import fabs
   ```

**导入的模块取别名：**

```python
from math import fabs as jueduizhi
```

## 自定义模块

```python
__name__
__all__
```



# 第三方库

## pip

pip是Python的包管理器，是一个工具，允许安装和管理第三方库和依赖。

pip指定源安装：pip install -i 指定源 库名

pip install

pip list

pip uninstall

## 网络爬虫





## 自动化



## 数据分析可视化



## 机器学习



# 面向对象

```python
class Cat:
    age = None
    name = None
    color = None


cat = Cat()
cat.name = "catName"
cat.age = 9
cat.color = "white"


print(cat.age)

```













































# PyCharm 快捷键

| 打开软件设置       | ctrl+alt+s       |
| ------------------ | ---------------- |
| 将当前代码上下移动 | shift+alt+上下键 |
| 搜索               | ctrl+f           |
| 重命名文件         | shift+F6         |
|                    |                  |

