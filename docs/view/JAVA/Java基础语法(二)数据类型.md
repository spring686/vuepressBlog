---
title: 'JAVA后端开发'
date: 2021-08-30 14:16:23
tags:
- '专业课'
categories:
- 'JAVA后端'
# 时间线
isTimeLine: true
# 导航
# sidebar: false
# 是否允许评论
isComment: false
# 指定禁用 侧边栏
# subSidebar: true
---


# Java基础语法（二）----数据类型

内容大纲![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401193139197.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



## 一，int整型类型

#### 1，基本语法格式

```
int 变量名 = 初始值;
```

代码示例：

```
int num = 10; // 定义一个整型变量
System.out.println(num) ;
```



#### 2，数值范围

nt 能够表示的范围是多大？

  在C语言中，有 有符号数 和 无符号数 ，但是记住了，在Java 中没有所谓的无符号数！

  我们看一下 int 表示的范围

  在 Java 中 int 占 4个字节 ，32个 bit 位，最高位是符号位，剩下的31位全是 数值位 。



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331203134689.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



使用以下代码查看 Java 中的整型数据范围:

public class Test {

    public static void main(String[] args) {
        System.out.println(Integer.MAX_VALUE);
        System.out.println(Integer.MIN_VALUE);
    
    }
}



编译结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220644235.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331204104780.png)

所以验证了 int 的 最大值为 2 ^ 31-1 , 最小值 为 - 2 ^31.(约-21亿——21亿)

  那么不禁有同学问了，如果我们想要打印一个Max+1，Min-1的值，打印出来的结果是什么呢？

 public static void main(String[] args) {

        System.out.println(Integer.MAX_VALUE + 1);
    
        System.out.println(Integer.MIN_VALUE - 1);
    
    }

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220727152.png)



Max +1的值= - 2 ^ 31

Min -1的值 =2^31 +1

为什么出现这样的结果呢？

首先 int 的数值范围表示是这样的：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401180818671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

所以当 int = Max_value + 1 时，正数变成负数

这个结论适合于所有的类型（小数 float double 除外）



#### 3.未定义时变量的默认初始值

**当变量未定义大小时，没有默认值**…

  当我们未定义变量是多少，打印这个变量的数值时候，Java 的编辑器会直接报错，这就体现了Java的安全性。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331203645388.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021033120365255.png#pic_center)

如果运算的结果超出了 int 的最大范围, 就会出现溢出的情况。21亿这样的数字对于当前的大数据时代来说, 是很容易超出的.

   针对这种情况, 我们就需要使用更大范围的数据类型来表示了。 Java 中提供了 long 类型来存储更大的数字。



#### 4.注意事项

```
（1）int 表示变量的类型是一个整型
```

```
（2） 变量名是变量的标识. 后续都是通过这个名字来使用变量
```

```
（3） Java 中 = 表示赋值(和数学不一样), 意思是给变量设置一个初始值.
```

```
（4） 初始化操作是可选的, 但是建议创建变量的时候都显示初始化.
```

```
（5） 最后不要忘记分号, 否则会编译失败.
```

```
（6） // 表示注释. 注释作为代码的解释说明部分, 不参与编译运行.
```



## 二，long长整型类型

### 1.基本语法格式

```
long 变量名 = 初始值;
```

代码示例：

```
long num = 10L; // 定义一个长整型变量, 初始值写作 10l 也可以(小写的 L, 不是数字1). 
System.out.println(num) ;

```

### 2.数值范围


long 在C语言中占4 个字节 ，但是在 Java 中占据 8 个字节。

所以 long 范围大小是

```
–2 ^ 63 ——2 ^ 63 - 1
```

我们根据 Java 的代码看一下具体的数值

```
 public static void main(String[] args) {
        System.out.println(Long.MAX_VALUE);
        System.out.println(Long.MIN_VALUE);
    }

```

打印结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220417933.png)

 8个字节，总之是一个足够大的数字。这个数据范围远超过 int 的表示范围. 足够绝大部分的工程场景使用.



### 3.long 定义变量

```
public static void main(String[] args) {
       // System.out.println(Long.MAX_VALUE);
       // System.out.println(Long.MIN_VALUE);

        long a=10L;
        System.out.println(a);
    }

```

### 4.注意事项

```
（1） 基本语法格式和创建 int 变量基本一致, 只是把类型修改成 long
```

```
（2）初始化设定的值为 10L , 表示一个长整型的数字. 10l 也可以.
```

```
（3）使用 10 初始化也可以, 10 的类型是 int, 10L 的类型是 long, 使用 10 L 或者 10 l 更好一些.
```

```
（4）Java 中 long 类型占 8 个字节. 表示的数据范围 -2^ 63 -> 2 ^ 63-1
```



## 三，double 双精度浮点数类型

Java 中的 double 是 8 个字节

### 1.基本语法类型

```
double 变量名 = 初始值;
```

代码示例：

```
double num = 1.0;
System.out.println(num)

```



### 2.double 定义变量

**代码一：**

```
public static void main(String[] args) {
        double num=12.5;
        System.out.println(num);
    }
   
```

代码编译效果![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220333635.png)

成功打印出 double num 的变量值 



**代码二：**

```
    public static void main(String[] args) {

        int a=1;
        int b=2;
        System.out.println(a/b);

    }
```

代码编译效果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220219343.png)

打印的结果为0， 两个 int 相除 ，得到的结果 也是 int 类型，所以 a/b 的结果等于0

  在 Java 中, int 除以 int 的值仍然是 int(会直接舍弃小数部分).

  如果想得到 0.5, 需要使用 double 类型计算.

