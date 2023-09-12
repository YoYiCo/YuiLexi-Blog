---
title: Java基础语法
date: 2023-4-26 00:00:00
update: 2023-7-24 00:00:00
categories: 
	- [Java,Java基础]
tags: [Java,面向对象,程序设计,Java基础语法,设计模式,服务器开发,Web开发]
description: Java基础语法，涵盖了Java的基础知识，包括Java的基本语法、面向对象、程序设计、设计模式、服务器开发、Web开发等。
image_path: Programming/Java知识库/Java基础语法/
---

# 一、认识 Java

Java 是目前软件设计中优秀的程序设计语言。不仅用来开发大型的应用程序，而且特别适合于 Internet 的应用开发，其已成为网络时代最重要的语言之一。

Java 技术目前最活跃的领域大致分为两个大方向

- 面向企业应用：旨在提升企业竞争力；
- 面向移动应用：旨在提供更多、更方便的个性化服务。

Java 具有三方面的内涵：

- 是一种编程语言
- 具有一套开发工具
- 具有一个运行环境

## 1.1 Java 简介

### 1.1.1 Java 的特点

1. 简单性

   ​ 语法简单，Java 语言不使用指针，并提供了自动垃圾回收机制，使程序员无需担忧内存管理。

2. 面向对象的程序设计语言

3. 跨平台：一次编译到处运行

   ![Java程序流](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/Java程序流.png)

4. 安全性

   1. 要求显式的变量类型声明
   2. 不支持指针，杜绝了内存的非法访问
   3. 自动内存单元收集防止了内存泄露
   4. 可以自动发现数组和字符串的越界，防止堆栈溢出
   5. 提供了异常处理机制，简化错误处理任务
   6. 运行时环境还有类装载器，字节码校验器和安全管理器这三个组。

   ![Java运行环境](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/Java运行环境.png)

5. 多线程性

   1. Java 运行时环境本身就是多线程的。若干个系统线程运行负责必要的无用单元回收、系统维护等系统级操作；
   2. 另一方面，Java 语言内置多线程控制，可大大简化多线程应用程序开发。

6. 动态性

   ​ Java 程序执行时所需要调用的类在运行时动态地加载到内存中，这使得 Java 程序运行所需的内存开销小。可以被用于许多嵌入式系统。

### 1.1.2 跨平台原理

1. Java 编译器生成与特定体系结构无关的字节码指令，
2. Java 运行时环境中的 Java 虚拟机（JVM：Java Virtual Machine）

![Java运行环境](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/Java运行环境.png)

JVM 的内部体系结构：

![JVM的内部体系结构](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/JVM的内部体系结构.png)

Java 有两种执行方式：

- **解释执行**：逐条读入字节码，逐条解释成机器指令
- **即时编译**：JVM 将解释后的字节码发给 JIT 编译器翻译成机器码，并保存起来以备再用。为了加快执行速度，只对经常使用的热代码编译。

## 1.2 Java 开发环境

### 1.2.1 JDK

JDK：**最基本的开发环境**。

JDK：

- 开发工具：主要是 JavaC 及基本核心类
- **运行环境**：JRE、JVM 及基本核心类
- 其他工具：Jar、Javadoc、Javah、Javap 等

  按 java 的应用环境分如下版本：

- JavaEE(java enterprise edition)

  ​ 主要用于开发企业级分布式的网络程序，如电子商务网站和 ERP 系统，核心为 EJB 。Java EE 主要包括：

  - Java SE
  - EnterpriceJavaBeans（EJB）
  - Java Servlets API
  - Java Server Pages（JSP）
  - Extensible Markup Language (XML)

  ​ 当前主流架构(SSH)：Struts + Spring + Hibernate/Mybatis

- JavaSE(java stand edition)

  ​ 主要用于桌面应用程序开发，是 JAVA 的基础。包含 Java 语言基础、JDBC 数据库操作、I/O 输入输出、网络通信、多线程等技术。

- JavaME(java micro edition)

  ​ 针对消费类的电子设备如掌上电脑、手机、汽车导航系统等。特点是：语言精简、运行环境高度优化。

Windows 操作系统下，JDK 的项目结构如下：

