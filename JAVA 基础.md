# JAVA 基础

## 第一阶段

### JAVA 概述



#### JAVA 特性

java 是==强类型机制==  ==跨平台机制== ==垃圾自动回收== ==解释性语言==

####  JDK、JRE和JVM

- <u>.java 文件</u> --- >编译成  <u>.class 文件</u>(字节码文件)
- JVM  包含在JDK 中 ， 虚拟机机制实现了 ==一次编译到处运行==
- ==JDK==(Java Development Kit) Java开发工具包  **JDK = JRE +Java 开发工具**
- ==JRE== (Java Runtime Envrioment)Java 运行环境  **JRE = JVM + Java的核心类库**
- 环境变量==path== ：为了在任何路径都能找到 JDK  
- JVM的内存分为三种 1.栈(存放基本数据类型) 2.堆(存放对象，数组也是属于对象) 3.方法区(常量池(字符串、常量)、类加载信息)。

#### 注意事项

1. 一个源文件只能有一个public类。其他类个数不限。
2. 如果一个源文件包含一个public类，文件名必须按该类名命名。
3. **浮点数相除 8.1/3 得到结果是一个近似于2.7的小数 而不是2.7**

####  常用快捷键

| shift + tab      | 整体向左移 |
| :--------------- | ---------- |
| ctrl + shift + f | 整理代码   |
| ctrl + /         | 注释       |
|                  |            |



#### 文档注释

使用JDK提供的工具javadoc(类和方法)

```java
//文档注释
/**
*@author xxx
*@version 1.0
*/

```

### 变量

####  ==数据类型==

##### 基本数据类型

1. 数值型

   整型：byte short int long

   浮点型：float double 

2. 字符型

   char (==unicode==编码) **占两个字节** 

3. 布尔型 

   boolean

   

1. ​					

##### 引用类型

1. 类
2. 接口
3. 数组



#### 基本数据类型和String类型的转换

1. 基本数据类型转成String类型

   **基本数据类型的值+""  即可**

   ```java
   int n1 = 100; 
   String s1 =n1 +"";
   System.out.println(s1 +" ");
   ```

2. String 类型转换成基本数据类型

   **通过基本类型的包装类调用==parseXX==方法即可**

   ```java
   String s1 = "123";
   int num1 = Integer.parseInt(s1);
   //s1.charAt(0) 得到s1字符串的第一个字符
   System.out.println(s1.charAt(0));
   ```

   ###  运算符和标识符

#### &&和&的区别

&& 短路与：如果第一个条件为false ，则第二个不会判断 最终结果为false 

&逻辑与：不管什么情况，两个条件都要判断。



#### 标识符命名规范

| 包名(所有字母都小写)             | aaa.bbb.ccc        |
| -------------------------------- | ------------------ |
| 类名、接口名(所有单词首字母大写) | TankShotGame大驼峰 |
| 变量名、方法名                   | tankShotGame小驼峰 |
| 常量名(所有字母大写)             | TAX_RATE           |

### 键盘输入语句

需要一个扫描器对象，也就是==Scanner==

步骤：

1. 导入该类所在的包，java.util.*
2. 创建该类对象
3. 调用里面的功能

```java
//接受用户的输入
import java.util.Scanner;
public class Input{
    public static void main(String []args){
        Scanner scanner = new Scanner(System.in);
        //当程序执行到next 方法时，会等待用户的输入。
        String string = scanner.next();//接受用户输入
        int age = scanner.nextInt();//接受整型输入
        
        
    }
    
}
```



### 控制结构

#### 跳转控制语句-continue

continue 结束==本次==循环，继续执行下一次循环。



### ==数组==

数组的长度 数组名.length;

#### 数组的定义

1. int a[] = new  int[5];  (动态初始化)

2. 先声明数组，在创建数组。(动态初始化)

   ```java
   int a[];
   a = new int[5];
   ```

3. int a[] = {1,2,3,4}; (静态初始化)



#### ==数组赋值机制==

基本数据类型赋值 ，赋值方式是值拷贝。



数组在默认情况下是引用传递，赋的值是地址，赋值方式是==引用==传递。(类似c++的起别名？)

```java
int arr1[] ={1,2,3};
//将arr1的地址赋值给arr2; arr1 和arr2 指向同一地址;
// 对arr2操作就相当于对arr1操作;
int arr2[] = arr1; 
arr2[0] = 10;
//arr1[]里面的内容变为 10，2，3;
```

#### 数组拷贝

两个数组拥有独立的数据空间。

```java
int arr1[] = {1,2,3};
//两个数组拥有独立的数据空间
//int arr2[] = arr1; 这种做法不对，arr2和arr1都指向同一数据空间。
int arr2[] = new int[arr1.length];
//再通过遍历把每个值拷贝到arr2中。
```

#### 二维数组



### IDEA快捷键



### 面向对象

#### 对象在内存中的存在形式

对象也是==引用==类型。(同数组)

```java
//有猫这个类
Cat cat = new Cat();
cat.name = "小白";
cat.age = 12;
cat.color ="白色";
```

JVM 内存图

![](D:/Picture/对象在内存中的存在形式.png)

#### 成员方法



##### 方法的调用机制

1. 当程序执行到方法是，就会开辟一个独立的内存空间(栈空间)。
2. 当方法执行完毕，或者执行到return语句，就会返回。
3. 返回到调用方法的地方。
4. 继续执行方法后面的代码。

##### ==成员方法传参机制==

- 基本数据类型传参机制：基本数据类型，传递的是值，形参的任何改变不影响实参。
- 引用数据类型传参机制：引用类型传递的是地址，可以通过形参来改变实参。

[[0212_韩顺平Java_方法传参机制3_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fh411y7R8?p=213&spm_id_from=pageDriver&vd_source=d4170c3e1efe8a4c60a0290f0137a78d)]:



##### 方法的重载(overload)

允许同一个类中，有同名方法的存在，但是要求形参列表不一致。



##### 方法的重写/覆盖(override)

子类有一个方法，和父类的某个方法一模一样，就说子类的方法覆盖了父类的方法。

---

1. 子类的返回类型和父类方法返回类型一样，或者是父类返回类型的子类

   ```java
   //父类中的方法
   public Object getInfo(){}
   //子类中的方法
   public String getInfo(){} //重写父类的getInfo()方法
   
   ```

2. 子类方法不能缩小父类的方法的访问权限





#####  重载和重写的区别

| 名称           | 发生范围 | 方法名   | 参数列表                  | 返回类型                                             | 修饰符                             |
| -------------- | -------- | -------- | ------------------------- | ---------------------------------------------------- | ---------------------------------- |
| 重载(overload) | 一个类内 | 完全相同 | 类型 个数 顺序 有一个不同 | 无要求                                               | 无要求                             |
| 重写(override) | 父子类   | 完全相同 | 相同                      | 子类重写的方法，返回类型与父类的一致，或者是其子类。 | 子类方法不能缩小父类方法的访问范围 |





#### 可变参数

java允许同一个类中，多个同名同功能但是参数个数不同的方法，封装成一个方法。

```java
//计算 两个数的和 计算三个数的和 计算三个数的和 ... 可以用重载比较麻烦
//可以使用可变参数的方法
public int sum(int... nums){
    int res = 0;
    for (int i = 0; i<nums.length;i++){
        res += nums[i];
    }
    return res;
}
```

int... 表示接受的是可变参数，类型是int。即可以接受多个int，**可以是零个或者任意多个**。

使用可变参数是，可以当作数组，==即把nums当成数组==。

#### 构造器（constructor）

就是构造方法、构造函数。

1. 构造器没有==返回值==，也不能为void
2. 完成对新对象的初始化
3. 在创建对象时，系统会自动调用该类的构造器完成对对象的初始化。
4. 构造器可以重载
5. 如果没有定义构造器，系统会自动给类生成一个默认无参构造器（ **javap 反编译**）
6. 一旦定义了自己的构造器，默认的构造器就被覆盖了，==就不能使用默认的无参构造器了==，可以自己定义一个无参的构造器。
6. **构造器的最前面隐含了super()**和调用普通代码块。静态相关的代码块，属性初始化，在类加载时，就执行完毕。

```java
class Person{
    String name;
    int age ;
    public Person(String name1,int age1){
        name = name1;
        age = age1;
    }
}
```

#### 对象创建的流程分析

[[0244_韩顺平Java_对象创建流程详解_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fh411y7R8/?p=245&spm_id_from=pageDriver&vd_source=d4170c3e1efe8a4c60a0290f0137a78d)]:

```java
class Person{
    int age = 90;
    String name;
    Person(String n,int a ){
        name =n;
        age = a;
    }
}
Person p = new Person("小明",20);
```



1.  加载Person类信息(Person.class)，只会加载一次。

2. 再堆中分配空间

3. 完成==对象初始化==（

   - 默认初始化 age= 0 ，name = null；
   - 显示初始化 age = 90 ，name = null；
   - 构造器初始化 age = 20，name =小明；

   ）

4. 把对象在堆中的地址，返回给p(**p是对象名，是对象的引用**)；



#### this

this 是当前对象的地址，this.age 相当于Person.age;

每个对象中隐含this

```java
class Person{
    String name;
    int age ;
    public Person(String name,int age){
        //当前对象的属性
        this.name = name;
        this.age = age;
    }
}
```

---

可以调用本类的构造器，必须放在构造器的第一行。 this(参数列表);

#### 包

本质：创建不同的文件夹来保存类文件。

1. 区分相同名字的类
2. 当类很多时，可以很好的管理类
3. 控制访问范围

##### 常用的包

- java.lang 包是基本包自动导入
- java.util 工具包
- java.net 网络包
- java.awt 界面开发的包
- 

#### 访问修饰符

| public    |                |
| --------- | -------------- |
| protected | 子类和同一个包 |
| 默认      | 同一个包       |
| private   |                |



#### 封装

1. 隐藏实现的细节（通过调用方法）
2. 可以对数据进行验证，保证安全合理。

封装实现的步骤

1. 将属性进行私有化
2. 提供一个公共（public）的set方法，用于对属性判断并赋值
3. 提供一个公共的get（public）方法，用于获取属性的值

#### 继承（extends）

可以使用继承来实现==代码复用性==

class 子类 extends父类{

}

----

继承的相关细节

1. 子类继承了所有的属性和方法，但是私有属性和方法不能直接在子类中直接访问，要通过私有方法去访问。
2. 子类必须先调用父类的构造器，完成父类的初始化。
3. 当创建子类对时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，==如果父类没有提供无参构造器，则必须在**子类每个构造器中**用super去指明使用父类的哪个构造器完成对父类的初始化工作==，否则，编译不会通过。
4. 可以显示地调用父类的指定构造器，使用super(参数列表);
5. super在使用时，必须放在构造器的第一行（==super只能在构造器中使用==）
6. super（）和this（）都只能放在构造器的第一行，因此这两个方法不能在一个构造器中
7. Object类是所有类的基类。
8. 父类构造器的调用不限于直接父类，将一直往上追溯到Object类（顶级父类）。
9. 单继承