```
public static void main5(String[] args) {

        double a = 1.0;
        double b = 2.0;
        System.out.println(a / b);

    }

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331222320770.png)



代码三：

```
 public static void main(String[] args) {
        double c=1.1;
        double d=1.1;
        System.out.println(c*d);
    }

```



代码编译效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210331220304122.png)

 我们知道 1.1 * 1.1 = 1.21，那么为什么结果出现了 1.210000…2呢？最后一位的2 从何而来？

  好的，这是由于 double 自身精度的问题，小数是没有精确的数字的。

  Java 的 double 类型的内存布局遵守 IEEE 754 标准(和C语言一样), 尝试使用有限的内存空间表示可能无限的小数, 势必会存在一定的精度误差.


## 四、float 单精度浮点数类型



### 1.基本语法格式

```
float 变量名 = 初始值;
```

```
  public static void main(String[] args) {
        float f=3.5f;
        System.out.println(f);
    }

```

编译结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401085633135.png)



### 2.float 定义变量

如果我们给 float 定义一个变量 f=3.5，我们来看结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401085745487.png)





![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401091834226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)



  在C 语言中我们3.5 是可以赋给 float 类型的变量的，为什么在Java中会进行报错呢？

  这里我们就要普及一个知识点：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401091440298.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

在 Java 当中 3.5、12.5、3.14 这些小数默认是 double 类型的，我们用 float 类型的变量接收，编译就会不通过 。我们在小数的后面加上一个f，强调这个数字是 float 类型的，这样编译就会通过了。

```
 public static void main(String[] args) {
        float f=3.5f;
        System.out.println(f);
    }

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401091808559.png)





## 五、char 字符类型

 在Java 中 ，char 类型的变量在内存中占 2 个字节

### 1.基本语法格式

```
char 变量名 = 初始值;
```

代码表示：

```
public static void main(String[] args) {
        char ch='a';
        System.out.println(ch);
    }


```

编译结果![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401093020510.png)



### 2.char 定义变量

代码一：

```
public static void main(String[] args) {
        char ch='a';
        System.out.println(ch);
    }

```

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401093020510.png)



**代码二**：

```
 public static void main(String[] args) {
        char ch='陈';
        System.out.println(ch);
    }

```

编译结果![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401093230245.png)



 我们可以用 char 类型 来定义一个 汉字



**代码三：**

```
 public static void main(String[] args) {
        char ch=97;
        System.out.println(ch);
    }

```

编译结果![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401093347535.png)

 我们可以给char 类型定义一个数字，编译的结果是在 Unicode 中相对应的 字符。



**代码四：**

```
 public static void main(String[] args) {
        char ch=-10;
        System.out.println(ch);
    }

```

编译结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401093607397.png)



![在这里插入图片描述](https://img-blog.csdnimg.cn/202104010937255.png)

  我们知道 C语言中 可以用数字来表示相应的英文字符、常用字符，这张表就是ASCII表

  与之相对应的是 Java 中也有这样的表格，叫做 Unicode ，他表示的字符范围更大，可以说包含了ASCII的范围。

  但是，他们的共同点就是 字符与数字对应的起始都是从0开始的，没有负数表示的字符。

  所以 Java 当中的 char 表示的一定是正数

### 3.注意事项

```
（1） Java 中使用 单引号 + 单个字母 的形式表示字符字面值.
```

```
（2） 计算机中的字符本质上是一个整数. 在 C 语言中使用 ASCII 表示字符, 而 Java 中使用 Unicode 表示字符. 因此一个字符占用两个字节, 表示的字符种类更多, 包括中文.
```



## 六、byte 字节类型

**代码一：**

```
public static void main(String[] args) {
        byte a=10;
        System.out.println(a);
    }
```

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401102426888.png)

我们给 a 赋值为 10，编译打印10.



**代码二：**

```
public static void main(String[] args) {
        byte a=128;
        System.out.println(a);
    }

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401102537511.png)

​        我们将 128 赋给 byte 类型的变量，但是发现编译时报错，说明什么？

  赋值的时候，不能给当前赋值范围外的数字，否则会报错。包括 int 类型也是这样。



**代码三：**

```
public static void main(String[] args) {
      byte b1=10;
      byte b2=20;
      byte b3=b1+b2;
        System.out.println(b3);
    }

```

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040110322926.png)

 有同学不仅问了: b1+b2=30,没有超过byte 的范围啊，为什么还会报错呢？

说明：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401104239101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

### 注意事项

```
（1）字节类型表示的也是整数. 只占一个字节, 表示范围较小 ( -128 -> +127 )
```

```
（2）字节类型和字符类型互不相干.
```



## 七、数值提升

 在上面介绍byte 类型的时候，我们提到了整型提升，那么我们来了解一下具体的提升规则吧！

  详细的整型提升规则请到我的往期博客——[隐式类型转换之整型提升](https://blog.csdn.net/rain67/article/details/113874311?spm=1001.2014.3001.5501)了解



### 1.int 和long混合运算

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401111240703.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

结论:

  当 int 和 long 混合运算的时候, int 会提升成 long, 得到的结果仍然是 long 类型, 需要使用 long 类型的变量来接收结果. 如果非要用 int 来接收结果, 就需要使用强制类型转换.

类型提升的意义： 加快了计算机 CPU 计算运行的速度

**强转后：**![image-20210621185927948](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621185927948.png)



### 2.byte 和 byte 的运算

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040111165686.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)



结论

  byte 和 byte 都是相同类型, 但是出现编译报错. 原因是,虽然 a 和 b 都是 byte, 但是计算 a + b 会先将 a 和 b 都提升成 int, 再进行计算, 得到的结果也是 int, 这时赋给 c, 就会出现上述错误.

  由于计算机的 CPU 通常是按照 4 个字节为单位从内存中读写数据. 为了硬件上实现方便, 诸如 byte 和 short 这种低于4 个字节的类型, 会先提升成 int, 再参与计算.

  正确的写法：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401112031894.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)



### 3.小结

**类型提升小结**

```
（1）不同类型的数据混合运算, 范围小的会提升成范围大的.
```

```
（2） 对于 short, byte 这种比 4 个字节小的类型, 会先提升成 4 个字节的 int , 再运算.
```



## 八.short 短整型类型

### 1.基本语法格式

```
short 变量名 = 初始值;
```

代码示例：![image-20210621192107921](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621192107921.png)



### 2.数值范围

在Java 中 short 占2 个字节， 16个bit位

所以他表示的数值范围就是

```
-32768 -> +32767
```



### 3.注意事项

```
（1）short 占用 2 个字节, 表示的数据范围是 -32768 -> +32767
```

```
（2）这个表示范围比较小, 一般不推荐使用.
```



## 九，Boolean 布尔类型

boolean 在Java和 C++ 中有这种类型，在C语言中没有该类型

### 1.基本语法格式

```
boolean 变量名 = 初始值;
```

代码示例：

```
 public static void main(String[] args) {
        boolean value = true;
        System.out.println(value);
    }

