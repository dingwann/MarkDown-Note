# Java语言特点

Java由C++开发作为可以跨平台的面向对象语言，其特点是**一次编译，到处运行（跨平台）**和 **自动垃圾回收机制**

跨平台的原因是Java在各平台都有其 JVM (Java的虚拟机)

JDK 里集成了 JVM

JavaSE 为基础衍生了 JavaEE（企业级开发）、JavaME （嵌入式开发）

Java的安装路径下bin目录存放其命令、lib存放其类库、lib/src.zip Java的源码

**javac ----> 编译             java.exe ----> 运行**

# Java的运行机制

![image-20240720141651291](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201416542.png)

编译：

.java程序源文件通过javac程序进行语法检查，通过后编译成.class字节码文件

运行：

通过java启动JVM

JVM对.class字节码文件进行以下操作

1. 通过classLoader加载.class文件，路径是默认从当前路径找，找不到根据classpath（不是path，隶属于JVM）寻找。classpath需要自己配置，大小写无所谓，建议不配置或者配置为 **.;路径**
2. 链接





JDK >> JRE >> JVM

![image-20240720143337542](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201433663.png)

# 编译乱码问题

JVM21用的是UTF-8，如果乱码则说明源码字符集不一致，更改后统一即可。

# Java注释

注释只存在于.java源码中，编译后不存在，给人看的。

## 单行注释

```java
// 单行注释
```



## 多行注释

```java
/*
多行注释
*/
```



## javadoc注释

这种注释能被javadoc命令提取并生成帮助文档出来

```java
/**
*@author:
*@version:
*@param:
*/
```

javadoc -d docs -author -version -encoding utf-8 [xxx].java

# HelloWorld 解释

```java
/*
public 公开的
class 定义类
HelloWorld 类名
*/
public class HelloWorld {
    // 类体
    // 类体中不能直接写Java语句
    
    /*
    main方法，也叫主方法
    main方法是JVM规定的，固定写法，程序的执行入口
    对于main方法来说只能更改args变量名
    
    public 公开的
    static 静态的
    void main方法执行结束后不返回任何数据
    */
    public static void main(String[] args){
        // 方法体
        // 方法体当中由一行一行Java语句构成
        // 任何一条java语句必须由;结尾
        // 方法体当中语句按顺序逐行执行
        System.out.println("Hello World!");
        
        // 该语句作用将引号中的内容打印输出到控制台，并且println是换行，不加ln不换行
        System.out.println("xxx");
    }
    
    // 类体
}
```



# public class和class区别

1.一个java文件**可以定义多个class**

2.一个class会编译生成一个class文件

3.**public class可以没有，有的话只能有一个，并且public的类名和源文件名保持一致**

4.任何一个class都**可以有main方法**，但对于一个软件来说，一般入口只有一个



# Java语法

## 标识符

通俗说，写代码时自己命名的名字就是标识符

变量、常量、类名、方法、包、接口名、注解名等...

标识符不能数字开头、不能是java的关键字、区分大小写

![image-20240720161921250](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201619391.png)



## 关键字

Java预留了已经占用的特殊含义单词

![image-20240720173230315](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201732445.png)



## 字面量

Java语言中直接使用的数据，不需要进行转换或者计算

![image-20240720173624391](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201736443.png)

字符型字面量（单个字符）使用单引号

字符串字面量使用双引号



+号：求和  or 拼接（一边有字符串，一定做拼接）



## 变量

变量就是内存当中的一块空间，用来存数据，是存储数据的最基本的单元。

变量三要素：

+ 数据类型（决定空间大小）
+ 变量名
+ 变量值

```java
int i;  // 声明一个整型变量，起名i
i = 100; // i赋值100
System.out.println(i); // 访问i变量：读操作
i = 200; // 访问i变量：改操作
```



![image-20240720185654680](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407201856804.png)

### 变量分类

- 局部变量

- 成员变量

  1.静态变量

  2.实例变量

```java
public class Test {
    public static void main(String[] args) {
        // 方法体里的变量为局部变量
        int a = 100;
    }
    
    // 类体里定义的为成员变量
    // 实例变量
    int b = 10;
    // 静态变量
    static int c = 1;
}
```



## 二进制(0b)