继承的本质

子类对象创建好后，建立==查找==的关系。

```java
package com.company.extends_;

public class ExtendsTheory {
    public static void main(String[] args) {
        Son son = new Son();

        System.out.println(son.name);//返回大头儿子
        System.out.println(son.age);//返回39
        System.out.println(son.hobby);//返回旅游
    }
}
 class GradPa{
        String name ="大头爷爷";
        String hobby ="旅游";

}
class  Father extends GradPa{
    String name ="大头爸爸";
    int age = 39;
}
class Son extends Father {
    String name = "大头儿子";
}

```

---

上述代码中的 System.out.println(son.name);语句，Son类中有name属性，Father、GradPa类也有name属性，要按照查找关系来返回信息。

1. 首先看子类是否有该属性
2. 如果子类有该属性，并且可以直接访问，则返回
3. 若没有该属性，就看父类是否有该属性，如果有则返回
4. 若父类也没有，则继续重复步骤3，直到Object类

---

上述代码的内存图

![](D:/Picture/继承的内存布局.png)



#### ==多态(polymorphic)==

可以提高代码的复用性，方法或者对象有多种形象。

多态的前提：两个对象存在继承关系。

---

多态的具体体现

1. 方法的多态(重写和重载)

2. ==对象的多态==

   - ==一个对象的编译类型和运行类型可以不一致==。可以让父类的引用指向一个子类对象（可以把引用理解成一个地址）

     ```java
     //animal 编译类型是Animal 运行类型是Dog
     Animal animal = new Dog();  //animal是对象引用，Dog才是真正的对象
     ```

   - ==编译类型在定义对象时，就确定了，不能改变==。

   - ==运行类型是可以改变的==

     ```java
     Animal animal = new Dog();
     animal = new Cat();//animal的运行类型就变成了Cat，编译类型仍然是Animal
     ```

   - ==编译类型看等号的左边，运行类型要看等号的右边==。







---

 **编译类型和运行类型的区别**

```java
class Animal{
    public void cry(){
        System.out.println("animal 的cry()");
	}
}
class Dog extends Animal {
    //重写父类的cry();
    public void cry(){
        System.out.println("dog 的cry()");
	}
}
class Cat extends Animal {
    //重写父类的cry();
    public void cry(){
        System.out.println("cat 的cry()");
	}
}

public class main{
    public static void main(String []args){
        //animal的编译类型是Animal,运行类型是Dog;
        Animal animal = new Dog();
        animal.cry();//执行到这一行时，animal的运行类型是Dog 
        			//所以执行Dog的cry()方法
    }
}
```

**执行到第23行时，animal的运行类型是Dog ，所以执行Dog的cry()方法**

---

##### 多态的向上转型

```java
Animal animal = new Dog();
```

本质：父类的引用指向了子类对象。

语法： 父类类型 父类引用 =  new 子类对象;

(**个人理解** 使用父类引用来操作dog对象，dog对象向上成为了父类 )



##### 多态的向下转型

1. 语法：子类类型 引用名 = （子类类型） 父类引用 ;

2. **只能强转父类的引用，不能强制转换父类的对象。**（对象不能改变）

3. **要求父类引用必须指向当前目标类型的对象。**

4. 向下转型后，可以调用子类类型中的所有成员。

   (**个人理解** 父类引用当作子类引用来使用)

```java 
Animal animal = new Cat();
//catchMouse()方法是Cat类所特有的方法。
Cat cat  = (Cat) animal; //向下转型
//可以调用子类特有的方法
cat.catchMouse();
```



##### 属性的重写问题

- 属性没有重写之说，==属性的值看编译类型==。

```java
public class Test{
	public static void main(String []args){
        Base base = new Sub();//向上转型
        System.out.println("base.count");//编译类型是Base 所以是访问Base中的count属性 输出1。
    }
    
}
class Base{
    int count = 1;
}
class Sub extends Base {
    int count = 2;
}
```

- **instanceOf** 比较操作符，用于判断对象的==运行类型==是否为XX类型或者是XX类型的子类型。

```java
public class Test{
	public static void main(String []args){
        BB bb = new BB();
   		System.out.println(bb = instanceOf BB );//输出 ture
        System.out.println(bb = instanceOf AA );//输出 ture
        
        AA aa = new BB();
         System.out.println(aa = instanceOf AA );//输出 ture
         System.out.println(aa = instanceOf BB );//输出 ture
    }
}
class AA{}
class BB extends AA{}

```



##### 多态数组

数组的定义类型为父类型，里面保存的实际元素类型是子类型。（使用了动态绑定机制）







#### ==动态绑定机制（重点）==

java的动态绑定机制：

1. 当调用对象方法时，==该方法会和该对象的内存地址/运行类型绑定==。
2. 当调用对象属性时，==没有动态绑定机制，哪里申明，哪里使用==。





##### 多态参数

方法定义的形参类型为父类类型，实参类型允许为子类型。





























#### super关键字

super代表对==父类的引用==，用于访问父类的属性、方法、构造器。

---

用法

1. 访问父类的属性，但不能访问父类的私有属性。 super.属性名
2. 访问父类的方法，但不能访问父类的私有方法。super.方法名（参数列表）
3. 访问父类的构造器，==必须在构造器函数体中==，只能放在构造器的第一行，且只能有一句。super(参数列表)

---

好处：

1. 分工明确，父类属性由父类初始化，子类属性由子类初始化。
2. 子类和父类又同名属性和方法时，可以使用super关键字，消除二义性。



#### Object类

在java.lang包内

---

- equals方法
- hashCode方法：返回对象的哈希码值
  1. 提高具有哈希结构容器的效率
  2. 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的。
  3. 两个引用，如果指向的是不同对象，则哈希值是不一样的。
  4. 哈希值是根据地址来计算的，但不能将哈希值等价于地址。
  5. 在集合部分，hashCode会重写

- toString方法：返回 全类名+@+哈希值的十六进制，子类一般会重写toString方法，用来返回对象的属性信息。 （当直接输出一个对象时，toString方法会被默认调用）

  ```java
   //toString 源码
  public String toString() {
      //getClass().getName()类的全类名（包名+类名）
          return getClass().getName() + "@"  +  Integer.toHexString(hashCode());
      }
  ```

- finalize 方法：
  1. 当对象被回收时，系统会自动调用该对象的finalize方法，子类可以重写该方法，做一些释放资源的操作。
  2. 什么时候被回收：当某个对象没有任何引用时，jvm会认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁对象，在销毁该对象前，会先调用finalize方法。
  3. 垃圾回收机制的调用，由系统来决定，也可以通过System.gc()主动触发垃圾回收机制。



## 第二阶段

### 类变量和类方法（静态）

#### 类变量

- 一个类中所有对象实例所共享的数据。
- 在类加载的时候就生成。

```java
public static int count = 0;
```

---

访问类变量的方法

- 类名.类变量【推荐】
- 对象名.类变量



#### 类方法

当方法使用了static进行修饰时，该方法就是静态方法。

静态方法就可以访问静态变量。

---

类方法的形式：访问修饰符 static 返回类型 方法名(){}

类方法的调用：

- **类名.类方法**
- 对象名.类方法

---

类方法的经典使用场景：

当方法中不涉及到任何和对象相关的成员，则可以将方法设计成静态方法，提高开发效率。例如工具类，Math类。（不需要创建对象，就可以使用方法）

---

类方法中的注意点：

1. 类方法中无this参数。
2. 类方法中不允许使用和对象有有关的关键字，如this，super
3. 类方法中只能访问静态变量和静态方法。
4. 普通成员方法，可以访问静态的也可以访问非静态的方法和变量。



### main方法

```java
public static void main(String []args){
    
}
```

1. main方法是虚拟机调用的。
2. java虚拟机需要调用main方法，所以访问权限必须是public
3. java虚拟机在执行main方法时不需要创建对象，所以方法必须是static
4. main方法接受String类型的数组参数，该数组中保存执行java命令时 传递给所运行的类的参数。
5. 执行程序时，传进参数。 java 执行类名 参数1，参数2，参数3 ...



### 代码块

**概念：**

​	代码块又叫初始化块，属于类的一部分，类似方法，只有方法体。在加载类时，或创建对象是隐式调用。

**基本语法：**

​		[修饰符]{

​		代码

​		};		

1. 修饰符可选，只能写static
2. 代码块分为两类，用static修饰的叫做静态代码块，无修饰的叫做普通代码块。
3. ；可写可不写

---

**注意事项：**

1. static代码块，随着**类加载**而执行只会执行一次，如果普通代码块，每**创建**一个对象就执行。

2. 普通代码块，创建对象实例时，会被隐式地调用，被创建一次，就会调用一次。

3. 如果使用类的静态成员时，普通代码块并不会执行。

4. 构造器的最前面隐含了super()和调用普通代码块。静态相关的代码块，属性初始化，在类加载时，就执行完毕。

   ```java
   class A{
       public A(){
           //隐含有super();
           //隐含 调用普通代码块
           System.out.println("ok");
       }
   }
   ```

5. 静态代码块只能调用静态成员，普通代码块可以调用任意成员。



### 单例设计模式

单例设计模式，就是采用一定的方法，保证在整个软件系统中，对某个类只能存在一的对象实例，并且该类只提供一个取得其对象实例的方法。

---



#### 饿汉式

步骤：

1. 构造器私有化，防止直接new
2. 在类的内部创建对象
3. 向外暴露一个静态的公共方法

#### 懒汉式

步骤：

1. 构造器私有化，防止直接new
2. 在类的内部创建对象
3. 向外暴露一个静态的公共方法



### final关键字

使用情况：

1. 不希望类被继承时，可以使用final修饰。
2. 不希望父类的某个方法被子类重写。
3. 不希望类的某个属性被修改
4. 不希望某个局部属性修改

注意点：

1. final修饰的属性又叫常量，用大写字母和下划线命名。
2. final修饰的属性在定义时，必须赋初值，并且以后不能修改。



### 抽象类

当父类的某些方法，需要声明，但又不确定如何实现时，可以将其声明为抽象方法，这个类就叫抽象类。（方法没有方法体）

---

注意点：

1. 抽象类不能实例化。（不能new）
2. 抽象类中可以没有抽象方法。
3. 一个类中包含了抽象方法，那这个类一定要申明为抽象类。
4. abstract 只能修饰类和方法。
5. 抽象方法没有方法体。
6. 一个类继承了一个抽象类，必须实现继承的抽象类的抽象方法，如果不实现抽象方法，也要把这个类声明为抽象方法。
7. ==抽象方法不能使用private，final和static来修饰==，因为这些关键字都是与重写相违背的。（抽象方法主要是为了让子类重写抽象方法。）



