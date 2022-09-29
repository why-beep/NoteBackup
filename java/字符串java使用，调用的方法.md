java的**字符**串使用，调用的方法

###### 比较字符串是否相等

字符串名.equals(与之比较的字符串)；

> 若是不区分大小写，用到的方法是："Hello".equalsIgnoreCase("hello");
>
> ==  是比较两个字符串是否在相同的位置上，
>
> 3. 只有字符串常量，通过==比较是相等的，共享的。

```java
 public static void main(String[] args) {
        //字符串拼接
        String a = "hello";
//        a.append()
        StringBuilder builder = new StringBuilder();
        builder.append("hello");
        builder.append(" why");
        System.out.println(builder);
    }
```



读取密码的类；