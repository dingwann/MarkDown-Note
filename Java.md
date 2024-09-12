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

**精度损失与否看转换后类型能否存下**

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

**因为==比较的是对象的值，字符串本质是String，自动装箱的因为String重写了equal方法所以没问题。new出来的话就会造成其内存地址不一样而造成误判**

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

出现在实例方法中，代表当前的对象。this 大部分情况下可以省略。

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

构造方法名 == 类名（必须）

> #### 构造方法会将new出的对象内存地址返回，但是我们不需要写 return，也不需要写返回值类型。



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

> **3.4 访问权限不能变低可以变高。public protected 默认 private**
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

- ### **前提是两种类型必须有继承关系才能编译通过。**

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
   Bird b = (Bird)a; 
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

没有名字的类，**只能使用一次。**

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
    // 另外一种实现接口方式
    WINTER("冬季", "x") {
        @Override
        public void eat() {
            ...
        }
    };
    
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

默认无参创建时的数组长度为0，当第一次调用add方法时，底层调用grow()方法会长度为10；

扩容为原来容量的1.5倍



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

**HashSet底层是HashMap，Set接口的实现类都是new的对应Map接口/类**

![image-20240907153730575](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202409071537634.png)

**将Map的key部分取出来对应的就是set集合**





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

