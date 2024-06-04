# Web前端基础

## Web标准

- HTML：负责网页的结构
- CSS：负责网页的表现
- JS：负责网页的行为

## HTML、CSS

#### 图像标签\<img>

- src:指定图像的URL
- width：图像的宽度
- height：图像的高度

#### 标题标签\<h1> - \<h6>

#### 超链接

<a href="" target="_self"></a>

href指定资源的url

target：表示在何处打开资源

- _blank 在空白页面打开
- _self 默认值，在当前页面打开

#### 视频

```html
 <video src=""></video>
```



### CSS引入方式

- 行内样式：写在标签的style属性中（不推荐）
- 内嵌样式：写在style标签中（通常写在head标签内）
- 外联样式：写在一个单独的.css文件中（用link引入）

## JS

JavaScript 中用var关键字来声明变量（弱类型语言）

var定义的变量 作用域为全局变量。

let定义的变量只在代码块内有效，且不允许重复声明。

js中函数通过function关键字进行定义

### JS对象

#### JS自定义对象

**定义格式：**

```javascript
var 对象名 = {
    属性名1:属性值1,
    属性名2:属性值2,
    函数名称:function(形参列表){}
};

var user = {
    name:"tom",
    age:20,
    eat:function(){
        alert("eat");
    }
};
```

**调用格式：**

对象名.属性名;

对象名.函数名();

#### JSON

JSON是通过JavaScript对象标记法书写的==文本==

**key用双引号标记。**

```javascript
{
    "name":"tom",
    "age":20
};
```

**JSON字符串转为JS对象**

var jsObject  = JSON.parse(useStr);

JS对象转为JSON字符串

var jsonStr = JSON.stringify(jsObject);

#### BOM

Browser Object Model:浏览器对象模型。

组成：

1. window：浏览器窗口对象。
2. Navigator：浏览器对象。
3. Screen：屏幕对象
4. History：历史记录对象
5. Location：地址栏对象

##### Window对象

浏览器窗口对象。

属性：

1. history
2. location
3. navigator

方法：

1. alter()
2. confirm():弹出对话框
3. setinterval()
4. setTimeout()

#### DOM

Document Object Model 文档对象模型

将标记语言的各个组成部分分装成对应的对象：

- Document：整个文档对象
- Element：元素对象
- Attribute：属性对象
- Text：文本对象
- Comment：注释对象

#### JS事件监听

事件：HTML事件时发生在HTML元素上的事情。例如：

- 按钮被点击
- 鼠标移动到元素上
- 按下键盘按键

事件监听：JS可以在事件被侦测到时执行代码。

## Vue

Vue是一套前端框架，简化书写。

基于MVVM（Model-View-ViewModel）思想，实现数据的**双向绑定**。

### Vue常用指令

指令：HTML标签上带有v-前缀的特殊属性。

常用指令：

| 指令      | 作用                                                |
| --------- | --------------------------------------------------- |
| v-bind    | 为HTML标签绑定属性值，如设置href，css样式等         |
| v-model   | 在表单元素上创建双向数据绑定                        |
| v-on      | 为HTML标签绑定事件                                  |
| v-if      |                                                     |
| v-else-if |                                                     |
| v-else    |                                                     |
| v-show    | 根据条件展示某元素，区别在于切换的是display属性的值 |
| b-for     | 列表渲染                                            |

### Vue的生命周期

## Ajax-Axios

对原生ajax进行了封装

步骤：

1. 引入Axios的js文件。

   ```html
   <script src = "js/axios-0.18.0.js"></script>
   ```