#### 抽象类 模板设计模式





### 接口

接口就是给出一些没有实现的方法，封装到一起，到某个类要使用的时候，再根据具体情况把这些方法写出来。

```java
interface interfaceName{
    //属性
    //方法（1.抽象方法2默认实现方法3.静态方法）
}
class className implements interfaceName{
    //自己的属性
    //自己的方法
    //必须实现接口的抽象方法
}
```

在jdk8之后可以有默认实现方法，需要使用default关键词修饰，也可以有static方法。

---

接口注意点：

1. 接口不能实例化。

2. 接口中的方法都是public方法，接口中抽象方法可以不用abstract修饰。

3. 一个类实现接口，必须将接口中的所有方法都实现。

4. 一个类可以同时实现多个接口。

5. 接口中所有的属性，只能是final的，而且只能时public static final修饰 int a = 1; 等价于 public static final int a = 1;

6. 接口不能继承其他类，但是可以继承多个接口。

7. 接口的修饰符 只能为public 或者默认

   

#### 接口的多态

**接口类型的变量 可以指向实现了 这个接口的对象实例。**

1. 多态参数
2. 多态数组
3. 接口的多态传递

### ==内部类（四种）==

**概念**：一个类的内部又完成的嵌套了另一个类的结构。被嵌套的类称为内部类。嵌套其他类的类叫做外部类。是我们类的第五大成员（==类的五大成员==：属性、方法、构造器、代码块、内部类），内部类最大的特点就是可以直接访问私有属性，并且可以体现类与类之间的包含关系。

**基本语法：**

```java
class Outer{ //外部类
    class Inner{//内部类
        
    }
}
```

**内部类的分类：**

- 定义在外部类的局部位置上（比如方法体内）：
  1. 局部内部类（有类名）
  2. ==匿名内部类（没有类名）==
- 定义在外部类的成员位置上：
  1. 成员内部类（没用static修饰）
  2. 静态内部类（使用static修饰）



#### 1.局部内部类

**概念**：局部内部类定义在外部类的局部位置，比如方法中，并且有**类名**。

```java
class Outer{//外部类
    private int n = 1;
    private void m1(){
        //在方法体内
        class Inner{//局部内部类（本质任然为一个类）
            private void f1(){
                 //可以直接访问外部类的私有成员和方法
                System.out.println(n); 
            }
        }
    }
}
```

**特点：**

1. 可以直接访问外部类的私有成员和方法
2. 不能添加访问修饰符，因为它的地位就是一个**局部变量**。局部变量不能使用修饰符，但是可以用final来修饰。
3. 作用域：仅仅在定义它的方法或代码块中。
4. 外部类在方法中，可以创建内部类的对象，然后调用内部类的方法，来达到访问内部类的目的。
5. 外部其他类 不能直接访问局部内部类
6. 如果外部类和局部内部类的成员重名时，默认遵循就近原则，如果想要访问外部类的同名成员时，可以采用 **外部类名.this.成员** 的方法。

#### ==2.匿名内部类==

**概念：**

1. 本质是类
2. 内部类
3. 该类**没有名字**
4. 同时还是一个对象

**基本语法：**

```java
new  类或者接口(参数列表){
    类体
}
```

##### **举例基于接口的匿名内部类的使用：**

- 传统方法：想使用IA接口，并创建对象。

```java

//测试类
public class AnonymousInnerClass{
    public static void main(String []args){
        Outer outer = new Outer();
        outer.method(); //输出  Tiger cry...
        
    }
}
//外部类
class Outer{
    private int n1 = 10;
    public void method(){
        //需求：想使用IA接口，并创建对象。
        //传统方法：写一个类实现该接口，并创建对象。
         IA tiger = new Tiger();
       	 tiger.cry();
    }
}

//接口
interface IA{
    void cry();
}
class Tiger implements IA{
    //重写IA接口中的cry方法
	public void cry(){
        System.out.println("Tiger cry...");
    }
}

```

**分析：**上述代码中，如果Tiger类只是使用一次，后面就不再使用，上述直接有一个Tiger类就显的有点多余，就引出了匿名内部类的方法，简化开发。

- 匿名内部类的方法

```java 
//测试类
public class AnonymousInnerClass{
    public static void main(String []args){
        Outer outer = new Outer();
        outer.method(); //输出  Tiger cry...
        
    }
}
//外部类
class Outer{
    private int n1 = 10;
    public void method(){
        //需求：想使用IA接口，并创建对象，Tiger类只使用一次。
        //匿名内部类方法
       IA tiger =  new IA(){
           //重写接口中的cry方法
            public void cry(){
      		  System.out.println("Tiger cry...");
      		 }
   	 	};
         
}

//接口
interface IA{
    void cry();
}
```

**分析：**上述代码中的15-20行如下

```java
  IA tiger =  new IA(){
           //重写接口中的cry方法
            public void cry(){
      		  System.out.println("Tiger cry...");
      		 }
   	 	};
//分析：
//tiger的编译类型是 IA
//tiger的运行类型是 匿名内部类
//上述代码的匿名内部类在底层如下所示
/*
	class Outer$1 implements IA{
   	 	//重写IA接口中的cry方法
		public void cry(){
       	 System.out.println("Tiger cry...");
    	}
	}
*/
//类名Outer$1是系统分配的（格式：Outer+$+数字）
//jdk 底层在创建匿名内部类Outer$1后，立即创建Outer$1实例，并把地址方返回给tiger
```



##### 基于类的匿名内部类的使用：

（个人理解：理解为不用创建新类来**继承**旧类，来重写类中的方法。）

```java
class Outer{
    private int n1 = 10;
    public void method(){
    
        Father father = new Father("jack"){
            //重写了test()方法
            public void test(){
                //代码
            }
        }; 
        //与 Father father = new Father("jack");不同
        //father的编译类型是Father
        //father的运行类型是 匿名内部类Outer$1
        /*底层会创建匿名内部类
        	class Outer$1 extends Father{
        		 public void test(){
                //代码
           		 }
        	}
        */
}
class Father{
    public Father(String name){}//构造器
    public void test(){}
}
```

##### 匿名内部类的使用场景

1. 当作实参直接传递，简洁高效。

```java
public class main{
    public static void main(String []args){
        //匿名内部类当作实参直接传递
        f1(new IA(){
            public void show(){
                  System.out.println("xxx");
            }
        });
        
    }
    //静态方法
    public static void f1(IA ia){
        ia.show();
    }
}


interface IA{
    void show();
}
```

#### 成员内部类

**概念：**成员内部类是定义在外部类的成员位置，并且没有static修饰。

**举例：**

```java
class Outer{
    private int n1 = 10;
    //可以添加访问修饰符
    //
    protected class Inner{
        public void	say(){
            System.out.println("xxx");
        }
    }
}

```



#### 静态内部类

**概念：**成员内部类是定义在外部类的成员位置，并且有static修饰。



### 枚举和注解

#### 枚举

**概念：**枚举是一组常量的集合，枚举是一种特殊的类，里面只包含一组有限的特定的对象。

**实现枚举的方式：**

- 自定义类实现枚举：

  1. 将构造器私有化，防止直接new对象。
  2. 去掉setXxx方法，防止属性被修改。
  3. 在类内部之间创建固定的对象，向往暴露（添加 public static final）。

- 使用自带的enum类

  1. 使用关键字，enum代替class
  2. 可以用SPRING("spring","温暖");代替public static final Season SPRING = new Season（"spring","温暖"）;
  3. 如果有多个常量，使用逗号隔开。
  4. 使用enum实现枚举，需将定义常量对象，写在最前面。（ SPRING("spring","温暖")写在前面 ）

  ```java
  enum Season{
      //多个用逗号隔开。
      SPRING("spring","温暖"),
      SUMMER("summer","炎热");
      private String name;
      private String desc;
  
      private Season(String name, String desc) {
          this.name = name;
          this.desc = desc;
      }
  
      public String getName() {
          return name;
      }
  
      public String getDesc() {
          return desc;
      }
  }
  
  ```

  ---

  **enum关键字的注意点：**

  1. 使用enum关键字开发一个枚举类时，默认**会继承Enum类**
  2. 传统的public static final Season SPRING = new Season（"spring","温暖")；简化成   SPRING("spring","温暖")；
  3. 如果使用无参构造器，实参列表和小括号都能省略。
  4. 枚举对象必须放在枚举类的行首。
  5. 使用enum关键字后，就不能再继承其他类了。
  6. enum类可以实行接口。

#### 注解(Annotation)

##### @override

**概念：**限定某个方法，重写父类的方法，只能用于方法。



##### @Deprecated

**概念：**用于表述某个程序元素过时。



##### @SuppressWarnings

**概念：**抑制编译器警告。





##### 四种元注解

1. Retention 指明注解的作用范围。
2. Target 指明注解可以在那些地方使用。
3. Documented 指明该注解是否会在javadoc中体现。
4. inherited 子类会继承父类注解。

### 异常

**概念：**程序运行中发生的不正常情况。

**分类：**

1. Error(错误)：jvm无法解决的严重问题。
2. Exception：一般性问题。分为运行时异常和编译时异常。

##### ==异常体系图==

![](D:/Picture/异常体系图.png)

五大运行时异常：

1. NullPointerException(空指针异常)
2. ArithmeticException(算数异常)
3. ArrayIndexOutOfBoundsException(数组下标越界)
4. ClassCastException(类型转换异常)
5. NumberFormatException(数字格式不正确异常)

##### 异常处理方式

- try-catch-final 捕获异常
- throws 抛出异常，交给调用者处理，最顶级的调用者就是jvm。

###### try-catch-final 捕获异常

```java
try{
    //可能出现异常的代码
    //如果异常发生了，则异常发生后面的代码不会执行，直接进入到catch 块。
}catch(Exception e){
    //捕获到异常时
    //系统将异常封装成Exception对象e，传递给catch。
    //得到异常对象时，程序员可以自己去处理。
}finally{
    //不管try中是否有异常发生，始终要执行finally。
    //通常将释放资源的代码放在finally中。
}
```

###### throws 抛出异常

1. 对于编译异常，程序必须处理。
2. 对于运行时异常，程序中如果没有处理，默认就是throws方式。
2. 子类重写父类的方法时，对抛出异常的规定：子类重写的方法，所抛出的异常类型要么和父类抛出的异常一致，要么为父类抛出异常类型的子类型。



##### 自定义异常

```java
//一般继承RuntimeException
class AgeException extends RuntimeException{
    public AgeException(String name){  //构造器
        super(message);
    }
}
```



##### throw和throws的区别



|        | 意义                     | 位置       | 后面跟的东西 |
| ------ | ------------------------ | ---------- | ------------ |
| throws | 异常处理的一种方式       | 方法声明处 | 异常类型     |
| throw  | 手动生成异常对象的关键字 | 方法体中   | 异常对象     |