![JDK项目结构](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/JDK项目结构.png)

### 1.2.2 配置环境变量

什么是环境变量：

环境变量也称为系统变量，是由操作系统提供的一种与操作系统中运行的程序进行通信的机制，一般可为运行的程序提供配置信息。环境变量一般为“名字:值”对。在 Shell 编程中以${变量名}来取某变量的值

**常用的 Java 环境变量包括**：

- JAVA_HOME
- CLASSPATH
- PATH

在安装完 JDK 之后，为了能在任何目录中使用编译器和解释器，可在系统特性中设置环境变量：path、classpath

JDK 中常用的工具：

- JShell：JDK9 出现的工具

![JDK中常用的工具](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/JDK中常用的工具.png)

### 1.2.3 文本编辑器

常用的 Java 文本编辑器有 Notepad++、EditPlus、Sublime 和 Visual Studio 等。

### 1.2.4 目前主流集成开发平台

- IBM 公司: Eclipse/MyEclipse

- Sun microsystem 公司: Netbeans（GUI）

- IntelliJ IDEA

- 甲骨文：Oracle JDeveloper

> 此文档中所有 Java 代码的开发环境为：IntelliJ IDEA 2023.1

# 二、Java 语法基础

## 2.1 Java 语法特点

### 2.1.1 Java 程序结构

第一个 Java 程序，具体代码如下：

```Java
public class MyJava_001 {
    public static void main(String[] args)
    {
        System.out.println("Hello world!");
    }
}
```

- Java 程序是由一个或多个类组成的

- 类是由类首部、类体两大部分组成

- 类体定义了成员变量和方法

  ​ 类的最简单定义如下：

  ```Java
  [修饰符] class 类名 {    //类首部
  成员:  fields         //成员变量，Java 中也称字段
  成员:  methods        //成员方法
  }

  ```

  ​

  ​ 方法定义形式如下所示：

  ```Java
  [修饰符] 返回值类型  方法名 ([类型1 形参1, 类型2 形参2,…]){
     局部变量;
     方法体
     语句或语句块;
  }

  ```

  ​

### 2.1.2 Java 代码规范

1. Java 是区分大小写的
2. Java 语句是最小的执行单位；每条语句以分号 “;” 结束
3. 大括号{ }内的一系列语句称为语句块
4. Java 源文件以“.java” 结尾，此文件中最多只能有一个类被声明为 public，保存时源文件名需与 public 类名相同，如果文件中不存在 public 类，源文件名无要求
5. 一个源文件包含几个类就可以编译出几个.class 文件。
6. 多个.java 文件如果他们之间有调用关系，那么编译时只要编译主文件其他的关联文件也会一并被联合编译

### 2.1.3 注释

1. 单行注释
2. 多行注释
3. 文档注释

### 2.1.4 关键字

|   abstract    |  boolean  |  break   |     byte     |   case   |   catch    |
| :-----------: | :-------: | :------: | :----------: | :------: | :--------: |
|     char      |   class   | const \* |   continue   | default  |     do     |
|    double     |   else    | extends  |    final     | finally  |   float    |
|      for      |  goto \*  |    if    |  implements  |  import  | instanceof |
|      int      | interface |   long   |    native    |   new    |  package   |
|    private    | protected |  public  |    return    |  short   |   static   |
| strictfp \*\* |   super   |  switch  | synchronized |   this   |   throw    |
|    throws     | transient |   try    |     void     | volatile |   while    |

> 注: \*当前未被使用，\*\*使用于 Java2

### 2.1.5 标识符

标识：常量、变量、数据类型、类和方法。

组成规则：

- 字母(A~Z、a~z)、特殊符号($、\_)和数字(0~9)
- 开头不能是数字
- 不能为关键词：true、false、null
- 大小写敏感

一般约定：

- 表示常量的标识符全部大写，如 RED
- 表示类名的标识符用 Pascal 命名规范
- 表示公有方法和实例变量的标识符用小写字母开始（小驼峰命名法）
- 表示私有或局部变量的标识符全部用小写字母，如 next_value

空白符：空格、换行符、制表符

分号：表示语句结束，或用于 for 循环语句中