2. 使用Axios发送请求，并获取响应结果。

   ```javascript
     axios({
       method:"get",
       url:"www.xxx.com"
     }).then((result)=>{
       console.log(result.data);
     });
     
       axios({
       method:"post",
       url:"www.xxx.com"
       data:"id=1"
     }).then((result)=>{
       console.log(result.data);
     });



# 前端工程化

## 环境准备

安装node.js

## Vue项目

图形化界面

命令行输入：vue ui

## Vue项目开发

Vue的组件以.vue结尾，每个组件由三部分组成\<template>、\<script>、\<style>

- \<template>模板部分，由它生成HTML代码
- \<script>控制模板的数据来源和行为
- \<style>css的样式部分

## Element UI

组件库

---

### 快速入门：

1. 安装ElementUI组件库（在当前工程的目录下），在命令行执行指令：

   ```powershell
   npm install element-ui@2.15.3
   ```

2. 引入ElementUI组件库(main.js)

   ```js
   import Element from 'element-ui';
   import 'element-ui/lib/theme-chalk/index.css';
   Vue.use(ElementUI);
   ```

3. 访问官网，复制组件代码，调整。

# Web 入门

## HTTP协议

### HTTP请求协议

格式：

- 请求行（请求方式，资源路径，协议）
- 请求头，格式key：value
- 请求体 POST请求，存放请求参数。

请求方式-GET：请求参数在请求行中，没有请求体，如：/brand/findall？name=name。get请求大小是有限制的。

请求方式-POST：请求参数在请求体中，POST请求大小是没有限制的。

### HTTP响应格式

格式：

- 响应行（协议，状态码，描述）
- 响应头 格式key：value
- 响应体 存放响应数据

状态码：

| 状态码 | 作用                                                         |
| ------ | ------------------------------------------------------------ |
| 1xx    | 响应中-临时状态码，表示请求已经接收告诉客户端应该继续请求或者如果它完成则忽略它 |
| 2xx    | 成功                                                         |
| 3xx    | 重定向-重定向到其他地方；让客户端再发起一次请求以完成整个处理。 |
| 4xx    | 客户端错误                                                   |
| 5xx    | 服务端错误                                                   |

## Tomcat





## 请求响应

- 请求（HttpServlerRequest）：获取请求数据
- 响应（HttpServletResponse）：设置响应数据

---

### 请求

接口测试工具postman

#### 简单参数和简单实体参数



#### 数组集合参数

数组：请求参数名与形参中数组变量名相同，可以直接使用数组来封装。

```java
@RequestMapping("\arrayParam")
public String arrayParam(String []hobby){
    System.out.println(Arrays.toString(hobby));
    return "OK";
}
```

集合：请求参数名与形参中数组变量名相同，通过@RequestParam来绑定参数关系。

```java
@RequestMapping("\listParam")
public String arrayParam( @RequestParam List<String> hobby){
    System.out.println(hobby);
    return "OK";
}
```

#### 日期参数

```java
@RequestMapping("\dateParam")
public String dateParam( @DateTimeFormat(pattern="yyyy-MMMM-dd HH:mm:ss")LocalDateTime updateTime){
    System.out.println(updateTime);
    return "OK";
}
```



#### JSON格式

JSON参数：JSON数据的key与形参对象的属性名相同，定义POJO类型形参即可接收参数，需要使用==@RequestBody==标识。

```java
@RequestMapping("\jsonParam")
public String jsonParam(@RequestBody User user){
    System.out.println(user);
    return "OK";
}
```

#### 路径参数

localhost:8080/path/1

其中的1既是路径，也是传递给服务端的参数。

---

```java
@RequestMapping("\path\{id}")
public String pathParam(@PathVariable Integer id){
	System.out.println(id);
    return "OK";
}
```

### 响应

@ResponseBody注解，位置在Controller方法上或者类上。作用是将方法返回值直接响应，如果返回值类型是实体对象，将会转换成JSON格式响应

@RestController = @Controller + @ResponseBody

#### 统一响应结果

```java
public class Result{
	//响应码
    private Integer code;
    //提示信息
    private String msg;
    //f
    private Object data;
  	