### 常用类

#### 包装类（wrapper）

针对八种基本数据类型相应的引用类型

| 基本数据类型 | 包装类        |
| ------------ | ------------- |
| boolean      | **Boolean**   |
| char         | **Character** |
| byte         | Byte          |
| short        | Short         |
| int          | Integer       |
| float        | Float         |
| long         | Long          |
| double       | Double        |

  Byte、Short、Integer 、Float 、Long 、Double的**父类是Number**

```java
//拆箱与装箱
public class Integer_int {
    public static void main(String[] args) {
        int i = 1;
        //手动装箱，两种方式。int --> Integer
        Integer integer = new Integer(i);
        Integer integer1 = Integer.valueOf(i);
        //手动拆箱 Integer --> int
        int a = integer.intValue();

        int n1 = 1;
        //自动装箱 int --> Integer
        Integer integer2 = n1; //底层为：Integer integer2 = Integer.valueOf(i);
        //自动拆箱 Integer --> int
        int n2 = integer2;//底层为：int n2 = integer.intValue();
    }
}
```

##### 包装类和String类型的相互转换

``` java
//以Integer --> String 为例
//方式一：
Integer i = 1；
String str1 = i +"";
//方式二：
String str2 = i.toString();
//方式三：
String str3 = String.valueOf(i);

// String-->  Integer
String str4 = "123";
Integer i2 = Integer.parseInt(str4);
Integer i3 = new Integer(str4); 
```



##### Integer和Character类常用方法



#### String类

**相关概念：**

1. String 对象用于保存字符串。
2. **字符串常量对象**是用双引号括起来的字符序列。
3. 字符串的字符使用Unicode编码，一个字符都占两个字节。
4. String 是final类。
5. String 有属性 private final char value[]; 用于存放字符串内容。
6. value是一个final类型，不可修改。==（是指value的地址不可修改。）==

##### 两种创建String对象的区别

- 直接赋值String s = "xx";

​	先从**常量池**查看是否有"xx"的数据空间，如果有直接指向；如果没有则直接创建，然后指向。s**最终指向的是常量池的空间地址。**

- String s = new String( "xx");

​	先在队中创建空间，里面维护了value属性，指向常量池的"xx"空间，如果常量池中没有，重新创建，如果有，通过value直接指向。**最终指向的是堆中的空间地址。**

###### String的常用方法

String类是保存字符串**常量**的，每次更新都出要重新开辟空间，效率较低，提供了**StringBuilder** 和**StringBuffer**来增强功能。

---

- equals 						//区分大小写判断内容是否相等
- equalsIgnoreCase     //不区分大小写判断内容是否相等
- length                        //获取字符串的个数，字符串的长度
- indexOf                    //获取字符再字符串中第一次出现的索引
- lastIndexOf             //获取字符再字符串中最后一次出现的索引
- substring                //截取指定范围的字串
- charAt                    //获取某索引处的字符，**不能使用Str[index]这种方式。**



#### StringBuffer类

**概念：**代表可变的字符序列，可以对字符串进行增删，StringBuffer也是**容器**。StringBuffer里面存放的是字符串变量，里面的值可以修改，StringBuffer的更新可以更新内容，**不用每次更新地址，**效率较高。

---

**知识点：**

1. StringBuffer的直接父类是**AbstractStringBuilder**
2. StringBuffer的对象可以串行化
3. 在父类中，**AbstractStringBuilder有属性 char value[],不是final。该value组数存放字符串内容，字符串存放在==堆==中。**
4. StringBuffer是final类
5. 构造一个其中不带字符的字符串缓冲区，其初始容量为16个字符。

##### String和StringBuffer的转换

- String --> StringBuffer

  ```java
  String str = "hello world";
  //方式一：使用构造器
  //返回的是StringBuffer对象，对str无影响。
  StringBuffer stringBuffer = new StringBuffer(str);
  //方式二：append方法
  StringBuffer stringBuffer1 = new StringBuffer();
  stringBuffer1 = stringBuffer1.append(str);
  ```

- StringBuffer-->String

  ```java
  //方式一：使用StringBuffer的toString方法。
  StringBuffer stringBuffer = new StringBuffer("hello world");
  String s = stringBuffer.toString();
  //方式二：使用构造器
  String s1 = new String(stringBuffer);
  ```



##### StringBuffer 的常见方法

| **增加** | append(); 返回类型还是StringBuffer                           |
| -------- | ------------------------------------------------------------ |
| 删除     | delete(index1,index2);  删除index1~index2的位置，不包括index2位置，**前闭后开**。 |
| 替换     | replace(index1,index2,"xxx")； index1~index2位置替换成xxx ，**前闭后开**。 |
| 插入     | insert(index,"xxx");  在索引index的位置插入xxx。             |
| 长度     | length();                                                    |



#### StringBuilder类

概念：StringBuilder不是线程安全的，该类被设计作为Stringbuffer的一个简易替换，**用在字符串缓冲区被单个线程使用的时候**，速度一般比StringBuffer快。主要操作是append和insert方法。

---

知识点：

1. StringBuilder的直接父类是**AbstractStringBuilder**，同StringBuffer。
2. Stringbuilder的对象可以串行化，同StringBuffer。
3. Stringbuilder是final，同StringBuffer。
4. 在父类中，**AbstractStringBuilder有属性 char value[],不是final。该value组数存放字符串内容，字符串存放在==堆==中。**同StringBuffer。
5. Stringbuilder的方法没有做互斥处理，在单线程的情况下使用。

#### Math类

常见方法（静态）：

1. abs 求绝对值
2. pow 求幂
3. ceil 向上取整
4. floor 向下取整
5. round 四舍五入
6. sqrt 开方
7. random 随机数（放回的是0-1之间的一个随机小数，包括零，不包括一）
8. min 最小值
9. max 最大值

#### Arrays类

常见方法：

1. toString  显示数组信息

2. sort 排序（待完善）

   sort定制排序，可以传入一个接口Comparator 实现定制排序，实现了Comparator接口的匿名内部类，要求实现compare方法。

3. binarySearch 二分查找（有序）

4. copyOf 拷贝

5. fill 数组元素填充 

6. equals 两个数组内容是否一致

7. asList 将值转换成List

   

#### System类

**常用方法：**

| exit      | 退出     |
| --------- | -------- |
| arraycopy | 拷贝数组 |
|           |          |
|           |          |



#### BigInteger和Bigdecimal

BigInteger 存放比较大的整型，Bigdecimal存放精度更高的浮点型。

#### 日期类

##### Date

Date：精确到毫秒。

SimpleDateFormat：指定格式。

```java
//java.util.date
Date d = new Date();//获取当前的系统时间，通常要对格式进行转换。
//有指定的格式规定
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss:E");
String format = sdf.format(d);
 System.out.println(format);//输出设置好格式的日期
```

##### Calendar

1. Calendar是一个抽象类 ，构造器是Protected
2. 可以通过getInstance()来获取实例

##### 第三代日期

1. LocalDate 年月日
2. LocalTime 时分秒
3. LocalDateTime 年月日，时分秒

```java
//时间格式化
DateTimeFormatter dtf = new DateTimeFormatter(格式);
String str = dtf.format(日期对象);
```



### 集合

**概念：**

1. 可以动态保存任意多个对象，使用方便。
2. 提供了方便的操作对象的方法。

#### 集合框架体系

1. 集合主要分为两组，单列集合和双列集合。
2. Collection接口有两个重要的子接口 List和set，他们的实现子类都是单列集合。
3. Map 接口的实现子类都是双列集合。

**collecrion的体系结构图**

![](D:/Picture/Collection的体系结构.png)

**Map的体系结构**

![](D:/Picture/Map的体系结构.png)



#### Collection

Collection实现类的特点：

1. Collection的实现子类可以存放多个元素，每个元素可以是Object对象。
2. 有些Collection的实现类，有些可以存放重复的元素，有些不可以。
3. 有些Collection的实现类，有些是有序的（List），有些是无序的（Set）。

Collection接口的常用方法：

| add         | 添加单个元素           |
| ----------- | ---------------------- |
| remove      | 删除指定元素           |
| contains    | 查找元素是否存在       |
| size        | 获取元素个数           |
| isEmpty     | 判断是否为空           |
| clear       | 清空                   |
| addAll      | 添加多个元素           |
| containsAll | 查找多个元素是否都存在 |
| removeAll   | 删除多个元素           |

Collection接口遍历元素的方式：

- 使用Iterator（迭代器）

  1.  Iterator对象称为迭代器，主要用于遍历Collection中的元素。

  2. 所有实现了Collection接口的集合类都有一个iterator()方法，放回一个迭代器。

     ```java
     //迭代器原理
     Iterator iterator = coll.iterator(); //得到一个集合的迭代器
     //hasNext()判断是否还有下一个元素
     //next()的作用 1，下移 2，将下移以后集合位置上的元素返回。
     while(iterator.hasNext()){
         System.out.println(iterator.next());
     }
     ```

- 增强for循环（简化版的iterator）

  **底层是迭代器**

  基本语法：
  for(元素类型 元素名：集合名或者数组名){
  	访问元素
  }

##### List

**特点：**

1. List集合类（实现List的子类）中的元素是**有序**的、可重复的、且可复制。
2. List集合类中每个元素都有其对应的顺序索引，即支持索引。
3. List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中的元素。

**List接口的常用方法：**

| indexOf     | 返回第一次出现的位置 |
| ----------- | -------------------- |
| lastIndexOf | 返回最后出现的位置   |
|             |                      |
|             |                      |
|             |                      |
|             |                      |
|             |                      |
|             |                      |

**List的三种遍历方法：**

1. iterator
2. 增强 for
3. 普通 for

###### ArrayList

**特点：**

1. 可以放所有的元素，包括空元素，可以加入**null**,并且多个。
2. ArrayList是由**数组**实现数据存储的。
3. ArrayList基本等同于Vector，但是ArrayList是**线程不安全**的。

###### ==ArrayList的底层==

特点：

1. ArrayList中维护了一个Object类型的**数组**elementData。（==transient==Object[] elementData；transient 表示该属性不会被序列化 ）
2. 当创建ArrayList对象时，如果使用无参构造器，则初始化**elementData为0**，第一次添加则扩容elementData大小为**10**，如需再次扩容，则扩容的elementData为**1.5倍**。
3. 如果使用指定大小的构造器时，则初始elementData容量为指定大小，如需扩容，则扩容的elementData为1.5倍。

###### Vector

**特点：**

1. Vector底层也是一个对象数组，protected Object[] elementData;
2. Vector是线程安全的。

###### LinkedList

**特点：**

1. LinkedList实现了**双向链表**和**双端队列**的特点。
2. 可以添加任意元素。
3. 线程不安全。

**底层原理：**

1. LinkedList底层维护了一个**双向链表**