计算机只能识别二进制。不管何语言，最后都是转换为二进制。

![image-20240720210517016](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202105136.png)

- 十进制转换为二进制

除2取余，一直到商0为止，最后将所有的余数**逆序输出。**

例如75：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202108709.png" alt="image-20240720210850654" style="zoom:50%;" />



- 二进制转换为十进制

每一位与权值相乘，最后求和。

例如将1001011转换为十进制

![image-20240720211310597](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202113650.png)

![image-20240720211632641](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202116672.png)



## 八进制(0)与十六进制(0x)

![image-20240720212105292](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202121339.png)

原理和二进制一样。

十进制转为八进制

例如十进制14：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202126345.png" alt="image-20240720212623313" style="zoom:50%;" />



八进制转为十进制

例如八进制20：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202127463.png" alt="image-20240720212736432" style="zoom:50%;" />

------

![image-20240720213103565](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202131617.png)

十进制转十六进制

例如17：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202136075.png" alt="image-20240720213625034" style="zoom:50%;" />



十六进制转十进制

例如10：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407202137746.png" alt="image-20240720213722715" style="zoom:50%;" />



```java
public class Jinzhi {
    public static void main(String[] args) {
        // 0b开头数字字面量后面接二进制
        // 0开头数字字面量后面接八进制
        // 0x开头数字字面量后面接十六进制
        System.out.println(0b11011);
        System.out.println(017);
        System.out.println(0x10);
    }
}
```



