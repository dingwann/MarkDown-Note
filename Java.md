# Java语言特点

Java由C++开发作为可以跨平台的面向对象语言，其特点是**一次编译，到处运行（跨平台）**和 **自动垃圾回收机制**

跨平台的原因是Java在各平台都有其 JVM (Java的虚拟机)

JDK 里集成了 JVM

JavaSE 为基础衍生了 JavaEE（企业级开发）、JavaME （嵌入式开发）

Java的安装路径下bin目录存放其命令、lib存放其类库、lib/src.zip ----> Java的源码

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



**整数型字面量会默认当作int处理**

**java允许小容量赋值给大容量变量**

**byte < short < int < long < float < double**

```java
int a = 100;
// 先在内存中开辟空间存储100，再赋值给变量a

// 自动类型转换
long b = 100;

// 在整数型字面量后添加类型
long c = 100L;   // 默认就是long类型，8字节。

long e = 2147483647  // ok
long e = 2147483648  // int整型溢出
```



**强制类型转换**

**大  ----> 小，可能造成精度损失，原理就是砍掉左侧多余的二进制**

***精度损失与否看转换后类型能否存下***

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
// float a = 3.3;  
// 编译报错，因为3.3默认为double类型
float a = 3.3F;
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

​			**char可以取到更大的正整数（因为char没有负数范围）**

​			**char和short能表示的数量一样**

4.在java中，字符char类型需用单引号‘ ‘

5.在Java中char类型统一采用的字符编码格式：unicode

**6.char可以存储一个汉字**

**7.char不允许放空字符**

**8.char默认值：\u0000**



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

查看class文件的字节码：

>  **javap -c 文件名.class**



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

// 底层实际操作为,具体可看字节码过程。  bipush 10  istore_1  iload_1  iinc 1,1 istore_1
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

// 因为1的二进制最后一位是1，按位与的话只有都为1结果才为1，因为奇数的最后一位也为1，所以能判断。
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

**对于扩展运算符，例如+=   -=   /= ，根据变量类型进行自动强转，哪怕损失精度**



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

**字符串比较不能用 == ，必须手动调用equals方法进行比较**

**因为==比较的是内存地址，字符串本质是String，自动装箱的因为会放在字符串常量池（String重写了equal方法）所以没问题。new出来的话就会造成其内存地址不一样而造成误判**

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

**JVM默认调用的main方法**



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

**当返回值类型不是void的时候，方法程序结束时必须用 return 值来完成数据的返回**

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

**元空间也是JVM的一部分，只不过用的是本地内存（为了解决OOM(Out Of Memory) 内存溢出问题）**



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

Alt + Enter == 纠错

Shift + Alt + 上下方向键 == 移动代码

Ctrl + o == 重写方法

变量名.castvar == 快速向下转型并生成变量名

Ctrl + Alt + T == 代码包围



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

public class StudentTest {
    public static void main(String[] args) {
        Student s1 = new Student();
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

public class StudentTest {
    public static void main(String[] args) {
        Student s1 = new Student();
        System.out.println(s1.name);
        System.out.println(s1.age);
        System.out.println(s1.gender ? "男" : "女");

        s1.name = "wangcai";
        s1.age = 18;
        s1.gender = true;
        
        Student s2 = new Student();
    }
}
// s1和s2是引用，保存的对象的内存地址
// 将图里的Study改为Student
```

![image-20240727170349219](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407271703435.png)

#### 实例变量和方法的访问

**加了 static 修饰符可以通过类名.变量/方法访问**

**没有加的话不可以**



#### 空指针异常的发生

```java
Student s1 = new Student();

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

出现**在实例方法中**，代表当前的对象。this 大部分情况下可以省略。

this也是个引用，代表当前的对象。

**this也是存当前对象的内存地址，存在实例方法的栈帧的局部变量表的0号槽位里**

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407272358342.png" alt="image-20240727235805141" style="zoom: 67%;" />



### 封装

![image-20240728000117501](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202407280001627.png)

说白了封装为了保护内部属性或者调用方法的权限设置，然后提高复用性。

方法：

#### 属性私有化

使用 private 进行修饰，所有被 private 修饰的都是私有的，**私有的只能在本类中访问。**

 ```java
 private int age;
 ```

**对外提供入口**

读：getter

```java
public 返回值类型 getAge() {}
```

改：setter

```java
public void setAge(int age) {}
```

```java
public void setAge(int age) {
    // age = age;
    this.age = age;
}
// 这时候的前面个age应该指对象的属性，所以要加this进行区分
```



**get和set方法IDEA可以自动生成**

**Alt + insert 选择即可**



#### 实例方法调用实例方法

说白了还是加this.就行

注意就是static方法不能调实例方法也不能用this，因为static方法是不需要new出对象的，所以方法并没有存this。

 

**构造代码块**

```java
{
    
}
每次new的时候默认调用一次，在构造方法之前执行，也能用this。
    
// 如果所有的构造方法在开头有相同的代码，就可以将公共的代码放在构造代码块里面。
```



### 构造方法

![image-20240802145129572](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408021451826.png)

作用：对象的创建（调用构造方法即可完成创建）

​			对象的初始化（属性赋值）

```java
// [修饰符] 构造方法名(形参列表) {
	// 构造方法体
}
// 使用new运算符调用
```

**构造方法名 == 类名（必须）**

> ##### 构造方法会将new出的对象内存地址返回，但是我们不需要写 return，也不需要写返回值类型。



### this 关键字

![image-20240802162902130](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408021629339.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408021700916.png" alt="image-20240802170003746" style="zoom: 80%;" />

个人理解：

调用构造方法之前对象已经创建，现在的this指向创建好的对象，向其传递三个参数，即默认去匹配构造方法。



### static 关键字

![image-20240802170543915](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408021705036.png)

**当一个属性是类级别的，就是类都有而且属性值一样，建议定义为static，在内存上只有一份，节省空间。**

**这种级别的属性不需要new对象，只需要类名.去访问**

**JDK8之后，静态变量存储在堆内存当中。**

静态变量什么时候开辟？

**执行时，在metaspace里进行类加载，加载类时，会在里面找有没有static，有的话就在堆内存中开辟空间。**

> ####  注意：类加载是在执行main方法之前执行的。

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041306531.png" alt="image-20240804130601376" style="zoom: 67%;" />

静态变量可以通过引用.属性访问，但是不推荐。

```java
public static void main(String[] args) {
    Chinese lisi = new Chinese();
    
    
    System.out.println(lisi.xxx);
    System.out.println(Chinese.xxx);
    // 但是如果让lisi指向null后还能访问
    lisi = null;
    
    // 仍然不报错，因为执行时会默认将lisi改为其类名Chinese
    System.out.println(lisi.xxx);
}
```

静态代码块

```java
static {
    xxxxxxxxx;
}
```

**类加载时执行，而且只执行一次。**

**静态代码块可以写多个，遵循自上而下的顺序执行。**



### 设计模式

![image-20240804142727417](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041427545.png)

#### 单例模式

只需要创建一个对象。

> **饿汉式单例模式**

```java
/*
构造方法私有化。
对外提供一个公开的静态方法，用这个方法获取单个实例。
定义一个静态变量，在类加载的时候初始化静态变量。（只初始化一次）
*/
public class Sigleton {
    private static Sigleton s = new Sigleton();
    
    private Sigleton() {
    }
    
    public static Sigleton get() {
        return s;
    }
    
}
```

```java
public class SigletonTest {
    public static void main(String[] args) {
        Sigleton s1 = Sigleton.get();
    }
}
```

> **懒汉式单例模式**

```java
/*
构造方法私有化。
对外提供一个公开的静态方法，用这个方法获取单个实例。
定义一个静态变量，值为null。
*/
public class Sigleton {
    private static Sigleton s = null;
    
    private Sigleton() {
    }
    
    public static Sigleton get() {
        if(s == null) {
            s = new Sigleton();
        }
        return s;
    }
    
}
```

```java
public class SigletonTest {
    public static void main(String[] args) {
        Sigleton s1 = Sigleton.get();
    }
}
```



### 继承

![image-20240808122348109](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081223344.png)

```java
[修饰符] class 类名 extends 父类 {
    
}
// 除了构造方法和私有属性、方法无法继承外其余全部继承。
```

**Java中没有显式继承类时，默认继承Object**

**Object是JDK类库中的根类（java.lang.Object）**

### 方法覆盖

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081354740.png" alt="image-20240808135457451" style="zoom: 80%;" />

从父类继承的方法不够业务场景时考虑方法重写（覆盖）

```java
public class Animal {
    public void eat() {
        System.out.println("eat...")
    }
    
    public void move() {
        System.out.println("move...")
    }
}
```

```java
public class Bird extends Animal {
    // 对继承的move不满意，需要改进就进行重写（覆盖）
    @Override
    public void move() {
        System.out.println("flying...")
    }
}
```

方法覆盖后，子类对象调用的时候是执行重写后的方法。

```java
@Override
// 只在编译阶段有用
// 该注解用来标注方法，用来标注的方法必须是重写的方法，不然报错。
```

![image-20240808141814629](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081418732.png)

> **3.4 访问权限不能变低可以变高。public protected 默认 private（高 ----> 低）**
>
> **3.5 抛出异常不能变多，只能变少。**



### 多态

![image-20240808151322743](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081513956.png)

- #### **因为多态和方法重写是相关联的，多态是父类型的引用指向子类型对象，但是静态方法的调用不需要对象的参与，那么静态方法也就和多态无关了，自然也和方法重写无关。**

- #### **方法覆盖针对的实例方法，和实例变量无关，编译时变量绑定的什么对象，执行就是什么对象的属性**



#### 向上转型和向下转型

> **除了基本数据类型之间转换外，对于引用数据类型也可以类型转换，也就是向上转型和向下转型**

**向上转型（upcasting）：**子 ----> 父（可以等同看作基本数据类型的**自动**类型转换）

**向下转型（downcasting）：**父 ----> 子（可以等同看作基本数据类型的**强制**类型转换）

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081530900.png" alt="image-20240808153042813" style="zoom: 67%;" />

- #### **前提是两种类型必须有继承关系才能编译通过。**

```java
package test;

public class Animal {
    public void eat() {
        System.out.println("eat");
    }
}

```

```java
package test;

public class Cat extends Animal {
    @Override
    public void eat() {
        System.out.println("cat eat...");
    }
    
    // 子类特有方法，父类没有
    public void catchMouse() {
        System.out.println("catchMouse...");
    }
}

```

```java
package test;

public class Bird extends Animal {
    @Override
    public void eat() {
        System.out.println("bird eat...");
    }
    
}

```

测试：

```java
package test;

public class Test {
    public static void main(String[] args) {
        Animal a = new Animal();
        Bird b = new Bird();
        Cat c = new Cat();
        
        a.eat();
        b.eat();
        c.eat();
        
        /*
          向上转型（upcasting）：子 ----> 父
          等同看作自动类型转换
          两种关系具有继承
          父类型引用指向子类型对象
        */
        Animal a2 = new Cat();
        // 下面语句输出："cat eat..."
        a2.cat();
        /*
        1. 编译的时候编译器只知道a2是Animal类型，在Animal里找得到cat方法没毛病，对Animal的eat进行绑定，此时叫做静态绑定。
        2. 程序运行的时候，堆内存中真实的Java对象是Cat对象类型，所以cat()的行为是Cat对象发生的，因此运行的时候会自动调用Cat对象的eat()方法，这种在运行期的绑定叫动态绑定。
        --编译期一种形态，运行的时候一种形态，因此得名多态。--
        */
        
        a2.catchMouse();
        // 编译报错，静态绑定失败。
		// 解决办法：
        /*
          向下转型（downcasting）：父 ----> 子
          两种类型具有继承关系
          调用方法是子类特有
          等同看作强制类型转换
        */
        Cat c2 = (Cat)a2;
        c2.catchMouse();
        
    }
}
```

```java
Animal a = new Cat();
Bird b = (Bird)a;

/*
编译没问题，运行报错 ClassCastException 。
因为Bird类型和Animal类型具有继承关系，但是运行时堆中内存a实际是Cat对象，运行阶段就会出错，不能将Cat转换为Bird类型。
*/
```

**怎么避免 ClassCastException 异常？**

**instanceof 运算符语法规则：**

- 结果一定是 true 或 false
- (引用 instanceof 类型)
- (a instanceof Cat)

true: a 引用指向的对象是 Cat 类型

false: a 引用指向的对象不是 Cat 类型

> **做向下转型之前，先用 instanceof 进行判断**

```java
if(a instanceof Bird) {
   Bird b = (Bird) a; 
}
```



#### 总结

![image-20240808161805016](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081618170.png)

#### 软件开发原则

![image-20240808162315241](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408081623370.png)

多态就符合 OCP 原则，多态面向抽象编程，解耦性强，扩展能力就强。



### super关键字

![image-20240808221905809](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408082219002.png)

super关键字不是保存的地址啥的，只是保存当前对象中的父类型特征。

![image-20240809105215489](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408091052701.png)

#### super()方法

```java
public class A {
    String name;
    int age;
    
    public A(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

```java
public class B extends A {
    String address;
    
    public B(String name, int age, String address) {
        // this.name = name;
        // this.age = age;
        // 通过子类构造方法调用父类的构造方法，这样调用不会用父类创建新的对象。
        super(name, age)
        this.address = address;
    }
}
```

- #### **构造方法会<span style="color:red;">默认在开头调用 super()</span>, 本质目的也是为了给继承的属性初始化，所以父类最好有缺省构造**

- #### **this()  和 super() 不能共存，因为都必须在构造方法第一行。**



### final 关键字

![image-20240809224826827](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408092248049.png)

- #### **final 修饰的实例变量本质在构造方法执行完之前必须手动附上值**

- #### **final 修饰的变量是可以先不给值后面再赋值的，等于有一次机会**

```java
// 常量
public static final double P = 3.1415926;

// 引用
class A {
    
}

final A wangcai = new A();
wangcai = new A();   // 报错
```



### 抽象类（abstract）

![image-20240809231244041](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408092312213.png)

- #### 非抽象类继承抽象类后，必须将抽象方法进行重写，或者在子类修饰符也加 abstract 进行抽象。

- #### 抽象类无法实例化的，但是可以有构造方法提供给子类使用。



### 接口（interface）

#### 语法

![image-20240810103318400](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408101033616.png)

- ### **第4点的限制只适合JDK8之前的版本**

```java
/*
接口是完全抽象的，所以常量和抽象方法不需要加修饰符
*/

public static final int a = 1;
int b = 1;

/*--------------------------------------------------------------------------*/
public abstract void m1();
void m2();
```

> **默认方法**

```java
interface MyInterFace {
    // 默认方法 default 修饰
    default void MyDefault() {
        
    }
}
```

- #### **默认方法并不需要强制在实现类里实现该方法，默认继承实现**

![image-20240827180329748](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408271803839.png)

> **静态方法**

- #### **JDK8之后允许写静态方法**

```java
interface MyInterFace {

    static void staticMethod() {
        System.out.println("...")
    }
}

// 静态方法只能这样调用
MyInterFace.staticMethod();
```

- #### **接口的实现类不能调用接口的静态方法**

- #### **JDK9之后允许定义私有的实例方法（给默认方法服务）和私有的静态方法（给静态方法服务），目的给本接口使用**

![image-20240827180349979](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408271803074.png)

> **实例方法**

![image-20240827180426324](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408271804399.png)



![image-20240810163703351](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408101637525.png)

> **面向抽象编程，接口完全抽象，接口+多态编程能降低耦合度，提高代码的扩展能力**



### 接口和抽象类的选择

![image-20240810170316413](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408101703578.png)

> **注意最后两点**

- #### **实现类向接口类型转型正确来说不叫向下转型，因为是从具体实现向抽象转换，通常是进行向上的自动转型，但是我们也可以这么向下强制转换，但要注意类型判断进行安全的强制转换。**



### 统一建模语言（UML）

![image-20240811004815997](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408110048227.png)



> **类之间的关系**

![image-20240811131832918](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111318061.png)

泛化 ==== 继承 

实现 ==== implements

![image-20240811132643475](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111326545.png)

关联 ==== a 里有 b

![image-20240811133341190](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111333250.png)

> **+ 号代表 public  - 号代表 private**



聚合关系：

![image-20240811142128114](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111421185.png)



组合关系：

![image-20240811142422726](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111424790.png)



依赖关系：



![image-20240811142710678](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111427739.png)



### 访问控制权限

![image-20240811142857863](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111428949.png)

**重点关注下缺省和 protected**

不同包 ----> 缺省和protected 无法访问

不同包但是继承了 ----> protected 可以访问



### Object根类

![image-20240811144142642](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111441752.png)



#### toString() 方法

> **将 java 对象转换为其字符串表现形式**

![image-20240811145744086](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111457172.png)

- **toString() 也可以进行重写。**



> **System.out.println() 打印输出引用时，会自动调用引用的 toString() 方法。**

![image-20240811150144625](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111501706.png)

![image-20240811150554959](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111505019.png)



**上面的原因是源码导致的，因为println会将其传入的引用转换为String对象，如果为空就返回null去转换，然后调用其toString方法。**



#### equals() 方法

> **判断两个对象是否相等，返回布尔类型**

其源码：

```java
public boolean equals(Object obj) {
    return (this == obj);
}
```

**== 原则：比较变量中保存的值是否相等**

![image-20240811160713665](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111607753.png)



- **String类型底层也是new 一个 String 创建字符串，所以字符串比较不能用 == ，因为此时比较的内存地址，肯定不同**
- **String 类型里的 equals 在底层已经进行了重写，此时是将字符串的byte数组值进行挨个比较，相等就判断两个字符串相等，而不是默认去比较的内存地址。**

- **另外，String() 也将 toString() 进行了重写，输出直接输出对应的字符串，而不是输出完整类名@十六进制数字**



#### hashCode 和 finalize

![image-20240811163813010](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111638095.png)



**hashCOde 将对象的内存地址转换为十进制整数返回**

在Object中默认的实现：

```java
public native int hashCode();
// native方法底层调用C++写的动态链接程序（xxx.dll）
```



finalize 在 JDK9+ 后过时

![image-20240811170056541](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111700642.png)

**该方法是java对象被回收时，GC回收器自动调用被回收对象的finalize方法，完成销毁前准备。**

Object 里的默认实现：

```java
protected void finalize() throws Throwable {}
// 需要子类重写
```

```java
// 建议启动垃圾回收器
System.gc();
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111715607.png" alt="image-20240811171532535" style="zoom: 80%;" />





#### clone

> **对象的拷贝：浅拷贝、深拷贝**

![image-20240811171923043](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111719099.png)

在本类中也能访问。

参加克隆的对象必须实现 Cloneable 接口（标志接口），否则报错不支持克隆

![image-20240827185808410](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408271858538.png)

------

![image-20240811172926380](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111729436.png)

![image-20240811173050899](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111730985.png)



> **浅克隆（拷贝）**

![image-20240811173236227](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408111732288.png)

浅拷贝的对象如果属性里还有对象字段，那这个对象的是无法被拷贝的，对克隆的新对象里的该对象属性进行操作，原对象里对象属性也会变。

![image-20240811223441285](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408112234391.png)



> **深克隆（拷贝）**

**克隆的时候除了该克隆对象被克隆外，该对象所关联的对象内存空间也复制一份。**

步骤：

- 将关联引用也写成可克隆、重写其clone()

- 重写类中clone方法

​			将自己类中属性字段为引用的也克隆下来，this.getXXX.clone() 拿到其对象地址。

- 最后将克隆后的对象里面引用的字段通过setXXX方法将上面关联引用克隆下来的赋值过去再返回即可



### 内部类

![image-20240811224542756](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408112245860.png)



#### 静态内部类

静态内部类等同静态变量

```java
public class OuterClass {
    
    private static int a = 1;
    
    private int b = 2;
    
    private static void m1() {};
    private void m2() {};
    
    // 对于静态内部类来说，修饰符可以使用
    public static class InnerClass {
        public void m3() {
            System.out.println(a);  // 能访问
            System.out.println(b);  // 不能
            m1();  // 能
            m2();  // 不能
        }
    } 
}
```

- ##### **静态内部类中，无法直接访问外部中实例数据**

- **使用方法一样的，外部类名.内部类new对象即可**



#### 实例内部类

实例内部类等同实例变量

```java
public class OuterClass {
    
    private static int a = 1;
    
    private int b = 2;
    
    private static void m1() {};
    private void m2() {};
    
    public class InnerClass {
        public void m3() {
            System.out.println(a);  // 能访问
            System.out.println(b);  // 能
            m1();  // 能
            m2();  // 能
        }
    } 
}
```

- **因为要使用InnerClass的前提是外部类new出对象来，所以实例相关能访问，静态更不用说**

![image-20240811230707373](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408112307451.png)



#### 局部内部类

局部内部类等同于局部变量

局部内部类能不能访问外部的实例相关取决于所在的局部方法修饰符

- **如果局部内部类在实例方法里，那外部的静态和实例相关都能访问**
- **如果局部内部类在静态方法里，那外部的静态相关能访问，但是实例相关不能访问**
- **局部内部类不能使用修饰符**

```java
public class OuterClass {
    
    private static int a = 1;
    private int b = 2;
    private static void m1() {};
    private void m2() {};
    
	public void x1() {
        class InnerClass {
            public void m3() {
                System.out.println(a);  // 能访问
                System.out.println(b);  // 能
                m1();  // 能
                m2();  // 能
            	}
    	}
        InnerClass innerClass = new InnerClass();
        innerClass.m3();
    }
    
    public static void x2() {
        class InnerClass {
            public void m3() {
                System.out.println(a);  // 能访问
                System.out.println(b);  // 不能
                m1();  // 能
                m2();  // 不能
            	}
    	} 
    }
}
```

- **局部内部类访问该类所在方法的局部变量时，局部变量需要 fianl 修饰，但在 JDK8 开始不需要手动添加了。**



#### 匿名内部类（重点）

new接口和类都是可以的，最后是没有名字的类，**只能使用一次。**

防止类爆炸

```java
public class Test {
    public static void main(String[] args) {
        computer computer = new computer();

        computer.conn(new Usb() {
            @Override
            public void read() {
                System.out.println("read");
            }

            @Override
            public void write() {
                System.out.println("write");
            }
        });
    }
}


class computer {
    public void conn(Usb usb) {
        usb.read();
        usb.write();
    }
}

interface Usb {
    void read();
    void write();
}
```





## 数组

### 数组概述

![image-20240816162801610](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408161628739.png)



![image-20240816162153615](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408161621719.png)

![image-20240816163311916](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408161633034.png)

- 数组中类型相同，占用内存相同，有下标，查找快，查找时间都一样，时间复杂度O(1)。



### 一维数组

![image-20240816234132475](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408162341577.png)

> **静态初始化一维数组**

```java
/**
* 1. 数据类型[] 变量名 = new 数据类型[]{};
* 2. 数据类型[] 变量名 = {};
*/

int[] arr = new int[]{};
int[] arr2 = {};

// C/C++风格
int arr[] = new int[]{};
```



- **访问**

```java
public class ArrTest {
	public static void main(String[] args) {
        int[] nums = {10, 20, 30, 40, 50};
        
        // 读
        System.out.println(nums[0]);
        
        // 改
        nums[0] = 100;
        System.out.println(nums[0]);
        
    }
}

// 数组长度
nums.length
```



- **for each(增强for循环)**

```java
/*
语法:
for(数组中数据类型 变量名 : 数组名) {

}
变量名代表数组中每个元素
*/

int[] arr = {11, 22, 33, 44}

for(int num : arr) {
    System.out.println(num);
}
```

优点：代码简洁，可读性强

缺点：没有下标



> **动态初始化一维数组**

- **创建数组时，不知道具体存哪些元素时**

- **初始化完成后，数组长度确定，数据中存储的元素将采用默认值**

```java
数据类型[] 数组名 = new 数据类型[长度];

int[] nums = new int[4];
```



![image-20240817125258995](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171252097.png)

数组中存的不是对象本身，存的是引用的内存地址。

![image-20240817131136403](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171311539.png)

![image-20240817131230199](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171312281.png)



### 获取数组中的最大值

```java
public class ArrTest {
    public static void mian(String[] args) {
        int[] arr = {1,23,45,67,44,33,566};
        int Max = searchMax(arr);
        System.out.println(Max);
    }
    
    public static int searchMax(int[] arr) {
        // 假设第一个最大
        int max = arr[0];
        for(int i = 0, i < arr.length, i++) {
            if(arr[i] > max) {
                max = arr[i];
            }
        }
        return max;
    }
}
```

- **找最大值的小标**

```java
public class ArrTest {
    public static void mian(String[] args) {
        int[] arr = {1,23,45,67,44,33,566};
        int MaxIndex = searchMaxIndex(arr);
        System.out.println("最大值下标：" + MaxIndex);
    }
    
    public static int searchMaxIndex(int[] arr) {
        int maxIndex = 0;
        for(int i = 0, i < arr.length, i++) {
            if(arr[i] > arr[maxIndex]) {
                maxIndex = i;
            }
        }
        return maxIndex;
    }

}
```

### 数组反转

```java
// 创建新数组进行反转

public calss ReverseTest {
    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9};
        reverse(arr);
        System.out.println(arr);
    }
    
    
    public static void reverse(int[] arr) {
        int[] newArr = new int[9];
        for(int i = 0; int < arr.length; i ++) {
            newArr[i] = arr[arr.length - 1 - i]
        }
        // 下面这样反转不改变原数组的内存地址，不考虑的话可以直接arr = newArr;
        for(int i = 0; i < newArr.length; i++) {
            arr[i] = newArr[i]
        }
    }
}

```

- 首尾交换进行反转

```java
// 无论数组中的数据是偶数还是奇数，循环次数都是数组长度的一半
// {1,2,3,4} ----> 1-4 2-3     2次
// {1,2,3,4,5} ----> 1-5 2-4 3不需要   2次


public class ReverseTest {
	public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9};
        reverse(arr);
        System.out.println(arr);
    }
    
    public static void reverse(int[] arr) {
        for(int i = 0; i < arr.length / 2; i++) {
            int temp = arr[i];
            arr[i] = arr[arr.length - 1 - i];
            arr[arr.length - 1 - i] = temp;
        }
    }
}
```



> **main方法的形参args**

- **接收命令行参数**

JVM负责调用main方法并且准备String数组

![image-20240817175655757](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171756935.png)



> **可变长度参数**

```java
// 语法： 数据类型(包括引用数据类型)...

public static m1(int... nums) {
    
}
```

- **可变长度参数使用了，那形参位置只能有它**
- **可变长度参数可当数组来用**



### 一维数组扩容

![image-20240817181941476](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171819593.png)

```java
// 该方法是native方法，效率可以
package Arr;

public class ArrTest {
    public static void main(String[] args) {

        int[] arr = {11,23,5,52,7677,88,44,25};
        int[] newArr = new int[arr.length * 2];

        System.arraycopy(arr, 0, newArr, 0, arr.length);

        for(int nums : newArr) {
            System.out.print(nums + " ");
        }
        // 11 23 5 52 7677 88 44 25 0 0 0 0 0 0 0 0
    }
}

```



### 二维数组

![image-20240817183607122](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408171836250.png)



> **静态初始化**

```java
package Arr;

public class ArrTest {
    public static void main(String[] args) {
        // 完整格式
        int[][] arr = new int[][]{{}, {}, {}};

        // 简化
        int[][] arr2 = {{}, {}, {}};
    }
}

```

- **查找元素**

```java
package Arr;

public class ArrTest {
    public static void main(String[] args) {
        // 完整格式
        int[][] arr = new int[][]{{11,22,33}, {1,2,3,4}, {111,222,333}};
		
        // 第一个数组中的第一位元素
        int a = arr[0][0]   // 11
        
    }
}
```

> **动态初始化**

```java
package Arr;

public class ArrTest {
    public static void main(String[] args) {
        // 等长，3个一维数组，每个数组长度为4。
        int[][] arr = new int[3][4];
        
        // 遍历
        for(int i = 0; i < arr.length; i++) {
            for(int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j]  + " ");
            }
            System.out.println();
        }
        
        // 不等长
        int[][] arr2 = new int[3][];
        arr2[0] = new int[]{1,2,3,4,5,6,7,8,9};
        arr2[1] = new int[]{11,22,33,44};
        arr2[2] = new int[]{100,200,300,400,500,600,700,800,900,1000};
    }
}
```



## Junit单元测试

![image-20240819123758134](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191237326.png)

![image-20240820225715235](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408202257297.png)



## 数据结构与算法（简易版）

![image-20240819133207241](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191332435.png)

### 算法

![image-20240819162138021](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191621266.png)

> **时间复杂度**

![image-20240819162521917](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191625052.png)

> **下面按消耗时间效率进行排序的**

![image-20240819170952335](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191709489.png)

![image-20240819171013691](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191710777.png)

![image-20240819171357914](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191713992.png)

![image-20240819171507354](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191715444.png)

![image-20240819171557245](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191715338.png)

![image-20240819171901463](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191719534.png)

![image-20240819172204348](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408191722459.png)

### 冒泡排序

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 8, 10, 1};

        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if(arr[j] > arr[j + 1]) {
                        int temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                };
            }
        }
        System.out.println(Arrays.toString(arr));
    }
}