2. LInkedList中维护了两个属性**firs**t和**last**分别指向首尾节点。

3. 每个节点（Node），里面又维护了prev、next和item三个属性。

4. LinkedList的添加删除，效率更高。

   

##### Set

**特点：**

1. Set 是**无序的**，没有索引。
2. **不允许有重复元素**，最多有一个空值。

**遍历方式（不可以用索引方式）：**

1. 迭代器
2. 增强for循环



###### HashSet

**特点：**

1. HashSet实现了Set接口

2. HashSet底层实际上是**HashMap**，HashMap的底层是 **数组+链表+红黑树**。

   ```java
   //HashSet的无参构造器
   public HashSet() {
           map = new HashMap<>();
       }
   ```

3. 可以存放null，但是只可以存放一个null。

4. HashSet不保证存放数据的顺序，取决于hash后，再确定索引的结果。

**HashSet底层：**

​	HashSet的添加元素的底层是如何实现的：

1. 添加一个元素，会得到Hash值， 然后转换成-->索引值。
2. 找到存储表table，看这个索引位置是否已经存放有元素。
3. 如果没有，直接加入。
4. 如果有，调用equals（程序员重写）比较，**如果相同，就放弃添加**，如果不相同，则添加到最后。
5. 再java8中，如果一条链表的元素个数达到 TREEIFY_THRESHOLD(默认是8)，并且table的大小>= MIN_TREEIFY_CAPACITY(默认为64)，就会进行树化（红黑树）。

###### LinkedHashSet（继承HashSet）

特点：

1. LinkedHashSet 底层是LinkedHashMap，底层维护了一个数组+双向链表。
2. 使用链表维护元素的次序（保存了插入数据顺序）。



###### TreeSet

特点：

1. TreeSet可以==排序==



```java
//当使用无参构造器，创建TreeSet时，仍然是无序的。
        //当希望添加的元素，按照字母表顺序来排序
        //使用TreeSet提供的一个构造器，可以传入一个比较器(匿名内部类)，来指定排序规则。
        TreeSet treeSet = new TreeSet(new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                //调用String的CompareTo方法进行比较
                return ((String)o1).compareTo((String)o2);
            }
        });
        treeSet.add("jack");
        treeSet.add("tom");
        treeSet.add("sp");
        treeSet.add("a");
        System.out.println(treeSet);//输出[a, jack, sp, tom]
```











#### Map

**特点：**

1. Map与Collection是并列存在的，用于保存具有映射关系的数据：key-value。
2. Map中的key和value可以是任意引用类型，会封装到HashMap$Node对象中。
3. Map中的key不允许重复。（插入同样的key值等价于替换）
4. Map中的value可以重复。
5. Map中的key和value都可以可以为空，但是key只能有一个空。
6. 常用String作为key。
7. key和value之间存在**单向一对一关系**，即通过key总能找到对应的value。
8. Map中，一对key-value存放在一个Node中，因为**Node实现了Entry**接口，有些时候也说，**一对key-value就是一个Entry**。
9. Node的结构 ：（hash，key，value，next）
10. key-value 为了**方便遍历**，还会创建一个**EntrySet的集合**，该集合存放的元素的类型是Map.Entry，(Map.Entry提供了getKey和getValue两个重要的方法，来实现遍历)而一个Entry对象里面就存放着key和value （EntrySet<Entry<k,v>>）

​															EntrySet结构图

![](D:/Picture/EntrySet结构.png)

**Map接口常用方法：**

| put         | 添加                             |
| ----------- | -------------------------------- |
| remove      | 根据key或者key-value删除映射关系 |
| get         | 根据key获取值，范围Object对象    |
| size        | 获取大小                         |
| isEmpty     | 判断是否为空                     |
| clear       | 清空                             |
| containsKey | 查找键值是否存在                 |
|             |                                  |

**Map接口的遍历方式：**

- 第一种：先取出所有的key，再通过key取出对应的value。

```java
Map map = new HashMap();
//...往map中使用put()放入一些数据
Set keyset = map.keySet();
//遍历Set类型 可以使用增强for或者迭代器。
//1）使用增强for
for(Object key : keyset){
     System.out.println(key + map.get(key));
}
//2)使用迭代器
 Iterator iterator = keyset.iterator();
 while (iterator.hasNext()) {
    Object key =  iterator.next();
    System.out.println(key + " " + map.get(key));    
   }
```

- 第二种：把所有的value 取出。

```java
Collection values = map.values();
//可以使用Collection的三种遍历方式。
//1）使用增强for循环方式举例。
   for (Object value : values) {
        System.out.println(value);
    }
//2）使用迭代器
 Iterator iterator = keyset.iterator();
 while (iterator.hasNext()) {
    Object value =  iterator.next();
    System.out.println(value);    
   }
```

- 第三种：通过EntrySet来获取key-value

```java
 //使用Map.Entry接口的getValue和getKey方法。
Set entrySet = map.entrySet();
//1）使用增强for
for (Object entry : entrySet) {
  Map.Entry mapentry = (Map.Entry)entry;
  System.out.println(mapentry.getKey()+" "+mapentry.getValue());
}
//2）使用迭代器
  Iterator iterator = entrySet.iterator();
        while (iterator.hasNext()) {
            Object next =  iterator.next();
            Map.Entry mapentry = (Map.Entry)next;
            System.out.println(mapentry.getKey()+" "+mapentry.getValue());

        }

```











#####  HashMap

特点：

1. HashMap是Map接口使用频率最高的实现类。
2. key-value形式存储数据（HashMap$Node类型）
3. 线程不安全
4. HashMap底层 = 数组+链表+红黑树

##### HashTable

特点：

1. 存放的元素是键值对，k-v
2. HashTable的键和值都不能为空
3. HashTable的使用方法基本和HashMap一致
4. HashTable是线程安全的
5. 底层有数组 类型为HashMap$Entry 初始化大小为11

##### Properties

特点：

1. Properties类继承自HashTable类并实现了Map接口，也是使用键值对形式。
2. 使用方法和HashTable类似
3. Properties还可以从xxx.properties文件中，加载数据到Properties类对象，进行读取和修改。
4. xxx.properties文件通常作为配置文件。

#### 工具类Collections

描述：

1. Colletions工具类是一个操作Set，List和Map等工具的工具类。
2. Collections工具类可以对集合元素进行排序、查询和修改等操作。

排序操作：

| reverse（List）           | 反转List中的顺序                           |
| ------------------------- | ------------------------------------------ |
| shuffle（List）           | 对List进行随机排序                         |
| sort（List）              | 按照元素自然顺序对List集合元素按照升序排序 |
| sort（List ，Comparator） |                                            |
| swap（List，int ，int）   | 交换两个位置                               |

查找和替换操作：

| max（collection）                          | 按照元素自然顺序，返回集合中最大元素 |
| ------------------------------------------ | ------------------------------------ |
| max（collection ，comparator）             |                                      |
| min（collection）                          |                                      |
| int frequency（collections，Object）       | 返回指定元素出现的次数               |
| void copy（List des，List src）            | src中元素复制到des中                 |
| boolean replaceAll（List，oldVal，newVal） |                                      |



### 泛型

**概念：**

1. 泛型又称为参数化类型，解决数据的安全性问题。
2. 在类声明或者实例化时只要指定好具体的类型即可。
3. 泛型可以保证程序在编译时没有发出警告，运行时就不会产生ClassCastException异常。
4. 泛型的作用是：可以在类声明时，通过一个表示表示类中某个属性的类型，或者某个方法的返回值类型，或者是参数类型。

**泛型的声明：** interface 接口<T>{} 和 class 类<K，V>{} //T为Type的缩写。

---

**泛型注意点：**

1. T，K，V只能是引用类型。

2. 在指定泛型的具体类型时，可以**传入该类型或者该类型的子类型**。

3. 泛型类适用形式：

   ```java
   List<Integer> list = new ArrayList<>();
   ```

   

**自定义泛型：**

1. 自定义泛型类。

   ```java
   //举例
   //使用泛型的数组，不能初始化。
   //静态方法、静态属性不能使用泛型。
   
   class Tige<T,R,M>{
       String name;
       R r;
       M m;
       T t;
   }
   ```

2. 自定义泛型接口

   ```java
   //静态成员不能使用泛型。
   //泛型接口的类型，在继承接口或者实现接口时确定。
   interface Usb<U,R>{
       
   }
   ```

3. 自定义泛型方法

   ```java 
   class Car{
       //普通方法
       public void fun(){
   	}
       //泛型方法
       public<T,R> Void fly(T t, R r){
           
       }
   }
   ```

   

**泛型的继承和通配符的说明：**

1. 泛型不具备继承性。
2. <?>支持任意泛型类型。
3. <? extends A>支持A类以及A类的子类，规定了泛型的上限。
4. <? super A>支持A类及A类的父类，不限于直接父类，规定了泛型的下限。



### 线程基础

**创建线程的两种方式（启动）：**

1. 继承Thread方法，重写run方法。

   ```java
   //当一个类继承了Thread类，该类就可以当作线程来使用。
   //重写run方法。
   class Cat extends Thread{
       @Override
       public void run() {
           super.run();
       }
   }
   ```

2. 实现Runnable接口，重写run方法。(底层使用了==代理模式==，静态代理)

   ```java
   public class Thread_ {
       public static void main(String[] args)
               throws InterruptedException {
           cat cat = new cat();
           //不能调用 cat.start() 方法
           //创建Thread对象，把cat对象放入Thread
           Thread thread = new Thread(cat);
           thread.start();
   
       }
   }
   class cat implements Runnable{
       int count = 0;
       @Override
       public void run() {
           System.out.println("叫" + count++ + Thread.currentThread().getName());
           try {
               Thread.sleep(1000);
           } catch (InterruptedException e) {
               e.printStackTrace();
           }
       }
   }
   
   ```

**线程的终止：**

**线程常用方法：**

| 设置名称   | setName     |
| ---------- | ----------- |
| 设置优先级 | setPriority |
| 得到名字   | getName     |
| 线程的礼让 | yield       |
| 线程插队   | join        |

**注意点：**

1. 当main线程启动一个子线程Thread-0,主线程不会阻塞，会继续执行。
2. 实现Runnable接口方式，更加适合多个线程共享统一资源的情况，并且避免了单继承的限制。

#### 用户线程和守护线程

用户线程：也叫工作线程，当线程任务执行完或通知方式结束。

守护线程：一般是为工作线程服务的，当所有用户线程结束，守护线程自动结束。常见的守护线程有 **垃圾回收机制。**

---

将线程设置成守护线程（daemon）：



#### 线程生命周期





#### 线程同步

**线程同步机制：**

在多线程编程中，一些敏感数据不允许被多个线程同时访问，此时就是用同步访问机制，保证数据在任何同一时刻，最多只有一个线程访问，保证数据的完整性。

**实现同步的方式-synchronized：**

