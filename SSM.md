# Spring

> 【黑马程序员SSM框架教程_Spring+SpringMVC+Maven高级+SpringBoot+MyBatisPlus企业实用开发技术】 https://www.bilibili.com/video/BV1Fi4y1S7ix/?p=11&share_source=copy_web&vd_source=a65e4b88935ee947c42eed89fdb6ef02

## 核心概念（解耦）

### IOC（Inversion of Control）

- 使用对象时，由主动new产生对象转换为由**外部**提供对象，此过程中对象的创建控制权由程序转移到**外部**，该思想称为控制反转。

- Spring技术对IOC思想进行了实现。

  Spring提供了一个容器，称为<font color=red>IOC容器</font>，用来充当IOC思想者中的<font color=red>“外部”</font>

  IOC容器负责对象的创建、初始化等一系列工作，被创建或被管理的对象在IOC容器中统称为<font color=red>Bean</font>



### DI(Dependency Injection)

在容器中建立Bean和Bean之间的依赖关系的整个过程，称为依赖注入。

## Bean

```java
public class App{
    public static void main(String[] args){
        //加载类路径下的配置文件
        ApplicationContext ctc = new ClassPathXmlApplicationContext("applicationContext.xml");
        //得到bean对象
        BookDao bookdao = ctx.getBean(Book.class);     
        
    }
}
```

### Bean的作用范围

- singleton（单例）：<font color=red>默认</font>。
- prototype（原型）：

### Bean的实例化

bean本质上就是对象，创建bean使用构造方法完成。

**实例化bean的三种方式：**

1. 提供可访问的无参构造方法（常用）。
2. 使用静态工厂创建（了解）。
3. 使用实例工厂
4. 使用FactoryBean（实用）

### Bean的生命周期



## 依赖注入的方式

### setter注入

#### 简单类型

xml中ref替换成value。

#### 引用类型

- 在bean中定义引用类型属性并提供可访问的set方法

  ```java
  public class BookServiceImpl implements BookService{
      private BookDao bookdao;
      public void setBookDao(BookDao bookdao){
          this.bookdao = bookdao;
      }
  }
  ```

- 配置中使用property标签ref属性注入引用类型对象。

  ```xml
  <bean id="boolService" class ="com.itheima.service.impl.BookServiceImpl">
      <property name= "bookDao" ref="bookDao"/>
  </bean>
  <bean id = "bookDao" class ="com.itheima.dao.BookDaoImpl"/>
  ```

### 构造器注入





### 依赖自动装配

按名称，按类型



### 加载Properties文件

步骤：

1. 在xml中开启context命名空间
2. 使用context空间加载properties文件
3. 使用属性占位符${}读取properties文件中的属性。



## 注解开发

### bean

#### 定义bean

@Component

- @Controller
- @Service
- @Repository

#### 作用范围

@Scope（"prototype"）/@Scope（"singleton"）

#### 生命周期

@PostConstruct 构造方法后，（初始化）

@PreDestroy 



### 配置文件

使用java类代替 Spring核心配置文件

```java
@Configuration
@ComponentScan("com.ithema")
@PropertySource("jdbc.properties")
@Import({jdbcConfig.class})
public class SpringConfig{
    
}
```

- @Configuration 注解用于设定当前类为配置类
- @ComponentScan注解用于设定扫描路径
- @PropertySource  加载外部properties配置文件。
- @Import  使用独立配置类管理第三方bean。



### 依赖注入

> 自动装配基于反射设计创建对象并暴力反射对应属性为私有属性初始化数据。

#### 引用类型：

@Autowired    //（根据类型装配）

@Qualifier（"name"）//与@Autowired搭配 根据名字装配。

#### 简单类型：

@Value（${}）



### 第三方bean管理

使用@Bean配置第三方类。



# SpringMVC