```

优化版：

```java
package Suanfa;

import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 8, 10, 1};

        for (int i = arr.length - 1; i >= 0; i--) {
            boolean flag = true;
            for (int j = 0; j < i; j++) {
                if(arr[j] > arr[j + 1]) {
                        int temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                    	flag = false;
                };
            }
            if(flag) break;
        }
        
        System.out.println(Arrays.toString(arr));
    }
}

```



### 选择排序

- **因为冒泡交换次数太频繁，不常用，因此这种算法更加高效**

```java
import java.util.Arrays;

/**
 * 选择排序：
 * 找出参与比较中最小的元素和其中最左边的元素进行比较然后交换位置
 *
 * 原理：
 * [2,5,8,9,3,1]
 *
 * 第一次参与比较：2, 5, 8, 9, 3, 1
 * 比较完成后：1, 5, 8, 9, 3, 2
 *
 * 第二次参与比较：5, 8, 9, 3, 2
 * 比较完成后：1, 2, 8, 9, 3, 5
 *
 * ...类推
 * */

public class Test {
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 8, 10, 1};

        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if(arr[j] < arr[i]) {
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }

        System.out.println(Arrays.toString(arr));
    }
}

```



### 查找算法

![image-20240820113338245](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201133439.png)

> **二分法（折半）**

```java
package Suanfa;

import java.util.Arrays;


public class Test {
    public static void main(String[] args) {
        int[] arr = {1,5,8,27,33,66,90,222,499,557};

        int targetIndex = serachIndex(arr, 222);

        System.out.println(targetIndex);
    }

    public static int serachIndex(int[] arr, int target) {
        int start = 0, end = arr.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (arr[mid] == target) {
                return mid;
            }else if (arr[mid] > target) {
                end = mid - 1;
            }else {
                start = mid + 1;
            }
        }
        return -1;
    }
}

```



## Arrays 工具类

![image-20240820115531644](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201155793.png)

> **第四点自定义类型做比较，这个自定义类型必须实现 comparable 接口，并且重写compareTo方法编写比较规则**

- **因为你调equals进行比较的引用类型的时候，底层是将其转型为comparable类型然后调用其compareTo方法，因为是多态机制，所以调用的实际是真实对象重写的compareTo()方法**

![image-20240820150041150](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201500380.png)



## 异常

![image-20240820151452921](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201514048.png)

![image-20240820152832004](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201528164.png)

> **概念版**

![image-20240820154324692](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201543806.png)

**程序员编程导致的错误一般在RuntimeException里，外在条件导致的错误在Exception的其余部分**



- **异常的发生需要两个阶段**
  	1. 创建异常对象
  	1. 让异常发生（手动抛出异常）

```java
public class ExceptionTest {
	public static main(String[] args) {
        // NullPointerException e = new NullPointerException();
        // throw e;
        
        throw new NullPointerException(); 
    }
}
```



### 自定义异常

![image-20240820155652153](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201556288.png)

### 异常处理

- **Java 中继承Exception的自定义异常在使用的时候编译器会报错，因为Exception属于编译时异常，解决如下：**
- **两种方法一般结合使用的**

```java
// 1.在方法定义的后面使用throws关键字进行异常的声明,目的是当当前方法出现异常时，将出现的异常抛给调用者进行处理

/**
* throws在方法体里有啥异常抛啥异常，向上找有调用者也得进行异常处理
* throws可以抛给异常的父类型异常处理，比如下面的抛给Exception
*/
public void m() throws IOException{
    throw new IOException();
}




// 2.对new的异常进行捕捉处理

/**
    try {
		// 这里写需要尝试执行的程序，这里的程序可能出现异常
		// try里的代码当出现异常时，出现异常的代码行以后的不再执行
    }catch(异常类型1 变量名) {
		...;
    }catch(异常类型2 变量名) {
    	...;
    }...进行捕捉异常

* catch可以写多个，但是遵循自上到下，从小到大
*/
public void m1() {
    try {
        ...;
    }catch(IOException e) {
        ...;
    }catch(Exception e) {
        ...;
    }
}

```

- **Java7 + 的 try catch 新特性**

```java
public void m1() {
    try {
        ...;
    }catch(IOException | Exception e) {
        ...;
    }
}
```

![image-20240820174045639](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201740750.png)

```java
public class ExceptionTest {
    public static void main(String[] args) {
        try {
            m1(10);
        }catch(xxx e) {
            String msg = e.getMessage();
            System.out.println(msg);
            // 得到"年龄不合法！"
        }
    }
    
    public void m1(int age) throws xxx {
        if(age < 18) {
            throw new xxx("年龄不合法！");
        }
    }
}
```



### finally 语句块

![image-20240820180817387](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408201808534.png)

- **finally 一定会执行，哪怕在try中执行了 return; 结束了方法**

- **但是如果在try中执行System.exit();结束了JVM，这种情况finally不执行**

```java
public class ExceptionTest {
    public static void main(String[] args) {
        int res = m1();    // 100
    }
    
    public static int m1(){
        int i = 100;
        try {
            return i;
        }finally {
            i++;
        }
    }
}
```



### 方法覆盖与异常

- **方法覆盖后抛出的异常只能变少！**

```java
public class ExceptionTest {
    public static void main(String[] args) {
        
    }
}

class Pet {
    public void run() throws xxx1, xxx2{
        
    }
}

class Dog extends Pet {
    // 正常写法
    @Override
    public void run() throws xxx1, xxx2{
        System.out.println("嘻嘻")
    }
    
    @Override
    public void run() throws xxx1{
        System.out.println("嘻嘻")
    }
    
    @Override
    public void run(){
        System.out.println("嘻嘻")
    }
    
    // 下面不行
    @Override
    public void run() throws xxx1, xxx2, xxx3{
        System.out.println("嘻嘻")
    }
}
```





## 常用类

### String 类

![image-20240820203315183](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408202033344.png)

![image-20240820212010733](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408202120074.png)

```java
String x = "aaa" + "bbb";
String y = "aaabbb";
System.out.println(x == b);   // true;
```

- 将堆中字符串对象放到字符串常量池中

```java
String var = 变量名.intern();
```



> **String 类的常用构造方法**

![image-20240820213212223](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408202132370.png)



> **String 类的常用方法**

![image-20240820225112364](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408202251667.png)

------

![image-20240821213204778](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408212132933.png)

------

![image-20240821235914047](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408212359173.png)

![image-20240822004949991](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408220049070.png)

- **最长字符串的长度**

![image-20240822155957979](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221559087.png)



### StringBuffer 和 StringBuilder

![image-20240822160128720](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221601813.png)

> **底层源码**

两者都继承了 **AbstractStringBuilder**

![image-20240822161251192](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221612277.png)

构造方法：

![image-20240822163811897](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221638962.png)

- **常用方法**

API文档有

![image-20240822163950704](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221639797.png)

![image-20240822164312694](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221643785.png)

### String 的效率问题

![image-20240822174703804](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221747989.png)

### 包装类

![image-20240822175241127](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221752211.png)

![image-20240822180001726](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221800855.png)

- **Boolean和Character也有拆箱方法的**

  

> **把包装类给转回基本数据类型的过程 ----> 拆箱**

```java
// 用Integer做代表学习

System.out.println("int最大值：" + Integer.MAX_VALUE);
System.out.println("int最小值：" + Integer.MIN_VALUE);
```

![image-20240822180840586](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221808656.png)

> **将基本数据类型构造成包装类的过程 ----> 装箱（手动的很少用了）**

![image-20240822180938184](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221809266.png)

> **Integer 常用方法**

![image-20240822181812309](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221818486.png)

![image-20240822183220172](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221832272.png)

```java
@Test
public void testLeixing() {
    // String --> int
    String s = "100";
    int i = Integer.parseInt(s);

    // int --> String
    int j = 10;
    String a = Integer.toString(j);

    // String --> Integer
    String s2 = "1212";
    Integer i1 = Integer.valueOf(s2);

    // Integer --> String
    Integer i2 = Integer.valueOf(900);
    String s3 = Integer.toString(i2);

    // int --> Integer
    int i4 = 999;
    Integer i3 = Integer.valueOf(i4);

    // Integer --> int
    Integer i5 = Integer.valueOf(222);
    int iii = i5.intValue();
}
```



### 自动装箱与拆箱

![image-20240822185142029](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221851280.png)

- **自动装箱与拆箱是编译阶段的功能**

- **提高编程效率的机制**

```java
// 手动的装箱与拆箱
Integer i = Integer.valueOf(10);
int x = i.intValue();

// auto boxing 和 auto unboxing
Integer j = 10;
int y = j;
```



### 整数型常量池问题

```java
public class IntegerTest {
    public static void main(String[] args) {
        Integer x = 10000;
        Integer y = 10000;
        System.out.println(x == y);  // false
        
        Integer a = 127;
        Integer b = 127;
        System.out.println(a == b);  // true
        
        Integer a1 = 128;
        Integer b1 = 128;
        System.out.println(a1 == b1);  // false
    }
}
```

**原因：**

**[-128 ~ 127] 有256个 Integer 对象在内存里提前new好了放在一个数组里（Integer[] integerCache），叫整数型常量池**

**因为这些数字太常用了，提前new好提高效率**

> **私有的静态内部类**

![image-20240822191603032](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221916268.png)



### 大数字

![image-20240822191721945](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408221917087.png)

```java
BigInteger num = new BigInteger("9999999999999999999");
System.out.println(num);
```

![image-20240822215432913](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222154189.png)

![image-20240822215839797](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222158920.png)

```java
    @Test
    public void testNumFormat() {
        // 创建数字格式化对象
        DecimalFormat decimalFormat = new DecimalFormat("###,###.##");
        DecimalFormat decimalFormat2 = new DecimalFormat("###,###.0000");

        // 格式化
        String format = decimalFormat.format(12345678.123);
        String format1 = decimalFormat2.format(12345678.123);

        System.out.println(format); // 12,345,678.12
        System.out.println(format1); // 12,345,678.1230
    }
```



### 日期API

![image-20240822220448801](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222204016.png)

![image-20240822224703152](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222247354.png)

```java
@Test
public void testDate() {
    // 当前时间
    Date date = new Date();
    System.out.println(date);  // Thu Aug 22 22:21:26 CST 2024

    // 传入毫秒计算从1970-1-1 00:00:00到现在的时间(东八区，所以成了00:00:00 + 08:00:00)
    Date date1 = new Date(3000);
    System.out.println(date1);  // Thu Jan 01 08:00:03 CST 1970
}
```

```java
@Test
public void testFormatDate() throws ParseException {
    // java.util.Date --> java.lang.String
    // 获取当前时间
    Date date = new Date();

    // 格式化
    // DateFormat是SimpleDateFormat的父类
    SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
    String format = simpleDateFormat.format(date);

    System.out.println(format);  // 2024-08-22 22:32:26 126

    // java.lang.String --> java.util.Date
    String strDate = "2008-01-23 12:22:55 111";

    Date parse = simpleDateFormat.parse(strDate);
    System.out.println(parse);  // Wed Jan 23 12:22:55 CST 2008
}
```



> **Java8+ 新的日期API**

![image-20240822231508422](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222315614.png)

- **都在 java.time 下了**

```java
@Test
public void testNewDateAPI() {
    // 获取当前时间，精确到纳秒
    LocalDateTime now = LocalDateTime.now();
    System.out.println(now);
    // 获取指定时间
    LocalDateTime localDateTime = LocalDateTime.of(2003, 01, 23, 12, 00, 01);
    System.out.println(localDateTime);  // 2003-01-23T12:00:01
    // 给日期进行加操作
    LocalDateTime localDateTime1 = localDateTime.plusYears(1);
    System.out.println(localDateTime1);  // 2004-01-23T12:00:01
    // 给日期进行减操作,支持链式调用
    LocalDateTime localDateTime2 = localDateTime1.minusDays(1).minusHours(1);
    System.out.println(localDateTime2);  // 2004-01-22T11:00:01
}
```

![image-20240822232822971](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222328104.png)

```java
@Test
public void testDate1() {
    // 时间戳
    long l = System.currentTimeMillis();
    System.out.println("时间戳：" + l);  // 1724340846059
    Date date = new Date(l);
    System.out.println(date);  // Thu Aug 22 23:31:52 CST 2024

    // Java8 新API
    Instant now = Instant.now();  // 系统当前时间，基于UTC（全球标准时间）
    long epochMilli = now.toEpochMilli();
    System.out.println("时间戳：" + epochMilli);  // 1724340846081
    System.out.println(now);  // 2024-08-22T15:31:52.633435100Z
}
```

![image-20240822233526191](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222335313.png)



```java
import java.time.Duration;
import java.time.LocalDateTime;

public class Test {
    public static void main(String[] args) throws Exception{

        LocalDateTime localDateTime = LocalDateTime.of(2008, 8, 8, 8, 8, 8);
        LocalDateTime localDateTime1 = LocalDateTime.of(2009, 9, 9, 9, 9, 9);
        Duration between = Duration.between(localDateTime, localDateTime1);

        long hours = between.toHours();
        System.out.println(hours);  // 9529

        long days = between.toDays();
        System.out.println(days);  // 397

    }
}
```



![image-20240822233847225](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222338435.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222340551.png" alt="image-20240822234058413" style="zoom: 67%;" />

![image-20240822234202092](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222342292.png)

------

![image-20240822234443551](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222344744.png)



### 数学类 Math

![image-20240822234900637](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222349829.png)



### System 类

![image-20240823155835939](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408231558058.png)



## 枚举

![image-20240822235841002](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408222358175.png)

![image-20240823150212231](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408231502454.png)

> **枚举实现接口**

```java
public interface Eatable {
    public void eat();
}
```

```java
public enum Season implements Eatable{
    SPRING("春季", "x"),
    SUMMER("夏季", "x"),
    AUTUMN("秋季", "x"),
    WINTER("冬季", "x");
    /* 另外一种实现接口方式
    WINTER("冬季", "x") {
        @Override
        public void eat() {
            ...
        }
    };
    */
    
    private String name;
    private String desc;
    
    Season(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }
    
    @Override
    public void eat() {
        ...
    }
}
```



## 随机数生成器Random

![image-20240823152354935](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408231523021.png)

```java
```



## UUID

![image-20240824125120745](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408241251944.png)

```java
UUID uuid = UUID.randomUUID();   // 32位
```



## 集合

![image-20240824142436377](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408241424489.png)



### Collection

![image-20240824144231987](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408241442147.png)

集合就是容器，存储的是引用地址，collection：存储单个元素 || map：以键值对存储元素两种集合。

![image-20240824195941170](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408241959247.png)



![image-20240824224140787](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408242241888.png)

- **contains方法底层调用了重写的equal方法进行比较值，而不是Object根类的比较内存地址。**

- **remove方法底层调用了重写的equal方法进行比较值，而不是Object根类的比较内存地址。**

![image-20240824230411600](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408242304683.png)

```java
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

public class Test {
    public static void main(String[] args) {
        Collection c = new ArrayList();

        c.add(100);
        c.add("wangcai");
        c.add(new Object());
        
        Iterator iterator = c.iterator();  // 拿到当前集合的迭代器对象
        while (iterator.hasNext()){   // hasNext()判断当前是否存在元素
            System.out.println(iterator.next());  // next()将当前元素返回并将光标移向下一位
        }

    }
}

```

![image-20240825132719145](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251327357.png)



![image-20240825135700461](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251357558.png)



### 泛型

![image-20240825141419545](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251414656.png)

![image-20240825153412107](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251534270.png)

- 自定义泛型，可以定义多个

```java
// 语法
// class 类名<泛型1, 泛型2...>{}

public class Ttest<T, A> {
    private T name;
    private A age;

    public Ttest(T name, A age) {
        this.name = name;
        this.age = age;
    }

    public T getName() {
        return name;
    }

    public void setName(T name) {
        this.name = name;
    }

    public A getAge() {
        return age;
    }

    public void setAge(A age) {
        this.age = age;
    }
}

```

![image-20240825155232331](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251552438.png)

> **为什么静态方法不能用类上定义的泛型？因为类上定义的泛型我们在new对象时会指定泛型的类型，而静态方法不用new对象无法指定，那定义的泛型就没有意义。**

- **在静态方法上定义泛型**

```java
// 需在静态方法的返回值前面定义好泛型

public static <T> void m(T type) {
    ...
}
```

- **在接口上定义泛型**

```java
public interface i<T> {
    
}
```

![image-20240825161630870](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251616975.png)



### 集合的并发修改异常

![image-20240825164159165](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251641263.png)

集合的remove会出错，迭代器的不会

![image-20240825164549828](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408251645952.png)



### List 接口

![image-20240825214059849](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408252141096.png)

![image-20240825215457823](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408252154943.png)

- **remove和set方法，调用了previous()也行的。**



> **Comparator接口**

![image-20240825233548090](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408252335211.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408260000611.png" alt="image-20240826000000532"  />

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408252359166.png" alt="image-20240825235944059"  />

> **匿名内部类**

```java
new 接口名() {
    @Override
    ...
}
```



### ArrayList

![image-20240826002002619](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408260020729.png)

![image-20240826125041309](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261250398.png)

**默认无参创建时的数组长度为0，当第一次调用add方法时，底层调用grow()方法会长度为10；**

**扩容为原来容量的1.5倍**



修改元素：set方法会返回修改前的数据

```java
List<String> arrList = new ArrayList<>();
arrlist.add("zhangsan");
String s = arrList.set(0, "李四")  // s == zhnagsan
```



插入元素add

```java
arrlist.add(0, "xixi");
```

![image-20240826151904153](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261519256.png)



删除元素remove

![image-20240826152043640](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261520712.png)

![image-20240826152200398](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261522465.png)



### Vector

![image-20240826155355937](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261553034.png)

线程安全的数组实现List

默认容量为10

扩容后为原容量的2倍



### 链表

![image-20240826155530319](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261555407.png)



### LinkedList

![image-20240826162337463](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261623530.png)

> ***属性***

```java
LinkedList<String> ll = new LinkedList<>();
// 创建一个空链表  size=0  有头结点和尾结点

ll.add("1")
```

![image-20240826163712952](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261637037.png)



> ***插入操作***

![image-20240826165824700](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261658813.png)



> ***修改操作***

**找到结点改其item值就行，然后返回一个改前的旧值**



> ***删除操作***

![image-20240826170359588](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261703668.png)

![image-20240826171030687](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408261710740.png)



**remove方法返回被删除的值**





### 手写单向链表

```java
// add

// add(index, item)

// remove

// set(index, item)

// get
```







### 栈

数组模拟，后进先出，对尾元素进行添加，尾元素进行弹出。

双向链表模拟

![image-20240907143740084](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071437272.png)

------

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071442474.png" alt="image-20240907144245396" style="zoom: 80%;" />

![image-20240907144351069](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071443170.png)

```java
import java.util.ArrayDeque;
import java.util.LinkedList;
import java.util.Stack;

/**
 *  java.util.Stack  底层是数组，线程安全，Java6+不建议使用
 *  java.util.ArrayDeque   底层也是数组，实现了Stack和双端队列
 *  java.util.LinkedList   底层双向链表，实现了Stack和双端队列
 *
 * */

public class StackTest {
    public static void main(String[] args) {
        // 创建栈对象
        Stack<String> stack1 = new Stack<>();
        ArrayDeque<String> stack2 = new ArrayDeque<>();
        LinkedList<String> stack3 = new LinkedList<>();

        // 压栈
        stack1.push("1");
        stack1.push("2");
        stack1.push("3");
        stack1.push("4");

        // seach 从栈顶往下搜索，返回数字
        System.out.println("position: " + stack1.search("1"));

        // 弹栈
        System.out.println(stack1.pop());
        System.out.println(stack1.pop());
        System.out.println(stack1.pop());

        // peek
        System.out.println("Stack top：" + stack1.peek());

        // 压栈
        stack2.push("a");
        stack2.push("b");
        stack2.push("c");
        stack2.push("d");
        // 弹栈
        System.out.println(stack2.pop());
        System.out.println(stack2.pop());
        System.out.println(stack2.pop());
        System.out.println(stack2.pop());

        // 压栈
        stack3.push("A");
        stack3.push("B");
        stack3.push("C");
        stack3.push("D");
        // 弹栈
        System.out.println(stack3.pop());
        System.out.println(stack3.pop());
        System.out.println(stack3.pop());
        System.out.println(stack3.pop());
    }
}

```



### 队列与双端队列

![image-20240907150035188](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071500407.png)

- **入队：offer**
- **出队：poll**



**LinkedList双向链表模拟**

**ArrayDeque逻辑上是一个环形数组模拟的**

![image-20240907151335622](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071513713.png)

> **Queue**

```java
import java.util.ArrayDeque;
import java.util.LinkedList;
import java.util.Queue;

/**
 * java.util.ArrayDeque
 * java.util.LinkedList
 * 以上两个类都实现FIFO结构
 * */

public class QueueTest {
    public static void main(String[] args) {
        // 创建队列对象
        Queue<String> deque1 = new ArrayDeque<>();
        Queue<String> deque2 = new LinkedList<>();

        // 入队
        deque1.offer("1");
        deque1.offer("2");
        deque1.offer("3");
        deque1.offer("4");
        // 出队
        System.out.println(deque1.poll());
        System.out.println(deque1.poll());
        System.out.println(deque1.poll());
        System.out.println(deque1.poll());

        // 入队
        deque2.offer("a");
        deque2.offer("b");
        deque2.offer("c");
        deque2.offer("d");
        // 出队
        System.out.println(deque2.poll());
        System.out.println(deque2.poll());
        System.out.println(deque2.poll());
        System.out.println(deque2.poll());
    }
}

```

> **Deque**

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class DequeTest {
    public static void main(String[] args) {
        // 队尾进，队头出
        Deque<String> deque1 = new ArrayDeque<>();
        // 进
        deque1.offerLast("1");
        deque1.offerLast("2");
        deque1.offerLast("3");
        // 出
        System.out.println(deque1.pollFirst());
        System.out.println(deque1.pollFirst());
        System.out.println(deque1.pollFirst());

        // 队头进，队尾出
        // 进
        deque1.offerFirst("a");
        deque1.offerFirst("b");
        deque1.offerFirst("c");
        // 出
        System.out.println(deque1.pollLast());
        System.out.println(deque1.pollLast());
        System.out.println(deque1.pollLast());
    }
}

```





### Set 接口

![image-20240913133204487](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131332596.png)



**HashSet底层是HashMap，Set接口的实现类都是new的对应Map接口/类**

![image-20240907153730575](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071537634.png)

**将Map的key部分取出来对应的就是set集合**