    //...
}
```



## 三层架构

三层架构：

- Controller：控制层，接收前端发送的请求，对请求进行处理，并响应数据。
- service：业务逻辑层，处理具体的业务逻辑
- dao：数据访问层（Data Access Object）负责数据的访问操作，crud

## 分层解耦

### 控制反转（Inversion Of Control）

简称为 **IOC**。

对象的创建控制权由程序自身转移到外部（容器），这种思想成为控制反转。

---

在DAO和Service类上 加上注解@Component:将当前类交给IOC容器管理，成为IOC容器中的bean



### 依赖注入（Dependency Injection）

简称为**DI**

容器为应用程序提供运行时，所依赖的资源，称为依赖注入。

---

@Autowired ：运行时IOC容器会提供该类型的bean对象，并赋值为该对象。

---

@Autowired 注解默认是按照**类型**进行的，如果存在多个相同类型的bean，将会报错。解决方法：

- @Primary 
- @Qualifier， 指定要注入哪个bean
- @Resource ，按照**名称**注入，替代@Autowire注解

### Bean 对象

IOC容器中创建、管理的对象，称为**bean**。

**bean的声明：**

| 注解        | 说明                 | 位置                                          |
| ----------- | -------------------- | --------------------------------------------- |
| @Component  | 声明bean的基础注解   |                                               |
| @Controller | @Component的衍生注解 | 标注在控制器类上                              |
| @Service    | @Component的衍生注解 | 标注在业务类上                                |
| @Repository | @Component的衍生注解 | 标注在数据访问类上（与mybatis整合，使用较少） |

**Bean组件扫描**：

- bean的四大注解，想要生效，还需要被组件扫描注解@ComponentScan扫描
- @ComponentScan注解虽然没有显示配置，但是实际上已经包含在了启动类声明注解@SpringBootApplication中，**默认扫描范围时启动类所在的包及其子包。**





# maven

mavne是apache旗下用于管理和构建java项目的工具。

---

## maven的作用

1. **依赖管理**

   方便快捷的管理项目依赖的资源（jar包），它基于项目对象模型（ project object model ，POM）的概念，避免版本冲突问题。

2. **统一项目结构**

   提供标准的，统一的项目结构。

   maven-project

   ​	src

   ​		main 

   ​			java

   ​			resources

   ​		test

   ​			java

   ​			resources

   ​	pom.xml

3. **标准的项目构建流程**

   标准跨平台的自动化项目构建方式。
   
   

# Spring



## SpringBoot

### 快速入门

步骤：

1. 创建springboot工程，并勾选web开发相关依赖。
2. 定义HelloController类，添加方法hello，并添加注解。
3. 运行测试。



# MyBatis

MyBatis是一款优秀的**持久层**框架，用于简化JDBC的开发

## 使用MyBatis查询所有用户数据

1. 准备工作（创建springboot工程，数据表user，实体类user）

2. 引入MyBatis的相关依赖，配置MyBatis

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-parent</artifactId>
           <version>2.7.4</version>
           <relativePath/> <!-- lookup parent from repository -->
       </parent>
       <groupId>com.springboot</groupId>
       <artifactId>mybatis</artifactId>
       <version>0.0.1-SNAPSHOT</version>
       <name>mybatis</name>
       <description>Demo project for Spring Boot</description>
       <properties>
           <java.version>8</java.version>
       </properties>
       <dependencies>
           <dependency>
               <groupId>org.mybatis.spring.boot</groupId>
               <artifactId>mybatis-spring-boot-starter</artifactId>
               <version>2.2.2</version>
           </dependency>
   
           <dependency>
               <groupId>com.mysql</groupId>
               <artifactId>mysql-connector-j</artifactId>
               <version>8.0.32</version>
               <scope>runtime</scope>
           </dependency>
   
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-test</artifactId>
               <scope>test</scope>
           </dependency>
       </dependencies>
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.springframework.boot</groupId>
                   <artifactId>spring-boot-maven-plugin</artifactId>
               </plugin>
           </plugins>
       </build>
   
   </project>
   
   ```

   

3. 编写SQL语句

   ```java
   @Mapper
   public interface actorMapper {
       @Select("select * from actor")
       public List<actor> list();
   }
   ```

   