```



### 2.注意事项

```
（1） boolean 类型的变量只有两种取值, true 表示真, false 表示假.
```

```
（2）Java 的 boolean 类型和 int 不能相互转换, 不存在 1 表示 true, 0 表示 false 这样的用法.
```

```
（3）boolean 类型有些 JVM 的实现是占 1 个字节, 有些是占 1 个比特位, 这个没有明确规定.
```

**代码一**![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401174609961.png)

编译结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401174641524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

所以 int 和 boolean 是两种毫不相干的类型，不能进行运算



**代码二**![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401175417484.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401175506536.png)



将0，1 赋给 boolean 类型，则编辑器会报错

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401175254373.png#pic_center)

### 基本数据类型总结

| 数据类型 | 包装类    | 字节         |
| -------- | --------- | ------------ |
| int      | Integer   | 4            |
| short    | Short     | 2            |
| char     | Character | 2            |
| byte     | Byte      | 1            |
| long     | Long      | 8            |
| float    | Float     | 4            |
| double   | Double    | 8            |
| boolean  | Boolean   | 没有明确规定 |



## 十，String 字符串类型

把一些字符放到一起就构成了字符串

### 1.基本语法格式

```
String 变量名 = “初始值”;
```

代码示例:

```
 public static void main(String[] args) {
        String name = "zhangsan";
        System.out.println(name);
    }


```

编译结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401181135822.png)



### 2.注意事项

```
（1）Java 使用 双引号 + 若干字符 的方式表示字符串字面值.
```

```
（2） 和上面的类型不同, String 不是基本类型, 而是引用类型(后面重点解释).
```

```
（3）字符串中的一些特定的不太方便直接表示的字符需要进行转义.
```



### 3.转义字符

| 转义字符 | 解释       |
| -------- | ---------- |
| \n       | 换行       |
| \t       | 水平制表符 |
| ’        | 单引号     |
| "        | 双引号     |
| \        | 反斜杠     |

还有很多，目前先介绍这些转义字符…



### 4.字符串常见操作

#### （1） + 操作, 表示字符串拼接

**代码一**

```
   public static void main(String[] args) {
        String a = "hello";
        String b = "world";
        String c = a + b;
        System.out.println(c);
    }

```

编译结果如下：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401182457869.png)



#### （2）+可用字符串和整数进行拼接（2）+可用字符串和整数进行拼接

**代码二**：

```
    public static void main(String[] args) {
        String str = "result = ";
        int a = 10;
        int b = 20;
        String result = str + a + b;
        System.out.println(result);
    }

```

编译结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401182655827.png)



#### （3）小结

 以上代码说明, 当一个 + 表达式中存在字符串的时候, 都是执行字符串拼接行为.

  因此我们可以很方便的使用 System.out.println 同时打印多个字符串或数字.



## 十一，变量

### 1，变量的作用域

作用域就是该变量能生效的范围，一般是变量定义所在的代码块（大括号）

**代码一：**

```
 public static void main(String[] args) {

        int x = 10;
        System.out.println(x); // 编译通过;
    }

```

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401183126972.png)

成功打印出10



**代码二：**

```
    public static void main(String[] args) {

        {
            int x = 10;
            System.out.println(x); // 编译通过;
        }
        System.out.println(x);
    }

```

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401183259699.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

 此时x被定义在局部的代码块里，出了该局部范围后，x被销毁，所以第二次打印x编译未通过。



**改正后的代码：**

```
    public static void main(String[] args) {

        {
            int x = 10;
            System.out.println(x); // 编译通过;
        }
        int x=5;
        System.out.println(x);
    }