1. 同步代码块

   synchronized（对象）{ //得到对象的锁，才能操作同步代码。

   //需要被同步的代码

   }

2. synchronized还可以放在方法声明中，表示整个方法为 同步方法

   public synchronized void m（String name）{

   //需要被同步的代码

   }

### 文件

文件在程序中是以流的形式来操作的。

---

**创建文件对象的构造器和方法：**

- new File（String pathname） //根据路径构建一个File对象。

  ```java
     public static void create01(){
          String filePath = "d:\\Files\\test.txt";
          File file = new File(filePath);
          try {
              file.createNewFile();
              System.out.println("文件创建成功");
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
  ```

  

- new File（File parent，String Child）//根据父目录文件+ 子路径构建

  ```java
     public void create02(){
          File file = new File("d:\\Files");
          String FileName = "test2.txt";
          File file1 = new File(file, FileName);
          try {
              file1.createNewFile();
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
  ```

  

- new File（String parent，String Child）//根据父目录+ 子路径构建

  ```java
    public void create03(){
          String FilePath = "d:\\Files";
          String FilePath1 = "test3.txt";
          File file = new File(FilePath, FilePath1);
          try {
              file.createNewFile();
              System.out.println("文件创建成功");
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
  ```

  

- createNewFile 创建新文件

**获取文件的信息：**

| 方法名          | 功能 |
| --------------- | ---- |
| getName         |      |
| getAbsolutePath |      |
| getParent       |      |
| lenth           |      |
| exits           |      |
| isFile          |      |
| isDictionary    |      |



**目录操作和文件删除：**

创建目录：mkdir 创建一级目录，mkdirs 创建多级目录，delete删除空目录或者文件。

#### IO流

字节流：分为输入流（InputStream）和输出流（OutputStream）。

字符流：分为输入流（Reader）和输出流（Writer）。

```上述的四个类都是抽象类 ```

##### FileInputStream

字节输入流

##### FileOutputStream

字节输入流

##### FileReader



##### Properties类

专门用于读写配置文件的集合类。

配置文件的格式：

键=值

键=值

---

**常用方法：**

| 方法名                    | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| load                      | 加载配置文件的键值对到Properties对象                         |
| list                      | 将数据显示到指定设备                                         |
| getProperty（key）        | 根据键获取值                                                 |
| setProperty（key，value） | 设置键值对到Properties对象中                                 |
| store                     | 将Properties中的键值对存储到配置文件，在idea中，保存信息到配置文件，如果含有中文，会存储Unicode |



## 第三阶段

### 网络编程

#### InetAddress类

**常用方法举例：**

```java
    public static void main(String[] args) throws IOException {
        //获取本机的InetAddress对象。
        InetAddress localhost = InetAddress.getLocalHost();
        System.out.println(localhost);//输出内容Isaac/169.254.202.201

        //根据指定的主机名获取InetAddress对象
        InetAddress hostName = InetAddress.getByName("Isaac");
        System.out.println(hostName);

        //根据域名放回InetAddress对象
        InetAddress byName = InetAddress.getByName("www.baidu.com");
        System.out.println(byName); 
        

    }
```



#### Socket

Socket套接字，通信两端都要有Socket，是两台机器通信的端点。网络通信实际上就是Socket间的通信。数据在两个Socket之间通过IO进行传输。

---





### 反射

通过外部文件（例如Properties文件）配置，在不修改源码的情况下，来控制程序，符合设计模式OCP原则（开闭原则：不修改源码，开扩功能）。

---

反射机制：

1. 反射机制允许程序在执行期间借助于Reflection API取得任何类的内部信息（比如成员变量，构造器，成员方法等等），并能操作对象的属性和方法。反射在设计模式和框架底层都会用到。
2. 加载完类之后，在堆中就产生了一个Class类型的对象（一个类只有一个Class对象），这个对象包含了类的完整结构信息。通过这个对象得到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，形象的称之为：反射。

原理图：

![](D:/Picture/反射原理图.png)

**反射机制的作用：**

1. 在运行时判断任意一个对象所属的类
2. 在运行时构造任意一个类的对象
3. 在运行时得到任意一个类所具有的成员变量和方法
4. 在运行时调用任意一个对象的成员变量和方法
5. 生成动态代理

**反射的主要类：**

1. Java.lang.Class :代表一个类，Class对象表示某个类加载后在堆中的对象
2. java.lang.reflect.Method:代表类的方法
3. java.lang.reflect.Field:代表类的成员变量
4. java.lang.reflect.Constructor:代表类的构造方法

**反射的优缺点：**

1. 优点：可以动态的创建和使用对象，使用灵活。
2. 缺点：使用反射基本是解释执行，对执行速度有影响。

#### Class类

##### 概念：

1. Class也是类，继承Object类
2. Class不是new出来的，是系统创建的
3. 对于某个类的Class类对象，在内存中只有一份，因此类只加载一次。
4. 每个类的实例都会记得自己是由哪个Class实例生成的。
5. 通过Class对象可以完整地得到一个类的完整结构，通过一系列API
6. Class对象存在于堆上。

##### Class类中常用方法举例：

```java
//Car类
package com.Reflection;

public class Car {
    public String brand = "Audi";
    public int price = 1000;
    public String color = "black";

    @Override
    public String toString() {
        return "Car{" +
                "brand='" + brand + '\'' +
                ", price=" + price +
                ", color='" + color + '\'' +
                '}';
    }
}
//Class_类
package com.Reflection;

import java.lang.reflect.Field;

public class Class_ {
    public static void main(String[] args) throws Exception {
        String classAllPath = "com.Reflection.Car";
        //获取到Car类对应的Class对象
        Class cls = Class.forName(classAllPath);
        //输出cls
        System.out.println(cls); //输出为：class com.Reflection.Car
        //得到包名
        System.out.println(cls.getPackage().getName());//输出为：com.Reflection
        //通过cls创建对象实例
        Car car = (Car)cls.newInstance();
        //通过反射获取属性brand
        Field brand = cls.getField("brand");
        System.out.println(brand.get(car));//输出：Audi
        //通过反射给属性赋值
        brand.set(car,"BMW");
        System.out.println(brand.get(car));//输出：BMW
        // 得到所有的属性
        Field[] fields = cls.getFields();
        for (Field field :fields) {
            System.out.println(field.get(car));//输出：BMW 1000 black
        }


    }
}

```

##### 获取Class类的方法

1. 前提：已知一个类的全类名，且该类在类路径下，可以通过Class的静态方法forName()获取。```多用于配置文件，读取类全路径，加载类```

2. 前提：若已知具体的类，通过类的class获取，该方式最为安全可靠，程序性能最高。Class cls = Cat.class;``` 多用于参数传递，比如通过反射得到对应构造器的对象```

3. 前提：已知某个类的实例，调用该实例的getClass()方法获取Class对象。Class cls = 对象.getClass();```通过创建好的类，获取Class对象。```

4. 通过类加载器获取到类的Class对象。

5. 基本数据类型，按如下方式得到Class对象。

   Class cls = 基本数据类型.class;

6. 基本数据类型对应的包装类，可以通过.TYPE获取到Class对象。 Class cls = Integer.TYPE;

#### 类加载

**反射机制**是Java实现动态语言的关键，也就是**通过反射实现类的动态加载。**

1. 静态加载：编译时加载相关的类，如果有则报错，依赖性太强。
2. 动态加载：运行时**加载需要的类**，如果运行时不用该类则不报错，降低了依赖性。（需要什么类再加载什么类）

---

类加载的时机：

1. 当创建对象时（new）（静态加载）
2. 当子类被加载时，父类也加载。（静态加载）
3. 调用类中的静态成员。（静态加载）
4. 通过反射。（动态加载）

---

##### **类加载流程**

1. 加载阶段

   JVM再该阶段的主要目的是将字节码从不同的数据源转化为二进制字节流加载到内存中，并生成一个代表该类的java.lang.Class对象。

2. 链接阶段

   1. 验证：

      目的为了确保Class文件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机自身的安全。

   2. 准备：

      JVM会在该阶段对静态变量，分配内存并默认初始化。

   3. 解析

      将常量池中的符号引用替换为直接引用的过程。

3. 初始化阶段

   1. 初始化阶段，才真正开始执行类中定义的java程序代码，此阶段是执行<clinit>()方法的过程。
   2. <clinit>()方法是由编译器按语句在源文件中出现的顺序，依次自动收集类中的所有==静态变量==的赋值动作和==静态代码块==中的语句，并进行合并。

   

#### 通过反射获取类的结构信息



#### 通过反射创建对象

1. 方式一：调用类中的public修饰的无参构造器。
2. 方式二：调用类中的指定构造器。

```java
package com.Reflection;

import java.lang.reflect.Constructor;

public class ReflectionCreateInstance {
    public static void main(String[] args) throws Exception {
        //1.先获取到User类的Class对象
        Class cls = Class.forName("com.Reflection.User");
        //2.通过public的无参构造器创建实例
        Object o = cls.newInstance();
        //3.通过public的有参构造器创建实例
        Constructor constructor = cls.getConstructor(String.class);
        Object object = constructor.newInstance("name1");
        System.out.println(object);
        //4.通过非public的有参构造器创建实例
        Constructor declaredConstructor = cls.getDeclaredConstructor(int.class, String.class);
        declaredConstructor.setAccessible(true);//爆破：使用反射可以访问私有的构造器
        Object o2 = declaredConstructor.newInstance(19, "name2");

    }
}
class User{
    private int age = 10;
    private String name = "name";
    public User(){}

    public User(String name) {
        this.name = name;
    }

    private User(int age, String name) {
        this.age = age;
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}
```



#### 通过反射访问类中的成员

```java
package com.Reflection;

import java.lang.reflect.Field;

public class ReflectionAccessProperties {
    public static void main(String[] args) throws Exception {
        //1.得到Student类对应的Class对象
        Class<?> cls = Class.forName("com.Reflection.Student");
        //2.创建对象
        Object o = cls.newInstance();
        //3.通过反射得到age属性对象
        Field age = cls.getField("age");
        age.set(o,88);
        //4.通过反射操作name属性对象
        Field name = cls.getDeclaredField("name");
        name.setAccessible(true);//爆破
        name.set(o,"name");
        

    }
}
class Student{
    public int age;
    private static String name;
    public Student(){
    }


}
```



#### 通过反射访问类中的成员

```java
package com.Reflection;

import java.lang.reflect.Method;

public class ReflectionAccessMethod {
    public static void main(String[] args) throws Exception {
        //1.得到Class对象
        Class<?> cls = Class.forName("com.Reflection.Boss");
        //2.创建对象
        Object o = cls.newInstance();
        //3.得到hi方法对象
        Method hi = cls.getDeclaredMethod("hi",String.class);
        //调用
        hi.invoke(o,"hello");

        //调用private static方法
        Method say = cls.getDeclaredMethod("say", int.class, String.class, char.class);
        //爆破
        say.setAccessible(true);
        System.out.println(say.invoke(o, 10, "hello", '男'));
        
    }
}
class Boss{
    public int age;
    private static String name;
    public Boss(){}
    private static String say(int n,String s,char c){
        return n +" " + s +" " +c;
    }
    public void hi(String s){
        System.out.println("hi " +s);
    }
}

```

