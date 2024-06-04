# 文件操作

## 路径

### **获取当前的文件路径和改变当前路径**

```python
import os
# 获取当前文件的目录
path = os.getcwd()
print(path)
# 改变路径
os.chdir("D:/software")
```

### 路径连接

```python
import os

path1 = 'D:\software'
path2 = 'Coding'
path = os.path.join(path1, path2)
print(path)
```

### 显示文件夹中所有元素

```python
import os
os.chdir("D:/software")
docList = os.listdir()
print(docList)
```

### 判断是否为文件和文件夹

```python
import os
os.chdir("D:/software")
docList = os.listdir()

for document in docList:
    # 判断document是否为文件夹 使用os.path.isdir() 是文件夹返回True 否则返回False
    # os.path.isfile() 判断document是否为文件
    print(document, os.path.isdir(document), os.path.isfile(document))
```

### 遍历目录（路径）

```python
import os
for i in os.scandir("D:/software"):
    # i的类型是DirEntry
    print(i.name, i.is_dir())
```

### **查看指定格式的文件**

```python
import os
for i in os.scandir("D:/software"):
    # 看excel文件的个数
    if i.name.endswith("xlsx"):
        print(i.name)
```

### 遍历文件夹（os.walk）

```python
import os
# os.walk(top,topdown = true, onerror = None, followlinks = False)
# 返回三元组（root, dirs, files）
# root: 当前所指文件的地址
# dirs: 该文件夹中所有目录的名字 ，不包含子目录
# files：是list 内容是该文件夹中所有文件 不包含子目录

for rootAddress, dirs, files in os.walk("D:/software"):
    for i in files:
        if i.endswith("xlsx"):
            print(rootAddress, i)
```

### 搜索匹配文件名

1. 利用字符串内置方法：.startswith(),endswith()
2. glob模块
3. fnmatch模块

glob模块

```python
import os
import glob
os.chdir("D:/software")
# *代表多个字符 ？代表一个字符 [0-9]表示0-9任意一个数字 表达式
print(glob.glob('**/*.xlsx', recursive=True)) # recursive=True 表示在子目录中也查找 '**/*.xlsx' **/表示任意层文件夹

```



```python
# glob.iglob('**/*.xlsx', recursive=True) 返回可迭代对象
import os
import glob
os.chdir("D:/software")
iterator = glob.iglob('**/*.xlsx', recursive=True)
for i in iterator:
    print(i)
```

fnmatch模块

```python
import os
import fnmatch
fileList = os.listdir('D:/software')
for i in fileList:
    if fnmatch.fnmatch(i, '*.xlsx'):  # 返回值为bool类型
        print(i)
```

## 文件夹

### 创建文件夹(mkdir)

```python
import os

def makeDir(path):
    if not os.path.exists(path):
        os.mkdir(path)
        print(f"路径：{path} 添加成功")
    else:
        print(f"路径：{path} 添加失败")


path = os.getcwd()+'\\Test'
if __name__ == "__main__":
    makeDir(path)
```

### 创建多重文件夹(makedir)

```python
import os
def makeDirs(path):
    if not os.path.exists(path):
        os.makedirs(path)
        print(f"路径：{path} 添加成功")
    else:
        print(f"路径：{path} 添加失败")


path = os.getcwd() + '\\Test\\test1'
if __name__ == "__main__":
    makeDirs(path)
```

### shutil模块

#### 复制文件

```python
import os
import shutil

path1 = os.getcwd()+'\\test.txt'
path2 = os.getcwd() + '\\Test\\test1'
shutil.copy(path1, path2) #是当前时间创建的
shutil.copy2(path1, path2) # 和源文件创建时间一样
```

#### 复制文件夹

```python
shutil.copytree()
```

#### 移动文件和文件夹

```python
import shutil
path1 = os.getcwd()+'\\test.txt'
path2 = os.getcwd() + '\\Test\\test1'
shutil.move(path1, path2)
```

#### 删除文件夹

```python
import shutil
import os
shutil.rmtree(path)
os.remove(path2)
```

#### 重命名文件和文件夹

```python
import os
path1 = os.getcwd()+'\\test.txt'
path2 = os.getcwd() + '\\Test\\test1'
os.rename(path2, os.getcwd() + '\\Test1')
```

### 文件读写

访问模式：

1. r 只读
2. w写入，会覆盖原有内容
3. a追加，在原有内容基础上追加内容

文件对象.read(num)  :num 表示从文件中读取数据的长度

文件对象.readlines()

文件对象.readline()

# pandas操作Excel

## 数据类型

csv和txt ：pd.to_csv

excel: pd.to_excel

sql:pd.to_excel

## 新建文件

```python
import pandas as pd

path = 'D:\\PythonProject\\Study\\Test1\\test.xlsx'
diction = {'no': [1, 2, 3], 'name': ['tom', 'bob', 'jerry']}
data = pd.DataFrame(diction)
data = data.set_index('no')
data.to_excel(path)
```

## 读取txt和csv文档

```python
import pandas as pd
path = 'D:\\PythonProject\\Study\\Test1\\test.txt'
data = pd.read_csv(path, header=None, names=['no', 'name'], index_col='no', nrows=1)
print(data)
```

## 读取MySql文件

```python
import pandas as pd
import pymysql


connetion1 = pymysql.connect(host= 'localhost', user='root',password='root', database='db',charset='utf8')
data = pd.read_sql("select * from actor", con = connetion1)
print(data)
```

## 读取和修改Excel文件