```

编译结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401183504958.png)

编译通过，打印出两个x 的值：10 、5



### 2，变量的命名规则

#### （1）命名的规则

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401185409739.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

### （2）软性要求

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401185540792.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

### （3）小驼峰命名规则

 当一个变量名由多个单词构成的时候, 除了第一个单词之外, 其他单词首字母都大写.

命名示例：

```
int maxValue = 100;
```

```
String studentName = “张三”;
```



## 十二，常量

上面讨论的都是各种类型的变量, 每种类型的变量也对应着一种相同类型的常量.

  常量指的是运行时类型不能发生改变.

  常量主要有以下两种体现形式:

### 1.字面值常量

| 10    | **int 字面值常量(十进制)**                                   |
| ----- | ------------------------------------------------------------ |
| 010   | int 字面值常量(八进制) 由数字 0 开头. 010 也就是十进制的 8   |
| 0x10  | int 字面值常量(十六进制) 由数字 0x 开头. 0x10 也就是十进制的 16 |
| 10L   | long 字面值常量. 也可以写作 10l (小写的L)                    |
| 1.0   | double 字面值常量. 也可以写作 1.0d 或者 1.0D                 |
| 1.5e2 | double 字面值常量. 科学计数法表示. 相当于 1.5 * 10^2         |
| 1.0f  | float 字面值常量, 也可以写作 1.0F                            |
| true  | boolen 字面值常量, 同样的还有 false                          |
| ‘a’   | char 字面值常量, 单引号中只能有一个字符                      |
| “abc” | String 字面值常量, 双引号中可以有多个字符                    |



### 2.final关键字修饰的常量

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401184726200.png)



编译结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401184749680.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

 Java 中的 final 类似与 C 语言中的 const ，使得修饰的变量变成了常变量，常量不能在程序运行过程中发生修改.



## 十三，类型转换

 Java 作为一个强类型编程语言, 当不同类型之间的变量相互赋值的时候, 会有较严格的校验

  我们通过下面几个代码来了解数据的类型转换：

### 1.int 和 long/double 相互赋值

**代码一：**![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401185841142.png)

long 表示的范围更大, 可以将 int 赋值给 long, 但是不能将 long 赋值给 int.



**代码二：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401185932276.png)



 double 表示的范围更大, 可以将 int 赋值给 double, 但是不能将 double 赋值给 int.

**结论：**

   不同数字类型的变量之间赋值, 表示范围更小的类型能隐式转换成范围较大的类型, 反之则不行.



### 2.int 和 boolean 相互赋值

**代码：**![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401190155816.png)

**结论**: int 和 boolean 是毫不相干的两种类型, 不能相互赋值.



### 3.int 字面值常量 给 byte 赋值

**代码如下：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401190352412.png)

**注意**: byte 表示的数据范围是 -128 -> +127, 256 已经超过范围, 而 100 还在范围之内.

**结论**: 使用字面值常量赋值的时候, Java 会自动进行一些检查校验, 判定赋值是否合理.



### 4.强制类型转换

如何使用强制类型转换?

代码一示例：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401190811350.png)



编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401190826601.png)



 结果成功编译，使用强制类型转换，将int 类型的数据转换为 byte，使得a的值可以赋给 b.



**代码二：**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401191033943.png)

编译结果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210401191100654.png)

  所以我们得知，并不是所有类型的数据都可以强制类型转换。

结论：![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040119141965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

### 5.小结

```
（1）不同数字类型的变量之间赋值, 表示范围更小的类型能隐式转换成范围较大的类型.
```

```
（2）如果需要把范围大的类型赋值给范围小的, 需要强制类型转换, 但是可能精度丢失.
```

```
（3）将一个字面值常量进行赋值的时候, Java 会自动针对数字范围进行检查.
```



 最后，我们将强制类型转换和隐式类型转换联系在一起，看一下两者的区别：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040119245969.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

# Java基础语法（三）——运算符





#### 六，关键字

![img](https://img-blog.csdnimg.cn/20210403161705613.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)







# Java基础语法（四）——程序逻辑控制



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210407200252592.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

## 一.选择结构

#### 1. if 语句

##### （1）基本书写格式

```
书写格式一
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210407203501761.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

```
书写格式二
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210407203813882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

```
书写格式三-----多分支的情况
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210407220424980.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

##### （2）练习

###### 练习一

题目要求：

```
判断奇偶数
```

代码实现：![image-20210614110809637](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614110809637.png)

编译实现效果![image-20210614110853346](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614110853346.png)

###### 练习二

```
判定一个数字是正数还是负数
```

代码实现

![image-20210614111231050](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614111231050.png)

编译结果![image-20210614111252550](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614111252550.png)



###### 练习三

```
判定某一年份是否是闰年
```

代码实现![image-20210614113210898](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614113210898.png)

编译效果![image-20210614113228433](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614113228433.png)

##### （3）注意事项

###### 1.悬垂else问题

```
int x = 10;
int y = 10;
if (x == 10) 
   if (y == 10)
   System.out.println("aaa");
else
 System.out.println("bbb");
```

  if 后面可以不加上大括号，但是只能执行跟在其后面的一条语句，在这个代码中，我们视觉的看到 else 和第一个 if 相匹配 ， 但是 在不加大括号的情况下，else 只和 最近的 if 相匹配.


  还有，为了避免出现自己的判断错误，尽量在需要加大括号的语句全部加上大括号（不要省略）.



###### 2.代码风格问题