## lombok

Lombok 是一个使用的java类库，能够通过通过注解的形式自动生成构造器，getter setter equals hashcode toString等方法，并可以自动化生成日志变量，简化java开发，提高效率。

| 注解               | 作用                                            |
| ------------------ | ----------------------------------------------- |
| @Getter\Setter     | 为所有属性提供get\set方法                       |
| @ToString          | 自动为类生成易于阅读的toString方法              |
| @EqualsAndHashCode | 重写equals和hashcod方法                         |
| @Data              | （@Getter\Setter+@ToString+@EqualsAndHashCode） |
| @NoArgsConstructor | 无参构造器方法                                  |
| @AllArgsConstrutor |                                                 |

原代码

```java
public class actor {
    private Integer id;
    private String NAME;
    private String sex;
    private String phone;

    public actor() {
    }

    public actor(Integer id, String NAME, String sex, String phone) {
        this.id = id;
        this.NAME = NAME;
        this.sex = sex;
        this.phone = phone;
    }

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getNAME() {
        return NAME;
    }

    public void setNAME(String NAME) {
        this.NAME = NAME;
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    @Override
    public String toString() {
        return "actor{" +
                "id=" + id +
                ", NAME='" + NAME + '\'' +
                ", sex='" + sex + '\'' +
                ", phone='" + phone + '\'' +
                '}';
    }
}
```



使用lombok后

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class actor {
    private Integer id;
    private String NAME;
    private String sex;
    private String phone;

}
```

## 基础操作

### 删除操作

```java
//根据id删除数据
@Delete("delete from emp where id = #{id}")
//#{}为占位符
public int delete(Integer id); //返回值为删除的行数
```

### 新增操作

```java
//多个参数使用实体类来封装 
@Insert("insert into emp (username,name,gender,image,job,entrydate,dept_id,create_time,update_time)" +
            "values (#{username},#{name},#{gender},#{image},#{job},#{entrydate},#{deptId},#{createTime},#{updateTime})")
    public void insert(Emp emp);
```

### 更新操作

```java
   @Update("update emp set username =#{username},name = #{name},gender =#{gender},image =#{image},job =#{job},entrydate =#{entrydate},dept_id=#{deptId},update_time =#{updateTime} " +
            "where id = #{id}")
    public void update(Emp emp);
```

### 查询操作

```java
@Select("select * from emp where id = #{id}")
public Emp getById(Integer id);
```

#### 条件查询

```java
@Select("select * from emp where name like '%${name}%' and gender = #{gender} order by update_time desc ")
public List<Emp> list(String name,short gender);
```

## XML映射文件

规范：

1. XML映射文件的名称与Mapper接口一致，并且将XML映射文件和Mapper接口放置在相同包下。
2. XML映射文件的namespace属性为Mapper接口全限定名一致。
3. XML映射文件中sql语句的id与Mapper接口中的方法名一致，并且保持返回类型一致。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.springboot.mybatis.mapper.EmpMapper">
        <select id="list" resultType="Emp">
            select * from emp where name like '%${name}%' and
            gender = #{gender} order by update_time desc
        </select>
</mapper>
```

## 动态SQL

### if标签

用于判断条件是否成立。使用test属性进行条件判断，如果条件为true，则拼接SQL。<where><set>

```xml
<if test = "name!=null">
name like %#{name}%
</if>
```

### foreach标签

collection ：遍历的集合

item：遍历出来的元素

separator：分隔符

open：遍历开始前拼接的SQL片段

close：遍历结束后拼接的SQL片段

```xml
<delete id="delete">
        delete from emp where in
	<foreach collection="ids" item="id" separator="," 			open="(" close=")">
       		 #{id}
	</foreach>
</delete>
```

### sql和include标签

sql标签对sql语句进行抽取

include

# 配置文件

## yml

基础语法：

1. 大小写敏感
2. 数值前必须有空格，作为分隔符
3. 使用缩进表示层级关系，缩进时，不允许使用Tab，只能用空格
4. \# 表示注解

