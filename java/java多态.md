#### 多态



之前的继承是 is  a 

现在的多态，是  has  a



下面的是向上转型，不是多态

```java
class Animal {
    public String name;
    
    public void eat() {
        sout("Students：eat()");
    } 
    public Animal(String name) {
        this.name = name;
    }
}
class Cat extends Animal{
    public Cat(String name) {
        super(name);
    }
}
```

向上转型的三种用法:     直接赋值  返回值    参数

向上转型，父类引用子类的对象

1.  父类使用子类的方法，（只能访问父类的方法或者属性，如果有子类有额外的变量，不会调用它。）

```java
public class Main {
    public static void main(String[] args) {
        Animal animal = new Cat("小帕");//变量的类型，和开辟的空间类型不同
        
    }
}
```

> 向上转型 -- >  父类引用   引用子类对象。

2. 

```java
public class Main {
    public static void func(Animal animal) {//这里的参数。
           animal.eat();
    }
    public static void main(String[] args) {
        Cat cat = new Cat("小帕");
        func(cat);
    }
}
```

3. 返回值

```java
public class Main {
    
    public static Animal func() {//返回值
        /*
        Cat cat = new Cat("小帕");
        return cat;
        */
        return new Cat("小帕");
    }
    
    public static void main(String[] args) {
        Animal animal = func();
        animal.eat();
    }
}
```









##### 动态绑定

动态绑定，又叫 运行时绑定。

没发生在**预编译**的时候，

在**运行**的时候，发生。

使用javac 和javap 命令查看反汇编，

```java
class Animal {
    public String name;
    
    public void eat(){
        sout("Animal:eat()")
    }
    public Animal(String name) {
        this.name = name;
    }
}
class Cat extends Animal{
    public Cat(String name) {
        super(name);
    }
    public void eat() {
        sout("Cat:eat()");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Cat("小帕");
        animal.eat();
    }
}
//打印的是Cat:eat();
```



在发生运行时，绑定的时候，会发生重写操作。



运行时绑定：

父类引用     引用子类对象。同时，通过父类引用调用同名的覆盖的方法。

此时会发生运行时绑定。



***

与重载相当的重写，

重载：overload,再同一个类中。

方法名相同，参数列表不同（参数类型，个数）、返回值不做要求。

重写：override,再不同的类，有继承关系的。

方法名相同、参数列表相同、返回值**相同**

> 关于重写的注意事项：
>
> 1. 需要重写的方法，不能是被final修饰的。被final修饰后，方法就是密封的，不能被修改。
> 2. 被重写的方法，访问修饰符一定不能是private。
> 3. 被重写的方法，子类当中的访问修饰限定要 >= 父类的访问修饰限定。可以是protected and public
> 4. 被static修饰的方法是不可以被重写的。
>
> private < default < protected < public






> 误区：
>
> - [x] 在动态方法中可能会发生动态绑定。
>
> 解释：
>
> 父类
>
> ```java
> class Animal {
>     public String name;
> 
>     public void eat() {
>         sout("Animal:eat()");
>     }
>     public Animal(String name) {
>         this.name = name;
>         this.eat();
>     }
> 
> }
> class Cat extends Animal{
>     public Cat(String name) {
>         super(name);
>     }
>     public void eat() {
>         sout("Cat:eat()");
>     }
> }
> //向上转型的过程，在main方法中，
> //打印 
> //Cat:eat();
> //Cat:eat();
> ```
>
> > 上面的已经被重写了，
> >
> > 因为要子类要先帮父类构造，调用了父类的构造中的eat()，eat(),又被重写了，至此。打印了两遍的Cat:eat()；





* 向下转型

  父类的引用       赋值给了   子类

```java
  public static void main(String[] args) {
//        向下转型
        Animal animal = new Bird("小木");
        animal.eat();
//        animal.fly();//这里无法访问到子类的fly();
        Bird bird = (Bird)animal;
        bird.fly(); 
    }
```



不安全性：

父类的子类，多了，访问错了。cat和bird

```java
  public static void main(String[] args) {
//        向下转型
        Animal animal = new Cat("小木");
        animal.eat();
//        animal.fly();//这里无法访问到子类的fly();
        Bird bird = (Bird)animal;
        bird.fly();
    }
```

使用关键字instanceof判断

```java
public static void main(String[] args) {
    Animal animal = new Cat("小木");
    
    if(animal instanceof Bird) {
        Bird bird = (Bird)animal;
        bird.fly();
    }
}
```

* instanceof关键字   

  A    instanceof   B   判断A  是不是  B 的一个实例。

学到一个异常：

```java
ClassCastException     //类型转换异常。
```





### 多态



什么是多态：思想

1. 父类引用    引用子类对象
2. 父类和子类有同名的覆盖方法。
3. 通过父类引用这个重写方法的时候。多态发生了。



好处：多态能让类的调用者连这个类型是什么都不必知道，只需要知道这个对象具有某种方法即可。

```java
class Shape {
    public void draw() {
        //多态的使用
    }
}

class Cycle extends Shape {
    @Override
    public void draw() {
        System.out.println("⚪");
    }
}
class React extends Shape{
    @Override
    public void draw() {
        System.out.println("♦");
    }
}
class Flower extends Shape{
    @Override
    public void draw() {
        System.out.println("❀");
    }
}


public class TestDemo {
    public static void drawMap(Shape shape) {
        shape.draw();
    }
    public static void main(String[] args) {
        Shape shape1 = new Cycle();
        Shape shape2 = new React();
        Shape shape3 = new Flower();
        drawMap(shape1);
        drawMap(shape2);
        drawMap(shape3);
    }
}

```



```java
  public static void main(String[] args) {
        Shape[] shapes = {new Cycle(),new React(),new Cycle(),new React(),new React()};

        for(Shape shape: shapes) {
            shape.draw();
        }
    }
```





