### JDBC

#### JDBC程序编写步骤

1. 注册驱动---加载Driver
2. 获取连接---得到Connection
3. 执行增删改查---发送SQL到mysql执行
4. 释放资源

```java
public class jdbc01 {
    public static void main(String[] args) throws SQLException {
        //前置操作
        // 1. 注册驱动---加载Driver
        Driver driver = new Driver();
        //2. 获取连接---得到Connection
        String url = "jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true";
        Properties properties = new Properties();
        //将用户名和密码放入到Properties对象中
        properties.setProperty("user","root");
        properties.setProperty("password","root");
        Connection connect = driver.connect(url, properties);
        //3. 执行增删改查---发送SQL到mysql执行
        String sql ="insert into actor values(null,'tom','男','1990-11-11','110')";
        Statement statement = connect.createStatement(); //statement用于执行静态SQL语句并返回执行的对象
        int row = statement.executeUpdate(sql);//返回影响的行数。
        System.out.println(row>0?"成功":"失败");
        //4. 释放资源
        statement.close();
        connect.close();
    }
}
```

**连接数据库的方式（五种方式）：**

```java
public class jdbcConnect {
   @Test
   //方式一：
    public void connect01() throws SQLException {
        Driver driver = new Driver();
        //2. 获取连接---得到Connection
        String url = "jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true";
        Properties properties = new Properties();
        //将用户名和密码放入到Properties对象中
        properties.setProperty("user","root");
        properties.setProperty("password","root");
        Connection connect = driver.connect(url, properties);
        System.out.println(connect);
    }
    //方式二:使用反射,更加灵活
    @Test
    public void connect02() throws ClassNotFoundException, IllegalAccessException, InstantiationException, SQLException {
        Class<?> cls = Class.forName("com.mysql.cj.jdbc.Driver");
        Driver driver = (Driver)cls.newInstance();

        String url = "jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true";
        Properties properties = new Properties();
        //将用户名和密码放入到Properties对象中
        properties.setProperty("user","root");
        properties.setProperty("password","root");
        Connection connect = driver.connect(url, properties);
        System.out.println(connect);
    }
    //方式三：使用DriverManager代替Driver 进行统一管理
    @Test
    public void connect03() throws Exception {
        Class cls = Class.forName("com.mysql.cj.jdbc.Driver");
        Driver driver = (Driver)cls.newInstance();

        String url = "jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true";
        String user = "root";
        String password = "root";

        DriverManager.registerDriver(driver);
        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println(connection);
    }
    //方式四：与方式三少了 DriverManager.registerDriver(driver);
    //使用最多
    @Test
    public void connect04() throws Exception {
        Class cls = Class.forName("com.mysql.cj.jdbc.Driver");

        String url = "jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true";
        String user = "root";
        String password = "root";


        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println(connection);
    }
    //第五种方式：使用配置文件
    @Test
    public void connect05() throws Exception {
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");
        Class.forName(driver);
        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println(connection);
    }

}

```

#### ResultSet

概念：

1. 表示数据库结果集的数据表
2. ResultSet对象保持一个光标指向其当前的数据行。最初光标指向表头。
3. next方法将光标移动到下一行，当ResultSet对象中没有更多行时，返回false，因此可以在while循环中使用循环遍历结果集。

```java
public class ResultSet {
    @SuppressWarnings("all")
    public static void main(String[] args) throws Exception {
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");
        Class.forName(driver);
        Connection connection = DriverManager.getConnection(url, user, password);

        Statement statement = connection.createStatement();
        String sql = "select * from actor";
        java.sql.ResultSet resultSet = statement.executeQuery(sql);

        while (resultSet.next()){
            int id = resultSet.getInt(1);
            String name = resultSet.getString(2);
            String sex = resultSet.getString(3);
            Date date = resultSet.getDate(4);
            System.out.println(id + "\t" + name + "\t" + sex + "\t" + date);
        }


        connection.close();
        statement.close();
        resultSet.close();
    }
}
```



#### Statement

概念：

1. Statement对象用于执行静态SQL语句并返回其生成的对象
2. Statement存在SQL注入风险

#### PreparedStatement

概念：

1. PreparedStatement执行的SQL语句中的参数用问号来表示，调用PreparedStatement对象的setXxx()方式来设置这些参数。setXxx()方法有两个参数，第一个参数是要设置的SQL语句中的参数的索引（从1开始），第二个是设置的SQL语句中的参数的值。
2. 调用executeQuery()，返回ResultSet对象。
3. 调用executeUpdate()，执行更新操作。

```java
public class PreparedStatement_ {
    public static void main(String[] args) throws Exception {
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");
        Class.forName(driver);
        Connection connection = DriverManager.getConnection(url, user, password);
        String sql = "select * from actor where name = ?";
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        preparedStatement.setString(1,"tom");
        ResultSet resultSet = preparedStatement.executeQuery();

        while (resultSet.next()){
            int id = resultSet.getInt(1);
            String name = resultSet.getString(2);
            String sex = resultSet.getString(3);
            Date date = resultSet.getDate(4);
            System.out.println(id + "\t" + name + "\t" + sex + "\t" + date);
        }
        connection.close();
        preparedStatement.close();
        resultSet.close();  
}
```

#### JDBCUtils(模板设计模式)

完成连接、关闭操作

```java
//Utils类
//完成mysql的连接和关闭操作
public class JDBCUtils {
    private static String user;
    private static String password;
    private static String url;
    private static String driver;
        //在static代码块初始化
    static {
            Properties properties = new Properties();
            try {
                properties.load(new FileInputStream("src\\mysql.properties"));
                user = properties.getProperty("user");
                password = properties.getProperty("password");
                url = properties.getProperty("url");
                driver = properties.getProperty("driver");
            } catch (IOException e) {
               throw new RuntimeException(e);
            }
        }

    // 连接数据库，返回Connection
    public static Connection getConnect(){
        try {
            return DriverManager.getConnection(url,user,password);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }

    }
    //关闭资源
    public static void close(ResultSet resultSet, Statement statement,Connection connection){
          try {
              if(resultSet!=null)resultSet.close();
              if(statement!=null)statement.close();
              if(connection!=null)connection.close();
          }catch (SQLException e){
              throw new RuntimeException(e);
          }
    }

}
```



```java
//使用Utils类完成操作
public class JDBCUtils_Test {
    @Test
    public void Test() throws Exception {
        Connection connect = JDBCUtils.getConnect();

        String sql = "update actor set name = ? where id = ?";

        PreparedStatement preparedStatement = connect.prepareStatement(sql);

        preparedStatement.setString(1,"bob");
        preparedStatement.setInt(2,1);
        preparedStatement.executeUpdate();

        JDBCUtils.close(null,preparedStatement,connect);


    }
}
```

#### 事务

概念：

1. JDBC程序中当一个Connection对象创建时，默认情况下时自动提交事务：每次执行一个SQL语句，如果执行成功，就会向数据库自动提交，而不能回滚。

2. JDBC程序中为了让多个语句作为一个整体执行，需要使用事务。

3. 调用Connection的setAutoCommit（false）取消自动提交。

4. 在所有SQL语句执行成功后，调用commit()方法提交事务。

5. 在某个操作失败或出现异常，调用rollback()方法回滚。

   

### 连接池

JDBC的数据库连接池使用javax.sql.DataSource来表示，DataSource是一个接口，由第三方实现。

**基本概念：**

1.  预先在缓冲池中放入一定数量的连接，当需要建立数据库连接时，只需从“缓冲池”中取出一个，使用完毕之后再放回去。
2. 数据库连接池负责分配，管理和释放数据的连接，它允许应用程序重复使用一个现有的数据库连接，而不是重新建立一个。
3. 当应用程序向连接池请求的连接数超过最大的连接数量时，这些请求将会被加入到等待队列中。

#### C3P0

连接方式1：

```java
public class c3p0_ {
    @Test
    public void test_c3p0() throws Exception {
        //1.创建一个数据源对象
        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();
        //2.通过配置文件获取相关的信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");

        //3.给数据源comboPooledDataSource设置相关的参数。
        comboPooledDataSource.setDriverClass(driver);
        comboPooledDataSource.setJdbcUrl(url);
        comboPooledDataSource.setUser(user);
        comboPooledDataSource.setPassword(password);

        //4.初始化连接池的连接数
        comboPooledDataSource.setInitialPoolSize(10);
        comboPooledDataSource.setMaxPoolSize(50);
        Connection connection = comboPooledDataSource.getConnection();
        System.out.println("连接成功");
        connection.close();

    }
}
```

连接方式2：（使用配置文件模板）





#### Druid(德鲁伊)

切换德鲁伊连接池

```xml
 <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.2.8</version>
 </dependency>
```



##### 连接

```properties
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/db?serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true
username=root
password=root
initialSize=10
minIdle=5
maxActive=20
maxWait=5000
```

```java
public class Druid_ {
    @Test
    public void test_Druid() throws Exception {
        //1.加入Druid的jar包
        //2.加入配置文件
        //3.创建Properties对象
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\Druid.properties"));

        //4.创建一个指定参数的数据库连接池
        DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
        Connection connection = dataSource.getConnection();
        System.out.println("ok");
        connection.close();


    }
}
```

##### Druid工具类

```java
public class UtilsByDruid {
    private static DataSource ds;

    //在静态代码块完成对DataSource的初始化
    static {
        Properties properties = new Properties();
        try {
            properties.load(new FileInputStream("src\\Druid.properties"));
            ds = DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    //编写getConnection方法
    public static Connection getConnection() throws SQLException {
        return ds.getConnection();
    }
    //关闭连接，放回连接池
    public static void close(ResultSet resultSet, Statement statement,Connection connection){
        try {
            if(resultSet!=null)resultSet.close();
            if(statement!=null)statement.close();
            if(connection!=null)connection.close();
        }catch (SQLException e){
            throw new RuntimeException(e);
        }
    }


}
```



###  Apache-DBUtils

**DBUtils类：**

1. QueryRunner类：封装了SQL的执行，是线程安全的，可以实现，增删改查批处理。
2. 使用QueryRunner类实现查询。
3. ResultSetHandler接口：用于处理ResultSet，将数据转换为另一种形式。