逗号：变量之间的分隔

冒号：? : /switch 循环中的 case 语句

花括号：类体、方法体、复合语句(for/while/switch/if)

## 2.2 基本数据类型

### 2.2.1 数据类型

值类型

内置的基本数据类型如下：

|  类型   |                   说明                    |      范围      | 表示法 |
| :-----: | :---------------------------------------: | :------------: | :----: |
|  byte   |    8 位、有符号、二进制补码表示的整数     |   -128 ~ 127   |   12   |
|  short  |    16 位、有符号、二进制补码表示的整数    | -32768 ~ 32767 |  321   |
|   int   |   32 位、有符号的、二进制补码表示的整数   | -2^31 ~ 2^31-1 |  412   |
|  long   |    64 位、有符号、二进制补码表示的整数    | -2^63 ~ 2^63-1 | 3219L  |
|  float  | 单精度、32 位、符合 IEEE 754 标准的浮点数 |                |  0.0f  |
| double  | 双精度、64 位、符合 IEEE 754 标准的浮点数 |                |  0.0d  |
| boolean |              表示一位的信息               | true 和 false  |        |
|  char   |       一个单一的 16 位 Unicode 字符       |                |        |

引用类型：

- 在 Java 中，引用类型的变量非常类似于 C/C++的指针。引用类型指向一个对象，指向对象的变量是引用变量。变量一旦声明后，类型就不能被改变了。
- 对象、数组都是引用数据类型。
- 所有引用类型的默认值都是 null。
- 一个引用变量可以用来引用任何与之兼容的类型。

### 2.2.2 类型转换

将一种类型的数据转换为另一种类型的数据

- 操作数转换为同种类型，然后运算

- 整数型、实数型和字符型

- 表达形式: (类型) 操作数

两种方法

1. 隐型类型转换:：自动类型转换(系统完成)

   ​ 宽化转换(widening conversion)

   ```Java
   byte j=60;
   short k=4;
   int l=31;
   long m=4l;

   long result=0l;
   result +=j-8;
   result *=k+2;
   result /=m+1;
   result -=l;
   result %=m;
   ```

2. 显型类型转换: 强制类型转换

   ​ 窄化转换 (narrowing conversion)

   ```Java
   double a = 1.5;
   float b = a;

   System.out.println(“b=" + b);
   ```

   ​ 编译: “possible loss of precision”。数据精度丢失 → 数据丢失

   ```Java
   double a = 1.5;

   float b = (float)a;

   System.out.println(“b=" + b);
   ```

## 2.3 运算符与表达式

### 2.3.1 算数运算符

表格中的实例假设整数变量 A 的值为 10，变量 B 的值为 20：

| 操作符 | 描述                              | 例子               |
| :----: | :-------------------------------- | :----------------- |
|   +    | 加法 - 相加运算符两侧的值         | A + B 等于 30      |
|   -    | 减法 - 左操作数减去右操作数       | A – B 等于 -10     |
|   \*   | 乘法 - 相乘操作符两侧的值         | A \* B 等于 200    |
|   /    | 除法 - 左操作数除以右操作数       | B / A 等于 2       |
|   ％   | 取余 - 左操作数除以右操作数的余数 | B%A 等于 0         |
|   ++   | 自增: 操作数的值增加 1            | B++ 或 ++B 等于 21 |
|   --   | 自减: 操作数的值减少 1            | B-- 或 --B 等于 19 |

**自增自减运算符**：

1. 自增（++）自减（--）运算符是一种特殊的算术运算符，在算术运算符中需要两个操作数来进行运算，而自增自减运算符是一个操作数。
2. 前缀自增自减法(++a,--a)： 先进行自增或者自减运算，再进行表达式运算。
3. 后缀自增自减法(a++,a--)：先进行表达式运算，再进行自增或者自减运算

### 2.3.2 关系运算符

表格中的实例整数变量 A 的值为 10，变量 B 的值为 20：

