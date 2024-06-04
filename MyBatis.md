# MyBatis概述

>【MyBatis视频零基础入门到进阶，MyBatis全套视频教程源码级深入详解】 https://www.bilibili.com/video/BV1JP4y1Z73S/?p=2&share_source=copy_web&vd_source=a65e4b88935ee947c42eed89fdb6ef02

## ORM思想

> Object Relational Mapping（对象关系映射）

- O（Object）:JVM中的java对象
- R（Relational）：关系型数据库
- M（Mapping）：映射

MyBatis 是一个**ORM**框架。

![](D:/Picture/MyBatis-ORM.png)

User这样的类有多种称呼：

1. **pojo**
2. **bean**
3. **domain**

# MyBaits入门程序

入门程序的开发步骤：

1. 打包方式jar

2. 引入依赖

   - mybatis依赖
   - mysql驱动

3. 从XML中构建SqlSessionFactory

   mybatis中有两种主要的配置文件

   - mybatis-config.xml专门用来编写配置SQL语句的配置文件
   - XxxMapper.xml 这个文件专门用来编写SQL语句的配置文件（一张表对应一个）

4. 编写XxxMapper.xml （编写sql语句）

5. 在mybatis-config.xml文件中指定XxxMapper.xml的位置。

6. 编写MyBatis程序。

   > 在MyBatis中**SqlSession**负责来执行SQL语句。是Java程序与数据库的一次会话。
   >
   > 想获取SqlSession对象，首先要获取**SqlSessionFactory**对象生产SqlSession对象。
   >
   > 想获取SqlSessionFactory对象，首先要获取**SqlSessionFactoyBuilder**对象，然后的通过SqlSessionFactoryBuilder的build方法，来获取一个SqlSessionFactory对象。

   ```java
   public class MyBatisIntroductionTest {
       public static void main(String[] args) throws IOException {
           //1.获取SqlSessionFactoryBuilder对象
           SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
           //2.获取SqlSessionFactory对象
           InputStream inputStream = Resources.getResourceAsStream("mybatis-config.xml");
           SqlSessionFactory sqlSessionFactory = sqlSessionFactoryBuilder.build(inputStream);
   
           //3.获取SqlSession对象(不支持自动提交)
           SqlSession sqlSession = sqlSessionFactory.openSession();
           //4.执行SQL语句
           int count = sqlSession.insert("insertCar");
   
           System.out.println(count);
           sqlSession.commit();
   
       }
   }
   ```

   

## 一个完整的MyBatis程序

```java
public class MybatisCompleteTest {
    public static void main(String[] args) {
        SqlSession sqlSession=null;
        try {
            SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
            SqlSessionFactory sessionFactory = sqlSessionFactoryBuilder.build(Resources.getResourceAsStream("mybatis-config.xml"));
            //开启会话
           sqlSession = sessionFactory.openSession();
            //执行sql语句
            int count = sqlSession.insert("insertCar");
            System.out.println(count);
            sqlSession.commit();
        } catch (Exception e) {
            if (sqlSession != null) {
                //出现异常回滚事务人
                sqlSession.rollback();
            }
            e.printStackTrace();
        }finally {
            //关闭会话，释放资源。
            if (sqlSession != null) {
                sqlSession.close();
            }
        }
    }
}
```

## Mybatis集成日志框架logback

mybatis-config.xml

```xml
<settings>
    <setting name="logImpl" value="SLF4J"/>
</settings>
```

logback.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<configuration  debug="false">

    <!--输出到控制台-->
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <!---->
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} 【%thread】 %-5level %logger{50} -%msg%n</pattern>
        </encoder>
    </appender>    <!--mybatis log configure-->
    <logger name="com.apache.ibatis" level="TRACE"></logger>
    <logger name="java.sql.Connection" level="DEBUG"></logger>
    <logger name="java.sql.Statement" level="DEBUG"></logger>
    <logger name="java.sql.PreparedStatement" level="DEBUG"></logger>

    <!-- 日志输出级别 logback日志级别包括5个,TRACE < DEBUG < INFO < WARN < ERROR-->
    <root level="DEBUG">
        <appender-ref ref="STDOUT"/>
        <appender-ref ref="FILE"/>
    </root>