```yaml
server:
  port: 9000
```

数据格式：

- 对象/Map集合

  ```yaml
  user:
    name: tom
    age: 19
    password: 12345
  ```

  

- 数组/List/Set集合

  ```yaml
  hobby:
    -java
    -game
    -sport
  ```

  

# 登录校验

## 会话技术

会话：用户打开浏览器，访问web服务器资源，会话建立，知道有一方断开连接，会话结束。在一次会话中可以包含多次请求和响应。

会话跟踪：一种维护浏览器状态的方法，服务器需要识别多次请求是否来自同一浏览器，以便在同一次会话的多次请求间共享数据。

会话跟踪方案：

- 客户端：Cookie
- 服务端：Session
- 令牌技术

### Cookie

HTTP协议中支持的技术

### Session



### JWT令牌

JSON Web Token

---

组成：

- 第一部分：Header（头），记录令牌类型、签名算法等。
- 第二部分：Payload（有效负荷），携带一些自带信息，默认信息。
- 第三部分：Signature（签名），防止token被篡改，确保安全性。



令牌生成

```java
@Test
public void testGenJwt(){
    Map<String,Object> claims = new HashMap<>();
    claims.put("id",1);
    claims.put("name","tom");
    String jwt = Jwts.builder()
            .signWith(SignatureAlgorithm.HS256, "jwtlllll")
            .setClaims(claims)
            .setExpiration(new Date(System.currentTimeMillis() + 3600 * 1000))
            .compact();
    System.out.println(jwt);
}
```

令牌校验

```java
@Test
public void testParseJwt(){
    Claims claims = Jwts.parser().setSigningKey("jwtlllll")
                .parseClaimsJws("eyJhbGciOiJIUzI1NiJ9.eyJuYW1lIjoidG9tIiwiaWQiOjEsImV4cCI6MTcxNzE1NjMwMX0.tCPGzM0XVjRe63FxuGP_El3HY8ZVbDv3gdOQERcsuJg")
                .getBody();
    System.out.println(claims);
}
```

### 过滤器Filter

#### 执行流程

先执行放行前逻辑->放行（chain.doFilter()）->放行后的逻辑

#### 过滤器链

一个web应用中，可以设置多个过滤器，这多个过滤器就形成了一个过滤器链。



### 拦截器interceptor

是一种动态拦截方式调用的机制，类似过滤器。Spring框架中提供的，用来动态拦截控制器方法的执行。



# 事务管理

操作：

1. 开启事务：start transaction/begin；
2. 提交事务：commit；
3. 回滚事务：rollback：



## rollbackFor

默认情况下，只有出现RuntimeException才回滚异常，rollbackFor属性用于控制出现何种何种异常类型，回滚事务。

## propagation

事务传播行为：指的是当一个事务被另一个事务方法调用时，这个事务方法应该如何进行事务控制。

# AOP

## AOP概述

AOP：Aspect Oriented Programming 面向切面编程，就是面向特定方法编程。

## AOP核心概念

连接点：JoinPoint，可以被AOP控制的方法。

通知：Advice，共性的功能

切入点：PointCut，匹配连接点的条件，通知仅会在切入点方法执行时被应用。

切面：Aspect，描述通知和切入点的对应关系（通知+切入点）。

目标对象：Target，通知所应用的对象。 

## 通知类型

@Around

@Before

@After

@AfterReturning

@AfterThrowing

## 切入点表达式

决定项目中哪些方法需要加入通知

- execution：根据方法的签名来匹配
- @annotation:根据注解匹配

### execution

execution(访问修饰符？ 返回值  包名.类名.?方法名（方法参数）throw 异常？)

> ？表示可以省略的部分

### @annotation





## 连接点

Spring种用JoinPoint抽象了连接点，用它可以获得方法执行时的相关信息，如目标类名，方法名，方法参数等。

# SpringBoot原理

## 起步依赖



## 自动配置的原理

