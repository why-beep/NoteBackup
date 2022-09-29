修改java数据类型 笔记

* 
  打印代码的不同。

* ```java
  int a = 10;
  System.out.println(a);//打印的是变量  换行    main
  System.out.print(a);//打印变量  不换行。
  System.out.printf("%d\n",a);//以格式化的形式进行输出内容，\n  才换行。
  ```

---

##### 变量的命名规范
* 标识符：数字、下划线、$

```java
int _a = 0;//ok  不支持
int __________a = 0;//不知道几个_。
/**/
int $a = 0;//ok,    也不支持
/**/
int 2a = 0;//err    编程错误。
```