</configuration>
```

## MyBatis工具类

```java
public class SqlSessionUtil {
    //工具类的构造方法一般是私有的
    //工具类中的所有方法都是静态的
    //为了防止new对象，将构造方法私有化
    private  static SqlSessionFactory sqlSessionFactory;
    private SqlSessionUtil(){}
    //SqlSessionUtil 在类加载的时候解析mybatis-config.xml文件，创建SqlSessionFactory对象
    static {
        try {
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(Resources.getResourceAsStream("mybatis-config.xml"));
        } catch (IOException e) {
            e.printStackTrace();
        }

    }

    public static SqlSession openSession(){
//        SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
//        //SqlSessionFactory对象：一个SqlSessionFactory对应一个environment，一个environment对应一个数据库。
//        SqlSessionFactory sqlSessionFactory = sqlSessionFactoryBuilder.build(Resources.getResourceAsStream("mybatis-config.xml"));
        return  sqlSessionFactory.openSession();
    }
}
```

  

# 使用MyBatis完成CRUD

>C:Create
>
>R:Retrieve
>
>U:Update
>
>D:Delete

---

 Java程序中使用<font color=red>POJO类</font>给Sql语句中的<font color=red>占位符</font>传值。

<font color=red>严格意义上来说：如果使用Pojo对象来传递值的话，#{}中写的是pojo类中get方法的方法名去掉get,然后将剩余的单词首字母小写,然后放进去</font>

>getUsername() ==>#{username}
>
>getEmail() ==> #{email}

---

## Insert

1. **POJO类：Car**

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Car {
    private Long id;
    private String carNum;
    private String brand;
    private Double guidePrice;
    private String produceTime;
    private String carType;
}
```