| 运算符 | 描述                                                             | 例子             |
| :----: | :--------------------------------------------------------------- | :--------------- |
|   ==   | 检查如果两个操作数的值是否相等，如果相等则条件为真。             | （A == B）为假。 |
|   !=   | 检查如果两个操作数的值是否相等，如果值不相等则条件为真。         | (A != B) 为真。  |
|   >    | 检查左操作数的值是否大于右操作数的值，如果是那么条件为真。       | （A> B）为假。   |
|   <    | 检查左操作数的值是否小于右操作数的值，如果是那么条件为真。       | （A <B）为真。   |
|   >=   | 检查左操作数的值是否大于或等于右操作数的值，如果是那么条件为真。 | （A> = B）为假。 |
|   <=   | 检查左操作数的值是否小于或等于右操作数的值，如果是那么条件为真。 | （A <= B）为真。 |

### 2.3.3 位运算符

下表列出了位运算符的基本运算，假设整数变量 A 的值为 60 和变量 B 的值为 13：

| 操作符 | 描述                                                                               | 例子                              |
| :----: | :--------------------------------------------------------------------------------- | :-------------------------------- |
|   ＆   | 如果相对应位都是 1，则结果为 1，否则为 0                                           | （A＆B），得到 12，即 0000 1100   |
| &#124; | 如果相对应位都是 0，则结果为 0，否则为 1                                           | （A&#124;B）得到 61，即 0011 1101 |
|   ^    | 如果相对应位值相同，则结果为 0，否则为 1                                           | （A ^ B）得到 49，即 0011 0001    |
|   〜   | 按位取反运算符翻转操作数的每一位，即 0 变成 1，1 变成 0。                          | （〜A）得到-61，即 1100 0011      |
|   <<   | 按位左移运算符。左操作数按位左移右操作数指定的位数。                               | A << 2 得到 240，即 1111 0000     |
|   >>   | 按位右移运算符。左操作数按位右移右操作数指定的位数。                               | A >> 2 得到 15 即 1111            |
|  >>>   | 按位右移补零操作符。左操作数的值按右操作数指定的位数右移，移动得到的空位以零填充。 | A>>>2 得到 15 即 0000 1111        |

### 2.3.4 逻辑运算符

下表列出了逻辑运算符的基本运算，假设布尔变量 A 为真，变量 B 为假

|    操作符    | 描述                                                                                      | 例子                      |
| :----------: | :---------------------------------------------------------------------------------------- | :------------------------ |
|      &&      | 称为逻辑与运算符。当且仅当两个操作数都为真，条件才为真。                                  | （A && B）为假。          |
| &#124;&#124; | 称为逻辑或操作符。如果任何两个操作数任何一个为真，条件为真。                              | （A&#124;&#124; B）为真。 |
|      ！      | 称为逻辑非运算符。用来反转操作数的逻辑状态。如果条件为 true，则逻辑非运算符将得到 false。 | ！（A && B）为真。        |

### 2.3.5 赋值运算符

下面是 Java 语言支持的赋值运算符：

| 操作符  | 描述                                                         | 例子                                     |
| :-----: | :----------------------------------------------------------- | :--------------------------------------- |
|    =    | 简单的赋值运算符，将右操作数的值赋给左侧操作数               | C = A + B 将把 A + B 得到的值赋给 C      |
|   + =   | 加和赋值操作符，它把左操作数和右操作数相加赋值给左操作数     | C + = A 等价于 C = C + A                 |
|   - =   | 减和赋值操作符，它把左操作数和右操作数相减赋值给左操作数     | C - = A 等价于 C = C - A                 |
|  \* =   | 乘和赋值操作符，它把左操作数和右操作数相乘赋值给左操作数     | C _ = A 等价于 C = C _ A                 |
|   / =   | 除和赋值操作符，它把左操作数和右操作数相除赋值给左操作数     | C / = A，C 与 A 同类型时等价于 C = C / A |
| （％）= | 取模和赋值操作符，它把左操作数和右操作数取模后赋值给左操作数 | C％= A 等价于 C = C％A                   |
|  << =   | 左移位赋值运算符                                             | C << = 2 等价于 C = C << 2               |
|  >> =   | 右移位赋值运算符                                             | C >> = 2 等价于 C = C >> 2               |
|   ＆=   | 按位与赋值运算符                                             | C＆= 2 等价于 C = C＆2                   |
|   ^ =   | 按位异或赋值操作符                                           | C ^ = 2 等价于 C = C ^ 2                 |
| &#124;= | 按位或赋值操作符                                             | C &#124;= 2 等价于 C = C \| 2            |