#### HashSet

![image-20240913134914702](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131349832.png)



HashSet面试题：

![image-20240913142103985](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131421149.png)



#### LinkedHashSet

![image-20240913135337588](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131353655.png)





#### TreeSet

![image-20240913135455636](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131354716.png)









### Map 接口

map的继承实现结构和set类似，但是和collection没有继承关系，自己就是顶级接口。

以key-value进行存储，都是引用类型。

key主导，value是附属作用。

![image-20240907154058021](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071540077.png)



> **继承和实现结构**

![image-20240907155444402](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071554507.png)



> **Map 常用方法**

![image-20240907155543582](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071555679.png)

遍历Map集合：

```java
// 对key进行遍历用get得到其value
Map<Integer, String> maps = new HashMap<>();

Set<Integer> keys = maps.keySet();
Iterator<Integer> it = keys.iterator();
while(it.hasNext()) {
    Integer key = it.next();
    String value = maps.get(key);
}

// for-each

// 下面该方式效率较高
// 调用map集合的entrySet方法拿到一个set集合，该集合存储的元素就是map集合的键值对
Set<Map.Entry<Integer, String>> entries = maps.entrySet();
```

![image-20240909194243412](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409091942582.png)



#### key 的特点

> **Hashmap：**

- **key无序不可重复（无序指存的顺序和取的顺序不一定一样）**

- **key重复的话，value会覆盖**

**Hash == 散列**

![image-20240910094910345](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409100949493.png)

上面是单向链表，其Node结点有四个属性，put方法的本质就是new node结点

hash值是调用根类中的hashCode方法根据key得到的



![image-20240910100341526](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101003660.png)

> **Hash表的一维数组的长度永远是2的倍数**



#### 哈希表存储原理

![image-20240910104430443](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101044546.png)



> **Hash表的存储原理**

![image-20240910100633835](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101006934.png)



**用哈希值对数组长度取模的作用是其索引值永远不会越界！**



> **哈希表中的key如果是自定义类的话，为了满足以上哈希表的特性，其中的hashCode和equals都得必须一起重写，idea工具提供快捷操作。**



例如下面的User类：

![image-20240910103520791](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101035930.png)





> **Hash表的key可以是null**

![image-20240910104527853](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101045940.png)

- **null不会走存储原理的流程，直接存在哈希表的0号索引处。**



#### 手写HashMap

![image-20240910104659894](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101047005.png)



```java
public class MyHashMap<K, V> {

    private Node<K, V>[] table;

    private int size;

    public int size() {
        return size;
    }


    @SuppressWarnings("unchecked")
    public MyHashMap() {
        this.table = new Node[16];
    }

    static class Node<K, V> {
        int hash;
        K key;
        V value;
        Node<K, V> next;

        public Node(int hash, K key, V value, Node<K, V> next) {
            this.hash = hash;
            this.key = key;
            this.value = value;
            this.next = next;
        }

        @Override
        public String toString() {
            return "[" + key + "," + value + "]";
        }
    }

    public V put(K key, V value) {
        if(null == key) {
            return keyOfNull(key, value);
        }

        int hash = key.hashCode();
        int index = Math.abs(hash % table.length);

        Node<K, V> node = table[index];
        if(null == node) {
            node = new Node<K, V>(hash, key, value, null);
            this.size++;
            return value;
        }

        Node<K, V> prevNode = null;
        while (node != null) {
            if(node.key == key) {
                V oldValue = value;
                node.value = value;
                return oldValue;
            }
            prevNode = node;
            node = node.next;
        }
        prevNode.next = new Node<>(hash, key, value, null);
        return value;

    }

    private V keyOfNull(K key, V value) {
        Node<K, V> node = table[0];

        if(node == null) {
            node = new Node<>(0, key, value, null);
            this.size++;
            return value;
        }

        Node<K, V> prevNode = null;
        while (node != null) {
            if(node.key == null) {
                node.value = value;
                this.size++;
                return node.value;
            }
            prevNode = node;
            node = node.next;
        }

        prevNode.next = new Node<>(0, key, value, null);
        this.size++;
        return value;
    }


    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < table.length; i++) {
            Node<K, V> node = table[i];
            while (node != null) {
                sb.append(node);
                sb.append("\n");
                node = node.next;
            }
        }
        return sb.toString();
    }
}

```



![image-20240910143626897](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101436126.png)



```java
```





#### HashMap在Java8及以后的改变

![image-20240910144935961](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101449059.png)





> **HashMap容量问题**

![image-20240910151906236](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101519418.png)

- **取模操作想要和按位与一样必须要求其值是2的次幂**





> **HashMap初始化容量设置**

![image-20240910154410692](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409101544889.png)

- **为了提高程序效率，应该减少HashMap的扩容次数**

- **初始化为理论存储容量的2的次幂长度，但是有负载因子，所以最终设置值要乘0.75算出来的去接近设置的理论值**



------

#### LinkedHashMap

![image-20240911140614046](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111406125.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111406739.png" alt="image-20240911140632663" style="zoom: 67%;" />

- **有序不可重复**
- **有序指有下标，可以保证元素的插入顺序和取出顺序一致**
- **LinkedHashMap是HashMap的子类，用法和HashMap几乎一致**
- **LinkedHashMap的key也得同时重写equals和hashCode**



```java
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Set;

public class LinkedHashMapTest {
    public static void main(String[] args) {
        LinkedHashMap<Integer, String> maps = new LinkedHashMap<>();
        maps.put(11, "a");
        maps.put(2888, "b");
        maps.put(3, "c");
        maps.put(22, "d");
        
        // 遍历
        Set<Map.Entry<Integer, String>> entries = maps.entrySet();
        for (Map.Entry<Integer, String> entry : entries) {
            System.out.println(entry.getKey() + " " + entry.getValue());
        }
    }
}

```

开销大，一般不用，有需求才用。





#### HashTable

![image-20240911140913613](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111409709.png)



```java
import java.util.*;

public class Hashtable {
    public static void main(String[] args) {
        // Hashtable中独有的迭代方式

        Hashtable<Integer, String> hashTable = new Hashtable<>();

        hashTable.put(1, "a");
        hashTable.put(2, "b");
        hashTable.put(3, "c");

        // 迭代
        // key 迭代
        Enumeration<Integer> keys = hashTable.keys();
        while (keys.hasMoreElements()) {
            Integer i = keys.nextElement();
            System.out.println(i);
        }
        
        // value迭代
        Enumeration<String> elements = hashTable.elements();
        while (elements.hasMoreElements()) {
            String s = elements.nextElement();
            System.out.println(s);
        }
    }
}

```



#### Properties

![image-20240911144602600](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111446675.png)

![image-20240911144536949](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111445082.png)





#### 二叉树

![image-20240911144750089](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111447193.png)



> **排序二叉树**

![image-20240911145107818](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111451919.png)

![image-20240911145738598](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111457691.png)



> **平衡二叉树**

![image-20240911145914304](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111459414.png)





> **红黑树**

![image-20240911150741040](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409111507199.png)



#### TreeMap

![image-20240912221839794](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409122218860.png)

- **该集合存储的key会排好序。**
- **key不能为null，但是value可以**



>  **自定义类做key**

实现comparable接口实现comparaTo方法（适合比较规则不变的情况）

单独的比较器完成排序（比较规则可能改变）

- 因为TreeMap有一个构造方法参数可以传递比较器对象

![image-20240913132502718](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131325857.png)

比较器可以采用匿名内部类的方式

![image-20240913133111200](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131331277.png)



#### 集合null问题的总结

- **Hashtable的 key和 value都不可以为null**
- **properties的 key和 value也不可以为null**
- **TreeMap的key不可以为null**
- **TreeSet不能添加null**





#### Collections工具类

![image-20240913142206179](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131422268.png)



>  **sort排序集合元素为自定义类型时也需要实现排序接口或者比较器进行排序。**



![image-20240913142919731](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409131429813.png)





------



# IO 流

## 概述

![image-20240916141142825](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161411237.png)



> **输入和输出是相对于内存说的**



![image-20240916142245383](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161422568.png)





> **体系结构**

![image-20240916143605937](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161436143.png)



*xmind：*

![image-20240916143650077](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161436292.png)



## FileInputStream

- **文件字节流，负责读**
- **万能的读，但是建议读非文本文件（二进制）**



> **构造方法**

![image-20240916145702126](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161457375.png)

String name：文件的路径



> **常用方法**

![image-20240916145733747](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161457955.png)

int read()：调用一次read方法读取一个字节，返回读到的字节本身，读不到任何数据返回 -1

![image-20240916151948487](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161519651.png)

int read(byte[] b)：一次最多可以读b.length个字节，返回值是读取到的**字节数量**，如果这一次读不到任何数据返回 -1

![image-20240916151853514](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161518748.png)

![image-20240916152240064](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161522234.png)

int read(byte[] b, int off, int len)：一次读len个字节，读取到的数据从off位置开始放，如果这一次读不到任何数据返回 -1

![image-20240916152847267](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161528602.png)

文件内容：abcdef

// 0 0 97 98 99 100 101 0 0 0



long skip(long n)：跳过n个字节



int available()：获取流中预估计的剩余字节数

![image-20240916153344657](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409161533817.png)





## FileOutputStream

![image-20240916204420630](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162044815.png)

- **文件字节输出流，负责写**



> **构造方法**

![image-20240916202902984](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162029211.png)

**FileOutputStream(String name)**  ----  创建一个文件字节输出流对象，这个流在使用的时候，**最开始（第一次写的时候）会将原文件内容全部清空，然后写入。**

**FileOutputStream(String name, boolean append)**  ----  创建一个文件字节输出流对象，**当append为true的时候，不会清空原文件的内容，会在原文件的末尾追加写入，append为false时会清空覆盖。**



> 常用方法

![image-20240916203454813](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162034056.png)

flush：将缓存内容全部写出进行刷新，输出流都有该方法。

![image-20240916203709803](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162037990.png)



> **拷贝文件**

- **使用FileInputStream读文件，使用FileOutputStream写文件**
- **一边读，一边写**

![image-20240916205107763](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162051983.png)



## try-with-resources

Java7新特性

**资源自动关闭：**

​	凡是实现了AutoCloseable接口的流都可以使用try-with-resources，都会自动关闭。

​	**AutoCloseable是Closeable的父亲，意思所有流都支持。**

语法：

```java
try(
    声明流;
    声明流;
    声明流;
) {
    
}catch(Exception e) {
    
}
```

![image-20240916210149456](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162101649.png)



## FileReader

![image-20240916211030259](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162110426.png)

- **文件字符输入流，以字符形式，只适用读普通文本文件**

- **一次至少读取一个完整的字符**



![image-20240916210942389](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162109578.png)



## FileWriter

![image-20240916211058996](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162110170.png)



![image-20240916211553123](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162115316.png)



> **复制普通文本文件**

![image-20240916211920142](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409162119459.png)





## Buffered 缓冲流

![image-20240917152828834](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171528146.png)

![image-20240917150325794](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171503050.png)

写就是利用这个大的bytes数组一次写过去，读的时候也不是和硬盘进行交互，会提前将内容放在内存的大byte数组中，然后程序员去读，目的都是为了**减少IO次数。**



### BufferedInputStream

```java
@Test
public void bufferedInputStreamTest() {
    /*该包装流需要节点输入流*/
    BufferedInputStream bis = null;
    try {
        bis = new BufferedInputStream(new FileInputStream("src/file.txt"));

        byte[] bytes = new byte[1024];
        int readCount = 0;
        while ((readCount = bis.read(bytes)) != -1) {
            System.out.println(new String(bytes, 0, readCount));
        }

    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    } catch (IOException e) {
        throw new RuntimeException(e);
    } finally {
        if (bis != null) {
            try {
                bis.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```



### BufferedOutputStream

```java
@Test
public void bufferedOutputStreamTest() {
    BufferedOutputStream bos = null;
    try {
        bos = new BufferedOutputStream(new FileOutputStream("src/file2.txt"));

        bos.write("wangcai".getBytes());

    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    } catch (IOException e) {
        throw new RuntimeException(e);
    } finally {
        if (bos != null) {
            try {
                bos.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```



> **BufferedReader和BufferedWriter同理**

``BufferedReader中有个方法readLine()是按\n读取一行，当读不到或者末尾了时返回 null 值而不是 -1``





### mark() 与 reset()

![image-20240917154543466](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171545697.png)



读取到什么位置时调用了mark方法就会打上一个标记后接着读

调用reset就会回到刚才上一次打mark方法的位置重复读

目的是重复读取



```java
@Test
public void markAndresetTest() {
    // Reader及子类支持，Writer不支持该机制
    // FileReader 不是节点流
    BufferedReader br = null;
    try {
        br = new BufferedReader(new FileReader("src/file.txt"));

        System.out.println(br.read());
        System.out.println(br.read());
        br.mark(3);
        System.out.println(br.read());
        System.out.println(br.read());
        br.reset();
        System.out.println(br.read());
        System.out.println(br.read());
        System.out.println(br.read());

    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    } catch (IOException e) {
        throw new RuntimeException(e);
    } finally {
        if (br != null) {
            try {
                br.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
/*
97
98
99
100
99
100
101
*/
```



## FileReader

按理说不会乱码的，但是**涉及到解码**的问题，**平台字符集和文档不一致时就会乱码。**

![image-20240917161708752](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171617980.png)



## FileWriter

按理说不会乱码的，但是**涉及到编码**的问题，**平台字符集和文档不一致时就会乱码。**

![image-20240917162306784](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171623002.png)

测试的时候用append方式，不然默认会将测试文档的原有字符集改成平台默认编码UTF-8



## InputStreamReader(转换流)

- **使用InputStreamReader可以指定字符集，可以解决读乱码问题**
- **InputStreamReader是字符流**
- **InputStreamReader是输入的过程，解码的过程**

![image-20240917163126844](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171631143.png)

![image-20240917163152033](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171631215.png)



> **构造方法**

![image-20240917163513934](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171635089.png)



```java
@Test
public void inputStreamReaderTest() {

    InputStreamReader isr = null;
    try {
        isr = new InputStreamReader(new FileInputStream("src/file.txt"), StandardCharsets.UTF_8);

        char[] chars = new char[1024];
        int readCount = 0;
        while((readCount = isr.read(chars)) != -1) {
            System.out.println(new String(chars, 0, readCount));
        }

    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    } catch (IOException e) {
        throw new RuntimeException(e);
    } finally {
        if (isr != null) {
            try {
                isr.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```



> **InputStreamWriter（转换流）同理**



## FileReader是包装流

> **因为它的父类就是包装流**

![image-20240917165358589](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171653778.png)

上小节代码过于冗长，在IO流中给InputStreamReader提供了一个子类：FileReader

![image-20240917165004170](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171650383.png)

- 这里指定字符集不是字符串，是Charset对象

```java
// 可以这样生成该对象
Charset.forName("GBK");

FileReader fr = new FileReader(src, Charset.forName(""));
```





## **OutputStreamWriter(转换流)**

- **使用OutputStreamWriter可以指定字符集，可以解决写乱码问题**
- **OutputStreamWriter是字符流**
- **OutputStreamWriter是输出的过程，编码的过程**
- **FileWriter是OutputStreamWriter的子类，也是包装流**

![image-20240917163152033](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171657614.png)

![image-20240917170544745](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171705984.png)





## DataOutputStream(数据输出流)

> **可以带着数据类型的状态写入文件当中**

- **DataOutputStream写的数据只能用DataIntputStream去读**
- **数据字节输出流，直接将内容写到文件中，写进去就是二进制**
- **写的效率很高，因为不需要转码，包括DataIntputStream**



![image-20240917171323271](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409171713477.png)



```java
@Test
public void dataOutputStreamTest() {
    // 包装流
    DataOutputStream dos = null;
    try {
        dos = new DataOutputStream(new FileOutputStream("src/xixi"));

        byte b = 127;
        short s = 32767;
        int i = 233434;
        long l = 1288888L;
        float f = 2.0F;
        double d = 22.4;
        boolean flag = false;
        char c = '国';
        String str = "嘟嘟哒";

        dos.writeByte(b);
        dos.writeShort(s);
        // ...
        dos.writeUTF(str);

    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    } catch (IOException e) {
        throw new RuntimeException(e);
    } finally {
        if (dos != null) {
            try {
                dos.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```





## DataInputStream(数据输入流)

- **数据字节输入流**
- **专门读取DataOutputStream流写入的文件**
- **读取顺序要和写入的顺序一致（要不然无法恢复原样）**

![image-20240917213815779](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409172138971.png)







## 序列化和反序列化（对象）

![image-20240917215338721](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409172153815.png)



## ObjectOutputStream

- **对象字节输出流**
- **完成对象的序列化过程**
- **可以将JVM中的对象序列化到文件/网络中**
- **序列化：将Java对象转换为字节序列的过程（字节序列可以在网络中传输。）**
- **序列化：serial**



> 构造方法

![image-20240917214655950](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409172146036.png)



```java
@Test
public void objectStreamTest() {
    ObjectOutputStream oos = null;
    try {
        oos = new ObjectOutputStream(new FileOutputStream("data"));

        // 创建Java对象
        Date date = new Date();

        // 序列化 serial
        oos.writeObject(date);

        // 刷新
        oos.flush();

    } catch (IOException e) {
        throw new RuntimeException(e);
    }finally {
        if (oos != null) {
            try {
                oos.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```





## ObjectInputStream

- **对象字节输入流**
- **完成反序列化的（将字节序列转换为JVM中的Java对象）**



> **涉及到多个对象的序列化和反序列化，一般是用集合存储了进行序列化**



```java
@Test
public void objectInputStreamTest() {
    ObjectInputStream ois = null;

    try {
        ois = new ObjectInputStream(new FileInputStream("data"));

        try {
            Date date =(Date) ois.readObject();
            System.out.println(date);

        } catch (ClassNotFoundException e) {
            throw new RuntimeException(e);
        }

    } catch (IOException e) {
        throw new RuntimeException(e);
    }finally {
        if (ois != null) {
            try {
                ois.close();
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```





## 序列化和反序列化自定义类型

> **自定义类型必须实现java.io下的Serializable标志接口**

- **类实现该接口后，编译器会自动给该类添加一个序列化版本号属性**

- ***序列化版本号：serialVersionUID***

- **序列化版本号作用：**

  **在Java语言中是如何区分Class版本的？**

  **首先通过类的名字，然后再通过序列化版本号进行区分**

  **最初的对象序列化以后对该类进行了修改，再进行反序列化时就会报错。**

- **只有同一个Class（类名 + 序列化版本号）才能序列化和反序列化**

![image-20240917222155349](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409172221579.png)



> 建议如果确定这个类还是以前的类，没有问题，建议将序列化版本号写死！

```java
private static final long serialVersionUID = 24455543233L;
```

这样后续修改了代码也能正常反序列化。



注解：

**@java.io.Serial**：检查下面的属性序列号是否正确

在注解上Alt + Enter可以随机生成一个版本序列号。





## transient关键字

> **不让某些属性参与序列化，在属性修饰符上添加transient**



```java
private transient int age;
// 反序列化时只会得到该属性的默认值
```





## PrintStream

![image-20240918104328541](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181043680.png)



> **构造方法**

![image-20240918104800908](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181048002.png)



![image-20240918105250960](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181052059.png)





## PrintWriter

![image-20240918105410980](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181054067.png)



![image-20240918105733396](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181057498.png)





## 标准输入流

![image-20240918110103212](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181101307.png)



```java
@Test
public void inputStreamTest() throws Exception{
    // 获取标准输入流（全局输入流）, 不需要手动关, JVM退出的时候自动关闭该流。
    InputStream in = System.in;  // System.in从控制台读数据

    Scanner sc = new Scanner(in);  // 扫描器

    byte[] bytes = new byte[1024];
    int readCount = in.read(bytes);

    for (int i = 0; i < readCount; i++) {
        System.out.println(bytes[i]);  // 最后的回车是换行符 == 10;
    }
}
```



> 改变标准输入流的数据源（没啥意义）

```java
// System.setIn(InputStream in);

// 修改标准输入流的数据源
System.setIn(new FileInputStream("data"));

// 修改后获取标准输入流
InputStream in = System.in;  // System.in从控制台读数据
```





## 使用缓冲流包装标准输入流

```java
@Test
public void systemInTest() throws Exception{
    // 创建BufferedReader包装流, 为了用它的readLine();
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

    String s = null;
    while((s = br.readLine()) != null) {
        System.out.println("输入了：" + s);
    }

}
```



> **Java已经实现了更好的Scanner扫描器**





## 标准输出流

```java
@Test
public void systemOutTest() throws Exception{
    // 标准输出流对象
    PrintStream out = System.out;  // 向控制台输出

    out.println("s");
}
```



> **标准输出流也可以改变输出方向**

- **可以做日志记录**

```java
@Test
public void systemOutTest2() throws Exception{
    System.setOut(new PrintStream("log"));

    // 获取标准输出流对象
    PrintStream out = System.out;  // 向控制台输出

    out.println("wangcai");
}
```





## File类

> **路径的抽象表现形式，所以File既可能是文件也可能是目录**

- **File和IO流没有继承关系，父类是Object**



![image-20240918114549062](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181145204.png)



```java
@Test
public void fileTest() throws Exception{
    File file = new File("e:\\data\\a\\b\\c");

    /*        if (!file.exists()) {
            file.createNewFile();
        }*/

    if (!file.exists()) {
        file.mkdir();  // 适用一层目录
    }

    if (!file.exists()) {
        file.mkdirs();  // 创建多层目录
    }
    System.out.println(file.getCanonicalPath());
}
```



> **常用方法**

- **delete**
- **getAbsolutePath**
- **getName**
- **getParent**
- **isAbsolute**
- **isDirectory**
- **isFile**
- **isHidden**
- **lastModified**     // 返回long值毫秒数，获取文件最后修改时间点
- **length**  // 获取文件的总字节数（大小）
- **rename**
- **listFiles**







## 筛选过滤后的文件

![image-20240918141031054](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181410207.png)



> **File[] listFiles()**

```java
@Test
public void fileTest() throws Exception{
    File file = new File("E:\\Program Files");

    // 获取所有的子文件包括子目录
    File[] files = file.listFiles();

    for(File f : files) {
        System.out.println(f.getName());
    }
}
```



> **筛选**

```java
@Test
public void fileTest() throws Exception{
    File file = new File("E:\\Git\\Git");

    // 获取所有的子文件包括子目录
    File[] files = file.listFiles(new FilenameFilter() {
        @Override
        public boolean accept(File dir, String name) {
            return name.endsWith(".exe");
        }
    });

    for(File f : files) {
        System.out.println(f.getName());
    }
}
```





## 目录的递归拷贝

listFiles获取所有文件，递归调用进行判断文件类型去拷贝。

```java
@Test
public void dirCopy() {
    // 拷贝源
    File src = new File("E:\\Fonts");
    // 目标
    File pos = new File("E:\\test\\a\\b");

    // 获取拷贝源所有的文件及目录进行拷贝
    copy(src, pos);

}

private void copy(File src, File pos) {
    if(src.isFile()) {
        // 如果是文件进行拷贝文件
        try(FileInputStream in = new FileInputStream(src);
            FileOutputStream out = new FileOutputStream(pos.getAbsolutePath() + src.getAbsolutePath().substring(2))) {

            byte[] bytes = new byte[1024 * 1024];
            int readCount = 0;
            while ((readCount = in.read(bytes)) != -1) {
                out.write(bytes, 0, readCount);
            }

            out.flush();
        }catch (FileNotFoundException e) {
            throw new RuntimeException(e);
        } catch (IOException e) {
            throw new RuntimeException(e);
        } ;
        return;
    };

    // 进入到此处证明是目录, 是目录进行拷贝目录
    
    // 生成路径
    File newFile = new File(pos.getAbsolutePath() + src.getAbsolutePath().substring(2));
    if (!newFile.exists()) {
        newFile.mkdirs();    // 创建多层目录
    }

    File[] files = src.listFiles();
    for(File f : files) {
        System.out.println(f.getAbsolutePath());
        copy(f, pos);
    }
}
```





## 读取属性配置文件

![image-20240918150934542](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181509711.png)



```java
@Test
public void propertiesTest() {

    String path = Thread.currentThread()
        .getContextClassLoader()
        .getResource("jdbc.properties")
        .getPath();

    // pro.load需要Reader流或者InputStream流
    Reader reader = null;
    try {
        reader = new FileReader(path);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }

    Properties pro = new Properties();
    try {
        pro.load(reader);
    } catch (IOException e) {
        throw new RuntimeException(e);
    }

    // 获取属性和值
    // 1. 遍历
    /*        Enumeration<?> enumeration = pro.propertyNames();
        while (enumeration.hasMoreElements()) {
            String names =(String) enumeration.nextElement();
            String value = pro.getProperty(names);
            System.out.println(names + "=" + value);
        }*/

    // 2. 获取需要的, 推荐这种
    String user = pro.getProperty("user");
    String password = pro.getProperty("password");
    String url = pro.getProperty("url");

    System.out.println(user);
    System.out.println(password);
    System.out.println(url);
}
```





## ResourcesBundle资源绑定

java.util.ResourcesBundle绑定属性配置文件



```java
@Test
public void bundleProperties() {
    // 获取资源绑定器   . 或者 / 都可以, 不要加后缀，当做类
    // 从类根路径开始找
    ResourceBundle bundle = ResourceBundle.getBundle("IOStream.jdbc");

    String user = bundle.getString("user");
    String password = bundle.getString("password");
    String url = bundle.getString("url");

    System.out.println(user);
    System.out.println(password);
    System.out.println(url);

}
```





## 装饰器设计模式

![image-20240918161247226](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409181612410.png)

- **目标：在松耦合前提下，完成功能的扩展，代替继承防止类爆炸**
- **在装饰器设计中，两个重要角色：装饰者与被装饰者**

- **装饰器设计模式中，要求装饰者与被装饰者应实现同一个接口/同一些接口/继承同一个抽象类**

- **因为实现同一个接口以后，对于客户端程序来说，使用装饰者时就像在使用被装饰者一样**
- **装饰者中含有被装饰者的引用（A has a B），尽量使用has a[耦合度低一些]，不要使用is a**

``has a == 关联关系，存在其实例属性位置``

``is a == 继承关系 ``



> **简易实现**

```java
// 被装饰者

public interface flyable {
    void fly();
}
```

```java
// 被装饰者

public class Bird implements flyable{
    @Override
    public void fly() {
        System.out.println("Bird fly...");
    }
}
```

```java
public class dog implements flyable{
    @Override
    public void fly() {
        System.out.println("dog can't fly");
    }
}
```

```java
/**
 *  装饰者
 *  有一个被装饰者的引用。
 *  这个引用最好是抽象的，不是具体的。
 *  因为Bird和dog都实现了接口flyable。
 *  因此这里的被装饰者引用，它的类型是flyable。
 * */

public class DecoratorFlyable implements flyable{

    private flyable flyable;

    public DecoratorFlyable(flyable flyable) {
        this.flyable = flyable;
    }

    @Override
    public void fly() {
        // 完成对原功能的扩展
        long start = System.currentTimeMillis();
        flyable.fly();
        long end = System.currentTimeMillis();
        System.out.println("耗时：" + (end - start) + "毫秒");
    }

}
```

```java
public class DecoratorTest {
    public static void main(String[] args) {

        flyable f1 = new DecoratorFlyable(new Bird());
        f1.fly();
        flyable f2 = new DecoratorFlyable(new dog());
        f2.fly();

    }
}
```



> **多个装饰器**

```java
// 被装饰者

public interface flyable {
    void fly();
}
```

```java
// 被装饰者

public class Bird implements flyable{
    @Override
    public void fly() {
        System.out.println("Bird fly...");
    }
}
```

```java
public class dog implements flyable{
    @Override
    public void fly() {
        System.out.println("dog can't fly");
    }
}
```

```java
// 抽象装饰者类

/**
 *  装饰者
 *  有一个被装饰者的引用。
 *  这个引用最好是抽象的，不是具体的。
 *  因为Bird和dog都实现了接口flyable。
 *  因此这里的被装饰者引用，它的类型是flyable。
 * */

public abstract class DecoratorFlyable implements flyable{

    private flyable flyable;

    public DecoratorFlyable(flyable flyable) {
        this.flyable = flyable;
    }

    @Override
    public void fly() {
        flyable.fly();
    }

}
```

```java
// 装饰者实现类1

public class TimeDecorator extends DecoratorFlyable{
    public TimeDecorator(flyable flyable) {
        super(flyable);
    }

    @Override
    public void fly() {
        long start = System.currentTimeMillis();
        super.fly();
        long end = System.currentTimeMillis();
        System.out.println("fly time:"+(end-start));
    }
}
```

```java
// 装饰者实现类2

public class PreDecorotor extends DecoratorFlyable{
    public PreDecorotor(flyable flyable) {
        super(flyable);
    }

    @Override
    public void fly() {
        System.out.println("PreDecorotor");
        super.fly();
    }
}
```

```java
// 测试
public class DecoratorTest {
    public static void main(String[] args) {

        flyable f1 = new PreDecorotor(new TimeDecorator(new Bird()));
        f1.fly();

    }
}
/*
    PreDecorotor
    Bird fly...
    fly time:0
*/
```



***继承关系：***

![image-20240919141434686](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191414790.png)





## GZIPOutputStream(压缩流)

![image-20240919141645464](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191416595.png)

 

```java
@Test
public void gzipOutputStream() throws Exception{

    // 文件输入流
    FileInputStream file = new FileInputStream("e:/test.txt");

    // 创建压缩流
    GZIPOutputStream gzip = new GZIPOutputStream(new FileOutputStream("e:/test.gz"));

    // 读取了压缩写入
    byte[] bytes = new byte[1024];
    int readCount = 0;
    while((readCount = file.read(bytes)) != -1) {
        gzip.write(bytes, 0, readCount);
    }

    // 标志压缩完成并且自动刷新, 不需要手动刷新, 必须写
    gzip.finish();

    file.close();
    gzip.close();
}
```





## GZIPInputStream(解压缩)

节点流不需要手动 刷新，在关闭的时候自动刷新，包装流才需要手动。



```java
@Test
public void gzipInputStreamTest() throws Exception{
    // 解压缩流
    // 创建gzip输入流
    GZIPInputStream gzip = new GZIPInputStream(new FileInputStream("e:/test.txt.gz"));

    // 创建输出流
    FileOutputStream fos = new FileOutputStream("e:/test.txt");

    byte[] bytes = new byte[1024];
    int readCount = 0;
    while((readCount = gzip.read(bytes)) != -1) {
        fos.write(bytes, 0, readCount);
    }

    gzip.close();
    fos.close();
}
```







## 字节数组流(内存流)

![image-20240919144054049](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191440229.png)

![image-20240919144618293](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191446445.png)



> **它两属于节点流**

### ByteArrayOutputStream

```java
@Test
public void byteArrayOutputStreamTest() {

    ByteArrayOutputStream baos = new ByteArrayOutputStream(); // 默认 new 32字节的byte数组

    // 写
    baos.write(1);
    baos.write(2);
    baos.write(3);

    // 获取该byte数组
    byte[] byteArray = baos.toByteArray();
    for(byte b : byteArray) {
        System.out.println(b);
    }

}
```



> **使用包装流包装数组输出流**

```java
@Test
public void byteAaaryOutputStreamAndObjectOutputStream() throws Exception{

    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    ObjectOutputStream oos = new ObjectOutputStream(baos);

    // 写
    oos.write(124);
    oos.writeBoolean(true);
    oos.writeDouble(3.14);
    oos.writeUTF("wangcai");
    oos.writeObject(new Date());

    // 包装流需要手动刷新
    oos.flush();

    // 获取byte数组
    byte[] byteArray = baos.toByteArray();
    for(byte b : byteArray) {
        System.out.println(b);
    }

}
```



### ByteArrayInputStream

> **可以将输出流写入内存的数据恢复原样**

```java
@Test
public void byteAaaryOutputStreamAndObjectOutputStream() throws Exception{

    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    ObjectOutputStream oos = new ObjectOutputStream(baos);

    // 写
    oos.write(124);
    oos.writeBoolean(true);
    oos.writeDouble(3.14);
    oos.writeUTF("wangcai");
    oos.writeObject(new Date());

    // 包装流需要手动刷新
    oos.flush();

    // 获取byte数组并恢复数据
    byte[] byteArray = baos.toByteArray();

    ByteArrayInputStream bais = new ByteArrayInputStream(byteArray);
    ObjectInputStream ois = new ObjectInputStream(bais);

    System.out.println(ois.readInt());
    System.out.println(ois.readBoolean());
    System.out.println(ois.readDouble());
    System.out.println(ois.readUTF());
    System.out.println(ois.readObject());
}
```





## 对象深克隆

![image-20240919152159027](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191521211.png)

**目前为止对象的拷贝方式：**

- **调用Object的clone方法，默认浅克隆，需要深克隆需要重写clone**
- **通过序列化和反序列化完成对象的克隆**
- **通过ByteArrayOutputStream和ByteArrayInputStream完成对象的深克隆**

```java
import java.io.Serial;
import java.io.Serializable;

public class User implements Serializable {

    @Serial
    private static final long serialVersionUID = 5681527863603289588L;

    private String name;
    private int age;
    private Addr add;

    public User(String name, int age, Addr add) {
        this.name = name;
        this.age = age;
        this.add = add;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Addr getAdd() {
        return add;
    }

    public void setAdd(Addr add) {
        this.add = add;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", add=" + add +
                '}';
    }
}
```

```java
import java.io.Serial;
import java.io.Serializable;

public class Addr implements Serializable {
    @Serial
    private static final long serialVersionUID = 5681527863603289589L;

    private String city;

    public Addr(String city) {
        this.city = city;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    @Override
    public String toString() {
        return "Addr{" +
                "city='" + city + '\'' +
                '}';
    }
}
```

```java
import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;

public class Test {
    public static void main(String[] args) throws Exception{
        Addr add = new Addr("成都");
        User user = new User("wangcai", 21, add);

        ByteArrayOutputStream bos = new ByteArrayOutputStream();
        ObjectOutputStream oos = new ObjectOutputStream(bos);

        oos.writeObject(user);
        oos.flush();

        ByteArrayInputStream bis = new ByteArrayInputStream(bos.toByteArray());
        ObjectInputStream ois = new ObjectInputStream(bis);

        User user2 = (User) ois.readObject();
        user2.getAdd().setCity("泸州");

        System.out.println(user);
        System.out.println(user2);
    }
}
/*
	User{name='wangcai', age=21, add=Addr{city='成都'}}
	User{name='wangcai', age=21, add=Addr{city='泸州'}}
*/
```



## IO流总结



















# 线程

## 概述

![image-20240919155459337](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409191554559.png)

- **进程和进程之间是独立的，内存不会共享**



> **JVM规范**

![image-20240920163219138](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409201632457.png)



> **分析下面的线程**

```java
public class Test {
    public static void main(String[] args) {
        System.out.println("main begin");
        m1();
        System.out.println("main end");
    }

    public static void m1() {
        System.out.println("m1 begin");
        m2();
        System.out.println("m1 end");
    }

    public static void m2() {
        System.out.println("m2 begin");
        m3();
        System.out.println("m2 end");
    }

    public static void m3() {
        System.out.println("m3 begin");
        System.out.println("m3 end");
    }
}
```

- **启动了除GC线程外一个线程：main主线程**

- **不是一个方法就是一个线程，main方法和其他方法都在一个虚拟机栈中依次压栈执行的**





## 并发编程与并行编程

![image-20240920180122609](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409201801813.png)





![image-20240920180229830](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409201802937.png)





![image-20240920181653733](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409201816960.png)





## 线程调度模型

![image-20240921111327800](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211113074.png)



> **Java采用的抢占式调度模型**



## 实现线程的方式①

- **编写一个类继承java.lang.Thread**
- **重写run方法**
- **new 线程对象**
- **调用线程对象的start方法来启动线程**

​	

```java
public class implementThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("MyThread" + i);
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        // new线程对象
        implementThread myThread = new implementThread();

        // 启动线程, 开新的栈   run不会启动新线程, 只有run执行完所有的代码才执行下面的代码。
        // start也得执行完才执行下面的，但是start方法栈帧目的是启动线程，开新的栈空间，执行很快，分配完该栈帧就结束。
        myThread.start();

        // 继续编写的代码属于main方法的在主线程中执行
        for (int i = 0; i < 10000; i++) {
            System.out.println("mainThread" + i);
        }
    }
}
```



**start内存图：**

![image-20240921114324712](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211143845.png)

![image-20240921115148194](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211151344.png)





------



**run方法内存图**

![image-20240921114441071](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211144167.png)

![image-20240921114353636](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211143734.png)





## 实现线程的方式②

- **编写类实现java.lang.Runnable接口（可运行的接口）**
- **实现接口中的run方法**
- **new 线程对象**
- **启动start方法**
- **它是普通的类，只不过实现了Runnable接口，并不是线程类**



```java
// 不是线程类，普通类，实现了Runnable接口而已

public class ImplementThread2 implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("t ------> " + i);
        }
    }
}

```

```java
public class Test {
    public static void main(String[] args) {
        // 创建Runnable对象
        Runnable r = new ImplementThread2();
        // new线程对象
        Thread t = new Thread(r);
        
        // Thread t = new Thread(new ImplementThread2());

        // 启动线程, 开新的栈
        t.start();

        // 继续编写代码属于main方法的在主线程中执行
        for (int i = 0; i < 100; i++) {
            System.out.println("mainThread" + i);
        }
    }
}

```

![image-20240921120423228](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211204353.png)



> **更推荐第二种方式，可扩展性更高，保留了类的继承**



> **匿名内部类的方式实现**

```java
public class Test {
    public static void main(String[] args) {
        Thread t = new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 100; i++) {
                    System.out.println("Mythread" + i);
                }
            }
        });

        t.start();
        
        /*  
        	new Thread(new Runnable() {
            	@Override
                public void run() {
                    // ...
                }
        	}).start();
        */

        for (int i = 0; i < 100; i++) {
            System.out.println("mainThread" + i);
        }
    }
}

```

![image-20240921120854527](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409211208670.png)





## 线程常用的三个方法

> **实例方法**

```java
// String getName();   获取线程对象的名字
// void setName(String threadName);   给线程起名字   
```



> **静态方法**

```java
//static Thread  -- currentThread();   // 获取当前的线程对象的引用（地址）
```



```java
public class implementThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("MyThread" + i);
        }

        Thread thread = Thread.currentThread();
        System.out.println(thread.getName());   // Thread-0
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Thread t = new implementThread();

        t.start();

        System.out.println(Thread.currentThread().getName());  // main
    }
}
```







## 线程的生命周期

![image-20240922113036001](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409221130137.png)



**Thread.State ----> enum类型**

- **1. NEW**

​        新建状态

- **2. RUNNABLE**

​        可运行状态

​        细分分为两个子状态：

​                2.1 就绪状态

​                2.2 运行状态

- **3. BLOCKED**

​        阻塞状态

​                遇到锁之后进入锁状态（什么是锁）

- **4. WAITING**

​        等待状态

​                 无期限的等待，没有时长限定。

- **5. TIMED_WAITING**

​        超时等待状态

​                 该状态有时长限定 

- **6. TERMINATED**

​        终止状态（死亡状态）



> **面试时，线程的生命周期说7个状态**

1. 新建状态
2. 就绪状态
3. 运行状态
4. 超时等待状态
5. 等待状态
6. 阻塞状态
7. 终止状态



![image-20240923145639339](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231456519.png)





## 线程的休眠

静态方法 sleep()：

```java
static void sleep(long millis)
```

静态方法，没有返回值。

**作用：**

​			**让当前线程进入休眠，也就是让当前线程放弃占有的CPU时间片，让其进入阻塞状态，如果占有对象锁不会放弃对象锁**

​			**阻塞参数毫秒时长，指定时间内当前线程没有权限抢夺CPU时间片**

```java
public class Test {
    public static void main(String[] args) {
        try {
            Thread.sleep(1000 * 5);  // 当前线程主线程休眠5秒
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        for (int i = 0; i < 10; i++) {
            System.out.println("---->" + i);
        }
    }
}

```



> **sleep面试题**

下面让main休眠还是t线程？

```java
public class ImplementThread2 implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("t ------> " + i);
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {

        Thread t = new Thread(new ImplementThread2());
        t.setName("t");
        t.start();

        try {
            t.sleep(1000 * 5);   // 等同于Thread.sleep()
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        for (int i = 0; i < 10; i++) {
            System.out.println("main----> " + i);
        }
    }
}
```

- ***休眠的是主线程***





## 中断线程的阻塞

解除线程因sleep导致的阻塞，让其开始抢夺时间片。



> **xxx.interrupt();   // 实例方法, 利用了异常机制**

```java
public class Test {
    public static void main(String[] args) {
        Thread t = new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + " ----> begin");
                try {
                    Thread.sleep(1000 * 60 * 60 * 24 * 365);  // 休眠365天
                } catch (InterruptedException e) {
                    e.printStackTrace();   // java.lang.InterruptedException: sleep interrupted
                }

                // 休眠后执行的代码
                System.out.println(Thread.currentThread().getName() + " ----> do some");
            }
        });

        t.start();

        // 主线程
        // Thread-0线程原本休眠一年, 我要求5秒后就起来干活
        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        // Thread-0起来干活
        t.interrupt();   // 打扰干扰的意思, 立即让Thread-0抛异常, 异常抛出后try-catch立即结束, 于是结束休眠, 利用了异常处理机制。
    }
}

```





## 终止线程的执行

> **一个线程t一直在运行，实际中我们会用打标记的方式进行终止**



```java
public class ImplementThread2 implements Runnable{
    boolean run = true;

    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if(run) {
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName() + "------> " + i);
            }else {
                return;
            }
        }
    }
}

```

```java
public class Test {
    public static void main(String[] args) {

        ImplementThread2 mr = new ImplementThread2();
        Thread t = new Thread(mr);

        t.setName("t");
        t.start();

        // 5s后终止
        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        mr.run = false;

    }
}
```





## 守护线程

> **在Java中线程被分为两大类，一类是用户线程（非守护线程），一类是守护线程（后台线程）**

之前的内容就是用户线程

在JVM中，有一个隐藏的守护线程一直在守护着，就是GC线程

**守护线程的特点：所有的用户线程结束后，守护线程自动退出/结束**

 **main线程默认是用户线程**



``xxx.setDaemon(true);``

```java
public class Test {
    public static void main(String[] args) {
        Thread myThread = new MyThread();
        myThread.setName("t");

        // 设置为守护线程
        myThread.setDaemon(true);
		
        // 设置完后再启动线程
        myThread.start();

        // main线程10s结束
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName() + " ----> " + i);

            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }


    }
}


class MyThread extends Thread {
    @Override
    public void run() {
        int i = 0;
        for (; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + " ----> " + i);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```

- **守护线程就是为用户线程服务的**







## 定时任务

- **java.util.Timer**

![image-20240923140719560](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231407711.png)

![image-20240923140731864](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231407969.png)



```java
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.TimerTask;

public class LogTimerTask extends TimerTask {
    SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
    int count;

    @Override
    public void run() {
        Date date = new Date();
        String sdfTime = sdf.format(date);
        System.out.println(sdfTime + ": " + count++);
    }
}
```

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Timer;

/**
 * JDK提供的类库：（真实开发中也不用，后面框架封装了）
 * java.util.Timer       // 定时器
 * java.util.TimerTask   // 定时任务
 * 定时器 + 定时任务 == 间隔xxx执行一次定时任务
 * */
public class Test {
    public static void main(String[] args) {
        // 创建定时器对象(本质上就是一个线程)
        // 如果该线程是后台任务，建议设置为守护线程
        Timer timer = new Timer(true);  // 设置为守护线程

        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
        Date firstTime = null;
        try {
            firstTime = sdf.parse("2024-9-23 14:23:00 000");
        } catch (ParseException e) {
            throw new RuntimeException(e);
        }
        // 指定定时任务
        timer.schedule(new LogTimerTask(), firstTime, 1000);
    }
}
```

- **LogTimerTask也可以采用匿名内部类的方式传入schedule**





## 线程合并

> **1. 调用join()完成线程合并**
>
> **2. join()是一个实例方法**
>
> **3. 假设在main方法（main线程）中调用了t.join()，后果是什么？**
>
> ​		**t 线程合并到主线程中，主线程进行阻塞状态，直到 t 线程执行结束，主线程阻塞结束**
>
> **4. t.join()作用就是让当前线程进入阻塞状态，直到 t 线程执行结束，当前线程阻塞解除（阻塞当前线程，先完成 t 线程的活）**
>
> **5. 和sleep方法有点类似，但不一样：**
>
> ​		**sleep是静态方法，join是实例**
>
> ​		**sleep可以指定阻塞的时长，join不能保证**
>
> ​		**sleep和join都是让当前线程进入阻塞**
>
> ​       **sleep阻塞结束是时间结束，join阻塞结束是调用方法的线程执行结束了**



```java
public class joinThread {
    public static void main(String[] args) {
        Thread myThread = new MyThread();
        myThread.setName("t");

        myThread.start();

        System.out.println("main begin");

        try {
            // join也可以指定预计时间毫秒, 但是和sleep不一样, 指定的时间代表只合并多少秒, 但是不一定，如果指定时间内线程就结束了那阻塞也立即结束。
            // myThread.join(8);  合并8毫秒
            myThread.join(8);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + "----> " + i);
        }

        System.out.println("main end");
    }
}

