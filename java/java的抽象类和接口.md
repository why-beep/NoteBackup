#### java的抽象类



抽象类：

1. 抽象方法：一个方法被abstract修饰，那么这个方法就是抽象方法。抽象方法可以没有具体的实现。
2. 包含抽象方法的类，抽象类。

注意：

1. 抽象类不可以被实例化。不能`Shape shape = new Shape();`
2. 类内的数据成员，和普通类没有区别。
3. 抽象类主要就是用来被继承的。就是向上转型。重写，多态。
4. 如果一个类继承了这个抽象类，那么这个类必须重写抽象类当中的抽象方法。    不是加`abstract`.或者说，不写方法的话，就加abstract
5. 当抽象类A 继承  抽象类B 那么A可以不重写B中的方法，但是一旦A要是被继承，那么一定要重写这个抽象方法。
6. 抽象类或者抽象方法，一定是不能是不能被final修饰的。





```java
abstract class Shape {
    public abstract void draw();
}
class Cycle extends Shape{
    public void draw() {
        System.out.println("hello");
    }
}
public class TestDemp {
    public static void main(String[] args) {
        Shape shape1 = new Cycle();
        shape1.draw();
    }
}

```









### 接口

接口是更进一步的抽象类，抽象类还能包括非抽象方法和字段，但**接口**中的方法都是抽象方法，字段了，只能包含静态常量。

```java
interface Shape {
    public static final int a = 10;
    public abstract void draw();
    //
    int b = 10;
//    void draw0();
}
class Cycle2 implements Shape,A{
    @Override
    public void draw(){
        System.out.println();
    }
}
interface A {
}

public class TestInterface {
    public static void main(String[] args) {
        Shape shape = new Cycle2();
    }
}
```

> 接口（interface）：
>
> 1. 接口当中的方法，都是抽象方法。
> 2. 其实可以有具体实现的方法，方法是被defult修饰的。（jdk1.8加入的）
> 3. 接口当中定义的成员变量，默认是常量。`public static final`int a = 10;
> 4. 接口当中的成员变量默认是：public static final    成员方法是：public abstract
> 5. 接口不可以实例化   Shape shape = new Shape();
> 6. 接口和类之间的关系 : implements
> 7. 接口的出现，为了解决java单继承的问题，可以实现多个接口。
> 8. 只要这个类  实现了该接口，那么你就可以进行想上转型了。

项目中一个接口一个类，new 新建。和创建java一样的。





多接口继承，

> 一个类可以继承一个普通类/抽象类，并且可以同时实现多个接口

```java
package com.bit.demo2;

/**
 * @anthor : why
 * @date : 2022/6/14 18:05
 * @description : some description
 */

interface Shape {
    public static final int a = 10;

    public abstract void draw();
    //
    int b = 10;
//    void draw0();
}

class Cycle2 implements Shape,A{
    @Override
    public void draw(){
        System.out.println();
    }
}
interface A {
}
class Animal {
    public String name;
    public void Animal(String name) {
        this.name = name;
        System.out.println("hello");
    }
}
class Cat1 extends Animal implements A,Shape{
    public void Cat(String name) {
        super.Animal(name);
    }
    public void draw() {
        System.out.println("world");
    }
}

public class TestInterface {
    public static void main(String[] args) {
        Shape shape = new Cycle2();
        shape.draw();

    }
}

```



接口使用实例：

给对象数组排序。

> art  +   insert     和     ctrl + O      快捷键的区别？





> ctrl + O  光标放在compareable后面，就会弹出弹窗。







##### Clonable接口和深接口

实现自定义类型的**深拷贝**,(深拷贝，创建自定义类型的副本)。

```java
class Person implements  Cloneable{
    public int age;
    
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
public class TestDemoDeepCopy {
    public static void main(String[] args) throws CloneNotSupportedException {
        Person person1 = new Person();
        Person person2 = (Person)person1.clone();

        System.out.println(person1.age);
        System.out.println(person2.age);
        person2.age = 10;
        System.out.println(person1.age);
        System.out.println(person2.age);
    }
}
```



* 创建对象中对象的副本

```java
class Money implements Cloneable{
    double money = 12.6;


    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
class Person implements  Cloneable{
    public int age;

    Money m = new Money();
    @Override
    protected Object clone() throws CloneNotSupportedException {
//        return super.clone();
        //克隆对象中的对象，对重写clone的方法。
        Person p = (Person)super.clone();
        p.m = (Money) this.m.clone();
        return p;
    }
}

public class TestDemoDeepCopy {
    public static void main(String[] args) throws CloneNotSupportedException {
        Person person1 = new Person();
        Person person2 = (Person)person1.clone();

        System.out.println(person1.m.money);
        System.out.println(person2.m.money);
        person2.m.money = 10;
        System.out.println(person1.m.money);
        System.out.println(person2.m.money);
    }
}
```





如果，想克隆自定义类型

1. 实现接口

   public interface Cloneable {   }

右键转到定义，发现是空接口，

空接口，也叫标记接口，只要一个类实现了这个接口，那么就标记这个类，可以进行clone的。

2. 重写clone方法，   - > Object

需要强制类型转换，art+enter，添加抛出错误，art + insert 重写 clone方法。





* 接口也可以，通过extends关键字来扩展（继承）其他接口。

```java
interface A {
    void fun1();
}

interface B {
    void fun2();
}

interface C extends A,B {
    void fun3();
}
class Test implements C {
    public fun3(){
        
    }
    public fun2() {
        
    }
    public fun1() {
        
    }
}
//Test 要实现的是三个方法。
```







> 接口和接口之间是扩展，类和接口之间是实现。





