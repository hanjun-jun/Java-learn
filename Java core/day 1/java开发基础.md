---
#第一部分java开发基础

---

##一.什么是java
> java是一种可以编写跨平台应用的面向对象的程序设计语言，是由Sun Microsystems公司于1995年5月推出的Java程序设计语言和Java平台（即JavaSE, JavaEE, JavaME）的总称。

##二.java开发环境搭建
###1.下载安装jdk
> ​ [Java官网](http://https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
> ​	JDK：Java SE Development Kit
> ​	Java集成开发工具，当前最新版本JDK13，公司开发一般用jdk-8u144-windows-x64.exe；u144的意义：u：update，144：144次更新。

###2.环境变量配置
- 1.打开电脑属性-高级系统设置-环境变量
- 2.配置系统环境变量Path,添加jdk安装目录下bin文件的路径，默认安装一般是C:\ProgramFiles\Java\jdk1.8.0_144\bin
- 3.在系统变量中新建一个CLASSPATH：类路径，值是 .;(应切换到英文输入法下)

####问题
- 问题1：Path和CLASSPATH大小写区分吗？
  答：Windows系统不区分，Linux、Unix、Mac下严格区分
- 问题2：Path和CLASSPATH的区别？
  答：Path环境变量记录的是可执行文件，如exe,对可执行文件先在当前路径下去找，如果没有找到就去Path环境变量中配置的路径去找：CLASSPATH环境变量记录的是Java类运行文件所在的目录，"."表示当前路径。
- 问题3：Windows下，如果用户变量和系统变量名字一样，哪个生效？
  答：用户变量生效，系统变量会被覆盖。

####检查环境变量是否配置成功（dos系统）

- 1.方式一：用javac或java命令
  - 问题：javac和java从哪里来的？
    答：Path环境变量的值，就是JDK的bin目录。

- 2.方式二：set命令（设置或查看环境变量）
  使用set classpath或set path，查看显示的值是不是我们需要的。在set设置的时候，设置结果仅对当前控制台（命令行）窗口有效，当控制台关闭后，set设置的结果失效。
  - 问题：如何查看当前机器上起效的JDK版本？
    答：java -version命令

##四.编写HelloWorld程序，不带包。

- 编写Java代码的工具：记事本、Atom、Notepad++、EditPlus（商业）、Sublime、 VS Code.

> Java文件实际上就是文本文件。

- 编译之前需要访问文件所在目录，例如：d: 就切换到d盘下了，然后cd(change directory) + 文件名：就到了相关目录下；在使用命令时，可以用Tab键进行自动补全。

- 其他DOS命令：

  - 1.dir+回车：查看当前目录都有哪些文件（可以查看文件类型和大小）

  - 2.如果想退回上一级目录：cd ..+回车即可

  - 3.如果想直接退回根目录上：cd \  +回车

  - 4.Tab键:自动补全文件名


- 编译：用javac命令：javac HelloWorld.java（编译后出现class文件），如果因GBK编码导致编译出现汉字乱码报错，使用下面的方法编译： javac  -encoding utf-8  HelloWorld.java。

- 执行：用java HelloWorld命令（执行的是class文件）
- 编写规范
> - 必须加规范的注释（版权注释、JavaDoc注释、类的功能）
> - 缩进4个空格
> - 类名、方法名后有一个空格
> - Java严格区分大小写

##五.编写HelloWorld程序，带包。

- 包名命名规则：
- 全小写，不建议数字
- 域名倒写
- "."表示当前目录

```java
package cn.edu.java.day1;
 /**
    在屏幕上输出Hello（类功能）
 	@author name
	@version 1.0
*/
public class HelloWorld {
 	public static void main(String [] args) {
     	System.out.println("Hello");
 	}
}
```

- 编译：javac -encoding utf-8 -d  . HelloWorld.java
- 执行：java cn.edu.java.day1.HelloWorld

##六.在一个.java文件中写多个class，编译后产生什么？如何执行？

```Java
package cn.edu.java.day1;

/**
	在一个java文件中写多个class
 	@author name
	@version 1.0
*/
public class Person {
}
class Student {
}
class Teacher {
}
```

- 问题1：如何编译？ 答：javac  -d .  Person.java
- 问题2：如何执行？指定谁，执行谁。
- 问题3：将Person.java另存为Student.java，为什么编译无法通过？
  答：如果一个类被public修饰，保存文件的时候，文件名和类名完全相同。
- 问题4：将Student修饰为public，为什么无法通过编译？
  答：一个java文件中，只能有一个类被public修饰。如果所有类都不是public的，保存时文件名随意。
- 拓展：一个java文件中如果有多个类，被private修饰的类智能在该java文件中访问，未加修饰的类只能被在同一个包的java文件访问，不同包的只能访问公共类。

---

##面试问题

###一.JDK、JRE、JVM是什么关系？
- 1.三者分别是什么？
  - JDK(Java SE Development Kit):Java集成开发工具包
  - JRE(Java Runtime Environment):Java运行环境
  - JVM(Java Virtual Machine):Java虚拟机

- 2.它们之间的关系
- JDK中包含JRE运行环境，JRE运行环境中包含JVM虚拟机。
  - JDK：包含有一些工具，比如：javac、Java、javadoc等。
  - JRE：包含API，支持Java程序的执行。
  - JVM：将class文件解释成特定平台的机器指令。

###二.Java程序的执行过程？
- Javac命令对程序进行编译成class文件，然后JVM翻译成对应的机器指令
- .class文件是什么文件？答：字节码文件Bytecodes
- .class文件中放的是什么东西？答：JVM可以识别的字节码，内容是16内容是16进制表示的。
- .class文件是平台相关还是平台无关？答：平台无关（跨平台），由于java写的程序是跨平台的。
- .class文件内容能看到吗？答：能，使用UltraEdit可以看到。其开头的是CAFEBABE
- JVM是平台相关还是无关？答：JVM平台相关，不同的操作系统有不同的虚拟机
- JVM的作用是：答：将class文件解释成特定平台的机器指令。

## 三.Java平台划分？(从小到大划分 面试回答前三个即可)

- 1.Java ME（Java平台的微型版）

- 2.Java SE（Java平台的标准版）*

- 3.Java EE（Java平台的企业版）*原名：J2EE

- 4.Java Card

## 四.Java语言有哪些特点？

- 面向对象Object oriented
- 跨平台Architecture neutral
- 简单
- 开源
- 多线程
- 可移植性

## 五.Java语言是编译型还是解释型？

- Java是两种的结合

## 六.C/C++/Java的区别?

- 1.应用场景不同:
  - C语言：面向过程的，主要做硬件编程、操作系统的底层编程、算法。
  - C++语言：面向对象的和面向过程的混合体，不是纯正的OOP(面向对象)，是在C的基础上加入了OOP的内容。主要做图形图像处理、通信软件、控制软件、工具软件、游戏等。
  - Java语言：面向对象的，纯OOP语言，主要用在大型管理系统开发、大数据开发、Android手机开发、硬件开发、教务系统等；它是平台无关的。
- 2.面向对象和面向过程的区别？
   例如：将大象装进冰箱里
   - 面向过程：首先打开冰箱门，然后把大象装进去，最后把冰箱门关上
   - 面向对象：建立冰箱对象，冰箱对象有两个方法，打开冰箱门和关闭冰箱门，建立大象对象，大象有一个方法，进去。冰箱.门打开()；大象.进去（）；冰箱.门关闭（）；
- 2.执行效率。
  - 一般来说C、C++执行效率高于Java，但主要取决于计算机的性能。

## 七.HelloWorld的面试题

- 1.public static void main(String[] args) {}  :入口，固定写法。
  - public可以去掉吗？答：去掉后能编译，不能执行。
  - static可以去掉吗？答：去掉后能编译，不能执行。
  - void可以去掉吗？答：不可以，没有返回类型。
  - []去掉可以吗?编译通过，答：去掉后能编译，不能执行。
  - String[] args去掉可以吗？答：去掉后能编译，不能执行。
  - []换成...可以吗? 答：完全可以。
  - args换成a可以吗？答：可以，相当于变量。
  - static public这样写可以吗？答：可以。
  - static void public这样写可以吗？答：不可以。
  - void main(){}可以吗？答：可以。

- 2.public class HelloWorld{}
  - public可以去掉吗？ 答：可以。
  - class可以去掉吗？ 答：不可以。
  - HelloWorld可以换成别的名字吗？ 答：可以

## 八.Javac和Java的面试题？

- 1.控制板上：编译时：在windows下文件名大小写不区分，其他平台下不行（文件名是HelloWorld）

> 例如: javac helloworld.java 或者 JAva Helloworld.java都可以编译,但是javac HelloWorld.JAVA不能编译。

- 2.java严格区分大小写（包括文件名）

> 例如：java HelloWorld  或者  JAVA HelloWorld 正确      java  helloworld  错误

## 九. Java语言哪年出现？
- 1991年出现，1995年5月23号发布。