2. **CarMapper.xml**

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="namespace">
<insert id="insertCar">
    insert into t_car(id,car_num,brand,guide_price,produce_time,car_type)
    values(null,#{carNum},#{brand},#{guidePrice},#{produceTime},#{carType})
<!-- #{}中写Pojo类中的属性名，底层调用Car类中的get方法-->
</insert>
</mapper>
```

<!-- #{}中写Pojo类中的属性名，底层调用Car类中的get方法-->

3. **测试类**

```java
@Test
public void testCarMapperByPojo(){
    SqlSession sqlSession = SqlSessionUtil.openSession();
    Car car = new Car(null,"111","byd",30.2,"2020-11-11","新能源");
    //第一个参数：sqlID 从CarMapper.xml中复制。
    //第二个参数：封装数据的对象（ORM思想）
    sqlSession.insert("insertCar",car);
    sqlSession.commit();
    sqlSession.close();
}
```



## Delete

1. CarMapper.xml

```xml
<delete id="deleteByID">
    delete from t_car where id = #{id}
</delete>
```

2. 测试类

```java
@Test
public void testDeleteById(){
    SqlSession sqlSession = SqlSessionUtil.openSession();
    sqlSession.delete("deleteByID",2);
    sqlSession.commit();
    sqlSession.close();
}
```



## Update

CarMapper.xml

```xml
<update id="updateById" >
    update t_car set car_num=#{carNum},brand=#{brand} where id = #{id}
</update>
```

测试类

```java
@Test
public void testUpdateById(){
    SqlSession sqlSession = SqlSessionUtil.openSession();
    Car car = new Car(1L,"1007","audi",null,null,null);
    sqlSession.update("updateById",car);
    sqlSession.commit();
    sqlSession.close();
}
```

## Select

<font color= red>特别要注意!!! select标签中resultType属性,这个属性来告诉mybatis,查询结果要封装成什么类型的java对象</font>

### 查一个

CarMapper.xml

```xml
<select id="selectById" resultType="com.mybatis.Pojo.Car" >
    select * from t_car where id = #{id}
</select>
```

测试类

```java
@Test
public void testSelectById(){
    SqlSession sqlSession = SqlSessionUtil.openSession();
    Object car = sqlSession.selectOne("selectById", 1);
    System.out.println(car);
    sqlSession.commit();
    sqlSession.close();
}
```

---

测试结果为:Car(id=1, carNum=null, brand=audi, guidePrice=null, produceTime=null, carType=null)只有id,和brand有值

原因为:**数据库中查询回来的列名为car_num,guid_price,produce_time,car_type 与pojo类Car中的属性名不同,所以是空值.**

解决方法:**起别名as**,CarMapper.xml改为

```xml
<select id="selectById"  resultType="com.mybatis.Pojo.Car">
    select id,
           car_num as carNum,
           brand,
           guide_price as guidePrice,
           produce_time as produceTime,
           car_type as carType
    from t_car
    where id = #{id}
</select>
```

### 查所有

CarMapper.xml

```xml
<select id="selectAll" resultType="com.mybatis.Pojo.Car">
    select id,
           car_num as carNum,
           brand,
           guide_price as guidePrice,
           produce_time as produceTime,
           car_type as carType
    from t_car
</select>
```

测试类

```java
@Test
public void testSelectAll(){
    SqlSession sqlSession = SqlSessionUtil.openSession();
    List<Car> cars = sqlSession.selectList("selectAll");
    for (Car car :cars) {
        System.out.println(car);
    }
}
```

## Mapper映射文件中的namespace

在sql mapper.xml文件中有一个属性是namespace，这个属性是用来指定命名空间的。防止id重复。

# MyBatis核心配置文件

## environment标签

```xml
<!--    default表示默认使用的环境-->
    <environments default="development">
<!--        这是其中的一个环境，连接名字为mybaits的数据库-->
<!--        一个环境会对应一个SqlsessionFactory-->
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.cj.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybaits"/>
                <property name="username" value="root"/>
                <property name="password" value="root"/>
            </dataSource>
        </environment>

    </environments>
```

## transactionManager标签

作用：配置事务管理器。指定mybatis具体使用什么方式管理事务。

- JDBC：使用原生的JDBC代码管理事务
- MANAGED：mybatis不在负责事务的管理，交给其他容器管理（比如Spring）

##  dateSource 数据源

dateSource的作用是为程序提供**Connection对象**。

dateSource规范是JDK规定的。

### type属性

**type属性**用来指定数据源的类型，就是指定具体使用什么方式来获取Connection对象。

type属性有三个属性：必须三选一

1. UNPOOLED: 不使用连接池技术
2. POOLED：使用MyBatis自己实现的数据库连接池
3. JNDI：集成其他第三方的数据库连接池

## properties标签

jdbc.properties文件

```properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/mybaits
jdbc.username=root
jdbc.password=root
```

mybatis-config.xml

```xml
<properties resource="jdbc.properties"/>
<environments default="development">

        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="${jdbc.driver}"/>
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
        </environment>

    </environments>
```



# 使用javassist生成类

mybatis当中实际上采用代理模式。在内存中生成dao接口的代理类，然后创建代理类的实例。

使用MyBatis这种机制的前提是：<font color =red>sqlMapper.xml文件中的namespace必须是dao接口的全限定名称，id必须是dao接口中的方法名。</font>

# Mybatis小知识点

## #{}和${}的区别

#{}：底层使用**PreparedStatement**。特点：先进行SQL语句的编译，然后给SQL语句的占位符问号**？**传值。==默认带' '==

${}：底层使用**Statement**。特点：先进行SQL语句的拼接，然后再对SQL语句进行编译。存在SQL注入的风险。

---

使用${} 的情况：

1. 如果SQL语句的关键字放到SQL语句中，只能使用${},例如 order by \${}
2. 拼接表名

## 批量删除（删除多条记录）

```xml
<delete id= "deleteBatch">
delete from t_car where id in (${ids})
</delete>
```

## 模糊查询

使用<font color =red>concat函数</font>

```xml
<select id = "selectByBrandLike" resultType="com.pojo.car">
  select * 
    from t_car
    where 
    	brand like	concat('%',#{},'%')
</select>
```

## 别名机制

```xml
<typeAliases>
<!-- type：指定给哪个类型起别名
	alias:指定别名
-->
    <typeAlias type = "com.car" alias = "aaa"></typeAlias>
    
</typeAliases>
```



