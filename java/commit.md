java一次编译，到处运行



十大特性：可移植（int类型无论是在32位、还是64位都是4个字节）




> 相较于C/C++,java 没有指针、头文件、结构、联合、枚举等概念。
>
> 并且java，是面向对象的，是抽象的对象。C/C++是面向过程的。C++是C的面向对象。



#### 配置环境

* JDK -        java Development Kit 配置环境

配置系统变量，创建JAVA_HOME \PATH \ CLASSPATH .

* 一些常用的命令



打开powershell窗口，按住shift+右键，打开当前目录的powershell窗口。

***

命令：输入java Hello World.java 嫌麻烦重复输入，使用上下键，输入，因为输入的内容保存到了粘贴板上了。



cmd and powershell  commit      有关单链表

jps   查看进程号

jmap  -histo:live "一串数字"  > c:\\\why.txt      debugger后，输出重定向，查看文件，instance，是否存在。

***

* 声明类的时候，类名开头要大写，虽然没有明确规定。
* Welcome   。







***

> 一个数能被3整除  ，也能被5  整除   ===                  能被15整除







##### IDEA   用法  和  快捷键

1. psvm    直接写出main方法

2. sout    打印 == System.out.println();

3. 在有返回值的方法后面输入`.sout`,直接输出，

`maxNum(a,b).sout` ==`System.out.println(maxNum(a,b))`

4. maxNum(a:23,b:23,c:345);

这样的格式，是在()内直接输入，数值，a，b，c表示的是该方法中的形参。

5. 调试的时候，打断点，蓝色的条，表示执行到当前代码，但还没有执行，

可以看下面的variables窗口。

6. shift + enter  换空行，下面
7. 对方法 查看原码 ， CTRL+左键。  类的话，查看jdk文档。
8. 注意：类名首字母**大写**，变量名首字母**小写**，都是用驼峰，一个小驼峰，一个大驼峰。
8. 黄色底色，是警告。

***

cmd命令：1.粘贴 ：光标选中，右键  ，再在想要复制的位置，右键，内容就被粘贴了。

​    shell:startup  开机启动项      %tmp%    清空缓存







###### cmd

assoc.bat = batfile   enter  恢复注册表默认设置。





###### 电脑快捷键：

Fn  + esc  是否使用辅助快捷键Fn



###### jdk文档的使用

返回值是  static  类型的，可以直接使用，不用，实例化对象 

比如：

```
int i = Marh.sqrt(x);
```

返回值 没有static 修饰的，必须要实例化对象

比如：

```
Scanner scan = new Scanner(System.in);
int num = scan.nextInt();
```





###### commit  javap -c TestDemo

java反汇编命令

```
int i = 2;
int j = 3;
```

<img src="D:\java学习\image\Javap -c commit.png" style="zoom:50%;" />

>对于int i= 2；首先会在栈中创建一个变量为i的引用，然后查找有没有字面值为2的地址，没找到，就开辟一个存放2这个字面量的地址，然后将i指向2的地址。

* ###### idea terminal 

* cd  转到路径。

可以转到java中，javac好像不用。

* javac 预编译，

javac -encoding utf8 有后缀的java文件。

* javap -c 文件名

java反汇编中的英文解释：

invokespeccial 标识调用了构造方法；

invokevirtual  表示调用了方法（非静态的fangfa)

后面都跟着解释；

在解释java运行时绑定，继承 的时候解释到了。