### 2.3.6 其他运算符

1. 条件运算符也被称为三元运算符。该运算符有 3 个操作数，并且需要判断布尔表达式的值。该运算符的主要是决定哪个值应该赋值给变量。

   ```Java
   variable x = (expression) ? value if true : value if false
   ```

2. instanceof 运算符。该运算符用于操作对象实例，检查该对象是否是一个特定类型（类类型或接口类型）。

   ```Java
   (Object reference variable) instanceof  (class/interface type)
   ```

   ​

### 2.3.7 运算优先级

下表中具有最高优先级的运算符在的表的最上面，最低优先级的在表的底部：

| 类别     | 操作符                                          | 关联性   |
| :------- | :---------------------------------------------- | :------- |
| 后缀     | () [] . (点操作符)                              | 左到右   |
| 一元     | expr++ expr--                                   | 从左到右 |
| 一元     | ++expr --expr + - ～ ！                         | 从右到左 |
| 乘性     | \* /％                                          | 左到右   |
| 加性     | + -                                             | 左到右   |
| 移位     | >> >>> <<                                       | 左到右   |
| 关系     | > >= < <=                                       | 左到右   |
| 相等     | == !=                                           | 左到右   |
| 按位与   | ＆                                              | 左到右   |
| 按位异或 | ^                                               | 左到右   |
| 按位或   | &#124;                                          | 左到右   |
| 逻辑与   | &&                                              | 左到右   |
| 逻辑或   | &#124;&#124;                                    | 左到右   |
| 条件     | ？：                                            | 从右到左 |
| 赋值     | = + = - = \* = / =％= >> = << =＆= ^ = &#124; = | 从右到左 |
| 逗号     | ，                                              | 左到右   |

### 2.3.8 表达式

- 算术表达式

  ​ 数字或变量进行算术运算，本质上还是一个数。

- 赋值表达式

  ​ 作用：将**赋值运算符**右边量的值（或者算术表达式的值），赋给左边的变量。

- 逻辑表达式

  ​ 逻辑表达式，其本身相当于一个 boolean 类型的变量。根据具体情况，表达式会取 true 或者 false 。

## 2.4 常量与变量

### 2.4.1 常量

程序执行过程中，值保持不变的量，称为**常量**。常量有以下类型：整型常量、实型常量、布尔型常量、字符型常量、字符串常量

### 2.4.2 变量

程序执行过程中，值可以改变的量，称为**变量**。整型变量、实型变量、字符型变量、字符串变量、布尔变量等。

变量定义语法如下：

```Java
类型 变量名[ = 初值];
//For example
int age = 18;
```

### 2.4.3 变量的作用域

变量的使用范围，一般如下图所示：