![image-20240721104757723](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211047822.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211052817.png" alt="image-20240721105230779" style="zoom:50%;" />

b1e2转为二进制：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211056033.png" alt="image-20240721105620989" style="zoom:50%;" />



## 原码反码补码

计算机底层存的补码

![image-20240721105804238](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211058294.png)

![image-20240721110745582](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211107654.png)

正数的原码反码补码都一样，127=128-1

128的二进制为10000000  -   1   =  0111  1111



**负数的原码取绝对值的二进制，将最高位改为1**

**反码以原码参考，符号位不变，其他位取反**

**补码以反码参考，符号位不变，加1**

例如-6：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211120735.png" alt="image-20240721112019693" style="zoom:67%;" />

-20:

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211126538.png" alt="image-20240721112655494" style="zoom:50%;" />

![image-20240721113751088](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211137218.png)



## 数据类型

### 整数型

![image-20240721114605267](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211146341.png)

![image-20240721120112901](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211201982.png)

**成员变量没有手动赋值时基本数据类型默认为0，引用数据类型默认为null**

**局部变量必须赋值**



整数型字面量会默认当作int处理

java允许小容量赋值给大容量变量

**byte < short < int < long < float < double**

```java
int a = 100;
// 先在内存中开辟空间存储100，再赋值给变量a

// 自动类型转换
long b = 100;

// 在整数型字面量后添加类型
long c = 100L;   // 默认就是long类型，8字节。

long e = 2147483647  // ok
long e = 2147483648  // 整型溢出
```



**强制类型转换**

**大  ----> 小，可能造成精度损失，原理就是砍掉左侧多余的二进制**

精度损失与否看转换后类型能否存下

```java
byte = (byte)150;  // ()强制转换
```

例如：

```java
long a = 55L;
int b = (int)a;
// 不存在精度损失
```

![image-20240721134013887](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211340966.png)

**注意：**

整数型字面量大小没有超出byte范围时可以赋值给byte不需要强制转换

整数型字面量大小没有超出short范围时可以赋值给short不需要强制转换

整数型字面量大小没有超出char范围时可以赋值给char不需要强制转换

```java
byte a = 127;   // 行
byte b = 128;   // 不行

short c = 32767;   // 行
short d = (short)32768;   // -32768
```



**两个int计算后结果还是int类型**

10 / 3 = 3



**byte、char 和 short 做混合运算的时候，各自转换为 int 再运算**

byte + byte  --> int

byte + short --> int

short + short --> int

char + char --> int

char + byte --> int

......

**多种类型做运算，各种转换为最大类型了再运算**

```java
byte a = 12;
int b = 100;
long c = 112233;
// int res = a + b + c 不行，因为最大类型转为了long
long res = a + b + c;
```



![image-20240721170025489](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211700618.png)



### 浮点型

**浮点型字面量默认被当作double，如果要做float类型，请添加 F 或 f**

float 单精度，可以到7位小数

double双精度，可以到15位小数

**double 更加常用**

```java
float a = 3.3;  
// 编译报错，因为3.3默认为double类型
// float a = 3.3F;
```

两种表示形式：

1.十进制

```java
double x = 1.23;

double y = 0.23;

double z = .23;
// 1.23   0.23   0.23
```

2.科学计数法

```java
double x = 0.123E2;    // 0.123 * 10^2
// 12.3
double y = 123.34E-2;  // 123.34 / 10^2（123.34 * 10^-2）
// 1.2334
```

#### 浮点型储存原理

**float是4字节 double是8字节，按道理应该double比float储存范围更大，但是实际是float > double。**

![image-20240721171909286](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407211719406.png)

**double所有的比特位都用来存的二进制0和1，所以实际存储容量没有float大，float可以指数级增大。**



注意：

**一旦有浮点型数据参与运算得出的结果，一定不要用 “==” 与其他数字进行 “相等比较”**

**因为浮点型数据在计算机底层存储的是它的近似值。**



### boolean

**true / false**

用于逻辑、条件判断

```java
int a = 100;
int b = 200;
int c = a;
a = b;
b = c
```



### char

1.字符型

2.占用2字节

3.取值范围：0-65535

​			char和short都是2字节

​			char可以取到更大的正整数（因为char没有负数范围）

​			char和short能表示的数量一样

4.在java中，字符char类型需用单引号‘ ‘

5.在Java中char类型统一采用的字符编码格式：unicode

6.char可以存储一个汉字

7.char不允许放空字符

8.char默认值：\u0000



**字符编码**

人为规定的文字与二进制的转换关系

ASCII：

**a:97(b:98)**

**A:65(B:66)**

**0:48(1:49)**

ASCII能表示键盘所有字符

Unicode是Java采用的编码方式，占用2或4字节

UTF-8是基于Unicode的可变长度编码方式，使用1-4字节表示一个字符，英文：1字节，汉字：3字节。（Web开发常用）



**定义char类型时，如果右边是整数，会把这个值当作ASCII码值处理**

char 参与运算

```java
char c = 'a' + 1
    
// 'a' = 97, 'a' + 1 = 98 --> b
```



### 基本数据类型转换规则

**八种基本数据类型除boolean外，可以互相转换**

**小容量可以自动转为大容量，称自动类型转换**

**byte < short < int < long < float < double**

​            **char <** 

**大容量不能自动转为小容量，除强制转换()，可能损失精度**

**当整数型字面量没有超出byte short char 范围时，可以直接赋值**

**byte short char 混合运算时，先转换为int再运算**

**多种类型做运算，各自先转换为其最大的类型再运算**



## 运算符

![image-20240722125934714](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407221259820.png)

取模公式：x - x / y * y



获取键盘输入内容

```java
public class test {
    public static void main(String[] args) {
        // 键盘扫描器对象, sc 为变量名
        java.util.Scanner sc = new java.util.Scanner(System.in);

        // 程序到此会停下，等待键盘输入，直到输入内容。
        int num = sc.nextInt();
        System.out.println(num);

        // 其余类型同理, 注意next()接收的是第一个空格之前的内容
        String str = sc.next();
        System.out.println(str);
        
        // nextLine(),接收第一个换行符之前的。
    }
}
```

![image-20240722154203274](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407221542349.png)

调用键盘扫描器的方法后，会在缓存里留下\r

调用nextline时会先读\r，所以得调用两次



### ++ 和 --

**++ 和 -- 可以在变量前也可以在变量后**

**无论在前还是在后，执行结束后都会让变量自加1**



++在变量后：

先赋值后自加1

```java
public class test {
    public static void main(String[] args) {
        int a = 10;
        int b = a++;
        // 先赋值运算再自加
        System.out.println(a); // 11
        System.out.println(b); // 10
    }
}
```



++在变量前：

先自加再赋值

```java
public class test {
    public static void main(String[] args) {
        int a = 10;
        int b = ++a;
        // 先自加再赋值运算
        System.out.println(a); // 11
        System.out.println(b); // 11
    }
}
```



```java
public class test {
    public static void main(String[] args) {
        int a = 10;
        // 先自加再赋值运算
        System.out.println(a++); // 10,和底层源码有关
        System.out.println(a); // 11
    }
}
```



--操作同理。



### 字节码

![image-20240722171033611](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407221710714.png)

查看class文件得字节码：

**javap -c 文件名.class**

```java
public class test {
    public static void main(String[] args) {
        int a = 1;
    }
}

// a = 1字节码为
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: iconst_1
       1: istore_1
       2: return
}

// a = 10 字节码为
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: istore_1
       3: return
}
```

**重点注意：**

**bipush 和 istore_1**

在Java中，**任何一个方法执行时都会为这个方法分配专属得内存空间供其使用，其中有两块比较重要得内存空间。**

**一块叫局部变量表（存储局部变量）**

**另一块叫操作数栈（储存程序运行中参与运算的数据）**

![image-20240722202608983](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407222026115.png)

**bipush    10： 将10字面量压入操作数栈**

**istore_1：将操作数栈顶的元素弹出，然后将其储存到局部变量表的1号槽位上**

```java
public class test {
    public static void main(String[] args) {
        int i = 10;
        int j = i;
    }
}
```

其字节码为：

```java
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: istore_1
       3: iload_1
       4: istore_2
       5: return
}
```

**iload_1：将局部变量表1号槽位的数据复制一份，压入操作数栈**

**istore_2：将操作数栈顶元素弹出，存储到局部变量表2号槽位上**

```java
public class test {
    public static void main(String[] args) {
        int i = 10;
        int j = i;
        j++;
    }
}

// 字节码
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: istore_1
       3: iload_1
       4: istore_2
       5: iinc          2, 1
       8: return
}
```

**iinc          2, 1：将2号槽位的数据加1**



```java
public class test {
    public static void main(String[] args) {
        int i = 10;
        int j = i++;
    }
}

// 字节码
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: istore_1
       3: iload_1
       4: iinc          1, 1
       7: istore_2
       8: return
}
```

将10压入操作数栈 ----> 把操作数栈顶元素弹出到1号槽位 ----> 复制1号槽位数据并压入操作数栈 ----> 对1号槽位的数据进行 +1 操作 ----> 将操作数栈顶元素弹出到2号槽位

2 ----> 10

1 ----> 11



```java
public class test {
    public static void main(String[] args) {
        int i = 10;
        int j = ++i;
    }
}

// 字节码
Compiled from "test.java"
public class test {
  public test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: istore_1
       3: iinc          1, 1
       6: iload_1
       7: istore_2
       8: return
}
```

将10压入操作数栈 ----> 把操作数栈顶元素弹出到1号槽位 ----> 对1号槽位的数据进行 +1 操作 ----> 复制1号槽位数据并压入操作数栈 ---->  将操作数栈顶元素弹出到2号槽位

2 ----> 11

1 ----> 11



```java
public class test {
    public static void main(String[] args) {
        int i = 10;
        i = i++;
        System.out.println(i);  // 10
    }
}
// 底层实际操作为,具体可看字节码过程。
int i = 10;
int temp = i;
i++;
i = temp;
```



### 关系运算符

简单，略。

<  >  <=  >= == !=

关系比较的结果是boolean值。



### 逻辑运算符

**逻辑与（&）、逻辑或（|）、逻辑非（!）、逻辑异或（^）、短路与（&&）、短路或（||）**

特点：两边都是布尔类型，结果也是。

![image-20240722214619660](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407222146780.png)

&&和||与&和|运算一样，只是存在短路现象，可以提高效率不去运行不该运行的。

&和|不管咋样都会执行左右两边的



### 按位运算符

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231058731.png" alt="image-20240723105857626" style="zoom: 80%;" />



#### 左移运算符

![image-20240723110515537](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231105611.png)

例如：

![image-20240723110407654](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231104706.png)



2 变成 8：  2 << 2  ---->  2 * 2^2

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231113117.png" alt="image-20240723111340030" style="zoom:80%;" />

#### 右移运算符

![image-20240723111454441](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231114513.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231122154.png" alt="image-20240723112227061" style="zoom:80%;" />



#### 无符号右移

![image-20240723112350369](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231123432.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231128784.png" alt="image-20240723112853702" style="zoom:80%;" />



#### 按位与

![image-20240723130929118](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231309284.png)

1 & 1 --> 1

1 & 0 --> 0

35 & 26:

![image-20240723131828794](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231318855.png)

```java
if((num & 1) == 1) {
    // num是奇数
}
```



#### 按位或

![image-20240723132310197](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231323277.png)

#### 按位异或

![image-20240723133202698](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231332787.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231335305.png" alt="image-20240723133557236" style="zoom:80%;" />



#### 按位取反

![image-20240723133914174](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231339259.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231345029.png" alt="image-20240723134516947" style="zoom:80%;" />



### 赋值运算符

基础简单，略。

```java
// i += 10 和 i = i + 10一样吗？
byte m = 10;
m = m + 20;
// 不兼容类型，因为20是int

m += 20;   // 这样可以，底层对应的是m = (byte)(m + 20);
```

**对于扩展运算符，例如+= -= /= ，根据变量类型进行自动强转，哪怕损失精度**



### 条件运算符

![image-20240723143106950](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231431100.png)

```java
 public class test {
    public static void main(String[] args) {
        boolean flag = true;
        int a = flag ? 10 : 20;
        System.out.println(a);
    }
}
```



## 控制语句

![image-20240723145317355](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231453461.png)



### 分支语句

#### 1. if语句

```java
if() {
    
}else {
    
}

// 一行语句可以这样
if() xxx;
```

字符串比较不能用 == ，必须手动调用equals方法进行比较

```java
String name = "wangcai"
if(name.equals("admin")) {
    ...
}else {
    ...
}
```

![image-20240723150502689](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231505763.png)

![image-20240723150548480](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231505545.png)





#### 2. switch语句

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231626622.png" alt="image-20240723162602472" style="zoom:80%;" />

expression：int / 枚举 / 字符串

byte/short/char  也行，底层会自动类型转换

```java
public class test {
    public static void main(String[] args) {
        int x = 2;
        switch(x) {
            case 1:
                System.out.println("1");
                break;
            case 2:
                System.out.println("2");
                break;
            case 3:
                System.out.println("3");
                break;
            case 4:
                System.out.println("4");
                break;
            default:
                System.out.println("default");
        }
    }
}
```

case可以合并的

```java
switch(x) {
    case 1: case 2: case 3:
        xxx
        break;
};
```



switch ---- java12新特性：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407231909013.png" alt="image-20240723190931921" style="zoom:80%;" />



### 循环语句

#### 1. for

当某段代码片段需要多次执行时。

```java
for(int i = 0; i < 10; i++) {  // 初始化表达式;条件表达式;更新表达式
    xxx   // 循环体
}
/*  初始化表达式最先执行，且只执行1次
	条件表达式必须是布尔类型的值
	更新表达式负责更新变量值
*/
```

**执行原理：**

初始化表达式最先执行1次

条件表达式 ---- true ---- 循环体 ---- 更新表达式

条件表达式 ---- true ---- 循环体 ---- 更新表达式

条件表达式 ---- true ---- 循环体 ---- 更新表达式

条件表达式 ---- true ---- 循环体 ---- 更新表达式下

条件表达式 ---- false



#### 2. while

![image-20240725173528255](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407251735497.png)



#### 3. do while

![image-20240725174635838](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407251746931.png)

do while 无论如何先执行一次。

**特别注意：while() 后面有;**



### 跳转语句

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407251912224.png" alt="image-20240725191240129" style="zoom:80%;" />

#### 1. break

默认终止当前层循环，但是可以指定，但是使用较少。

![image-20240725191703089](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407251917154.png)

#### 2. continue

跳出本次循环体执行的操作，不进行终止循环。

continue也可以加标记进行控制循环



**注意：**

**return 进行方法的终止**

**break 进行循环的终止**



## 方法

![image-20240725193029293](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407251930415.png)

设计方法应该达到解耦、高复用、独立性。

```java
public class test {
    public static void main(String[] args) {
        sum(2,6);  // 方法调用
        sum(8,10);
    }
	
    // 方法定义
    public static void sum(int a, int b) {
        int sum = a + b;
        System.out.println(sum);
    }
}
```

**JVM调用的main方法**



#### 方法定义

``` java
// 语法格式   [可选项]
[修饰符列表] 返回值类型 方法名(形式参数列表) {
    方法体;
}

// 目前修饰符统一写 public static
// 返回值类型可以是java中任何一种数据类型（基本数据类型、引用数据类型）
// 如果方法执行结束时不返回任何数据给调用者写void，不能空着不写。
```

当返回值类型不是void的时候，方法程序结束时必须用 return 值来完成数据的返回

```java
public static void m() {
    return;
}
// 可以编译，因为并没有返回值
// 这里的return的作用就是结束方法
```



**当调用方法要接收时，定义的变量类型要和方法返回值类型一致或者能够进行自动类型转换。**

**可以选择不接收返回值。**



#### 方法的调用

**如果一个方法的修饰符列表有 static 那么调用的时候就得用类名.方法名(实际参数列表);**

实参和形参的类型和个数都要一一对应。

```java
public class test {
    public static void main(String[] args) {
        // 省略类名
        sum(2,6);
        // 类名.方法名();
        test.sum(8,10);
        // 调用A类的方法haha
        A.haha();
    }

    public static void sum(int a, int b) {
        int sum = a + b;
        System.out.println(sum);
    }
}

class A {
    public static void haha() {
        System.out.println("haha");
    }
}
```

**类体中调用方法可以省略类名**

**类不一样时不能省**



判断1-100的质数：

```java
public class test {
    public static void main(String[] args) {
        for(int i = 1; i <= 100; i++) {
            if(isPrime(i)) {
                System.out.println(i);
            }
        }
    }

    public static boolean isPrime(int x) {
        for(int i = 2; i <= (int)Math.sqrt(1.0 * x); i++) {
            if(x % i == 0) {
                return false;
            }
        }
        return true;
    }
}
```



#### 方法执行的内存图

**方法如果只定义不调用是不会分配内存空间的（从Java8开始，方法的字节码存储在元空间 metaspace 中，元空间使用的是本地内存）**

**方法调用的瞬间，会在栈内存中分配活动场所，此时会发生push压栈动作。**

**方法结束，给该方法分配的空间就会释放，pop弹栈操作**

```java
public class test {
    public static void main(String[] args) {
        System.out.println("main start");
        m1();
        System.out.println("main end");
    }
    
    public static void m1() {
        System.out.println("m1 start");
        m2();
        System.out.println("m1 end");
    }

    public static void m2() {
        System.out.println("m2 start");
        m3();
        System.out.println("m2 end");
    }

    public static void m3() {
        System.out.println("m3 start");
        System.out.println("m3 end");
    }
}

// 结果
main start
m1 start
m2 start
m3 start
m3 end
m2 end
m1 end
main end
```

------

![image-20240725211441320](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407252114440.png)

**元空间也是JVM的一部分，只不过用的是本地内存（为了解决OOM问题 Out Of Memory）**



#### 方法重载机制(overload)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407252142651.png" alt="image-20240725214259546" style="zoom:80%;" />

```java
public class test {
    public static void main(String[] args) {

    }

    public static void m(int a, int b) {
        System.out.println(a + b);
    }
    
    public static void m(int a, int b, int c) {
        System.out.println(a + b + c);
    }
}

```

#### 递归

![image-20240725221241036](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407252212145.png)



#### package

![image-20240726120348789](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261203902.png)

用了package后类名叫包名.类名

加了package的要在对应文件夹中

```java
package com;

java com.类名运行
```

加-d . 进行编译自动生成



#### import

![image-20240726121815076](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261218161.png)

import 在 package 和 代码中间部分

同一包下不需要调用 import



## IDEA

Alt + Insert == 新建任何东西 ----> 输入即可

ESC == 关闭任何窗口

Ctrl + Shift + F12 == 代码区全屏开/关

psvm == 生成main方法

sout == 打印方法

“Hello World!”.sout == 自动生成对应打印语句

IDEA 自动保存、自动编译

Alt + 编号 == 开/关对应窗口  Alt+1 == 项目窗口  Alt+4 ==Terminal 

两次 Shift 选择类 输入类名 == 查找类

Ctrl + / == 单行注释

Ctrl + Shift + / == 多行注释

Alt + 左右 == 切换窗口（Tab 和 Shift+Tab也行）

Ctrl + y == 删除一行

Ctrl + d == 复制一行

fori == 生成for循环语句

在类中查找方法 == Ctrl + F12

快速生成创建对象 == 类名.new.var

（布尔类型）.if == 生成if语句



## 面向对象（得精通）

一种开发方式，Java、Python、C#都是支持的

![image-20240726144315028](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261443176.png)

![image-20240726150520410](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261505507.png)

### 类与对象

![image-20240726150741499](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261507614.png)

#### 类

![image-20240726183343817](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407261833948.png)



#### 对象的创建和使用

成员变量没有手动赋值时，系统默认赋值。

```java
package dingwan;

public class Student {
    // 实例变量
    String name;
    int age;
    boolean gender;
    
}

```

```java
package dingwan;

public class Student {
    public static void main(String[] args) {
        Study s1 = new Study();
        // 访问
        System.out.println(s1.name);
        System.out.println(s1.age);
        System.out.println(s1.gender ? "男" : "女");
        
        // 修改
        s1.name = "wangcai"
    }
}

```

#### JVM内存分析

```java
package dingwan;

public class Student {
    public static void main(String[] args) {
        Study s1 = new Study();
        System.out.println(s1.name);
        System.out.println(s1.age);
        System.out.println(s1.gender ? "男" : "女");

        s1.name = "wangcai";
        s1.age = 18;
        s1.gender = true;
        
        Study s2 = new Study();
    }
}
// s1和s2是引用，保存的对象的内存地址
```

![image-20240727170349219](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407271703435.png)

#### 实例变量和方法的访问

**加了 static 修饰符可以通过类名.变量/方法访问**

**没有加的话不可以**



#### 空指针异常的发生

```java
Student s1 = new Student;

s1 = null;

// 因为引用地址指向了null，编译可以通过，但是运行就空指针异常报错
```



#### 方法调用时参数的传递

```java
package dingwan;

public class Student {
    public static void main(String[] args) {
        int i = 10;
        add(i);
        System.out.println(i);
    }

    public static void add(int i) {
        i++;
        System.out.println("add---->" + i);
    }
}
/*
add---->11
10
*/
```

**调用add方法时，i怎么传的？**

**实际上是将 i 复制一份传入**

如果传的是引用数据类型例如对象呢？

```java
public class User {
    int age;
}
```

```java
public class Test {
    public static void main(String[] args) {
        User u = new  User;
        u.age = 10;
        // 虽然u也是复制一份传的，但是u保存的是对象的地址，传过去的地址一样，所以add的更改也生效
        add(u);
        System.out.println("main----" + u.age)
    }
    
    public static void add(User u) {
        u.age++;
        System.out.println("add----" + u.age)
    }
}
// 11, 11
```



#### this关键字

出现在实例方法中，代表当前的对象。this 大部分情况下可以省略。

this也是个引用，代表当前的对象。

**this也是存当前对象的内存地址，存在实例方法的栈帧的局部变量表的0号槽位里**

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407272358342.png" alt="image-20240727235805141" style="zoom: 67%;" />



### 封装

![image-20240728000117501](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407280001627.png)

说白了封装为了保护内部属性或者调用方法的权限设置，然后提高复用性。

方法：

#### 属性私有化

使用 private 进行修饰，所有被 private 修饰的都是私有的，私有的只能在本类中访问。

 ```java
 private int age;
 ```

**对外提供入口**

读：getter

```java
public 返回值类型 getAge() {}
```

改：s	etter

```java
public void setAge(int age) {}
```

```java
public void setAge(int age) {
    age = age
}
// 这时候的前面个age应该指对象的属性，所以要加this进行区分
```



**get和set方法IDEA可以自动生成**

**Alt + insert 选择即可**



#### 实例方法调用实例方法

说白了还是加this.就行

注意就是static方法不能调实例方法也不能用this，因为static方法是不需要new对象的，所以方法并没有存this。



​	构造代码块

```java
{
    
}
new的时候默认调用一次，在构造方法之前执行，也能用this。
    
// 如果所有的构造方法在开头有相同的代码，就可以将公共的代码放在构造代码块里面。
```

