class MyThread extends Thread {

    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + " ----> " + i);
        };
    }
}
```





## 线程的优先级

> **关于线程生命周期中的JVM调度**
>
> ​		**1. 优先级**
>
> ​		**2. 线程是可以设置优先级的，优先级高的，获得CPU时间片的总体概率高一些**
>
> ​		**3. Java采用的抢占式调度模型，优先级高，获得CPU时间片的总体概率就高**
>
> ​		**4. 默认情况下，一个线程的优先级是 5**
>
> ​		**5. 最低是 1，最高是 10**



```java
public class PriorityThread {
    public static void main(String[] args) {
        System.out.println("线程最低优先级：" + Thread.MIN_PRIORITY);  // 1
        System.out.println("线程最高优先级：" + Thread.MAX_PRIORITY);  // 10
        System.out.println("线程默认优先级：" + Thread.NORM_PRIORITY); // 5
    }
}
```

![image-20240923150159609](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231501696.png)



- **main线程优先级**

```java
public class PriorityThread {
    public static void main(String[] args) {
        // 获取main线程优先级
        Thread mainThread = Thread.currentThread();
        System.out.println(mainThread.getPriority());  // 5
    }
}
```



> **设置优先级方法**

```java
public class PriorityThread {
    public static void main(String[] args) {
        // 获取main线程优先级
        Thread mainThread = Thread.currentThread();
        System.out.println(mainThread.getPriority());  // 5

        // 更改线程优先级, main线程为例
        mainThread.setPriority(10);
        System.out.println(mainThread.getPriority());  // 10
    }
}
```





## 线程让位

> **关于JVM的调度：**
>
> ​		**1. 让位**
>
> ​		**2. 静态方法：Thread.yield()**
>
> ​		**3. 让当前线程让位**
>
> ​		**4. 注意：让位不会让当前线程进入阻塞状态。只是放弃目前占有的时间片，让其进入就绪状态，继续抢夺时间片**
>
> ​		**5. 只能保证大方向上的，大概率，到了某个点让位一次**



```java
public class yieldThread {
    public static void main(String[] args) {
        Thread t1 = new MyThread2();
        t1.setName("t1");
        Thread t2 = new MyThread2();
        t1.setName("t2");

        t1.start();
        t2.start();
    }
}


class MyThread2 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 200; i++) {
            System.out.println(Thread.currentThread().getName() + " ----> " + i);
            if(Thread.currentThread().getName().equals("t2") && i % 10 == 0) {
                System.out.println(Thread.currentThread().getName() + "让位了" + "当前i：" + i);
                Thread.yield();
            }
        }
    }
}
```







## 线程安全问题

> **什么情况需要考虑线程安全？**
>
> ​	**1. 多线程的并发环境下**
>
> ​	**2. 有共享的数据**
>
> ​	**3. 共享数据涉及到修改操作**
>
> **一般情况下： 局部变量不存在线程安全问题[在栈中，栈是私有的]。（尤其是基本数据类型，引用数据类型另说）**
>
> ​								**实例变量存在线程安全，实例变量在堆中。堆是多线程共享的**
>
> ​								**静态变量也可能存在，因为静态变量在堆中。堆是多线程共享的**



![image-20240923164117317](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231641497.png)

- 让线程不要并发进行排队执行，叫做**线程同步机制**

- 不排队，就是并发，叫做**线程异步机制**

![image-20240923171927978](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231719128.png)





> **演示线程安全问题**



```java
public class synchronizedTest {
    public static void main(String[] args) {
        User user = new User("wc", 10000);

        Thread t1 = new Thread(new Withdraw(user));
        Thread t2 = new Thread(new Withdraw(user));

        t1.start();
        t2.start();
    }
}


class Withdraw implements Runnable {
    User user;

    public Withdraw(User user) {
        this.user = user;
    }

    @Override
    public void run() {
        this.user.QuKuan(1000);
    }
}

class User {
    private String userNo;
    private int money;

    public User(String userNo, int money) {
        this.userNo = userNo;
        this.money = money;
    }

    public String getUserNo() {
        return userNo;
    }

    public void setUserNo(String userNo) {
        this.userNo = userNo;
    }

    public int getMoney() {
        return money;
    }

    public void setMoney(int money) {
        this.money = money;
    }

    public void QuKuan(int money) {
        System.out.println(Thread.currentThread().getName() + "取款操作中" + money + "账户当前余额: " + this.getMoney());

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        // 取
        this.setMoney(this.getMoney() - money);

        System.out.println(Thread.currentThread().getName() + "取款完成" + "余额为：" + this.getMoney());
    }

```

![image-20240923175224383](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231752512.png)





## 同步代码块

> **同步代码块**



```java
/**
 * 使用线程同步机制来保证多线程并发下的数据安全问题
 * 1.线程同步的本质：线程排队执行
 * 2.语法格式：
 *      synchronized(必须是需要排队的这几个线程共享的对象) {
 *          // 需要同步的代码
 *      }
 *
 * 必须是需要排队的这几个线程共享的对象：必须选对，不然会无辜增加同步数量，导致效率变低。
 *
 * 3.原理：
 *      synchronized(obj) {
 *          // 同步代码块
 *      }
 *      假设obj是 t1 和 t2 两个线程共享的。
 *      t1和 t2一定会有一个先抢到CPU时间片, 一定有先后顺序。
 *      假设 t1 先抢到CPU时间片, 那 t1 线程找共享对象obj的对象锁, 找到后则占用这把锁。
 *      只要能够占有obj对象的对象锁, 就有权力进入同步代码块执行。
 *      当 t1 线程执行完同步代码块后, 会释放之前占有的对象锁（归还锁）
 *      同样, t2 线程抢到CPU时间片后, 也开始执行, 也会去找共享对象obj的对象锁, 但由于 t1 占有, t2线程只能在同步代码块外等待。
 *      同步代码块范围也不要无辜扩大
 * */

public class synchronizedTest {
    public static void main(String[] args) {
        User user = new User("wc", 10000);

        Thread t1 = new Thread(new Withdraw(user));
        Thread t2 = new Thread(new Withdraw(user));

        t1.start();
        t2.start();
    }
}


class Withdraw implements Runnable {
    User user;

    public Withdraw(User user) {
        this.user = user;
    }

    @Override
    public void run() {
        this.user.QuKuan(1000);
    }
}

class User {
    private String userNo;
    private int money;