![变量的作用域](https://imageshack.yuilexi.cn/Programming/Java知识库/Java基础语法/变量的作用域.png)

作用域(Scope)：在当前大括号 “{ }” 中声明的变量，作用范围只有大括号以内。

```Java
public class MyJava_001 {
    public static void main(String[] args)
    {
        if(true)
        {
            int a = 10;
        }
        System.out.println("Hello world!",a);
    }
}
```

运行上述代码，就会出现一下错误：

```txt
java: 找不到符号
  符号:   变量 a
  位置: 类 MyJava_001
```

**<font color='red'>final 变量</font>**：带有关键字 final 的变量。final 变量初始化后不能再改变

```Java
public class Study {
    public  static void main(String[] args)
    {
        final int a;
        a = 10;
        //a = 20;
    }
}
```

上述代码运行，程序不会报错。但是如果把注释的语句加上，那么程序就会抛出以下错误：

```txt
java: 可能已分配变量a
```

## 2.5 基本输入输出

### 2.5.1 Java 输出

语法如下：

```Java
System.out.println();
System.out.print();
System.out.printf();
```

说明如下：

- System 是一个类
- out 是一个 public static 字段：它接受输出数据

println()，print()和 printf()之间的区别

- print() ：它在引号内打印字符串。
- println() ：它在引号内打印字符串，类似于 print()方法。然后光标移动到下一行的开头。
- printf() ：Tt 提供**字符串格式化**（类似于 C / C ++编程中的 printf）

### 2.5.2 Java 输入

Java 提供了不同的方法来从用户那里获取输入。但是，您将学习使用 Scanner 类的对象从用户那里获取输入。

为了使用的对象 Scanner，我们需要导入 java.util.Scanner 包。

```Java
import java.util.Scanner;
```

然后，我们需要创建 Scanner 类对象。我们可以使用该对象从用户那里获取输入。

```Java
import java.util.Scanner;
public class Study {
    public  static void main(String[] args)
    {
        //创建Scanner对象
        Scanner input = new Scanner(System.in);
        //接受用户的输入
        int number = input.nextInt();
        System.out.println("\n你输入的是："+ number);
    }
}
```

System.in：对象读数据的基本单位是一个字节，可用方法 System.in.read()顺序读入一个字节，或利用方法 System.in.read(byte b[],int off,int length) 连续读入多个字节。用户程序通常需要将字节数据解析成不同类型的数据进行处理。

为了简化这部分工作，可以用 Scanner 对象将字节流转化成基本数据类型

# 三、流程控制语句

## 3.1 选择结构

### 3.1.1 单 if 语句

语法如下：

```Java
if(条件表达式1)
    语句;
if(条件表达式2)
{
    语句块;
}
```

### 3.1.2 if…else 语句

语法如下：

```Java
if(条件表达式1)
{
    语句块1;
}
else
{
    语句块2;
}
```

例如，下面代码;

```Java
import java.util.Scanner;
public class Study {
    public  static void main(String[] args)
    {
        boolean isChild = true;
        if(isChild)
        {
            System.out.println("我是孩子。");
        }
        else {
            System.out.printfIn("我不是孩子");
        }
    }
}
```

### 3.1.3 switch 语句

语法如下：

```Java
switch (表达式) {
    case 值1:  语句序列; [break;]
    case 值2:  语句序列; [break;]
        ......
    [default: 默认语句;]
}
```

## 3.2 循环结构

### 3.2.1 while 循环

语法如下：

```Java
while(逻辑表达式){
    循环体;
}
```

### 3.2.2 do-while 循环

语法如下：

```Java
do{
    循环体;
}while(逻辑表达式)
```

### 3.2.3 for 循环

语法如下：

```Java
for(赋值表达式;逻辑表达式;赋值表达式){
    循环体;
}
```

for 循环的几点注意

- 初始化部分和迭代因子可以包含多个语句，以“,”分开

  ```Java
  for (int i=0, j=10; i<j; i++, j--) {
      ....
  }
  ```

  ​

- 初始化部分、条件判断部分和迭代因子可以为空语句，但以“;”分开，表示无限循环

  ```Java
  for ( ; ; ) {  // infinite loop
      ....
  }
  ```

  ​

### 3.2.4 增强 for 循环（for-each）

Java5 引入了一种主要用于数组的增强型 for 循环。语法格式如下:

```Java
for(声明语句 : 表达式){
    ....
}
```

## 3.3 程序跳转语句

break 主要用在循环语句或者 switch 语句中，用来跳出整个语句块。break 跳出最里层的循环，并且继续执行该循环下面的语句。

continue 适用于任何循环控制结构中。作用是让程序立刻跳转到下一次循环的迭代。在 for 循环中，continue 语句使程序立即跳转到更新语句。在 while 或者 do…while 循环中，程序立即跳转到布尔表达式的判断语句。

return：方法返回

throw：抛出异常(Exception)

```Java
break;
continue;
```

# 四、复杂数据类型

## 4.1 数组

数组是一组**同类型**的变量或对象的集合。

- 数组的类型可以是基本类型，或类和接口
- 数组中**每个元素的类型相同**
- 引用数组元素通过数组名[下标]
- 数组下标(数组的索引)从 0 开始

数组是一种特殊的对象(Object)

- 定义类型 (声明)
- 创建数组 (分配内存空间) : new
- 释放 (Java 虚拟机完成)

一维数组、多维数组

### 4.1.1 一维数组的创建——<font color='red'>new</font>关键字

一维数组的元素只有一个下标变量。例如：整型数组 A[]

```Java
public class Study {
    public  static void main(String[] args)
    {
        int[] scores;
        System.out.println("我的分数是：",scores);
    }
}
```

但是，上述代码会报错，因为 Java 数组在声明时，并没有为其分配内存空间。

数组的创建：用 <font color='red'>new</font> 来创建数组，为数组元素分配内存空间，并对数组元素进行初始化。语法如下：

```Java
数组名 = new 类型[数组长度];
```

例如：

```Java
public class Study {
    public  static void main(String[] args)
    {
        int[] scores = new int[5];
    }
}
```

### 4.1.2 数组的初始化

1. 对每个元素初始化

   ​ 例如下面你代码：

   ```Java
   public class Study {
       public  static void main(String[] args) {
           int[] scores = new int[5];
           for(int a = 0;a<5;a++){
               scores[a] = 90 + a;
               System.out.println(scores[a]);
           }
       }
   }
   ```

2. 整体初始化

   ​ 例如下面的代码：

   ```Java
   public class Study {
       public  static void main(String[] args) {
           int[] scores = {1,2,3,4,5};
           for(int a = 0;a<5;a++){
               System.out.println(scores[a]);
           }
       }
   }
   ```

   ​

### 4.1.3 数组的操作

1. 一维数组的复制

   ```java
   package Java学习的代码测试;

   public class 数组复制 {
       public static void main(String[] agrs) {
           int[] a = { 2, 4, 6, 8 };
           int[] b;
           int[] c = { 1, 3, 5, 7, 9 };
           b = a;
           System.arraycopy(a, 1, c, 0, 3);
           System.out.println("a数组为：");
           for (int i = 0; i < a.length; i++) {
               System.out.print(a[i] + " ");
           }
           System.out.println();
           System.out.println("b数组为：");
           for (int i = 0; i < b.length; i++) {
               System.out.print(b[i] + " ");
           }
           System.out.println();
           System.out.println("c数组为：");
           for (int i = 0; i < c.length; i++) {
               System.out.print(c[i] + " ");
           }
           System.out.println();
       }
   }
   ```

   ​ 直接用等号进行复制，其实是赋给等号左边一个引用，二者共用一块内存空间。

   ​ `System.arraycopy(A[],int b, C[], int d, int l)`说明：

   - 将数组 A 从 A[b] 开始的 l 个元素赋给数组 C 的 C[d]开始的后 l 个元素

### 4.1.4 多维数组

多维数组的声明、创建、调用等与一维数组类似。

## 4.2 字符串

# 五、面向对象程序设计——类

## 5.1 基本概念

面向对象(Object Oriented-OO)

- 面向对象编程(Object Oriented Programming-OOP)
- 面向对象是一种软件开发的方法，

第一个面向对象的语言: Simula-67。第一个成功的面向对象编程语言: Smalltalk。目前的主流：C++, JAVA, C#等

1. 用客观世界中描述事物的方法来描述程序中要解决的问题
2. 万事万物都是对象
3. 程序便是成堆的对象，彼此通过消息的传递，请求其他对象进行工作

**五个基本概念：对象、类、封装性、继承性、多态性**

## 5.2 类的定义

### 5.2.1 类的基本格式

类的定义的格式如下：

```java
[修饰符] class 类名 [extends 父类] implements [接口]{
    成员变量;
    成员方法;
}
```

- 类的修饰符(modifier)
  - public：公共类，可以被其他任何类所使用
  - 无修饰/默认：仅能被同一个包中的其他类引用
  - abstract：抽象类，不能被实例化/即创建对象
  - final：最终类不能被继承
- extends：一个类继承另一个类
- implements：一个类实现一些接口(interface)的方法，用以变相实现多重继承

### 5.2.2 Package/包的概念

包(Package)的概念

- 通过包来管理命名空间(naming space)
- 防止同名的类发生冲突
- 形成层次化的结构，便于管理

### 5.2.3 类的成员

对象具有**状态**和**行为**。

​