```java
public class DBUtils_Test {
    //使用DBUtils和Druid方式实现对actor的crud
    @Test
    public void testQueryMany() throws Exception {
        //1.得到连接
        Connection connection = UtilsByDruid.getConnection();
        //2.使用DBUtils类和接口
        QueryRunner queryRunner = new QueryRunner();
        //3.queryRunner执行操作
        String sql = "select * from actor";
        List<Actor> list =
                queryRunner.query(connection, sql, new BeanListHandler<>(Actor.class));

        for (Actor actor :list) {
            System.out.println(actor);
        }

        //释放资源
        UtilsByDruid.close(null,null,connection);


    }
}
```

### BasicDAO

1. DAO（Data Access Object）
2. 将各个DAO共同操作放到BasicDAO中，简化代码，提高维护性。
3. BasicDAO是专门和数据库交互的，完成对数据库的crud操作。
4. 在BasicDao的基础上，实现一张表 对应一个Dao，比如：Customer表-Customer.java类（java bean） -CustomerDao.java

























## **IDEA快捷键**

| **快捷键**                |                                       |
| ------------------------- | ------------------------------------- |
| **迭代器while循环**       | **itit**                              |
| **删除当前行**            | **自己配置ctrl+d**                    |
| **复制当前行**            | **自己配置ctrl+alt+下方向键**         |
| **环绕代码（try-catch）** | **选中代码块+ctrl+alt+t**             |
| **补全代码**              | **alt+/**                             |
| **添加注释**              | **ctrl+/**                            |
| **代码格式化**            | **ctrl+alt+l**                        |
| **快速运行程序**          | **自己配置alt+r**                     |
| **生成构造器等**          | **alt+insert**                        |
| **查看类的继承关系**      | **ctrl+h**                            |
| **定位方法（查看源码）**  | **ctrl+b**                            |
| **自动分配变量名**        | **.var**                              |
| **实现借口的方法**        | **alt+enter/ctrl+i**                  |
| **所有快捷模板**          | **ctrl+j**                            |
| **增强for**               | **大写I** 或者 **集合数组后面加.for** |
| 选中特定符号              | 选中该符号 clt+j 连续按               |
| alt+鼠标移动键            |                                       |



| **模板快捷键（位置 file ->setting ->editor->Live templates）** |      |
| ------------------------------------------------------------ | ---- |
|                                                              |      |
|                                                              |      |
|                                                              |      |

| **断点调试快捷键** |                          |
| ------------------ | ------------------------ |
| **F7**             | **跳入方法内**           |
| **F8**             | **跳过（逐行执行代码）** |
| **shift+F8**       | **跳出（跳出方法）**     |
| **F9**             | **执行到下一个断点**     |



## **疑问**

1. **为什么一个类中只有一个公有类。**



## **面试题**

### **==和equals的区别**

- **==方法**

1. **==：既可以判断基本类型，又可以判断引用类型。**
2. **==：如果判断的是基本类型，判断的是值是否相等。**
3. **==；如果判断的是引用类型，判断的是地址是否相等。**

- **equals方法**

1. **equals方法：是Object中的方法，只能判断引用类型。**
2. **默认判断的是地址是否相等，子类中往往重写该方法，用于判断内容是否相等。（Integer，String 对该方法重写。）**

### **类什么时候被加载**

1. **创建对象实例时（new）**
2. **创建子类对象实例时，父类也会被加载。**
3. **使用类的静态成员时。**



### **在创建一个对象时，在一个类的调用顺序**

1. **调用静态代码块和静态属性初始化。（静态代码块和静态属性初始化调用优先级一样，有多个时，按照定义的顺序调用）**
2. **调用普通代码块和普通属性初始化。（普通代码块和普通属性初始化调用优先级一样，有多个时，按照定义的顺序调用）**
3. **最后调用构造器。**

### **创建一个子类对象时（继承关系），调用顺序**

**创建一个子类对象时（继承关系），他们的静态代码块，静态属性初始化，普通代码块，普通属性初始化，构造方法的调用顺序是什么。**

---

**调用顺序如下：**

1. **父类的静态代码块，静态属性初始化。**
2. **子类的静态代码块，静态属性初始化。**
3. **父类的普通代码块，普通属性初始化。**
4. **父类的构造器。**
5. **子类的普通代码块，普通属性初始化。**
6. **子类的构造器。**

### **实现接口和继承类的区别**

**继承 把父类的属性和方法都自动继承过来了。**

**实现接口 可以扩展功能。（实现接口是java对单继承机制的一种补充）**

**接口比继承更加灵活，继承是满足 is a 的关系，而接口只需要满足like a的关系。**

### String、StringBuffer 和StringBuilder的比较

1. StringBuilder和StringBuffer非常类似，均代表可变字符序列，而且方法也一样。
2. String为不可变字符序列，效率低，但是复用率高。
3. StringBuffer是可变字符序列，效率较高，线程安全。
4. StringBuilder是可变字符序列，效率最高，线程不安全。
5. 如果对String进行大量修改时，不使用String。

### Vector和ArrayList的比较

|           | 底层结构 | 版本   | 线程安全效率   | 扩容倍速                                                     |
| --------- | -------- | ------ | -------------- | ------------------------------------------------------------ |
| ArrayList | 可变数组 | jdk1.2 | 不安全，效率高 | 如果有参构造扩大1.5倍，如果无参，第一次是10，从第二次开始从1.5扩大。 |
| Vector    | 可变数组 | jdk1.0 | 安全，效率不高 | 如果无参，默认10，满后就按2倍扩容 ，如果指定大小，则每次直接按2倍扩。 |

# 正则表达式

## 转义符

转义号：\\\

\\\符号:检索某些特殊字符，需要使用转义字符。（java中的\\\表示其他语言的\）

## 字符匹配符

| 符号 | 作用                                              | 示例           | 说明                                                   |
| ---- | ------------------------------------------------- | -------------- | ------------------------------------------------------ |
| [ ]  | 可接收的字符列表                                  | [efgh]         | e、f、g、h中的任意一个字符                             |
| [^]  | 不可接收的字符列表                                | [^abc]         | 除a、b、c之外的任意一个字符，包括数字和特殊字符        |
| -    | 连字符                                            | A-Z            | 任意单个大写字母                                       |
| .    | 匹配除\n以外的任何字符                            | a..b           | 以a为开头，b结尾，中间包括2个任意字符的长度为4的字符串 |
| \\\d | 匹配单个数字字符，相当于[0-9]                     | \\\d{3}(\\\d)? | 包含3个或者4个数字的字符串                             |
| \\\D | 匹配单个非数字字符，相当于[ ^0-9]                 | \\\D(\\\d)*    | 以单个非数字字符开头，后接任意个数字字符的字符串       |
| \\\w | 匹配单个数字，大小写字母字符相当于[0-9a-zA-Z]     | \\\d{3}\\\w{4} |                                                        |
| \\\W | 匹配单个非数字，大小写字母字符相当于[ ^0-9a-zA-Z] |                |                                                        |

## 选择匹配符

| 符号 | 作用                         | 示例 | 说明   |
| ---- | ---------------------------- | ---- | ------ |
| \|   | 匹配 \| 之前或者之后的表达式 | a\|b | a或者b |

## 限定符

| 符号  | 含义                                 |
| :---- | ------------------------------------ |
| *     | 指定字符出现0次或者n次               |
| +     | 指定字符出现1次或者n次（至少为一次） |
| ？    | 指定字符出现0次或者1次（至多为一次） |
| {n}   | 只能输入n个字符                      |
| {n，} | 出现至少n次                          |
| {n,m} | 出现n-m次                            |

## 定位符

| 符号 | 含义                   |
| ---- | ---------------------- |
| ^    | 指定起始字符           |
| $    | 指定结束字符           |
| \\\b | 匹配目标字符串的边界   |
| \\\B | 匹配目标字符串的非边界 |

## 分组

| 常用分组构造形式  | 说明                             |
| ----------------- | -------------------------------- |
| (pattern)         | 非命名捕获。捕获匹配的子字符串。 |
| (?\<name>pattern) | 命名捕获。                       |
| (?:pattern)       |                                  |
| (?=pattern)       |                                  |
| (?!=pattern)      |                                  |

## 反向引用

圆括号的内容被捕获后，可以在这个括号后被使用。内部反向引用使用**\\\\**，外部使用$分组号。

# JAVA8

## Lambdab表达式

Lambda表达式的本质：作为接口的实例。

```java
public class lambda_ {
    @Test
    public void lambdaTest(){
        Runnable runnable = new Runnable() {
            @Override
            public void run() {
                System.out.println("hello world");
            }
        };
        runnable.run();
    }
    @Test
    public void lambdaTest1(){
        Runnable runnable = () ->{
            System.out.println("hello world");
        };
        runnable.run();

    }
}
```

---

### lambda表达式格式

1. 举例：（o1，o2） -> Integer.compare	(o1,o2);

2. 格式：->:lambda操作符

   ​			->左边：lambda形参列表（其实就是接口中抽象方法的形参列表）

   ​			->右边：lambda体（其实就是重写的抽象方法的方法体）

   

### lambda表达式的使用

```java
public class lambda_ {
    //1.无参，无返回值
    @Test
    public void lambdaTest1(){
        Runnable runnable = () ->{
                System.out.println("hello world");
        };
        runnable.run();
    }
    //2.有一个参数，但是无返回值
    @Test
    public void lambdaTest2(){
        Consumer<String> consumer = (String s) -> {
            System.out.println(s);
        };
        consumer.accept("hello");
    }
    //3.数据类型可以省略，可以类型推断
    @Test
    public void lambdaTest3(){
        Consumer<String> consumer = (s) -> {
            System.out.println(s);
        };
        consumer.accept("hello");
    }
    //4.只需要一个参数时，参数的小括号可以省略
    @Test
    public void lambdaTest4(){
        Consumer<String> consumer = s -> {
            System.out.println(s);
        };
        consumer.accept("hello");
    }
    //5.有两个或者两个以上的参数，多条执行语句，并且可以有返回值。
    @Test
    public void lambdaTest5(){
    Comparator<Integer> comparator1 = new Comparator<Integer>() {
        @Override
        public int compare(Integer o1, Integer o2) {
            System.out.println(o1);
            System.out.println(o2);
            return o1.compareTo(o2);
        }
    };
    comparator1.compare(12,13);
    //与匿名内部类达到相同的目的
    Comparator<Integer> comparator2 = (o1, o2) -> {
        System.out.println(o1);
        System.out.println(o2);
        return o1.compareTo(o2);
    };
    comparator1.compare(12,13);
    }
    //6.lambda体只有一条语句时，return 与大括号若有，都可以省略
    @Test
    public void lambdaTest6(){
        Comparator<Integer> comparator = (o1, o2) -> o1.compareTo(o2);
        comparator.compare(12,13);
    }

}
```

## StreamAPI

Stream主要是侧重计算

1. Stream 自己不会存储元素。
2. Stream不会改变源对象，相反，他们会返回一个持有结果的新Stream
3. Stream操作是延迟执行的。这意味着他们会等到需要结果的时候才执行。