    public User(String userNo, int money) {
        this.userNo = userNo;
        this.money = money;
    }

    public String getUserNo() {
        return userNo;
    }

    public void setUserNo(String userNo) {
        this.userNo = userNo;
    }

    public int getMoney() {
        return money;
    }

    public void setMoney(int money) {
        this.money = money;
    }

    public void QuKuan(int money) {
        // 当前对象this就是t1 和 t2 共享的对象
        synchronized (this) {
            System.out.println(Thread.currentThread().getName() + "取款操作中" + money + "账户当前余额: " + this.getMoney());

            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }

            // 取
            this.setMoney(this.getMoney() - money);

            System.out.println(Thread.currentThread().getName() + "取款完成" + "余额为：" + this.getMoney());
        }
    }
}
```

![image-20240923180813963](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409231808099.png)





## 同步实例方法

> **在实例方法上也可以添加synchronized修饰符 == 整个方法是同步代码块，但是方法上添加共享对象的对象锁一定是this对象**



```java
public synchronized void QuKuan(int money) {
    // 当前对象this就是t1 和 t2 共享的对象
    System.out.println(Thread.currentThread().getName() + "取款操作中" + money + "账户当前余额: " + this.getMoney());

    try {
        Thread.sleep(1000);
    } catch (InterruptedException e) {
        throw new RuntimeException(e);
    }

    // 取
    this.setMoney(this.getMoney() - money);

    System.out.println(Thread.currentThread().getName() + "取款完成" + "余额为：" + this.getMoney());

}
```

- **恰好共享对象是this和整个方法体都是同步代码块时这样用**







## 同步机制面试题

**1. **

```java
/**
 * m2在执行时需不需要等待m1的结束？
 * */
public class PreThreadTest {
    public static void main(String[] args) {
        MyClass mc = new MyClass();
        Thread t1 = new Thread(new MyRunnable(mc));
        Thread t2 = new Thread(new MyRunnable(mc));

        t1.setName("t1");
        t2.setName("t2");

        t1.start();

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        t2.start();
    }
}


class MyRunnable implements Runnable {
    private MyClass mc;

    public MyRunnable(MyClass mc) {
        this.mc = mc;
    }

    @Override
    public void run() {
        if(Thread.currentThread().getName().equals("t1")) {
            mc.m1();
        }
        if (Thread.currentThread().getName().equals("t2")) {
            mc.m2();
        }
    }
}

class MyClass {
    public synchronized void m1() {
        System.out.println("m1 begin");

        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        System.out.println("m1 over");
    }

    public void m2() {
        System.out.println("m2 begin");
        System.out.println("m2 over");
    }
}
```

![image-20240924105204521](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241052707.png)



> **m2的执行不需要等待m1的结束，因为m2没有synchronized修饰，不需要找对象锁**



**2.**

```java
public class PreThreadTest {
    public static void main(String[] args) {
        MyClass mc = new MyClass();
        Thread t1 = new Thread(new MyRunnable(mc));
        Thread t2 = new Thread(new MyRunnable(mc));

        t1.setName("t1");
        t2.setName("t2");

        t1.start();

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        t2.start();
    }
}


class MyRunnable implements Runnable {
    private MyClass mc;

    public MyRunnable(MyClass mc) {
        this.mc = mc;
    }

    @Override
    public void run() {
        if(Thread.currentThread().getName().equals("t1")) {
            mc.m1();
        }
        if (Thread.currentThread().getName().equals("t2")) {
            mc.m2();
        }
    }
}

class MyClass {
    public synchronized void m1() {
        System.out.println("m1 begin");

        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        System.out.println("m1 over");
    }

    public synchronized void m2() {
        System.out.println("m2 begin");
        System.out.println("m2 over");
    }
}
```

![image-20240924105436420](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241054513.png)





**3. **

```java
/**
 * m2在执行时需不需要等待m1的结束？
 * */
public class PreThreadTest {
    public static void main(String[] args) {
        MyClass mc1 = new MyClass();
        MyClass mc2 = new MyClass();
        Thread t1 = new Thread(new MyRunnable(mc1));
        Thread t2 = new Thread(new MyRunnable(mc2));

        t1.setName("t1");
        t2.setName("t2");

        t1.start();

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        t2.start();
    }
}


class MyRunnable implements Runnable {
    private MyClass mc;

    public MyRunnable(MyClass mc) {
        this.mc = mc;
    }

    @Override
    public void run() {
        if(Thread.currentThread().getName().equals("t1")) {
            mc.m1();
        }
        if (Thread.currentThread().getName().equals("t2")) {
            mc.m2();
        }
    }
}

class MyClass {
    public synchronized void m1() {
        System.out.println("m1 begin");

        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        System.out.println("m1 over");
    }

    public synchronized void m2() {
        System.out.println("m2 begin");
        System.out.println("m2 over");
    }
}
```

![image-20240924105702331](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241057428.png)



> **不需要等待m1结束，因为两个线程持有的对象锁不一致**





**4. **

> **synchronized出现在static方法上，线程同步会找类锁**
>
> **不管创建多少对象，类锁只有一把，因为类只有一个类**



```java
/**
 * m2在执行时需不需要等待m1的结束？
 * */
public class PreThreadTest {
    public static void main(String[] args) {
        MyClass mc1 = new MyClass();
        MyClass mc2 = new MyClass();
        Thread t1 = new Thread(new MyRunnable(mc1));
        Thread t2 = new Thread(new MyRunnable(mc2));

        t1.setName("t1");
        t2.setName("t2");

        t1.start();

        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        t2.start();
    }
}


class MyRunnable implements Runnable {
    private MyClass mc;

    public MyRunnable(MyClass mc) {
        this.mc = mc;
    }

    @Override
    public void run() {
        if(Thread.currentThread().getName().equals("t1")) {
            mc.m1();
        }
        if (Thread.currentThread().getName().equals("t2")) {
            mc.m2();
        }
    }
}

