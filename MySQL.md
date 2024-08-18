## 课程大纲目录

![image-20240812134400129](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408121344288.png)

## 什么是SQL

结构化查询语言（Structured Query Language），简称SQL，是一种特殊的编程语言。

- **SQL的分类**

![image-20240812141455564](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408121414672.png)



> **登录**

```mysql
mysql -uroot -p
passwordd:
```



![image-20240813154912045](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131549232.png)



## MySQL 命令行基本命令

- **列出当前数据库管理系统有哪些数据库**

```mysql
show databases;
```

![image-20240813155318107](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131553140.png)

mysql数据库里存储了很多表，包括user，user默认存在root。



- **创建新的数据库**

```mysql
create database 数据库名;
```

![image-20240813155630941](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131556970.png)

- **使用数据库和显示其所有表**

```mysql
use 数据库名;
show tables;
```

![image-20240813155814523](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131558550.png)

- **删除数据库**

```mysql
drop database 库名;
```

![image-20240813155946347](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131559375.png)

- **当前使用的数据库**

```mysql
select database();
```

![image-20240813160133252](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131601277.png)

- **查看MySQL 版本**

登录情况

```mysql
select version();
```

windows环境

```
mysql --version
```



## 数据库表的描述

![image-20240813183057808](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131830946.png)



> **SQL 脚本的使用**

- 在对应数据库里

```mysql
source xxx.sql;
```



查询数据库表的结构

```mysql
desc 表名;
```

![image-20240813185727669](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131857791.png)

查看该表的数据

```mysql
select * from 表名;
```

![image-20240813185753505](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131857533.png)



## 查询（DQL）

### 简单查询

**select 语句由：select 子句（查询内容）、from 子句（查询对象）、where 子句（查询条件）、order by 子句（排序方式）、group by子句（分组方式）等组成。**

#### 查一个字段

- **查询表里的一个字段，即一列**

```mysql
select 字段名 from 表名;
```

SQL 语句必须 ; 结尾。

SQL 语句大小写都可以。

示例：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408131908898.png" alt="image-20240813190846857" style="zoom: 80%;" />



#### 查多个字段

- **查询表里的多个字段，即几列。**

```mysql
select 字段1,字段2,... from 表名;
```

![image-20240813235107111](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408132351262.png)



#### 查询时字段可参与数学运算

```mysql
select 字段[+ - * /] from 表名;
```

![image-20240813235503203](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408132355243.png)



#### 查询时字段可起别名

```mysql
select 字段 as 字段新名 from 表名;
```

![image-20240813235801258](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408132358308.png)

>  **as 也可以省略，后面空格了写别名就行，但是别名里有空格会报错，别名含空格记得加 ' ' 包裹即可**



### 条件查询

顾名思义，在查询的时候拿出满足条件的数据，就是对数据进行条件过滤。

![image-20240814000225347](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408140002400.png)

- **语法格式**

```mysql
select ... from ... where 条件;
```

**执行顺序：**

1. 先执行 from 找到表
2. 再执行 where 进行过滤
3. 最后再 select 进行选择



#### 等于和不等于

```mysql
select ... from ... where xxx = xxx;
```

![image-20240814000946467](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408140009501.png)

```mysql
select ... from ... where xxx <>[!=] xxx;
```

![image-20240814001341126](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408140013246.png)

不等于推荐写 <>



#### 大于、大于等于、小于、小于等于

```mysql
select ... from ... where xxx > xxx;
```

![image-20240815150925826](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151509921.png)



```mysql
select ... from ... where xxx >= xxx;
```

![image-20240815151020136](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151510171.png)



```mysql
select ... from ... where xxx < xxx;
```

![image-20240815151034509](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151510548.png)



```mysql
select ... from ... where xxx <= xxx;
```

![image-20240815151053853](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151510899.png)



#### and 和 or

```mysql
select ... from ... where ... and[&&] ...;
```

![image-20240815151551635](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151515668.png)



```mysql
select ... from ... where ... or[||] ...;
```

![image-20240815151805994](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202408151518035.png)



> **and 的优先级大于 or ，如果不确定就加括号**



#### between ... and

等同于 >= and <=，写法不一样而已，效率和 >=  and  <= 没有区别

两边都是闭区间

```mysql
select ... from ... where ... between ... and ...;
```



![image-20240815152701560](C:\Users\liuwang\AppData\Roaming\Typora\typora-user-images\image-20240815152701560.png)



#### is null 和 is not null