```
// 风格1
      int x = 10;
      if (x == 10) {
          // 满足条件
      } else {
          // 不满足条件
      }


// 风格2
      int x = 10;
      if (x == 10) {
          // 满足条件
      }
      else
      {
          // 不满足条件
      }

```

 在 Java 中尽管两种代码风格都是合法的，但是Java还是更推荐 风格1

  { 放在 if / else 同一行.

###### 3.分号问题

```
    int x = 20;
      if (x == 10); {
      System.out.println("hehe");
      }
   // 运行结果
    hehe
```

  我们可以看到在if（）之后不小心加上了；，在此处多写了一个 分号, 导致分号成为了 if 语句的语句体, 而 { } 中的代码已经成为了和一个 if 无关的代码块.

  这样的错误我们要尽量避免.



#### 2.switch...case语句

##### （1）基本语法

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408000301878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

##### （2）代码示例

```
int day = 1;
switch(day) {
    case 1:
        System.out.println("星期一");
        break;
    case 2:
        System.out.println("星期二");
        break;
    case 3:
        System.out.println("星期三");
        break;
    case 4:
        System.out.println("星期四");
        break;
    case 5:
        System.out.println("星期五");
        break;
    case 6:
        System.out.println("星期六");
        break;
    case 7:
        System.out.println("星期日");
        break;
    default:
        System.out.println("输入有误");
        break; }


```

根据 switch 中值的不同, 会执行对应的 case 语句. 遇到 break 就会结束该 case 语句.

如果 switch 中的值没有匹配的 case, 就会执行 default 中的语句.



代码实现效果：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408190454140.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

我们建议一个 switch 语句最好都要带上 default.且default的位置不固定.

##### （3）注意事项

###### 注意事项1

```
break 不要遗漏, 否则会失去 “多分支选择” 的效果
```

代码示例：

```
public static void main(String[] args) {
        int day = 1;
        switch(day) {
            case 1:
                System.out.println("星期一");

            case 2:
                System.out.println("星期二");

            case 3:
                System.out.println("星期三");

            case 4:
                System.out.println("星期四");

            case 5:
                System.out.println("星期五");

            case 6:
                System.out.println("星期六");

            case 7:
                System.out.println("星期日");

            default:
                System.out.println("输入有误");
                 }
    }

```

实现效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408190708245.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



###### **注意事项2**

```
switch 中的值只能是 整数|枚举|字符|字符串
```

之前我们的代码示例switch（）中跟的都是 int 类型的数据

那么switch（）中的值可以是其他类型吗？

我们对其它类型的数据进行试验…

```
long
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408191658126.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

所以 switch （）中的数据不能是 long 类型



```
float
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408191415300.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

所以 switch （）中的数据不能是 float 类型



```
double
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408191834691.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

所以 switch （）中的数据不能是 double 类型



```
char
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408192100628.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408192111421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

switch（）中可以是 char 类型的数据



```
String
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408193516594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

代码实现效果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408193545167.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

所以 switch（）中的数据可以是 String 类型的.

总之，switch 中的值只能是 **整数|枚举|字符|字符串.**

###### 注意事项3

```
switch 不能表达复杂的条件
```

如果是这样的代码：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408193915913.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

这样的题目条件，明显使用 if 语句表达更为方便 ， 使用 switch 语句则无法表示.



## 二，循环结构

**循环中的关键字**

```
break
```

功能：  break 的功能是让循环提前结束，执行到 break 就会让循环结束，直接跳出循环



```
continue
```

功能：  continue 的功能是跳过这次循环, 立即进入下次循环.



#### 1.while循环语句

##### （1）基本语法格式![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408195033682.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

##### （2）练习

###### 练习一

题目要求：

```
打印 1 - 10 的数字
```

代码实现![image-20210614192721750](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614192721750.png)

实现效果![image-20210614192740046](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614192740046.png)



###### 练习二

题目要求

```
计算1--100的和
```

代码实现![image-20210614194324694](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614194324694.png)

实现效果

![image-20210614194340252](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210614194340252.png)





##### （3）注意事项

```
do while 循环最后的分号不要忘记
```

```
一般 do while 很少用到, 更推荐使用 for 和 while.
```



## 三，输入输出的表示

### 1.输出到控制台

#### （1）基础语法

```
`System.out.println(msg);` 输出一个字符串, 带换行
```

```
`System.out.print(msg);` 输出一个字符串, 不带换行
```

```
`System.out.printf(format, msg);` 格式化输出
```



####  (2) 注意点

```
println 输出的内容自带 \n, print 不带 \n
```

```
printf 的格式化输出方式和 C 语言的 printf 是基本一致的.
```



#### （3）格式化输出


什么是格式化输出？

将数据按以下类型（部分）进行输出：

| 转换符 | 类型         | 举例         |
| ------ | ------------ | ------------ |
| d      | 十进制整数   | ( “%d” ,10)  |
| x      | 十六进制整数 | ("%x", 100)  |
| f      | 单精度浮点数 | ("%f",100.0) |
| s      | 字符串       | ("%s",“abc”) |
| c      | 字符         | ("%c",‘1’)   |

  我们只是将部分格式化的数据列举出来，具体的格式化类型请大家自行查找.这种格式化打印在C语言中十分常见.

### 

### 2.从键盘输入

### （1）使用Scanner读取字符串/整数/浮点数

首先我们需要导入util包

```
import java.util.Scanner; *// 需要导入 util 包*
```

```
从键盘输入一个整形：
```

![image-20210616190032735](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190032735.png)

实现效果![image-20210616190056039](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190056039.png)



这里的 nextunt 是读取一个整形

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408214257447.png)

```
从键盘输入一个字符串
```

![image-20210616190413583](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190413583.png)

实现效果![image-20210616190430504](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190430504.png)

 这里的 nextline —— 是输入一行，且遇到空格不会中止读取

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408214320976.png)



```
从键盘输入一个浮点数：
```

![image-20210616190602370](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190602370.png)



实现效果：![image-20210616190620071](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210616190620071.png)

  这里的 nextDouble 是输入一个双精度浮点数 .

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408214639961.png)

### （2）使用Scanner 循环读取N个数字

代码实现：![image-20210621083428258](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621083428258.png)

实现效果：

![image-20210621083440178](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621083440178.png)

我们实现多组输入数字，最后ctrl + D 停止循环.

下面是hasNext 的具体使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040821515113.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)



### Java输入的建议

根据个人信息，输入输出如下：

![image-20210621085241488](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621085241488.png)

输入的类型依次是  字符串  整形  浮点型

实现效果![image-20210621085516481](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621085516481.png)





好，我们第二次改变输入类型的顺序.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408230619397.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

这次我们在输入时却碰到了一个问题…![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408230703674.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

  我们在输入整形数据18以后，按下回车，发现直接跳到了输入浮点型数据的内容，字符串类型直接跳过了，这样的输入就存在了问题.

  我们可以当作 把在输入整形后 的回车 当成了 输入字符串类型的内容，所以跳过了输入字符串.

  所以 对于 Java 的输入我们建议：**把输入字符串放在最前面，字符串的前面不要输入**


## 四，猜数字游戏

游戏规则:

```
系统自动生成一个随机整数(1-100), 然后由用户输入一个猜测的数字. 如果输入的数字比该随机数小, 提示 “低 了”, 如果输入的数字比该随机数大, 提示 “高了” , 如果输入的数字和随机数相等, 则提示 “猜对了”


```

### 1.编写过程

下面是Random的使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408220119288.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210408215635243.png)

 好了，我们熟悉了Random 的使用，这个游戏我们首先要生成一个 在 0-100范围内的随机数

#### （1）生成随机数字

```
//生成随机数字
 Randnum randNum = new Random();
 int randNum = Randdom.nextInt(100);

```

#### （2）输入你要猜的数字

```
    Scanner scanner = new Scanner(System.in);
     int num = scanner.nextInt();

```

#### （3）循环结构，进行数字比较

```
  将你猜的数字与随机数比较，如果猜小了，打印“你猜小了”，猜大了，打印“你猜大了”，猜对了，打印“你猜对了”，然后跳出循环. 没有猜对则一直比较.
```

我们用while（true）来一直循环,当num== randNum 时 break跳出循环.



```
  Scanner scanner = new Scanner(System.in);

 while(true){
            System.out.print("请输入要猜的数字:>");
            int num = scanner.nextInt();
        if(num<randNum){
            System.out.println("你猜小了");
        }else if(num>randNum){
                System.out.println("你猜大了");
        }else{
            System.out.println("你猜对了");
            break;
        }
 }

```

### 2.完整代码实现

![image-20210621093505360](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621093505360.png)



实现效果

![image-20210621093731519](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621093731519.png)

![image-20210621093756798](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210621093756798.png)





# Java基础语法（五）——方法的使用

内容大纲

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210413122449686.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

## 一. 方法的基本用法

### 1. 什么是方法(method)

方法 其实就是把一个重复的东西进行封装，把他封装成了一个功能了。

**方法存在的意义**（不要背，重在体会）

```
1.是能够模块化的组织代码（当代码规模比较复杂的时候）。
```

```
2.做到代码被重复使用，一份代码可以在多个位置使用.
```

```
3.让代码更好理解更简单。
```

```
4.直接调用现有方法开发。不必重复造轮子
```



### 2.方法定义语法

#### （1）方法的基本语法

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412221633341.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

#### （2）方法的调用

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412221731773.png)

代码示例：

求1-100之间的和

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412223027708.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412223105401.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



  我们看到，成功的调用了方法的内容，同时接收了方法的返回值。

  在这个代码练习中，我们知道了方法的基本语法及其调用。



#### （3）Java内存架构

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412223941745.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



 我们对方法的调用，是依赖于栈的

  每次调用一个方法，都会在栈上为这个方法开辟一个内存。把这个内存叫做：栈帧.

  以上面的代码为例，介绍一下方法在内存中的存放.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412225652347.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

 首先调用的方法是main方法，那么此时在内存中会开辟一块main的栈帧，此时在main里创建了一个ret变量，在main的内存中就存放了ret的空间.


  此时再调用add方法，再次开辟一个栈帧，形参为n，存放n的空间，往下走 创建了一个sum 的变量，在存放一个sum的空间，进入循环有创建了一个 i 的变量.

  此时栈空间的存放情况：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412225217574.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



add方法return结束语句，调用完毕后，出栈.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412225350723.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

main方法语句执行完毕，出栈.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412225446566.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

这就是一个完整的方法调用过程.



### 3.方法调用的执行过程

**基本规则**

```
1.定义方法的时候，不会执行方法的代码，只有调用的时候才会执行
```

```
2.当方法被调用的时候，会将实参赋值给形参
```

```
3.参数传递完毕后，就会执行到方法体代码
```

```
4.当方法执行完毕之后（遇到return语句），回到方法调用位置继续往下执行
```

```
5.一个方法可以被多次调用
```



### 4.实参和形参的关系（重要）

什么实参？什么形参？

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412231352157.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



我们通过一个练习来知道传参的使用.

题目要求：用方法来交换两个整形.

我们看一下下面的代码是否正确.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412231942575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

看似过程是正确的，我们看一下编译结果.

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021041223220788.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

并没有进行交换，那是为什么呢？


  我们知道，我们传的是实参的值，但是形参只是实参的一份拷贝，所以在swap方法中，我们只是交换的是 x,y 这两个形参的值，swap方法调用完毕后两个形参的值自动被销毁，所以实参的值不变.


  在C语言中，我们要想通过函数来交换两个整形的值，需要进行&其地址操作


  但是我们明确说明：

```
1.Java中 没有&取地址符号
```

```
2.Java当中 栈上的内存地址是无法取到的
```

```
3.Java中方法传参只能进行值传参，不能像C语言进行址传参.
```



 那么在Java中如何实现传地址操作呢？

  答案是传引用，只要是引用类型就可以，类、接口、抽象类、枚举、String、数组等…

  具体使用我们会在之后更新的博客中继续提到.



**传参时实参与形参的注意事项**：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412234848631.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



如上图所示：

1.参数的个数、类型、顺序都要一 一匹配.

2.方法的返回值类型与接受类型也要一 一对应.



## 二，方法重载

  有些时候我们需要用一个函数同时兼容多种参数的情况, 我们就可以使用到方法重载.



### 1.重载要解决的问题

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412235849283.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



  我们希望在向add方法传入两个double 类型的变量，实现浮点数的加法.

  但是编译结果：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210413000012963.png)



 我们只能将代码修改为

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021041300025548.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



 这两个方法实现的都是同一种功能，将两个数据进行加法运算.我们对不同的数据还得创建不同类型的函数，这样是不是过于麻烦，所以在Java中就有了方法重载的概念：用一个函数同时兼容多种参数.



### 2.使用重载

 还是对于上面的代码进行修改：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210413000844166.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

  方法的名字都叫 add. 但是有的 add 是计算 int 相加, 有的是 double 相加; 甚至有的计算两个数字相加, 有的还可以是计算三个数字相加.



  同一个方法名字, 提供不同版本的实现, 称为 方法重载



### 3.重载的规则

**规则**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210413001233166.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

看下面两个代码：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210413001318619.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)

 通过这两个代码的例子，我们可以知道在Java编辑器看来，sum 的两个方法仍然是两个相同的方法，因为其参数列表相同.所以会进行报错，所以返回值对方法的重载没有影响.



## 三，方法递归

### 1.递归的概念

 一个方法在执行过程中调用自身, 就称为 “递归”.

  递归相当于数学上的 “数学归纳法”, 有一个起始条件, 然后有一个递推公式.

  递归的注意点：![在这里插入图片描述](https://img-blog.csdnimg.cn/20210412210532437.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70)





```
1.程序调用自己
```

```
2.这个递归程序一定用一个趋近于中止的条件
```

```
3.核心：写递归程序的时候，需要自己来推导一个递推公式
```



例：

我们求 N!

起始条件: N = 1 的时候, N! 为 1. 这个起始条件相当于递归的结束条件.

递归公式: 求 N! , 直接不好求, 可以把问题转换成 N! => N * (N-1)!

代码实现：![image-20210622191305219](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210622191305219.png)



### 2.递归执行过程分析

 递归的程序的执行过程不太容易理解, 要想理解清楚递归, 必须先理解清楚 “方法的执行过程”, 尤其是 “方法执行结束之后, 回到调用位置继续往下执行”.





# Java基础语法（六）——数组的定义与使用

内容介绍大纲

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417134558236.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

## 一，数组基本用法

### 1.什么是数组

数组本质上就是让我们能 “批量” 创建相同类型的变量



例如：

```
如果需要表示两个数据，那么直接创建两个变量即可 int a; int b
```

```
 int a = 10;
 int b = 20;
```



```
如果需要表示五个数据, 那么可以创建五个变量 int a1; int a2; int a3; int a4; int a5;
```

```
 int a1 = 10;
 int a2 = 20;
 int a3 = 30;
 int a4 = 40;
 int a5 = 50;
```



```
  但是如果需要表示一万个数据, 那么就不能创建一万个变量了. 这时候就需要使用数组, 帮我们批量创建.
```

```
int[] array = {10,20,30,40,50};
```

上面就是整型数组.

注意事项: 在 Java 中, 数组中包含的变量必须是 相同类型.



### 2，创建数组

```
基本语法
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417125921460.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

 在上面的实例中，我们就以整型数组为例，创建了一个 int [ ] 类型的array数组，并且存放了5个整形数据.讲解了数组创建时的用法，Java数组的创建与C语言很是相似，但是还是有区别的.

C语言版本数组的创建：

```
   int arr[5] = {1,2,3,4,5}; 
```



Java版本数组的创建：

```
  int[] arr = {1,2,3,4,5};
```



 我们可以通过两种写法看到其中的区别. Java当中一定要 [ ] 和数据类型紧挨在一起.

  数组的数据在内存中是连续存放的.继续以上面的代码为例：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417131023306.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

 数组的每一元素都有其对应的下标，而下标->从0开始，我们要想找到这个数组中的某个数据，是通过数组的下标来进行访问的.



注意：

```
数组也被称为存放一组相同类型的数据的集合！！
```

```
下标是从0号位置开始的.
```



### 3，定义数组的方式

```
定义方式一
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417131636500.png#pic_center)

 上面我们写的代码是，定义并初始化了一个数组.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417131720988.png#pic_center)

这样的方式才只是定义了一个数组.这就是我们定义数组的第一种方式.且这样定义的数组默认大小为0.



```
定义方式二
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417132024610.png#pic_center)

这样也是定义了一个数组，不过这个数组定义是通过new 这样一个关键字，给 array 分配了一块内存，这块内存有10个数据可以存放.

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021041713243335.png#pic_center)

int [ 10 ] 分配的连续内存空间.

  不过此时，我们还未给 array 这个数组进行初始化，所以 array 此时的这十个数据默认值为0.



```
定义方式三
```

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417132712885.png#pic_center)







在Java当中在已经初始化之后， = 左边的 [ ] 中是不能填数字的， = 右边的 [ ] 只有在 定义方式二 中可以给定值.



在定义方式三中

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417133533450.png#pic_center)

总结定义数组的三种方式：

```
int[] array1={1,2,3,4,5};//定义一
int[] array2=new int{10};定义二
int[] array3=new int{1,2,3,4,5};//定义三
```

在这三种方式中，Java中定义数组最常用的是方式一。



### 4，数组的使用

#### （1）获取长4度

注意事项

```
1.使用arr.length 能够获取到数组的长度，这个操作为成员访问操作符，后面在面向对象中会经常用到
```



代码示例![image-20210623104959458](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623104959458.png)



编译效果：

![image-20210623105011613](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623105011613.png)





#### （2）访问数组中的元素

数组访问的方式：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417155122555.png#pic_center)

注意事项：

```
1.使用[]按下标取数组元素，需要注意，下表从0开始计数
```

```
2.使用[]操作既能读取数据，也能修改数据
```

```
3.下标访问操作不能超出有效范围[0,length)，如果超出有效范围，会出现下标越界异常
```

代码示例![image-20210623111531979](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623111531979.png)



#### （3）下标越界

数组下标从0开始，范围是[0，arr.length)左闭右开区间，或者是[0,arr.length-1)

如果我们将下标的值超出数组的范围

如下所示

![image-20210623113430380](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623113430380.png)

编译器报错：超出数组范围的错误



#### (4)遍历数组

所谓 “遍历” 是指将数组中的所有元素都访问一边，不重不漏，通常需要搭配循环语句



```
1.遍历方式（一）-----for循环
```

代码实现![image-20210623194654185](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623194654185.png)



编译效果：![image-20210623194708911](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623194708911.png)



 我们可以看到，用 for 循环 将数组中的元素一 一遍历 并打印出来.



```
2.遍历方式（二）--->for each
```

for-each 是 for 循环的另外一种使用方式，能够更方便的完成对数组的遍历，可以避免循环条件和更新语句写错



for-each 的基本使用

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417160659855.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

代码示例：![image-20210623195308843](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623195308843.png)



编译效果：![image-20210623195321342](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623195321342.png)



```
for-each 遍历原理
```



遍历array 里面的每一个元素，把每一个元素取出来，然后赋值给了 x ，最后打印 x,知道 array里面的元素全部都遍历完成。



```
for循环和for-each循环的区别
```

 

for 循环时可以拿到数组下标的，for-each拿不到数组小标， 所以for-each只能够全部遍历，无法对数组元素进行修改或进行操作



```
3.遍历方式（三）————使用操作数组的工具类进行数组的打印
```



Arrays 就是操作Java数组的工具类，你要对数组做什么事情，就可以通过他来做，当然有些事情他是完成不了的

比如说：我们要打印数组，我们本来是用for循环 或者 for-each 来写的，但是我们也可以用Arrays的工具类打印.

  通过JDK的工具文档，我们查找到了相应的工具类.

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/2021041716185830.png#pic_center)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417165222421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



代码示例：![image-20210623201047389](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623201047389.png)



编译结果：![image-20210623201058377](C:\Users\狐狸\Desktop\数据笔记\Java基础语法（二）----数据类型.assets\image-20210623201058377.png)





### 5，数组在内存中的存储

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417170341202.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

我们知道局部变量都在Java虚拟机栈上存放，而数组的数据则在堆上进行存放， 数组的数据在堆上都有特定的地址，而数组的变量存放的其实是这组数据的地址，栈上的这个变量根据这个地址找到堆上的数据.



数组的具体存储由下图所示：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417171629181.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

注意点：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417172304815.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417172542527.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210417172627988.png#pic_center)

 上图为arr指向的数据在堆中的地址，这个地址并不是真正的地址，它是通过正式的地址 hash 得到的.但是我们可以把它当作真实的地址，因为这个地址也是唯一的.

  那么真实的地址为什么要hash操作呢？

  这就是Java的安全性了，不会轻易暴露自己数据的地址.



## 二，数组作为方法的参数

### 1.基本用法

代码示例：打印数组内容

```
 public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        printArray(arr);
    }
    public static void printArray(int[] a) {
        for (int x : a) {
            System.out.println(x);
        }
    }

```







# Java基础语法（七）——类和对象

内容大纲

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422224828956.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

## 一，类和对象的初步认识

​    首先，类和对象是非常抽象的概念。我们要初步认识一下，什么是类？什么是对象？

```
类就是一类对象的统称
```

```
对象就是这一类具体化的一个实例
```



我们来形象的给大家举几个例子：



  相信大家都吃过月饼，我们做月饼的模子就是一个类，而通过这个模子可以做出月饼，那么在这个例子当中，类就是那个模子，而月饼就是那个对象,所以月饼就是一个实体。一个模子可以实例化无数个对象。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210424135809885.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



又或者说 ，类就相当于 一张房子的图纸， 我们根据这张图纸造出的房子就是 具体的对象，而一张图纸 可以造 多个房子 ，所以 一个类 可以实例化 多个对象。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210424140236911.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



类的多个实例化对象![在这里插入图片描述](https://img-blog.csdnimg.cn/20210424140607515.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)



而编程语言中的 面向对象，面向过程 这又是什么呢？

```
c语言是面向过程，关注的是过程，分析出求解问题的步骤，通过函数调用逐步解决问题
```

```
Java是基于面向对象的，关注的是对象，将一件事情拆分成不同的对象，靠对象之间的交互完成
```



面向对象 和 面向过程 的区别



```
面向过程注重的是过程，在整个过程中所涉及的行为，就是功能
```



```
面向对象注重的事对象，也就是参与过程所设计到的主体。是通过逻辑将一个个功能实现连接起来
```

我们对面向对象和过程举一个形象的例子：



```
面向过程： 1.把冰箱打开 2. 把大象放入 3. 冰箱关起来
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210424134631855.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JhaW42Nw==,size_16,color_FFFFFF,t_70#pic_center)

```
面向对象： 打开冰箱，储存，关闭都是对冰箱的操作，是冰箱的行为。
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210424134804621.png#pic_center)













































