class MyClass {
    public static synchronized void m1() {
        System.out.println("m1 begin");

        try {
            Thread.sleep(1000 * 5);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        System.out.println("m1 over");
    }

    public static synchronized void m2() {
        System.out.println("m2 begin");
        System.out.println("m2 over");
    }
}
```

![image-20240924110118829](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241101926.png)



> **需要等待，因为静态方法线程同步找类锁，只有一把类锁会排队**



**总结：**

- **静态方法添加synchronized实际是为了保障静态变量的安全**
- **实例方法添加synchronized实际是为了保障实例变量的安全**





## 死锁

![image-20240924111306086](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241113198.png)

> **t1先拿到o1的对象锁然后向下执行拿o2**
>
> **t2先拿到o2的对象锁然后向上执行拿o1**
>
> **此时会出现t1先拿到o1对象锁，t2先拿到o2对象锁，这时两个线程都想拿对方的对象锁，又不肯释放自己手里的锁，就会进入死锁状态**



**示例：**

```java
public class DeadlockExample {
    public static void main(String[] args) {
        Object resource1 = new Object();
        Object resource2 = new Object();

        // Thread 1
        Thread t1 = new Thread(() -> {
            synchronized (resource1) {
                System.out.println("Thread 1: Locked resource 1");

                try {
                    Thread.sleep(100); // 模拟其他操作，增加死锁的可能性
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                synchronized (resource2) {
                    System.out.println("Thread 1: Locked resource 2");
                }
            }
        });

        // Thread 2
        Thread t2 = new Thread(() -> {
            synchronized (resource2) {
                System.out.println("Thread 2: Locked resource 2");

                try {
                    Thread.sleep(100); // 模拟其他操作，增加死锁的可能性
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                synchronized (resource1) {
                    System.out.println("Thread 2: Locked resource 1");
                }
            }
        });

        // Start the threads
        t1.start();
        t2.start();
    }
}
```



## 线程生命周期（7种）

官方给的6个，7个是将Runnable细分为了就绪和运行

![image-20240923145639339](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241250037.png)







## 多线程卖票问题

```java
/**
 * 模拟三个窗口卖票
 * */
public class SellTicket {
    public static void main(String[] args) {

        MyRunnable mr = new MyRunnable();
        Thread t1 = new Thread(mr);
        Thread t2 = new Thread(mr);
        Thread t3 = new Thread(mr);
        t1.setName("1");
        t2.setName("2");
        t3.setName("3");

        t1.start();
        t2.start();
        t3.start();

    }
}


class MyRunnable implements Runnable {

    private int ticketTotal = 100;

    @Override
    public void run() {
        // 实现卖票业务
        while(true) {
            // synchronized 线程同步机制
            // synchronized 又叫互斥锁
            synchronized (this) {
                if(this.ticketTotal <= 0) {
                    System.out.println("票已售空");
                    break;
                }

                // 模拟出票
                try {
                    Thread.sleep(50);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                System.out.println("窗口" + Thread.currentThread().getName() + "售出一张票，还剩" + (--ticketTotal) + "张票");
            }
        }
    }
}
```







## 线程通信的三个方法

![image-20240924133046088](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241330300.png)

![image-20240924134454904](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241344059.png)

- **obj.wait()调用了，会释放之前占有的对象锁**

- **共享对象.notify()，调用后唤醒优先级最高的等待线程，如果优先级一样，则随机唤醒一个。**



``两个线程要求交替输出1-100``

```java
public class ThreadTest {
    public static void main(String[] args) {
        MyRunnable22 mr = new MyRunnable22();
        Thread t1 = new Thread(mr);
        Thread t2 = new Thread(mr);

        t1.setName("t1");
        t2.setName("t2");

        t1.start();
        t2.start();

    }
}

class MyRunnable22 implements Runnable {

    private int count = 0;

    @Override
    public void run() {
        while(true) {
            synchronized (this) {
                // 唤醒被等待的线程
                // 这里唤醒了也不会执行，因为对象锁被另外个线程占有了
                this.notify();

                if(count >= 100) break;
                // 模拟延迟
                try {
                    Thread.sleep(50);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                System.out.println(Thread.currentThread().getName() + " ----> " + (++count));

                try {
                    // 这里进入等待状态的可能是t1 也可能是t2
                    // 进入的无期限等待状态，并且等待的时候不占用对象锁
                    this.wait();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

- **同步代码块里的共享对象要和synchronized()里的保持一致**





``实现三个线程交替输出``

> **题目：**
>
> **按以下顺序**
>
> **t1 --> A**
>
> **t2 --> B**
>
> **t3 --> C**
>
> **...**
>
> **t1 --> A**
>
> **t2 --> B**
>
> **t3 --> C**
>
> **总共十组**

```java
public class ThreadTest {

    private static Object lock = new Object();

    private static boolean t1Output = true;
    private static boolean t2Output = false;
    private static boolean t3Output = false;

    public static void main(String[] args) {

        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized(lock) {
                    for (int i = 0; i < 10; i++) {
                        while (!t1Output) {
                            try {
                                lock.wait();
                            } catch (InterruptedException e) {
                                throw new RuntimeException(e);
                            }
                        }

                        System.out.println(Thread.currentThread().getName() + " ----> A");

                        t1Output = false;
                        t2Output = true;
                        t3Output = false;

                        // 唤醒所有线程
                        lock.notifyAll();
                    }
                }
            }
        }).start();

        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized(lock) {
                    for (int i = 0; i < 10; i++) {
                        while (!t2Output) {
                            try {
                                lock.wait();
                            } catch (InterruptedException e) {
                                throw new RuntimeException(e);
                            }
                        }

                        System.out.println(Thread.currentThread().getName() + " ----> B");

                        t1Output = false;
                        t2Output = false;
                        t3Output = true;

                        // 唤醒所有线程
                        lock.notifyAll();
                    }
                }
            }
        }).start();


        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized(lock) {
                    for (int i = 0; i < 10; i++) {
                        while (!t3Output) {
                            try {
                                lock.wait();
                            } catch (InterruptedException e) {
                                throw new RuntimeException(e);
                            }
                        }

                        System.out.println(Thread.currentThread().getName() + " ----> C");

                        t1Output = true;
                        t2Output = false;
                        t3Output = false;

                        // 唤醒所有线程
                        lock.notifyAll();
                    }
                }
            }
        }).start();
    }
}
```







## 总结线程通信

``线程完整的生命周期``

![image-20240924192502095](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409241925274.png)





## 懒汉式单例模式线程安全问题

```java
public class SingletonTest {

    private static Singleton s1 = null;
    private static Singleton s2 = null;

    public static void main(String[] args) {

        // 线程对象1
        Thread t1 = new Thread(new Runnable() {
            @Override
            public void run() {
                s1 = Singleton.getSingleton();
            }
        });

        // 线程对象2
        Thread t2 = new Thread(new Runnable() {
            @Override
            public void run() {
                s2 = Singleton.getSingleton();
            }
        });

        // 该方法只是启动线程，瞬间就结束了，run还没来得及结束，主线程就会执行下面的代码
        t1.start();
        t2.start();

        // 因为run还没执行，所以下面都是null和true
        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s1 == s2);

    }
}


// 懒汉式单例模式
class Singleton {

    private static Singleton singleton = null;

    private Singleton() {
    }

    public static Singleton getSingleton() {
        if(singleton == null) singleton = new Singleton();
        return singleton;
    }
}
```

![image-20240925112606603](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409251126784.png)



``要么让主线程sleep要么用join方法阻塞主线程``

```java
try {
    t1.join();
} catch (InterruptedException e) {
    throw new RuntimeException(e);
}

try {
    t2.join();
} catch (InterruptedException e) {
    throw new RuntimeException(e);
}
```





``多线程下如果t1进入if语句时还没执行完t2也进入了就会造成new两个对象``

```java
public class SingletonTest {

    private static Singleton s1;
    private static Singleton s2;

    public static void main(String[] args) {

        // 线程对象1
        Thread t1 = new Thread(new Runnable() {
            @Override
            public void run() {
                s1 = Singleton.getSingleton();
            }
        });

        // 线程对象2
        Thread t2 = new Thread(new Runnable() {
            @Override
            public void run() {
                s2 = Singleton.getSingleton();
            }
        });

        // 该方法只是启动线程，瞬间就结束了，run还没来得及结束，主线程就会执行下面的代码
        t1.start();
        t2.start();

        try {
            t1.join();
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        try {
            t2.join();
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        // 因为run还没执行，所以下面都是null和true
        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s1 == s2);

    }
}


// 懒汉式单例模式
class Singleton {

    private static Singleton singleton;

    private Singleton() {
    }

/*    第一种方案
    public static synchronized Singleton getSingleton() {
        if(singleton == null) {
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            singleton = new Singleton();
        }
        return singleton;
    }*/

    // 第二种方案也是拿类锁
    // 类名.class == 获取某个类
    public static Singleton getSingleton() {
        // 对象为空才去拿对象锁
        if(singleton == null) {
            synchronized (Singleton.class) {
                if(singleton == null) {
                    try {
                        Thread.sleep(2000);
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}
```





## ReentrantLock可重入锁

![image-20240925115438703](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409251154880.png)

线程同步不一定得synchronized，可以用re/entrant/Lock替代，比sync更加灵活，**官方文档更建议使用ReentrantLock**

``JUC == java.util.concurrent``



```java
import java.util.concurrent.locks.ReentrantLock;

public class SingletonTest {

    private static Singleton s1;
    private static Singleton s2;

    public static void main(String[] args) {

        // 线程对象1
        Thread t1 = new Thread(new Runnable() {
            @Override
            public void run() {
                s1 = Singleton.getSingleton();
            }
        });

        // 线程对象2
        Thread t2 = new Thread(new Runnable() {
            @Override
            public void run() {
                s2 = Singleton.getSingleton();
            }
        });

        // 该方法只是启动线程，瞬间就结束了，run还没来得及结束，主线程就会执行下面的代码
        t1.start();
        t2.start();

        try {
            t1.join();
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        try {
            t2.join();
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        // 因为run还没执行，所以下面都是null和true
        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s1 == s2);

    }
}


// 懒汉式单例模式
class Singleton {

    private static Singleton singleton;

    private Singleton() {
        System.out.println("构造方法执行了");
    }


    // 使用Lock实现线程安全
    // Lock是接口, Java5开始引入
    // Lock的一个实现类：ReentrantLock(可重入锁)
    // 要想使多线程达到同步，假设让t1, t2, t3达到, 这里的lock就得是共享对象, 所以static不能去
    private static final ReentrantLock lock = new ReentrantLock();

    public static Singleton getSingleton() {
        if(singleton == null) {
            try {
                // 加锁
                lock.lock();
                if(singleton == null) {
                    try {
                        Thread.sleep(2000);
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                    singleton = new Singleton();
                }
            } finally {
                // 解锁，为了百分百解锁，使用finally
                lock.unlock();
            }
        }
        return singleton;
    }
}
```





## 实现线程的方式③

``实现Callable接口中的call方法``



```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * 实现Callable接口, 实现call方法。
 * 这种方式可以获取线程的返回值。
 * */

public class Test2 {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        FutureTask<Integer> task = new FutureTask<>(new Callable<Integer>() {
            @Override
            public Integer call() throws Exception {
                // ....
                Thread.sleep(1000 * 5);
                return 1;
            }
        });

        Thread t = new Thread(task);  // 本质还是Runnable

        t.setName("t");
        t.start();

        // 获取未来任务的返回值
        // 会阻塞当前的线程，因为只有等task的线程执行完以后才能拿返回值
        Integer i = task.get();
        System.out.println(i);
    }
}
```





## 实现线程的方式④

``线程池Executors，本质也是缓存技术cache，顾名思义提前在池中创建好t1，t2，t3...线程，需要的时候直接拿，以此提高效率``



```java
// 一般是服务器启动的时候初始化
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Test3 {
    public static void main(String[] args) {

        // 初始化线程池对象，初始化3个线程
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // 将任务交给线程池对象即可，不需要接触线程对象
        executorService.submit(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 10; i++) {
                    System.out.println(Thread.currentThread().getName() + " ----> " + i);
                }
            }
        });

        // 最后关闭线程池
        executorService.shutdown();

    }
}

```

![image-20240930142231731](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409301422969.png)











# 反射

------

``提供一套类库可以操作/读取class字节码文件``

``反射机制最核心的几个类``

``java.lang.Class: Class类型的实例代表硬盘上的某个class文件。或者说代表某一种类型。``

***String.class文件***

***System.class文件***

***Date.class文件***

``java.lang.reflect.Field: Field类型的实例代表``

``java.lang.reflect.Constructor: Constructor类型的实例代表中的构造方法 ``

``java.lang.reflect.Method: Method类型的实例代表中的方法``

![image-20240930150221834](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409301502037.png)



``①静态方法Class.forname("")``

```java
public class ReflectTest01 {
    public static void main(String[] args) throws ClassNotFoundException {
        // stringClass就代表字符串类型
        // stringClass代表硬盘上的String.class文件

        Class stringClass = Class.forName("java.lang.String");

        Class userClass = Class.forName("Reflect.User");  // 会进行类加载
    }
}

```



``②obj.getClass()``

```java
public class ReflectTest01 {
    public static void main(String[] args) throws ClassNotFoundException {
        // stringClass就代表String类型
        // stringClass代表硬盘上的String.class文件

        Class stringClass = Class.forName("java.lang.String");

        Class userClass = Class.forName("Reflect.User");  // 会进行类加载

        String s = "wangcai";
        Class stringClass2 = s.getClass();

        // 某种类型的字节码文件在内存中只有一份
        System.out.println(stringClass == stringClass2);  // true, 都是String类型

    }
}
```



``③在Java中, 任何一种类型包括基本数据类型都有.class属性, 该属性可以获取Class实例``

```java
public class ReflectTest01 {
    public static void main(String[] args) throws ClassNotFoundException {

        Class intClass = int.class;
        Class stringClass = String.class;

        
    }
}
```



## 通过反射机制实例化对象

``Class类型.newInstance()``

```java
public class ReflectTest02 {
    public static void main(String[] args) throws Exception {

        // 获取Class类型的实例后，通过反射机制实例化对象
        Class<?> userClass = Class.forName("Reflect.User");

        // 通过userClass实例化对象，userClass代表的就是User类型 Java9后标注过时
        // 底层原理就是调用其无参构造方法完成实例化创建
        User user = (User) userClass.newInstance();

        System.out.println(user);

    }
}
```



## 结合配置文件灵活实例化对象

在配置文件中存储className

``.properties``

```properties
className=Reflect.User
```



```java
import java.util.ResourceBundle;

public class ReflectTest03 {
    public static void main(String[] args) throws Exception {
        ResourceBundle bundle = ResourceBundle.getBundle("Reflect.className");
        String className = bundle.getString("className");

        Class userClass = Class.forName(className);

        Object o = userClass.newInstance();
        System.out.println(o);

    }
}
```



## 反射Class的Field

``Vip类``

```java
public class Vip {
    public String name;

    private int age;

    protected String birth;

    boolean gender;

    public static String address = "四川成都";

    public static final String GRADE = "金牌";
}

```

``测试``

```java
import java.lang.reflect.Field;
import java.lang.reflect.Modifier;

/**
 * java.lang.reflect.Field(代表一个类中的字段/属性)
 * */
public class ReflectTest04 {
    public static void main(String[] args) throws ClassNotFoundException {
        // 拿到整个类
        Class<?> vipClass = Class.forName("Reflect.Vip");

        // 拿到公共的字段
/*        Field[] fields = vipClass.getFields();

        for (Field field : fields) {
            System.out.println(field.getName());
        }*/

        // 获取所有字段，包括私有的
        Field[] declaredFields = vipClass.getDeclaredFields();
        for (Field field : declaredFields) {
            // 获取属性名
            System.out.println(field.getName());

            // 获取属性类型
            Class<?> type = field.getType();

            // 获取属性类型的简单名字
            System.out.println(type.getSimpleName());

            // 获取修饰符
            // System.out.println(field.getModifiers());  // int
            System.out.println(Modifier.toString(field.getModifiers()));

        }

    }
}
```

![image-20241007193415927](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410071934067.png)

![image-20241007193916999](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410071939096.png)



## 反编译的字段

``反编译java.lang.String类中所有的属性``













## 通过反射为对象属性赋值

``Customer类``

```java
public class Customer {

    private String name;
    private int age;

}

```

``main``

```java
import java.lang.reflect.Field;

public class ReflectTest06 {
    public static void main(String[] args) throws Exception {
        Customer customer = new Customer();

        // 通过反射机制访问Field，访问属性的值，给属性赋值。
        // 获取类
        Class customerClass = Class.forName("Reflect.Customer");

        // 获取对应的Field字段
        Field ageFiled = customerClass.getDeclaredField("age");

        // 调用方法打破封装
        ageFiled.setAccessible(true);

        // 修改属性的值(set)
        // 三要素：给哪个对象的哪个属性赋什么值
        ageFiled.set(customer, 18);

        // 读取属性的值
        System.out.println(ageFiled.get(customer));

    }
}
```





## 反射一个类的Method

``和Field类似``

















## 通过反射机制调用方法

``UserService``

```java
public class UserService {

    public boolean login(String username, int password) {
        if("admin".equals(username) && password == 123456) {
            System.out.println("登录成功");
            return true;
        }

        return false;
    }

    public void logout() {
        System.out.println("退出系统");
    }

}
```

```java
import java.lang.reflect.Method;

public class ReflectTest08 {
    public static void main(String[] args) throws Exception{
        // 通过反射机制调用方法

        // 创建对象
        UserService userService = new UserService();

        // 获取类
        Class clazz = Class.forName("Reflect.UserService");

        Method login = clazz.getDeclaredMethod("login", String.class, int.class);
        
        // 调用方法
        Object retValue = login.invoke(userService, "admin", 123456);
        System.out.println(retValue);


    }
}
```





## 反编译类的构造方法











## 通过反射机制调用构造方法

> **虽然xxx.newInstanc()也能创建，但是已经标注过时，而且必须得有无参构造，不然报错，所以不再建议使用。**
>
> **所以得通过Class类型拿到构造方法，再通过构造方法调用newInstance实例化对象**

``Order类``

```java
public class Order {

    private String no;
    private double price;
    private String name;


    public Order() {
    }

    public Order(String no) {
        this.no = no;
    }

    public Order(String no, double price) {
        this.no = no;
        this.price = price;
    }

    public Order(String no, double price, String name) {
        this.no = no;
        this.price = price;
        this.name = name;
    }

    public String getNo() {
        return no;
    }

    public void setNo(String no) {
        this.no = no;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Order{" +
                "no='" + no + '\'' +
                ", price=" + price +
                ", name='" + name + '\'' +
                '}';
    }
}
```

``main类``

```java
import java.lang.reflect.Constructor;

public class ReflectTest09 {
    public static void main(String[] args) throws Exception{

        // 获取类
        Class clazz = Class.forName("Reflect.Order");

        // 无参构造
        Constructor declaredConstructor = clazz.getDeclaredConstructor();
        Object o = declaredConstructor.newInstance();
        System.out.println(o);

        // 三个参数构造方法
        Constructor threeConstructor = clazz.getDeclaredConstructor(String.class, double.class, String.class);
        Object o1 = threeConstructor.newInstance("1", 3.14, "wangcai");
        System.out.println(o1);

    }
}

```

![image-20241008135046267](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410081350444.png)





## 通过反射机制实现框架部分内容

``通过读取属性配置文件，获取类信息，方法信息，然后通过反射机制调用方法``











## 类加载的过程

![image-20241008140813856](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410081408050.png)





## 获取Class的方式

![image-20241008145910401](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410081459578.png)



```java
public class ReflectTest10 {
    public static void main(String[] args) throws Exception{

        // 通过类加载器获取Class
        // 该方法不进行类的初始化，直到类进行第一次使用
        ClassLoader systemClassLoader = ClassLoader.getSystemClassLoader();
        Class<?> userClass = systemClassLoader.loadClass("Reflect.User");

    }
}
```





## 虚拟机的三个类加载器

![image-20241008201715427](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410082017607.png)



```java
public class ReflectTest11 {
    public static void main(String[] args) {

        // 获取类加载器的方式①
        ClassLoader classLoader1 = ReflectTest11.class.getClassLoader();
        System.out.println("应用类加载器: " + classLoader1);

        // 获取类加载器的方式②
        ClassLoader classLoader2 = ClassLoader.getSystemClassLoader();
        System.out.println("应用类加载器: " + classLoader2);

        // 获取类加载器的方式③
        ClassLoader classLoader3 = Thread.currentThread().getContextClassLoader();
        System.out.println("应用类加载器: " + classLoader3);

        // 通过getParent()可以获取父类加载器
        System.out.println("平台类加载器： " + classLoader3.getParent());

        // 启动类加载器负责的是JDK的类库，这个类加载器名字看不到，直接输出是null
        System.out.println("启动类加载器： " + classLoader3.getParent().getParent());


    }
}
```





## 双亲委派机制

![image-20241008220017346](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410082200511.png)



## 反射父类的泛型

``Animal类``

```java
// 在类上定义泛型
public class Animal<Z, X, C> {
}
```



``Cat类``

```java
public class Cat extends Animal<String, Integer, Double> {
}
```



``Test``

```java
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;

public class ReflectTest12 {
    public static void main(String[] args) {

        // 获取子类继承的父类的泛型信息
        // 获取类
        Class<Cat> catClass = Cat.class;

        // 获取父类的泛型
        Type genericSuperclass = catClass.getGenericSuperclass();  // Type是个接口

        /*
        如果cat继承父类时没有用泛型，这里获取的就是个Class
        System.out.println(genericSuperclass instanceof Class);  // 此时返回true
        */

        // 用了泛型
        System.out.println(genericSuperclass instanceof ParameterizedType);  // true

        if (genericSuperclass instanceof ParameterizedType) {
            // 转型为参数化类型
            ParameterizedType parameterizedType = (ParameterizedType) genericSuperclass;
            Type[] actualTypeArguments = parameterizedType.getActualTypeArguments();

            for (Type a : actualTypeArguments) {
                System.out.println(a.getTypeName());  //
            }

        }

    }
}
```

![image-20241009094102077](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410090941234.png)





## 反射接口的泛型

``Flyable接口``

```java
public interface Flyable<X, Y> {
}
```



``Mouse类``

```java
public class Mouse implements Flyable<String, Integer>, Comparable<Mouse>{
    
    @Override
    public int compareTo(Mouse o) {
        return 0;
    }
    
}
```



``Test``

```java
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;

public class ReflectTest13 {
    public static void main(String[] args) {
        // 获取类
        Class<Mouse> mouseClass = Mouse.class;

        Type[] genericInterfaces = mouseClass.getGenericInterfaces();  // 这里返回Type数组的原因是一个类可以实现多个接口

        for (Type g : genericInterfaces) {
            if (g instanceof ParameterizedType) {
                ParameterizedType parameterizedType = (ParameterizedType) g;
                Type[] actualTypeArguments = parameterizedType.getActualTypeArguments();

                for (Type a : actualTypeArguments) {
                    System.out.println(a.getTypeName());
                }
            }
        }

    }
}
```

![image-20241009094923511](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410090949604.png)





## 反射属性上的泛型

``User类``

```java
import java.util.Map;

public class User {
    
    private Map<String, Integer> map;
    
}
```



``Test``

```java
import java.lang.reflect.Field;
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;

public class ReflectTest14 {
    public static void main(String[] args) throws Exception {
        Class<User> userClass = User.class;

        Field mapField = userClass.getDeclaredField("map");

        Type genericType = mapField.getGenericType();

        if (genericType instanceof ParameterizedType) {
            ParameterizedType parameterizedType = (ParameterizedType) genericType;

            Type[] actualTypeArguments = parameterizedType.getActualTypeArguments();
            for (Type a : actualTypeArguments) {
                System.out.println(a.getTypeName());
            }
        }

    }
}
```

![image-20241009095826843](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410090958972.png)







## 反射方法参数上的泛型

``MyClass``

```java
import java.util.List;
import java.util.Map;

public class MyClass {

    public void m(List<String> list, Map<String, Double> map) {

    }

}
```



``Test``

```java
import java.lang.reflect.Method;
import java.lang.reflect.ParameterizedType;
import java.lang.reflect.Type;
import java.util.List;
import java.util.Map;

public class ReflectTest15 {
    public static void main(String[] args) throws NoSuchMethodException {

        Class<MyClass> myClassClass = MyClass.class;

        Method m = myClassClass.getDeclaredMethod("m", List.class, Map.class);

        Type[] genericParameterTypes = m.getGenericParameterTypes();

        for (Type g : genericParameterTypes) {
            if(g instanceof ParameterizedType) {
                ParameterizedType parameterizedType = (ParameterizedType) g;

                Type[] actualTypeArguments = parameterizedType.getActualTypeArguments();

                for (Type a : actualTypeArguments) {
                    System.out.println(a.getTypeName());
                }
            }
        }

    }
}
```

![image-20241009100526110](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091005205.png)







## 反射方法返回值和构造方法参数的泛型

``和上面类似，方法拿方法，构造方法拿构造方法...``

















# 注解

------

![image-20241009101412698](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091014900.png)





## Java预置注解

![image-20241009102843710](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091028254.png)



## @Deprecated（已过时）

``过时注解``

```java
package Annotation;

public class AnnotationTest01 {

    public static void main(String[] args) {
        MyClass m = new MyClass();
        m.m1();
        int b = MyClass.a;
    }

}


@Deprecated
class MyClass {

    // 从Java9版本开始, forRemoval = true代表移除
    @Deprecated(since = "9", forRemoval = true)
    public static int a = 100;

    @Deprecated
    public void m1() {

    }

}
```

![image-20241009110953463](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091109577.png)

![image-20241009111406865](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091114981.png)









## @Override（重写）

``标注实例方法，代表重写父类方法``

```java
public class AnnotationTest02 {

    @Override
    public boolean equals(Object obj) {
        return super.equals(obj);
    }
    
}
```







## @SuppressWarnings

``SuppressWarnings("rawtypes")：抑制未使用泛型的警告``

``SuppressWarnings("resource")：抑制未使用资源的警告``

``SuppressWarnings("deprecation")：抑制使用了已过时资源时的警告``

``SuppressWarnings("all")：抑制所有警告``



> **实际中尽量不忽略警告，尽力去解决**



```java
import java.io.FileInputStream;
import java.util.ArrayList;
import java.util.List;


@SuppressWarnings("all")
public class AnnotationTest03 {

    public static void main(String[] args) throws Exception {

        @SuppressWarnings("rawtypes")
        List list = new ArrayList();

        @SuppressWarnings("resource")
        FileInputStream fis = new FileInputStream("e:/file.txt");

        @SuppressWarnings("deprecation")
        MyClass myClass = new MyClass();

    }

}
```









## 函数式接口注解

> **JDK1.8+ 该注解标注的接口只能有一个抽象方法，但是默认方法或静态方法可以有多个**



``FunctionalInterface``

```java
public class AnnotationTest04 {
    public static void main(String[] args) {

    }
}

// 函数式接口只允许一个抽象方法
@FunctionalInterface
interface MyInterface {
    void m1();

    // void m2();
    
    default void m3() {
        System.out.println("...");
    }

    static void m4() {
        System.out.println("...");
    }
}
```











## 自定义注解

![image-20241009115719700](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091157854.png)



> **所有自定义的注解，它的父类都是java.lang.annotation.Annotation**



**参考Java内置的Deprecated**

![image-20241009133505723](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091335870.png)



``自定义、使用``

```java
// 自定义的注解
public @interface MyAnnotation {
}
```

```java
@MyAnnotation
public class AnnotationTest05 {
    @MyAnnotation
    public static void main(String[] args) {
        // 使用注解
        @MyAnnotation
        int a = 1000;
    }

    private void m1(@MyAnnotation String a) {

    }
}
```



``定义注解``

```java
public @interface DataBaseInfo {
    /**
     * 注解也可以定义属性，但是属性名后面得加（）
     * */

    String driver();
    String url();
    String user();
    String password();
    
    // 指定默认值
    /*
    String driver() default "oracle.jdbc.driver.OracleDriver";
    String url() default "";
    String user() default "root";
    String password() default "123456";
    */

}
```

``Test``

```java
public class AnnotationTest06 {

    // 注解定义属性后，使用时必须给属性赋值，不然报错，除非定义时指定了默认值。
    @DataBaseInfo(driver = "a", url = "xxx.com", user = "admin", password = "123")
    public void connDB() {

    }

}
```





``注解属性可以是一维数组的形式``

```java
public @interface DataBaseInfo {
    /**
     * 注解也可以定义属性，但是属性名后面得加（）
     * */

    String driver() default "oracle.jdbc.driver.OracleDriver";
    String url() default "";
    String user() default "";
    String password() default "";


    String[] names();
    int[] ints();
}
```

```java
public class AnnotationTest06 {

    // 注解定义属性后，使用时必须给属性赋值，不然报错，除非定义时指定了默认值。
    @DataBaseInfo(
            driver = "a",
            url = "xxx.com",
            user = "admin",
            password = "123",
        	// 数组属性只有一个值的时候，{}可以省略
            names = {"w", "c", "a"},
            ints = 1
    )
    public void connDB() {

    }

}
```





``属性只有一个并且属性名是value，在使用时，value可以省略``

```java
public @interface DataBaseInfo {
    
    String value();
    
}

```

```java
public class AnnotationTest06 {

    // @DataBaseInfo(value="a")
    @DataBaseInfo("a")
    public void connDB() {

    }

}

```





## 元注解

![image-20241009141605211](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091416346.png)



### ``注解的保持性``

![image-20241009142755692](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091427840.png)



``MyAnnotation``

```java
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(value = RetentionPolicy.RUNTIME)
/*
    RetentionPolicy.SOURCE == 保留在java文件中
    RetentionPolicy.ClASS == 保留在class文件中, 不能被反射
    RetentionPolicy.RUNTIME == 保留在class文件中, 可以在运行阶段被反射
*/
public @interface MyAnnotation {

}
```

```java
@MyAnnotation
public class Test {
    public static void main(String[] args) {
        Class<Test> testClass = Test.class;

        // 获取这个类的指定注解
        MyAnnotation declaredAnnotation = testClass.getDeclaredAnnotation(MyAnnotation.class);

        System.out.println(declaredAnnotation);

    }
}

```

![image-20241009143805568](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091438681.png)







### ``设置注解可使用的位置``

![image-20241009144221707](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091442850.png)



``TargetTest``

```java
import java.lang.annotation.ElementType;
import java.lang.annotation.Target;

@Target(ElementType.METHOD)  // 限定注解只能出现在方法上
public @interface TargetTest {
}

```

```java
package MetaAnnotation;

@MyAnnotation
// @TargetTest 这里不能使用
public class Test {
    @TargetTest  // 这里可以用
    public static void main(String[] args) {
    }
}
```





### ``设置注解可以文档化``

![image-20241009145016909](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091450051.png)





![image-20241009150013877](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091500043.png)









### ``设置注解可以继承``

![image-20241009150305321](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091503450.png)



``InheritedTest``

```java
import java.lang.annotation.Inherited;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Inherited
@Retention(RetentionPolicy.RUNTIME)
public @interface InheritedTest {
}
```

``继承关系父子类``

```java
@InheritedTest
public class Animal {
}
```

```java
public class Cat extends Animal {
}
```

``Test``

```java
public class Test1 {
    public static void main(String[] args) {
        
        Class<Cat> catClass = Cat.class;
        InheritedTest declaredAnnotation = catClass.getAnnotation(InheritedTest.class);
        System.out.println(declaredAnnotation);
        
    }

}
```

![image-20241009151645511](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091516635.png)









### ``设置注解可以重复使用``

![image-20241009151803991](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091518113.png)



``Repeatble参数为注解名的复数形式.class``

``注解名字+s的注解里面属性固定为：注解名[] value()``



``Author``

```java
import java.lang.annotation.Repeatable;

@Repeatable(Authors.class)
public @interface Author {
    String name();
}
```

``Authors``

```java
public @interface Authors {

    Author[] value();

}
```

``Test``

```java
public class Test2 {

    @Author(name = "w")
    @Author(name = "c")
    public void doSome() {

    }

}
```









## 通过反射机制读取注解

![image-20241009152820179](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410091528347.png)

``isAnnotationPresent：判断有没有这个注解 ``



> **通过反射获取注解**

``Annotation1``

```java
import java.lang.annotation.*;

@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@Documented
public @interface Annotation1 {

    String name();
    int age();

}
```

``Annotation2``

```java
import java.lang.annotation.*;

@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@Documented
public @interface Annotation2 {

    String email();
    double price();

}
```

``Myclass``

```java
@Annotation1(name = "wc", age = 18)
@Annotation2(email = "xdd@qq.com", price = 3.14)
public class Myclass {

}
```

``Test``

```java
import java.lang.annotation.Annotation;

public class Test {
    public static void main(String[] args) {
        Class<Myclass> myClass = Myclass.class;

        // 获取类上的所有注解
        Annotation[] annotations = myClass.getAnnotations();
        for (Annotation a : annotations) {
            System.out.println(a);
        }

        // 先判断该类上是否存在该注解
        if(myClass.isAnnotationPresent(Annotation1.class)) {
            // 获取指定的注解
            Annotation1 a1 = myClass.getAnnotation(Annotation1.class);
            // 访问注解对象中的属性
            System.out.println(a1.name());
            System.out.println(a1.age());

        }


    }
}
```

![image-20241009205950876](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410092059040.png)









## 递归+注解+反射综合练习

![image-20241009213037162](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410092130324.png)











# 网络编程

## 概述

![image-20241009213408081](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410092134238.png)



``IP + 端口号 + 通信协议``





## IP地址

![image-20241009214030181](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410092140381.png)





## 域名和DNS

![image-20241009215016789](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410092150957.png)





## 端口号port

![image-20241010220802411](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410102208664.png)









## 通信协议

![image-20241011124923799](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410111249028.png)







## OSI参考模型

![image-20241011125355223](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410111253431.png)







## TCP/IP参考模型

![image-20241011130229488](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410111302662.png)





## InetAddress类

![image-20241011130706016](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410111307174.png)



```java
import java.net.InetAddress;
import java.net.UnknownHostException;

public class InetAddressTest {

    public static void main(String[] args) throws UnknownHostException {

        // 获取本机的IP + 主机名的封装对象
        InetAddress localHost = InetAddress.getLocalHost();

        // 获取本机的IP地址
        String hostAddress = localHost.getHostAddress();
        System.out.println("本机的IP地址：" + hostAddress);  // 本机的IP地址：192.168.32.1

        // 获取本机的主机名
        String hostName = localHost.getHostName();
        System.out.println("本机的主机名：" + hostName);     // 本机的主机名：LAPTOP-ECCDVE9O

        // 通过域名获取InetAddress对象
        InetAddress byName = InetAddress.getByName("www.baidu.com");
        System.out.println(byName.getHostAddress());   // 39.156.66.18
        System.out.println(byName.getHostName());  // www.baidu.com

    }

}
```







## URL类

![image-20241011131918311](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410111319542.png)



```java
import java.net.MalformedURLException;
import java.net.URL;
import java.net.UnknownHostException;

public class InetAddressTest {
    public static void main(String[] args) throws UnknownHostException, MalformedURLException {

        URL url = new URL("https://www.baidu.com:8000/api/user/login?username=admin&password=123#tip");

        String protocol = url.getProtocol();
        System.out.println("协议：" + protocol);

        String path = url.getPath();
        System.out.println("资源路径：" + path);

        // 获取默认端口号 http默认80, https默认443
        int defaultPort = url.getDefaultPort();
        System.out.println("默认端口：" + defaultPort);

        // 获取当前端口
        int port = url.getPort();
        System.out.println("当前端口：" + port);

        // 获取主机地址
        String host = url.getHost();
        System.out.println("主机地址：" + host);

        // 获取URL的数据
        String query = url.getQuery();
        System.out.println("需要提交给服务器的数据：" + query);

        // 获取描点
        String ref = url.getRef();
        System.out.println("获取锚点：" + ref);

        // 资源路径加数据
        String file = url.getFile();
        System.out.println(file);

    }

}
```

![image-20241011222543373](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112225637.png)



```java
package Inet;

import java.io.IOException;
import java.io.InputStream;
import java.net.MalformedURLException;
import java.net.URL;

public class InetAddressTest {
    public static void main(String[] args) throws IOException {

        URL url = new URL("https://tianqi.qq.com/");

        InputStream inputStream = url.openStream();

        byte[] bytes = new byte[1024];
        int readCount = 0;
        while ((readCount = inputStream.read(bytes)) != -1) {
            String s = new String(bytes);
            System.out.println(s);
        }

    }

}
```











## TCP/UDP协议

![image-20241011225205846](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112252108.png)



![image-20241011225258109](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112252276.png)

![image-20241011225623333](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112256463.png)





## TCP的三次握手（通道打开）

![image-20241011225905662](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112259849.png)

![image-20241011230004831](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112300995.png)











## TCP的四次挥手（通道关闭）

![image-20241011225930697](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410112259887.png)









## 基于TCP的编程

![image-20241012120052216](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410121200474.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410121202355.png" alt="image-20241012120255189" style="zoom:80%;" />





``Client``

![image-20241012162310424](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410121623682.png)





``Server``

![image-20241012162405674](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410121624866.png)





## 实现单向通信

![image-20241012202619480](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122026684.png)



``Cilent``

```java
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.OutputStreamWriter;
import java.net.InetAddress;
import java.net.Socket;
import java.net.UnknownHostException;

public class Client {
    public static void main(String[] args) throws UnknownHostException {

        InetAddress ia = InetAddress.getLocalHost();

        Socket cilentsocket = null;
        BufferedWriter bw = null;
        // 创建客户端套接字对象
        try {

            int port = 8888;
            cilentsocket = new Socket(ia, port);

            // 客户端向服务端发送消息
            bw = new BufferedWriter(new OutputStreamWriter(cilentsocket.getOutputStream()));

            // 发送消息
            bw.write("你好！");
            bw.write("hhhh");
            bw.write("\n");
            bw.write("嘿嘿嘿嘿嘿");

            bw.flush();

        } catch (IOException e) {
            throw new RuntimeException(e);
        }finally {
            if (bw != null) {
                try {
                    bw.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (cilentsocket != null) {
                try {
                    cilentsocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }

    }
}
```



``Server``

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.ServerSocket;
import java.net.Socket;

public class Server {
    public static void main(String[] args) {
        ServerSocket serverSocket = null;
        Socket clientSocket = null;
        BufferedReader br = null;
        try {
            // 启动服务器端
            int port = 8888;
            serverSocket = new ServerSocket(port);

            System.out.println("服务器启动完成...");

            // 接受客户端套接字
            clientSocket = serverSocket.accept();

            // 服务端接受消息
            br = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));

            // 读取
            String s = null;
            while ((s = br.readLine()) != null) {
                System.out.println(s);
            }

        } catch (IOException e) {
            throw new RuntimeException(e);
        }finally {
            if (br != null) {
                try {
                    br.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (clientSocket != null) {
                try {
                    clientSocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (serverSocket != null) {
                try {
                    serverSocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }

    }

}
```









## 实现双向通信

![image-20241012202637425](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122026563.png)



> **实现发送图片并返回消息**



``Server``

```java
import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

public class TwoServer {
    public static void main(String[] args) {

        ServerSocket serverSocket = null;
        BufferedInputStream bis = null;
        Socket cilentSocket = null;
        BufferedOutputStream bos = null;
        BufferedWriter bw = null;

        try {
            serverSocket = new ServerSocket(8888);
            System.out.println("服务启动成功");

            // 客户端套接字
            cilentSocket = serverSocket.accept();

            // 获取流
            bis = new BufferedInputStream(cilentSocket.getInputStream());

            // 新建输出流
            bos = new BufferedOutputStream(new FileOutputStream("./a.png"));

            // 开始读
            byte[] bytes = new byte[1024];
            int readCount = 0;
            while ((readCount = bis.read(bytes)) != -1) {
                // 将图片写入到服务器的硬盘上
                bos.write(bytes, 0, readCount);
            }

            bos.flush();

            // 服务器接收完后返回消息
            bw = new BufferedWriter(new OutputStreamWriter(cilentSocket.getOutputStream()));
            bw.write("已收到图片 \n");

            bw.flush();


        } catch (IOException e) {
            throw new RuntimeException(e);
        }finally {
            if (bw != null) {
                try {
                    bw.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (bis != null) {
                try {
                    bis.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (serverSocket != null) {
                try {
                    serverSocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (bos != null) {
                try {
                    bos.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (cilentSocket != null) {
                try {
                    cilentSocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }

    }
}
```



``Client``

```java
import java.io.*;
import java.net.InetAddress;
import java.net.Socket;
import java.net.UnknownHostException;

public class TwoCilent {
    public static void main(String[] args) throws UnknownHostException {
        Socket socket = null;
        BufferedOutputStream bos = null;
        BufferedInputStream bis = null;
        BufferedReader br = null;

        try {
            socket = new Socket(InetAddress.getLocalHost(), 8888);

            // 发送图片给服务器
            bos = new BufferedOutputStream(socket.getOutputStream());

            // 写图片到服务器
            // 一边读一边写（读本地图片，写入到服务器）
            bis = new BufferedInputStream(new FileInputStream("E:\\sx\\hh.png"));

            byte[] bytes = new byte[1024];
            int readCount = 0;
            while ((readCount = bis.read(bytes)) != -1) {
                bos.write(bytes, 0, readCount);
            }

            bos.flush();

            // 关闭向服务器的输出
            socket.shutdownOutput();

            // 收服务器返回的消息
            br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            String s = null;
            while ((s = br.readLine()) != null) {
                System.out.println(s);
            }

        } catch (IOException e) {
            throw new RuntimeException(e);
        }finally {
            if (br != null) {
                try {
                    br.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (bis != null) {
                try {
                    bis.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (bos != null) {
                try {
                    bos.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (socket != null) {
                try {
                    socket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }

    }
}
```









## 基于UDP的网络编程

![image-20241012202716465](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122027595.png)



![image-20241012202745568](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122027692.png)



![image-20241012202816192](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122028323.png)



``Receive``

```java
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class Receive {
    public static void main(String[] args) throws IOException {

        DatagramSocket ds = new DatagramSocket(8888);

        // 准备一个包接收数据
        byte[] bytes = new byte[64 * 1024];
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length);

        // 程序到这停下来等待接收
        ds.receive(dp);

        // 执行到这说明接收完成了
        String msg = new String(bytes, 0, dp.getLength());
        System.out.println("接收的数据：" + msg);

        ds.close();

    }
}
```







``Send``

```java
import java.io.IOException;
import java.net.*;

public class Send {
    public static void main(String[] args) throws IOException {

        DatagramSocket ds = new DatagramSocket();

        byte[] bytes = "哈哈哈🙂".getBytes();
        DatagramPacket dp = new DatagramPacket(bytes, 0, bytes.length, InetAddress.getLocalHost(), 8888);

        ds.send(dp);

        ds.close();

    }
}
```















# Lambda表达式

![image-20241012204549102](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122045311.png)



```java
package lambda;

import java.util.Comparator;
import java.util.TreeSet;

public class Test01 {
    public static void main(String[] args) {
        // 匿名内部类写法
        /*
        TreeSet<User> user = new TreeSet<>(new Comparator<User>() {
            @Override
            public int compare(User o1, User o2) {
                return o2.getAge() - o1.getAge();
            }
        });
        */

        /**
         * lambda表达式()代表函数式接口中的抽象方法的()，{}代表其方法体
         * 参数上的类型可以省, 语句只有一句时{}也可以省, 此时的return也能省
         * */
        
        TreeSet<User> user = new TreeSet<>((o1, o2) -> o1.getAge() - o2.getAge());
        
        /*
        TreeSet<User> user = new TreeSet<>((User o1, User o2) -> {
            return o2.getAge() - o1.getAge();
        });
        */


        User user1 = new User(10);
        User user2 = new User(20);
        User user3 = new User(30);
        User user4 = new User(40);

        user.add(user1);
        user.add(user2);
        user.add(user3);
        user.add(user4);

        System.out.println(user);

    }
}

class User {

    private int age;

    public User(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "age=" + age +
                '}';
    }
}
```





## 函数式编程

![image-20241012224050782](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122240032.png)



``怎么理解函数式接口``

![image-20241012225046008](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122250168.png)





## Lambda和匿名内部类

![image-20241012225148513](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122251625.png)







## Lambda语法

![image-20241012230842449](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410122308611.png)







## 无返回值函数接口



> **无返回值无参数的函数接口**



```java
public class Test02 {
    public static void main(String[] args) {
        // 匿名内部类
        NoParamNoReturn npnr = new NoParamNoReturn() {
            @Override
            public void test() {
                System.out.println("NoParameterNoReturn...");
            }
        };
        npnr.test();

        NoParamNoReturn npnr2 = () -> {
            System.out.println("NoParameterNoReturn...");
        };
        npnr2.test();

    }
}

@FunctionalInterface
interface NoParamNoReturn {
    void test();
}
```





> **无返回值一个参数**



```java
public class Test03 {
    public static void main(String[] args) {
        // 匿名内部类
        OneParameterNoReturn opnr = new OneParameterNoReturn() {
            @Override
            public void test(Integer num) {
                System.out.println("无返回值一个参数: " + num);
            }
        };
        opnr.test(100);

        // Lambda
        OneParameterNoReturn opnr2 = (Integer num) -> {
            System.out.println("无返回值一个参数: " + num);
        };
        opnr2.test(200);

    }
}

@FunctionalInterface
interface OneParameterNoReturn {
    void test(Integer num);
}
```





> **无返回值多个参数**



```java
public class Test04 {
    public static void main(String[] args) {
        // 匿名内部类
        MoreParameterNoReturn mpnr = new MoreParameterNoReturn() {
            @Override
            public void test(Integer num, String s) {
                System.out.println("Integer----> " + num + ", String----> " + s);
            }
        };
        mpnr.test(1, "wangcai");

        // Lambda
        MoreParameterNoReturn mpnr2 = (Integer num, String s) -> {
            System.out.println("Integer----> " + num + ", String----> " + s);
        };
        mpnr2.test(2, "dingwan");

    }
}

@FunctionalInterface
interface MoreParameterNoReturn {
    void test(Integer num, String s);
}
```







## 有返回值函数接口



> **有返回值无参数**



```java
public class Test05 {
    public static void main(String[] args) {
        // 匿名内部类
        NoParamHasReturn noParamHasReturn = new NoParamHasReturn() {
            @Override
            public Integer test() {
                return 1;
            }
        };
        System.out.println(noParamHasReturn.test());

        NoParamHasReturn noParamHasReturn1 = () -> {
            return 2;
        };
        System.out.println(noParamHasReturn1.test());

    }
}

@FunctionalInterface
interface NoParamHasReturn {
    Integer test();
}
```







> **有返回值一个参数**



```java
public class Test06 {
    public static void main(String[] args) {
        // 匿名内部类
        OneParamHasReturn oneParamHasReturn = new OneParamHasReturn() {
            @Override
            public Integer test(Integer num) {
                System.out.println("num----> " + num);
                return 1;
            }
        };
        System.out.println(oneParamHasReturn.test(100));

        OneParamHasReturn oneParamHasReturn1 = (Integer num) -> {
            System.out.println("num----> " + num);
            return 2;
        };
        System.out.println(oneParamHasReturn1.test(200));

    }
}

@FunctionalInterface
interface OneParamHasReturn {
    Integer test(Integer num);
}
```





> **有返回值多个参数**



```java
public class Test07 {
    public static void main(String[] args) {
        // 匿名内部类
        MoreParamHasReturn mphr = new MoreParamHasReturn() {
            @Override
            public Integer test(Integer num, String s) {
                System.out.println("Integer----> " + num + ", String----> " + s);
                return 1;
            }
        };
        mphr.test(100, "aaa");

        // Lambda
        MoreParamHasReturn mphr1 = (Integer num, String s) -> {
            System.out.println("Integer----> " + num + ", String----> " + s);
            return 2;
        };
        mphr1.test(200, "bbb");

    }
}

@FunctionalInterface
interface MoreParamHasReturn {
    Integer test(Integer num, String s);
}
```







## Lambda语法精简

![image-20241013111804538](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410131118686.png)









## JDK内置函数接口

![image-20241013112509403](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410131125524.png)



``消费型接口 ==== 消费``

``供给型接口 ==== 生产``

``函数式接口 ==== 转换``

``判断型接口 ==== 判断``









## Lambda的方法引用

![image-20241013205623651](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410132056852.png)



> **实例方法引用**



```java
import java.util.function.Consumer;

public class Test08 {
    public static void main(String[] args) {

        Consumer<String> consumer = new Consumer<String>() {
            @Override
            public void accept(String s) {
                System.out.println(s);
            }
        };

        consumer.accept("Test1");

        // Lambda
        Consumer<String> consumer1 = s -> System.out.println(s);
        consumer1.accept("Test2");

        // 实例引用
        Consumer<String> consumer2 = System.out :: println;
        consumer2.accept("Test3");

    }
}
```





> **静态方法引用**

![image-20241014105451211](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141054415.png)



```java
```







> **特殊方法引用**



![image-20241014105643877](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141056010.png)









> **构造方法引用**



![image-20241014113038943](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141130143.png)







> **数组引用**



![](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141138920.png)







## Lambda在集合中的应用

![image-20241014114115769](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141141908.png)



``示例``

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

public class Test09 {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1,2,6,8,3,88);

        list.forEach(new Consumer<Integer>() {
            @Override
            public void accept(Integer integer) {
                System.out.println(integer);
            }
        });

        System.out.println("------------------------");

        // Lambda
        list.forEach(integer -> System.out.println(integer));

        System.out.println("------------------------");

        // 实例方法引用
        list.forEach(System.out::println);
    }
}
```





``遍历Map``

```java
import java.util.TreeMap;
import java.util.function.BiConsumer;

public class Test10 {
    public static void main(String[] args) {
        TreeMap<Integer, String> treeMap = new TreeMap<>();

        treeMap.put(1, "a");
        treeMap.put(2, "b");
        treeMap.put(3, "c");
        treeMap.put(4, "d");

        treeMap.forEach(new BiConsumer<Integer, String>() {
            @Override
            public void accept(Integer k, String v) {
                System.out.println("key: " + k + " value: " + v);
            }
        });

        // Lambda
        treeMap.forEach((k, v) -> System.out.println("key: " + k + " value: " + v));

    }
}
```







## removeIf()

![image-20241014115252961](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141152163.png)

















# Stream API

![image-20241014115603815](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141156973.png)





## Stream流创建方法

### 通过Collection接口提供的方法

``通过Collection接口提供的stream()方法来创建Stream流。``

```java'
List<String> list = Arrays.asList("aa", "bb", "cc");
Stream<String> stream = list.stream();
```



### 通过Arrays类提供的方法

```java
String[] arr1 = {"aa", "bb", "cc"};
Stream<String> stream = Arrays.stream(arr1);

int[] arr2 = {11, 22, 33, 44};
IntStream intStream = Arrays.stream(arr2);

long[] arr3 = {11, 22, 33, 44};
LongStream longStream = Arrays.stream(arr3);

double[] arr4 = {1.0, 2.0, 3.0};
DoubleStream doubleStream = Arrays.stream(arr4);
```

``注意：Stream、IntStream、LongStream和DoubleStream都继承于BaseStream接口。``





### 使用Stream接口提供的方法

``通过Stream接口提供的of(T... values)静态方法来创建Stream流。``



```java
Stream<String> stringStream = Stream.of("aa", "bb", "cc");
Stream<Integer> integerStream = Stream.of(11, 22, 33, 44);
```





## 顺序流和并行流的理解

在前面获得Stream对象的方式，我们都称之为“顺序流”，顺序流对Stream元素的处理是单线程的，即一个一个元素进行处理，处理数据的效率较低。
如果Stream流中的数据处理没有顺序要求，并且还希望可以并行处理Stream的元素，那么就可以使用“并行流”来实现，从而提高处理数据的效率。
一个普通Stream转换为可以并行处理的Stream非常简单，只需要用调用Stream提供的parallel()方法进行转换即可，这样就可以并行的处理Stream的元素。那么，我们不需要编写任何多线程代码就可以享受到并行处理带来的执行效率的提升。
【示例】把顺序流转化为并行流

```java
// 创建一个“顺序流”Stream对象
Stream<String> stream = Stream.of("aa", "bb", "cc");
// 验证：stream是否为并行流
System.out.println(stream.isParallel());         // 输出：false
// 将Stream对象转化为“并行流”
// 注意：parallel()方法返回的就是“方法的调用者对象”
Stream<String> parallelStream = stream.parallel();
System.out.println(stream == parallelStream);    // 输出：true
// 验证：stream是否为并行流
System.out.println(stream.isParallel());         // 输出：true
```

在Collection接口中，还专门提供了一个parallelStream()方法，用于获得一个并行流。
【示例】使用parallelStream()方法获得一个并行流

```java
List<String> list = Arrays.asList("aa", "bb", "cc");
// 创建一个“并行流”Stream对象
Stream<String> stream = list.parallelStream();
// 验证：stream是否为并行流
System.out.println(stream.isParallel()); // 输出：true
```







## Stream API的中间操作

中间操作属于惰式执行，直到执行终止操作才会真正的进行数据的计算，此处调用中间操作只会返回一个标记了该操作的新Stream对象，因此可以进行链式操作。
在后续的操作中，我们调用StudentData类的getStudentList()静态方法，则就能获得一个存储Student对象的List集合，其代码实现如下：

```java
public class Student {
    private String name;
    private int age;
    private String sex;
    private String city;

    public Student() {}
    public Student(String name, int age, String sex, String city) {
        this.name = name;
        this.age = age;
        this.sex = sex;
        this.city = city;
    }
    /*setter和getter方法此处省略，代码自己用IDEA生成*/
    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", sex='" + sex + '\'' +
                ", city='" + city + '\'' +
                '}';
    }
}
```

```java
public class StudentData {
    /**
     * 获得一个存储Student对象的List集合
     */
    public static List<Student> getStudentList() {
        ArrayList<Student> list = new ArrayList<>();
        list.add(new Student("张三", 21, "男", "武汉"));
        list.add(new Student("李四", 18, "女", "重庆"));
        list.add(new Student("王五", 25, "女", "成都"));
        list.add(new Student("赵六", 22, "男", "武汉"));
        list.add(new Student("王麻子", 16, "女", "成都"));
        return list;
    }
}
```







### 筛选（filter）

筛选（filter），按照一定的规则校验流中的元素，将符合条件的元素提取到新的流中的操作。该操作使用了Stream接口提供的“Stream<T> filter(Predicate<? super T> predicate);”方法来实现。
【示例】使用筛选的案例

```java
// 需求：筛选出年龄大于20的学生对象
Stream<Student> stream1 = StudentData.getStudentList().stream();
stream1.filter(stu -> stu.getAge() > 20).forEach(System.out :: println);
// 需求：筛选出字符串长度大于3的元素
Stream<String> stream2 = Stream.of("hello", "too", "like", "ande");
stream2.filter(str -> str.length() > 3).forEach(System.out :: println);
```





### 映射（map）

映射（map），将一个流的元素按照一定的映射规则映射到另一个流中。该操作使用了Stream接口提供的“<R> Stream<R> map(Function<? super T, ? extends R> mapper);”方法来实现。
【示例】使用映射的案例

```java
// 需求：把字符串中的字母全部转化为大写
Stream<String> stream1 = Stream.of("hello", "too", "like", "ande");
// stream1.map(str -> str.toUpperCase()).forEach(System.out :: println);
stream1.map(String :: toUpperCase).forEach(System.out :: println);

// 需求：获得集合中所有学生的名字
Stream<Student> stream2 = StudentData.getStudentList().stream();
// stream2.map(stu -> stu.getName()).forEach(System.out :: println);
stream2.map(Student :: getName).forEach(System.out :: println);

// 需求：获得集合中性别为男的学生名字
// 思路：先筛选，后映射
Stream<Student> stream3 = StudentData.getStudentList().stream();
stream3.filter(stu -> stu.getSex().equals("男")).map(Student :: getName).forEach(System.out :: println);
```

在Stream接口中，可以实现“将多个集合中的元素映射到同一个流中”，该操作使用了Stream接口提供的“<R> Stream<R> flatMap(Function<? super T, ? extends Stream<? extends R>> mapper);”方法来实现。
【示例】将多个集合中的元素映射到同一个流中

```java
// 需求：将两个集合中的元素映射到同一个流中
List<String> list1 = new ArrayList<>();
list1.add("aa");
list1.add("bb");
list1.add("cc");

List<String> list2 = new ArrayList<>();
list2.add("dd");
list2.add("ee");
list2.add("ff");

Stream<List<String>> stream = Stream.of(list1, list2);
stream.flatMap(List<String>::stream).forEach(System.out::println);
```







### 去重（distinct）

除重（distinct），也就是除去重复的元素，``底层使用了hashCode()和equals(Object obj)方法来判断元素是否相等。``该操作使用了Stream接口提供的“Stream<T> distinct();”方法来实现。
【示例】演示除重的操作

```java
// 需求：除去重复的元素
Stream.of(11, 22, 33, 44, 33).distinct().forEach(System.out :: println);

// 需求：除去重复的学生（除重后输出学生对象）
StudentData.getStudentList().stream().distinct().forEach(System.out :: println);

// 需求：除去年龄相同的学生（除重后输出学生年龄）
// 思路：先映射，后除重
StudentData.getStudentList().stream().map(Student :: getAge).distinct().forEach(System.out :: println);
```







### 排序（sorted）

排序（sorted），也就是对元素执行“升序”或“降序”的排列操作。在Stream接口中提供了“Stream<T> sorted();”方法，专门用于对元素执行“自然排序”，使用该方法则元素对应的类就必须实现Comparable接口。
【示例】使用自然排序的案例

```java
// 需求：对元素执行“升序”排序
Stream.of(4, 1, 3, 6, 2, 5).sorted().forEach(System.out :: println);

// 需求：按照学生的年龄执行“升序”排序（排序后输出学生对象）
StudentData.getStudentList().stream().sorted().forEach(System.out :: println);

// 需求：按照学生的年龄执行“升序”排序（排序后输出学生年龄）
StudentData.getStudentList().stream().map(Student :: getAge).sorted().forEach(System.out :: println);
```

在Stream接口中还提供了“Stream<T> sorted(Comparator<? super T> comparator);”方法，专门用于对元素执行“指定排序”，这样就能对某一个类设置多种排序规则。
【示例】使用指定排序的案例

```java
// 需求：对元素执行“升序”排序
Stream.of(4, 1, 3, 6, 2, 5).sorted(Integer :: compare).forEach(System.out :: println);

// 需求：按照学生的年龄执行“降序”排序（排序后输出学生对象）
StudentData.getStudentList().stream().sorted((stu1, stu2) -> stu2.getAge() - stu1.getAge()).forEach(System.out :: println);

// 需求：按照学生的年龄执行“升序”排序（排序后输出学生年龄）
StudentData.getStudentList().stream().map(Student :: getAge).sorted(Integer :: compare).forEach(System.out :: println);
```







### 合并（concat）

合并（concat），也就是将两个Stream合并为一个Stream，此处使用Stream接口提供的“public static <T> Stream<T> concat(Stream<? extends T> a, Stream<? extends T> b)”静态方法来实现。
【示例】将两个Stream合并为一个Stream。

```java
Stream<String> stream1 = Stream.of("aa", "bb", "cc");
Stream<String> stream2 = Stream.of("11", "22", "33");
Stream.concat(stream1, stream2).forEach(System.out :: println);
```







### 截断和跳过

跳过（skip），指的就是跳过n个元素开始操作，此处使用Stream接口提供的“Stream<T> skip(long n);”方法来实现。
截断（limit），指的是截取n个元素的操作，此处使用Stream接口提供的“Stream<T> limit(long maxSize);”方法来实现。
【示例】从指定位置开始截取n个元素

```java
// 需求：从索引为2的位置开始截取3个元素
Stream.of(11, 22, 33, 44, 55, 66).skip(2).limit(3).forEach(System.out :: println);
```







## Stream API终止操作

``触发终止操作时才会真正执行中间操作，终止操作执行完毕会返回计算的结果，并且终止操作执行完毕那么操作的Stream就失效，也就是不能再执行中间操作或终止操作啦。``



### 遍历（forEach）

遍历（forEach），使用Stream接口提供的“void forEach(Consumer<? super T> action);”方法来遍历计算的结果。
【示例】遍历操作的案例

```java
List<Student> list = StudentData.getStudentList();
// 遍历所有的元素
list.stream().forEach(System.out :: println);
// 遍历学生年龄大于20的元素
list.stream().filter(stu -> stu.getAge() > 20).forEach(System.out :: println);
```



### 匹配（match）

匹配（match），就是判断Stream中是否存在某些元素，Stream接口提供的匹配方法如下：

1. boolean allMatch(Predicate<? super T> predicate);  检查是否匹配所有的元素
2. boolean anyMatch(Predicate<? super T> predicate);  检查是否至少匹配一个元素
3. boolean noneMatch(Predicate<? super T> predicate); 检查是否一个元素都不匹配
4. Optional<T> findFirst(); 获得第一个元素

``注意：此处的Optional是一个值的容器，可以通过get()方法获得容器的值。``
【示例】匹配操作的案例

```java
List<Student> list = StudentData.getStudentList();
// 需求：匹配学生名字是否都为“王五”
boolean all = list.stream().allMatch(stu -> stu.getName().equals("王五"));
System.out.println("检查是否匹配所有的元素：" + all);
// 需求：匹配学生名字是否至少有一个为“王五”
boolean any = list.stream().anyMatch(stu -> stu.getName().equals("王五"));
System.out.println("检查是否至少匹配一个元素：" + any);
// 需求：匹配学生名字中是否全部都没有“王五”
boolean none = list.stream().noneMatch(stu -> stu.getName().equals("王五"));
System.out.println("检查是否一个元素都不匹配：" + none);
// 需求：获得第一个学生
Student firstStu = list.stream().findFirst().get();
System.out.println(firstStu);
// 需求：获得第四个学生
// 思路：跳过前面3个学生，然后再获得第一个元素
Optional<Student> skipStu = list.stream().skip(3).findFirst();
System.out.println(skipStu);
```





### 归约（reduce）

归约（reduce），``将所有元素按照指定的规则合并成一个结果。``在Stream接口中，常用的归约方法如下：

1. Optional<T> reduce(BinaryOperator<T> accumulator);
2. T reduce(T identity, BinaryOperator<T> accumulator);

``identity:累加器（初始值）``

【示例】归约操作的案例

```java
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
// 需求：获得集合中所有元素“相加”的结果
// Integer sum = list.stream().reduce((x, y) -> x + y).get();
Integer sum = list.stream().reduce(Integer :: sum).get();
System.out.println(sum);
// 需求：获得集合中所有元素“相乘”的结果
Integer result = list.stream().reduce((x, y) -> x * y).get();
System.out.println(result);
// 需求：获得最大长度的元素
String str = Stream.of("I", "love", "you", "too").reduce((str1, str2) -> str1.length() > str2.length() ? str1 : str2).get();
System.out.println(str);
// 需求：获得所有学生的总年龄
Integer sumAge = StudentData.getStudentList().stream().map(Student::getAge).reduce((age1, age2) -> age1 + age2).get();
System.out.println(sumAge);
// 需求：获得10和集合中所有元素“相加”的结果
Integer sum1 = list.stream().reduce(10, Integer :: sum);
System.out.println(sum1);
```

reduce操作可以实现从一组元素中生成一个值，而max()、min()、count()等方法都属于reduce操作，将它们单独设为方法只是因为常用，在Stream接口中这些方法如下：
long count(); 获得元素的个数
Optional<T> max(Comparator<? super T> comparator); 获得最大的元素
Optional<T> min(Comparator<? super T> comparator); 获得最小的元素

【示例】获得最大、最小和元素的个数

```java
List<Student> list = StudentData.getStudentList();
// 需求：获得元素的个数
long count = StudentData.getStudentList().stream().count();
System.out.println(count);

// 需求：获得年龄“最大”的学生
Student maxStu = list.stream().max((stu1, stu2) -> stu1.getAge() - stu2.getAge()).get();
System.out.println(maxStu);
// 需求：获得学生的“最大”年龄
Integer maxAge = list.stream().map(Student::getAge).max(Integer::compare).get();
System.out.println(maxAge);

// 需求：获得年龄“最小”的学生
Student minStu = list.stream().min((stu1, stu2) -> stu1.getAge() - stu2.getAge()).get();
System.out.println(minStu);
// 需求：获得学生的“最小”年龄
Integer minAge = list.stream().map(Student::getAge).min(Integer::compare).get();
System.out.println(minAge);
```





### 收集（collect）

收集（collect），可以说是内容最繁多、功能最丰富的部分了。从字面上去理解，就是把一个流收集起来，最终可以是收集成一个值也可以收集成一个新的集合。
调用Stream接口提供的“<R, A> R collect(Collector<? super T, A, R> collector);”方法来实现收集操作，并且参数中的Collector对象大都是直接通过Collectors工具类获得，实际上传入的Collector决定了collect()的行为。

#### 归集（toList/toSet/toMap）

因为Stream流不存储数据，那么在Stream流中的数据完成处理后，如果需要把Stream流的数据存入到集合中，那么就需要使用归集的操作。在Collectors提供的toList、toSet和toMap比较常用，另外还有Collectors提供的toCollection等比较复杂一些的用法。
【示例】演示toList、toSet和toMap的实现

```java
List<String> stringList = Arrays.asList("I", "love", "you", "too");
// 需求：将Stream转化为List集合
List<String> list = stringList.stream().collect(Collectors.toList());
System.out.println(list);
// 需求：将Stream转化为Set集合
Set<String> set = stringList.stream().collect(Collectors.toSet());
System.out.println(set);
// 需求：将Stream转化为Map集合
// 明确：每个元素以“:”来分割，左边的为key，右边的为value
Stream<String> stream = Stream.of("张三:成都", "李四:武汉", "王五:重庆");
Map<String, String> map = stream.collect(Collectors.toMap(str -> str.substring(0, str.indexOf(":")), str -> str.substring(str.indexOf(":") + 1)));
map.forEach((k, v) -> System.out.println("key：" + k + "，value：" + v));
```

在以上的代码中，我们将Stream流中计算的数据转化为List和Set集合时，此时并没有明确存储数据对应集合的具体类型，想要明确存储数据对应集合的具体类型，则就需要使用toCollection来实现。
【示例】演示toCollection的实现

```java
List<String> list = Arrays.asList("I", "love", "you", "too");
// 需求：将Stream转化为ArrayList集合
ArrayList<String> arrayList = list.stream().collect(Collectors.toCollection(ArrayList::new));
System.out.println(arrayList);
// 需求：将Stream转化为LinkedList集合
LinkedList<String> linkedList = list.stream().collect(Collectors.toCollection(LinkedList::new));
System.out.println(linkedList);
// 需求：将Stream转化为HashSet集合
HashSet<String> hashSet = list.stream().collect(Collectors.toCollection(HashSet::new));
System.out.println(hashSet);
// 需求：将Stream转化为TreeSet集合
TreeSet<String> treeSet = list.stream().collect(Collectors.toCollection(TreeSet::new));
System.out.println(treeSet);
```

【示例】获得年龄大于20岁的女同学，然后返回按照年龄进行升序排序后的List集合

```java
List<Student> list = StudentData.getStudentList();
ArrayList<Student> arrayList =
 list.stream().filter(stu -> stu.getAge() > 18). // 过滤年龄小于等于18的学生
 filter(stu -> stu.getSex().equals("女")). // 过滤男性学生
 sorted(Comparator.comparing(Student::getAge)). // 按照年龄执行升序排序
 collect(Collectors.toCollection(ArrayList::new)); // 转化为ArrayList存储
arrayList.forEach(System.out :: println);
```

在归集的知识点中，我们实现了将Stream中计算的数据转化为集合或Map，那么能否将Stream中计算的数据转化为数组呢？答案是可以的，我们可以使用Stream提供的toArray静态方法来实现。
【示例】将Stream中计算的数据转化为数组

```java
List<String> list = Arrays.asList("aa", "bb", "cc", "dd");
// 需求：将Stream转化为数组
Object[] array = list.stream().toArray();
System.out.println(Arrays.toString(array));
// 需求：将Stream转化为“指定类型”的数组
String[] stringArray = list.stream().toArray(String[]::new);
System.out.println(Arrays.toString(stringArray));
```





#### 统计（counting/averaging）

Collectors提供了一系列用于数据统计的静态方法：

1. 计数：counting
2. 平均值：averagingInt、averagingLong、averagingDouble
3. 最值：maxBy、minBy
4. 求和：summingInt、summingLong、summingDouble
5. 统计以上所有：summarizingInt、summarizingLong、summarizingDouble

【示例】对学生的年龄进行统计

```java
List<Student> list = StudentData.getStudentList();
// 需求：获得元素的个数
Long count = list.stream().collect(Collectors.counting());
System.out.println(count);
// 需求：获得学生的平均年龄
Double averAge = list.stream().collect(Collectors.averagingDouble(Student::getAge));
System.out.println(averAge);
// 需求：获得最大年龄的学生
Student stu = list.stream().collect(Collectors.maxBy((stu1, stu2) -> stu1.getAge() - stu2.getAge())).get();
System.out.println(stu);
// 需求：获得所有学生年龄之和
Long sum = list.stream().collect(Collectors.summingLong(Student::getAge));
System.out.println(sum);
// 需求：获得年龄的所有的信息
IntSummaryStatistics collect = list.stream().collect(Collectors.summarizingInt(Student::getAge));
System.out.println(collect);
```





#### 分组（groupingBy）

分组（groupingBy），将Stream按条件分为两个Map，比如按照学生年龄分为两个Map集合。
【示例】按照学生性别分为两个Map集合

```java
List<Student> list = StudentData.getStudentList();
// 需求：按照学生性别进行分组
Map<String, List<Student>> map = list.stream().collect(Collectors.groupingBy(Student::getSex));
map.forEach((k, v) -> System.out.println("key：" + k + "，value：" + v));
```





#### 接合（joining）

接合（joining），把Stream计算的数据按照一定的规则进行拼接。
【示例】获得所有学生的名字拼接成一个字符

```java
List<Student> list = StudentData.getStudentList();
// 需求：将所有学生的姓名连接成一个字符串，每个名字之间以“,”连接
String allName = list.stream().map(Student::getName).collect(Collectors.joining(", "));
System.out.println(allName);
```









# Java新特性

## 概述

纵观Java这几年的版本变化，在Java被收入Oracle之后，Java以小步快跑的迭代方式，在功能更新上迈出了更加轻快的步伐。基于时间发布的版本，可以让Java研发团队及时获得开发人员的反馈，因此可以看到最近的Java版本，有很多语法层面简化的特性。同时，Java在支持容器化场景，提供低延迟的GC方面(ZGC等)也取得了巨大的进步。

注意一个新特性的出现通常会经过以下阶段：

1.  孵化器（Incubator）阶段：这是新特性最早的开发和试验阶段，此时新特性只能作为一个单独的模块或库出现，而不会包含在Java SE中。在这个阶段，特性的设计可能会有些不稳定，而且会经常调整和变更。 
2.  预览（Preview）阶段：在经过了孵化器阶段的验证和修改后，新特性进入了预览阶段，这是一种在Java SE内部实现的，开发人员可以使用并对其提供反馈的渠道。此时特性可能被包含在Java SE版本中，但是它默认是未开启的，需要通过特定的命令行参数或其他方式进行启用。 
3.  正式版（GA）阶段：在经过了预览阶段的反复测试和修复后，新特性最终会在Java SE的稳定版本中发布。此时，特性被默认开启，成为Java SE的一部分，并可以在各个Java应用程序中使用。 

需要注意的是，上述阶段并非一成不变，并不是所有JEP（Java Enhancement Proposal：Java增强方案）都需要经过孵化器阶段和预览阶段，这取决于特定的提案和规划。但是，Java SE领导小组通常会遵循这些阶段的流程，以确保新特性可以经过充分的评估和测试，以便能够稳定和可靠地使用在Java应用程序中。

在以下的内容中，我们对Java9到Java21新特性做一个简单的概述。



## Java9-Java21新特性

``Java8、Java11、Java17、Java21是长期支持版本。``

``Java8最多，新项目Java17。``



其余略。





## 语法方面的变化

### jShell

jShell命令是Java9引进的新特性，像Python和Scala之类的语言早就有交互式编程环境REPL (read-evaluate-print-loop)，以交互式的方式对语句和表达式进行求值。开发者只需要输入一些代码，就可以在编译前获得对程序的反馈。而之前的Java 版本要想执行代码，必须创建文件、声明类、提供测试方法方可实现。
我们打开DOS命令窗口，然后输入jshell，就能进入交互式编程环境REPL，如下图所示：

![image-20241014175806224](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410141758466.png)





### try-with-resources

众所周知，所有被打开的系统资源，比如流、文件、Socket连接等，都需要被开发者手动关闭，否则随着程序的不断运行，资源泄露将会累积成重大的生产事故。
在Java7以前，我们想要关闭资源就必须的finally代码块中完成。
【示例】Java7之前资源的关闭的方式

```java
public void copyFile1(File srcFile, File destFile) {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        // 实例化IO流（输入流和输出流）
        fis = new FileInputStream(srcFile);
        fos = new FileOutputStream(destFile);
        // 拷贝文件（存储和读取）
        int len = 0;
        byte[] bytes = new byte[1024];
        while ((len = fis.read(bytes)) != -1) {
            fos.write(bytes, 0, len);
        }
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        // 关闭资源
        if (fis != null) {
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if (fos != null) {
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

Java7及以后关闭资源的正确姿势：try-with-resource，该语法格式为：

```java
try(/*实例化需要关闭资源的对象或引用需要关闭资源的对象*/){
	// 书写可能出现异常的代码
} catch(Exception e) {
	// 处理异常
}
```

使用try-with-resource来自动关闭资源，则需要关闭资源的对象对应的类就必须实现java.lang.AutoCloseable接口，该接口中提供了一个close()的抽象方法，而自动关闭资源默认调用的就是实现于java.lang.AutoCloseable接口中的close()方法。
因为FileInputStream类和FileOutputStream类都属于java.lang.AutoCloseable接口的实现类，因此此处文件拷贝的操作就可以使用try-with-resource来自动关闭资源。
【示例】Java7之后资源的关闭的方式

```java
public void copyFile(File srcFile, File destFile) {
    // 实例化IO流（输入流和输出流）
    try (FileInputStream fis = new FileInputStream(srcFile);
         FileOutputStream fos = new FileOutputStream(destFile)) {
        // 拷贝文件（存储和读取）
        int len = 0;
        byte[] bytes = new byte[1024];
        while ((len = fis.read(bytes)) != -1) {
            fos.write(bytes, 0, len);
        }
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

通过try-with-resource来关闭放资源，即使资源很多，代码也可以写的很简洁，如果用Java7之前的方式去关闭资源，那么资源越多，用finally关闭资源时嵌套也就越多。
在Java9之后，为了避免在try后面的小括号中去实例化很多需要关闭资源的对象（复杂），则就可以把需要关闭资源的多个对象在try之前实例化，然后在try后面的小括号中引用需要关闭资源的对象即可，从而提高了代码的可读性。
【示例】Java9之后的使用方式

```java
public void copyFile(File srcFile, File destFile) throws FileNotFoundException {
    // 实例化IO流（输入流和输出流）
    FileInputStream fis = new FileInputStream(srcFile);
    FileOutputStream fos = new FileOutputStream(destFile);
    // 拷贝文件（存储和读取）
    try (fis; fos) {
        int len = 0;
        byte[] bytes = new byte[1024];
        while ((len = fis.read(bytes)) != -1) {
            fos.write(bytes, 0, len);
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

在以上代码中，表达式中引用了fis和fos，那么在fis和fos就自动变为常量啦，也就意味着在try代码块中不能修改fis和fos的指向，从而保证打开的资源肯定能够关闭。





### 局部类型推断

在Java10中，新增了局部变量类型判断。在方法体或代码块中，对于可以在编译期确定的类型，可以使用var来定义。这个特性并不意味着java是弱类型的语言，仅是提供了更简洁的书写方式。对于编译期无法确定的类型，依然要写清楚类型。
【示例】局部变量类型判断案例

```java'
// 使用var来作为变量的引用声明
var num = 123;
var str = "hello world";
var arr = new int[] {11, 22, 33};
var arrayList = new ArrayList<String>();
var calendar = Calendar.getInstance();
// 以下为不可以声明为var的情况
// 1.使用var必须要求变量必须初始化
// var userName;
// 2.不能给变量赋null值
// var userName = null;
// 3.lambda表达式不可以声明为var
// var function = (num) -> Math.round(3.51);
// 4.方法引用不可以声明为var
// var method = System.out :: println;
// 5.数组静态初始化不可以声明为var
// var arr = {"aa", "bb", "cc"};
// 6.类的成员变量不可以使用var类型推断
// 7.所有参数声明，返回值类型，构造方法参数都不可以
```







### instanceof的模式匹配

在JDK14中新增instanceof模式匹配增强(预览)，在JDK16中转正。通过instanceof模式匹配增强，我们就可以直接在模式匹配的括号内声明对应类型的局部变量。
【示例】执行向下转型的操作，从而调用show()方法

```java
/**
 * 以前的代码实现方式
 */
@Test
public void testOld() {
    // 父类引用指向子类对象（多态）
    Animal animal = new Dog();
    // 判断animal是否为Dog类的实例
    if (animal instanceof Dog) {
        // 指向向下转型的操作
        Dog dog = (Dog) animal;
        // 调用Dog类特有的show()方法
        dog.show();
    }
}
/**
 * 使用instanceof模式匹配增强的实现方式
 */
public void testNew() {
    // 父类引用指向子类对象（多态）
    Animal animal = new Dog();
    // 如果animal是Dog类的实例，则向下转型后就命名为dog
    if (animal instanceof Dog dog) {
        // 调用Dog类特有的show()方法
        dog.show();
    }
}
```

【示例】重写equals()，判断成员变量是否相等

```java
public class Tiger {
    String name;
    int age;

    /**
     * 以前的代码实现方式
     */
    /*@Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null) return false;
        // 如果obj属于Tiger类型，则就执行向下转型的操作
        if (obj instanceof Tiger) {
            // 执行向下转型的操作，恢复对象的实际类型
            Tiger tiger = (Tiger) obj;
            // 如果成员变量都相等，则返回true，否则返回false
            return age == tiger.age && Objects.equals(name, tiger.name);
        }
        // 如果obj不属于Tiger类型，则返回false即可
        return false;
    }*/

    /**
     * 使用instanceof模式匹配增强的实现方式
     */
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null) return false;
        // 如果obj属于Tiger类型并且成员变量值都相等，那么返回true
        if (obj instanceof Tiger tiger) {
            return age == tiger.age && Objects.equals(name, tiger.name);
        }
        // 如果obj不属于Tiger类型，则返回false即可
        return false;
    }
}
```







### switch表达式

目前switch表达式的问题：

1. 匹配自上而下，若无break，后面的case语句都会执行
2. 不同的case语句定义的变量名不能相同
3. 不能在一个case后面写多个值
4. 整个switch不能作为表达式的返回值

在Java12中对switch表达式做了增强（预览），能够使用更加简洁的代码来解决这些问题。
【示例】switch表达式使用的案例

```java
/**
 * 需求：根据月份输出对应季节的特点
 * 方案一：使用以前的技术来实现
 */
public static void normalSwitch(int month) {
    // 定义一个变量，用于保存季节的特点
    String season;
    // 判断month的取值，从而知晓对应的季节
    switch (month) {
        case 12:
        case 1:
        case 2:
            season = "白雪皑皑";
            break;
        case 3:
        case 4:
        case 5:
            season = "春意盎然";
            break;
        case 6:
        case 7:
        case 8:
            season = "夏日炎炎";
            break;
        case 9:
        case 10:
        case 11:
            season = "秋高气爽";
            break;
        default:
            throw new RuntimeException("没有该月份。。。");
    }
    // 输出month对应季节的特点
    System.out.println(season);
}

/**
 * 需求：根据月份输出对应季节的特点
 * 方案二：使用Java12的新特性来实现
 */
public static void newSwitch(int month) {
    // 判断month的取值，获得对应季节的特点
    String season = switch (month) {
        case 12, 1, 2 -> "白雪皑皑";
        case 3, 4, 5 -> "春意盎然";
        case 6, 7, 8 -> "夏日炎炎";
        case 9, 10, 11 -> "秋高气爽";
        default -> throw new RuntimeException("没有该月份。。。");
    };
    // 输出month对应季节的特点
    System.out.println(season);
}
```

在Java13中，增加关键字yield关键字（预览）， 用于在switch表达式中返回结果。到Java14版本中，Java12和Java13中关于switch的新特性都确定为正式版本。
【示例】switch表达式中的yield关键字（针对老语法）

```java
/**
 * 需求：根据月份输出对应季节的特点
 * 演示：Java13版本中新增的yield新特性
 */
public static void yieldSwitch1(int month) {
    // 判断month的取值，获得对应季节的特点
    String season = switch (month) {
        case 12, 1, 2:
            yield "白雪皑皑";
        case 3, 4, 5:
            yield "春意盎然";
        case 6, 7, 8:
            yield "夏日炎炎";
        case 9, 10, 11:
            yield "秋高气爽";
        default:
            throw new RuntimeException("没有该月份。");
    };
    // 输出month对应季节的特点
    System.out.println(season);
}
```





### 文本块

在Java语言中，通常需要使用String类型表达HTML，XML，SQL或JSON等格式的字符串，在进行字符串赋值时需要进行转义和连接操作，然后才能编译该代码，这种表达方式难以阅读并且难以维护。
在Java12版本中，新增了文本块（预览）。文本块就是指多行字符串，例如一段格式化后的xml、json等。而有了文本块以后，用户不需要转义，Java能自动搞定。因此，文本块将提高Java程序的可读性和可写性。
【示例】演示文本块的使用

```java
// 使用以前拼接的方式
String html1 = "<html>\n" +
        "      <body>\n" +
        "            <p>Hello， world</p>\n" +
        "      </body>\n" +
        "</html>";
System.out.println(html1);
// 使用文本块的方式
String html2 = """
        <html>
              <body>
                    <p>Hello， world</p>
              </body>
        </html>
        """;
System.out.println(html2);
```

在Java14版本中，针对文本块又新增两个特性（阅览）。

1)在一行的结尾增加“\”可以取消改行的换行符。

2)可以通过“\s”增加空格。
【示例】演示文本块新增特性

```java
// 取消换行（\）
String json1 = """
        {
            "username":"ande"，\
            "age":18
        }
        """;
System.out.println(json1);
// 添加空格（\s）
String json2 = """
        {
            "username"\s:\s"ande"，
            "age"\s:\s18
        }
        """;
System.out.println(json2);
```





### Record

早在2019年2月份，Java语言架构师Brian Goetz就吐槽了Java语言，他和很多程序员一样抱怨“Java太啰嗦”或有太多的“繁文缛节”，他提到：开发人员想要创建纯数据载体类，通常都必须编写大量低价值、重复的、容易出错的代码。例如：构造方法、getter/setter、equals()、hashCode()以及toString()等。
以至于很多人选择使用IDE的功能来自动生成这些代码。还有一些开发会选择使用一些第三方类库，如Lombok等来生成这些方法，从而会导致了令人吃惊的表现和糟糕的可调试性。
那么，Brian Goetz大神提到的纯数据载体到底指的是什么呢？我们举了一个简单的例子：

```java
public final class Tiger {
    private final String name;
    private final int age;

    public Tiger(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String name() {
        return name;
    }

    public int age() {
        return age;
    }

    @Override
    public boolean equals(Object obj) {
        if (obj == this) return true;
        if (obj == null || obj.getClass() != this.getClass()) return false;
        var that = (Tiger) obj;
        return Objects.equals(this.name, that.name) &&
                this.age == that.age;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }

    @Override
    public String toString() {
        return "Tiger[" +
                "name=" + name + ", " +
                "age=" + age + ']';
    }
}
```

这里面的Tiger其实就是一个纯数据载体，Tiger类中提供了name和age两个私有常量，并且只提供了全参构造方法和常量名相同的getter方法，以及一些equals、hashCode和toString等方法。于是，BrianGoetz大神提出一种想法，他提到，Java完全可以对于这种纯数据载体通过另外一种方式表示。
在Java14版本中，新增了Record类型。Record是Java的一种新的类型，Record使数据类型变得非常简洁，一般可以帮助我们定义一些简单的用于纯数据载体的实体类。

**Record类的特点：**
状态声明中的每个属性，都是默认采用了private和final修饰，则属性值就不可修改
在Record类中，默认已经重写了Object类提供的equals()，hashcode()，toString()方法
在Record类中，默认提供全参的构造方法，并且提供的getter方法名和属性名保持一致。
Record类采用了final修饰，并且显示的继承于java.lang.Record类，因此就不能继承别的父类。
【示例】将以上的Tiger类转化为Record类

```java
public record Tiger(String name, int age)  {

}
```

在以上的Record类中，Tiger类默认采用了final修饰，并且显示的继承于java.lang.Record抽象类，因此Tiger类就不能继承于别的父类。在Tiger类中，提供了name和age两个私有常量，并且还提供了一个public修饰的全参构造方法，提供的getter方法的名字和属性名保持一致，但是并没有提供setter方法。并且，在Tiger类中还重写了Object类提供的equals()，hashcode()，toString()方法。
在Record类中，我们还可以新增静态属性、无参构造方法、成员方法和静态方法，但是创建对象时不能调用无参构造方法，而是通过全参构造方法创建对象的时候，默认就会调用Record类中的无参构造方法。
【示例】在Record类中添加的内容

```java
public record Tiger(String name, int age)  {
    // 新增静态属性
    static double score;
    // 新增无参构造方法
    // 注意：通过全参构造方法创建对象，默认就会调用此处的无参构造方法
    public Tiger {
        System.out.println("无参构造方法");
    }
    // 新增成员方法
    void show() {
        System.out.println("show. ..");
    }
    // 新增静态方法
    static void method() {
        System.out.println("method ...");
    }
}
```





### 密封类

Java中的密封类是一种新的类修饰符，它可以修饰类和接口，可以控制哪些类可以扩展或实现该类或接口。下面是密封类的一些主要用途：

1. 维护类层次结构的封闭性

密封类的一个主要用途是确保类层次结构的封闭性。这意味着，如果您想保护一组类，而不希望其他类继承或实现它们，可以使用密封类来实现这一目标。这对于确保代码的安全性和稳定性非常有用。

2. 预防代码的意外扩展

密封类可以防止其他程序员意外地扩展一个类。在进行类设计时，您可能希望自己或其他程序员只能在特定的类中实现或继承指定的类。在这种情况下，您可以将类标记为“密封”，强制限制其他程序员可以实现或继承的类的范围。

3. 增强代码的可读性和可维护性



在Java15版本中，新增了密封类和密封接口（预览）。
使用sealed关键字修饰的类，我们就称之为密封类。密封类必须是一个父类，我们可以使用permits关键字来指定哪些子类可以继承于密封类，并且密封类的子类必须使用sealed、final或non-sealed来修饰。
【示例】密封类的演示

```java
// 密封类必须被继承，并且使用permits来指定哪些子类可以被继承
sealed class Animal permits Dog, Bird, Tiger { }
// 注意：密封类的子类必须使用sealed、final或non-sealed来修饰
// final关键字修饰的子类，则该子类不能被继承
final class Tiger extends Animal { }
// non-sealed修饰的子类，则该子类就是一个普通类
non-sealed class Bird extends Animal { }
// sealed修饰的子类，则该类就必须被继承，否则就会编译错误
sealed class Dog extends Animal {}
non-sealed class SmallDog extends Dog {}
```

使用sealed关键字修饰的接口，我们就称之为密封接口。密封接口必须使用permits关键字来指定实现类或子接口。针对密封接口的实现类，则必须使用sealed、final或non-sealed来修饰；针对密封接口的子接口，则必须使用sealed或non-sealed来修饰。
【示例】密封接口的演示

```java
// 使用sealed修饰的接口，则必须使用permits来指定实现类或子接口。
public sealed interface InterA permits Student, InterB { }
// 密封接口的实现类，必须使用sealed、final或non-sealed来修饰
non-sealed /*final*/ /*sealed*/ class Student implements InterA { }
// 密封接口的子接口，必须使用sealed或non-sealed来修饰
non-sealed /*sealed*/ interface InterB extends InterA {}
```

**sealed与record：**
因为Record类默认采用了final关键字修饰，因此Record类就可以作为密封接口的实现类。
【示例】密封接口和Record类

```java
// 密封接口
sealed interface Flyable permits SuperMan { }
// 让Record类作为密封接口的实现类
record SuperMan(String name, int age) implements Flyable { }
```









## API层面变化

### ``String存储结构改变``

在Java8及其之前，String底层采用char类型数组来存储字符；在Java9及其以后，String底层采用byte类型的数组来存储字符。将char[]转化为byte[]，其目的就是为了节约存储空间。

![image-20241014201338285](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410142013516.png)





### ``String 新增的方法``

在Java11版本中，对String类新增了一些方法，新增的方法如下：

```java
// 空格，制表符，换行等都认为是空的
boolean blank = "\t \n".isBlank();
System.out.println(blank); // 输出：true

String source = "\u3000\u3000\u3000\u3000\u3000\u3000\u3000\u3000www.baidu.com\u3000\u3000\u3000\u3000\u3000";
// 去除“前后”的中文空格
System.out.println(source.strip());
// 去除“开头”的中文空格
System.out.println(source.stripLeading());
// 去除“末尾”的中文空格
System.out.println(source.stripTrailing());

// 把字符串内容重复n份
String repeat = "xixi".repeat(3);
System.out.println(repeat); // 输出：xixixixixixi

// 按照换行来分割字符串，返回的结果是Stream对象
Stream<String> lines = "a\nb\nc\n".lines();
System.out.println(lines.count()); // 输出：3

"a\nb\nc\n".lines().forEach(System.out::println);  // a  b  c
```

在Java12版本中，对String类新增了一些方法，新增的方法如下：

```java
// 在字符串前面添加n个空格
String result2 = "Java Golang".indent(4);
System.out.println(result2);
```





### ``接口支持私有方法``

在Java8版本中，接口中支持“公开”的静态方法和公开的默认方法；在Java9版本中，接口中还允许定义“私有”的静态方法和成员方法，但是不能定义私有的默认方法。
【示例】演示接口中的私有静态方法和成员方法

```java
/**
 * 接口（JDK1.9）
 */
public interface Flyable {
    // 私有的静态方法
    private static void staticMethod() {
        System.out.println("static method ...");
    }
    // 私有的成员方法
    private void method() {
        System.out.println("default method ...");
    }
}
```





### ``标识符命名的变化``

在Java8及其之前，标识符可以独立使用“_”来命名。

```java
String _ = "hello";
System.out.println(_);
```

但是，在Java9中规定“_”不能独立命名标识符了，如果使用就会报错：

![image-20241014201525277](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410142015440.png)





### ``简化编译运行程序``

在我们的认知里面，要运行一个Java源代码必须先编译（javac命令），再运行（java命令），两步执行动作。而在Java 11版本中，通过一个java命令就直接搞定了。
需要执行的程序：

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("hello world");
    }
}
```

执行java命令进行运行，如下图所示：

![image-20241014201635338](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202410142016530.png)





### ``创建不可变集合``

在Java9版本中，我们可以通过List、Set和Map接口提供的of(E... elements)静态方法来创建不可变集合。通过此方式创建的不可变集合，我们不但不能添加或删除元素，并且还不能修改元素。
【示例】创建不可变集合

```java
// 创建不可变List集合
List<Integer> list = List.of(1, 2, 3, 4, 5);
System.out.println(list);
// 创建不可变Set集合
// 注意：如果Set集合中有相同的元素，则就会抛出IllegalArgumentException异常。
Set<Integer> set = Set.of(1, 2, 3, 4, 5, 4);
System.out.println(set);
// 创建不可变Map集合
Map<Integer, String> map = Map.of(123, "武汉", 456, "成都");
System.out.println(map);
```

Arrays.asList与List.of的区别：
List.of：不能向集合中添加或删除元素，也不能修改集合中的元素。
Arrays.asList：不能向集合中添加或删除元素，但是可以修改集合中的元素。

【示例】Arrays.asList与List.of的区别

```java
// 通过Arrays.asList()方法创建不可变集合
List<Integer> list1 = Arrays.asList(1, 2, 3, 4, 5);
// list1.add(6); // 抛出UnsupportedOperationException异常
// list1.remove(2); // 抛出UnsupportedOperationException异常
list1.set(2, 33); // 没有问题
System.out.println(list1); // 输出：[1, 2, 33, 4, 5]

// 通过List.of()方法创建不可变集合
List<Integer> list2 = List.of(1, 2, 3, 4, 5);
// list2.add(6); // 抛出UnsupportedOperationException异常
// list2.remove(2); // 抛出UnsupportedOperationException异常
// list2.set(2, 33); // 抛出UnsupportedOperationException异常
```

​	



### ``Optional API``

在Java8以前，Java程序员操作对象时，为了避免错误引用null造成的空指针异常，往往需要一系列繁杂冗余的判空操作，增加了许多重复代码，降低了代码可读性，于是Java 8引入Optional类，优雅简洁的对null值进行处理，从而避免出现空指针异常（NullPointerException）。
本质上，Optional 类是一个包含有可选值的包装类，这意味着 Optional 类中既可以含有对象也可以为null。

#### ``创建Optional对象``

使用Optional类提供的of()和ofNullable() 静态方法来创建包含值的Optioanal实例。
如果将null当作参数传进去of()会抛出空指针异常，如果将null当作参数传进去 ofNullable() 就不会抛出空指针异常。
因此当对象可能存在或者不存在，应该使用 ofNullable()方法来创建Optional实例。
【示例】创建一个Optional实例

```java
// 创建一个包含“null”的Optional示例
Optional<Object> optional1 = Optional.ofNullable(null);
// 创建一个包含“对象”的Optional示例
Optional<String> optional2 = Optional.ofNullable("hello");
```

#### ``Optional类的方法``

想要获得Optional实例中包含的值，那么就可以使用以下两个方法来实现。

| **方法名**               | **描述**                                                     |
| ------------------------ | ------------------------------------------------------------ |
| public T get()           | 如果值不为null，则直接取出该值；如果值为null，则抛出空指针异常。 |
| public T orElse(T other) | 如果值不为null，则直接取出该值；如果值为null，则取出的就是参数other的值。 |

开发中，我们获取Optional中存储的值，一般都是采用orElse(T other)方法来实现。
【示例】演示get()方法

```java
// 创建一个包含“null”的Optional示例
Optional<Object> optional1 = Optional.ofNullable(null);
Object obj1 = optional1.get(); // 抛出空指针异常
// 创建一个包含“对象”的Optional示例
Optional<String> optional2 = Optional.ofNullable("hello");
String str = optional2.get();
System.out.println(str); // 输出：hello
```

【示例】演示orElse(T other)方法

```java
// 创建一个包含“null”的Optional示例
Optional<Object> optional1 = Optional.ofNullable(null);
Object str1 = optional1.orElse("world");
System.out.println(str1); // 输出：world
// 创建一个包含“对象”的Optional示例
Optional<String> optional2 = Optional.ofNullable("hello");
String str2 = optional2.orElse("world");
System.out.println(str2); // 输出：hello
```

#### ``Optional的使用案例``

需求：有一场商业表演，原计划让“刘亦菲”来表演，如果“刘亦菲”不能参加，则就换“佟丽娅”来表演，该需求的实现代码如下：

```java
// 定义一个变量，用于保存表演者的名字
// String name = "刘亦菲"; // 原计划
String name = null; // 刘亦菲不能参加的情况
// 使用Optional来封装表演者的名字
Optional<String> optional = Optional.ofNullable(name);
// 获得实际参与表演对应人的名字
// 如果name的值为null，则就换为“佟丽娅”参与表演
String finalName = optional.orElse("佟丽娅");
// 输出实际表演者的名字
System.out.println(finalName);
```

```java
String name = null;

/*      
		Optional<String> name1 = Optional.ofNullable(name);
        String s = name1.orElse("dingwan");
*/
String s = Optional.ofNullable(name).orElse("dingwan");

System.out.println(s);   // dingwan
```









# 正则表达式

![image-20240822003806770](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408220038860.png)

### 常见符号

![image-20240822003844504](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408220038581.png)

![image-20240822004411833](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408220044929.png)























































































# Java 虚拟机规范

HotSpot ---->  Oeacle JDK、Open JDK在用

![image-20240804135113024](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041351144.png)

>  **Run-Time Data Areas**

![image-20240804135000558](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041350703.png)

> **JDK6:**

![image-20240804140852448](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041408531.png)

![image-20240804141125260](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041411339.png)



> **JDK7:**

![image-20240804141109691](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041411779.png)

![image-20240804141208598](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041412667.png)

> **JDK8**+

![image-20240804141654791](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041416895.png)

![image-20240804141356441](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408041413507.png)

