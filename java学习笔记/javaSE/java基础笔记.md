

# **java数据类型**

*旁白：*

**为什么要有数据类型**

因为java是**强类型**的语言，对于每一种 数据 都给出了明确的数据类型，不同的数据类型也分配了不同的内存空间，所以它们的表示数据的大小也不一样。



计算机储存设备的最小单元叫 “**位(bit)** ” 又称为比特位，用小写字母 “ b"表示。而计算机最小储存单元叫 ” **字节（byte）“**，用” B “ 表示，字节是由连续的8个位（bit）组成的

1B(字节) = 8bit  

1024B = 1KB

1MB = 1024KB

1GB = 1024MB

1TB = 1024GB





### 一、java基本数据类型

数据类型是以后开发中经常用到的东西，基本数据类型就9个关键字常用不用担心学不懂。



一、**数据类型有两大类型**：基本数列类型 和 引用数据类型

**基本数据类型：**

* 数值型：整数型（byte,short，int,long）浮点型（float，double）字符型（char）

* 非数值型：布尔（boolean）

	​	

**引用数据类型：(前期基本不学知道就好)**

​		类（class）

​		接口（intertace）

​		数组（ [] ）



### 1.常量的介绍：（认识就行）

| 常量：     |                      |                       |
| ---------- | -------------------- | --------------------- |
| 字符串常量 | 引号括起来的内容     | “hell”  ，“钱”        |
| 整数常量   | 不带小数点的数字     | 666， -666            |
| 字符常量   | 用单引号括起来的内容 | ‘c' 'A' 'o'           |
| 布尔常量   | 布尔值，表示真假     | true(真)，false（假） |
| 空常量     | 一个特殊的值，空值   | 值是null              |
| 小数常量   | 带小数的数字         | 12.13  -5.31          |

### 2.数据类型

| 整数型            | 位   | 字节 | 取值范围（可储存值的范围） |
| ----------------- | ---- | ---- | -------------------------- |
| byte（字节型）    | 8位  | 1B   | -128 ~ 127                 |
| short(短整形)     | 16位 | 2B   | -32768 ~ 32767             |
| int(默认)（整形） | 32位 | 4B   | -2的31次方 ~ 2的31次方-1   |
| long （长整型）   | 64位 | 8B   | -2的63次方 ~ 2的63次方-1   |

| 浮点型                       | 位   | 字节 | 取值范围(科学计数法表示)                                     |
| ---------------------------- | ---- | ---- | ------------------------------------------------------------ |
| float（单精度浮点型）        | 32位 | 4B   | 负数：-3.402823E+38 ~ -1.401298E-45    正数：1.401298E-45 ~ 3.402823E+38 |
| double(默认)（双精度浮点型） | 64位 | 8B   | 负数：-1.797693E+308 ~ -49000000E-324   正数：49000000E-324 ~ 1.797693E+308 |

| 字符              | 位   | 字节 | 取值范围                  |
| ----------------- | ---- | ---- | ------------------------- |
| char（字符型）    | 16位 | 2B   | 0~65535                   |
| **布尔**          |      |      |                           |
| boolean（布尔型） | 32位 | 1B   | true，false（就这两个值） |

**基本数据类型要记住**：byte，short,int,long,float,double,char,boolean 这几个类型和他们的字节占用空间就够用啦！

**默认类型**：整数型的默认类型是int，浮点型的默认类型是double

使用时要加后缀区分

*int 和long*:				*float和double：*

int a = 10;				float  f1 = 10f;

long b = 10L;								



### 二，变量

​		*旁白：*

​		上面了解了数据类型，那么接下来就来操作数据类型，首先用int(整形) 演示：



**变量：在程序运行过程中，其值可以发生改变的量，从本质上来说，变量是内存中的一小块区域。**

**变量的定义：**

组成：数据类型  变量名  = 变量值；

​			int  a  = 10；

数据类型（int）会在内存中的找一小块空间，空间大小是int的大小，a = 10；a的初始值是10存储到了int空间里面



**变量的使用：**

取值：(下面演示两种取值的方法)

​		int  a  = 10；

​		1.System.out.println(a);//打印值

​		2.int  b  = a  //a 赋值给b  ，a = 10；

修改值：

​			int a = 10;

​			a = 20；//这里a的值就被改变了

变量名不能重复定义：

​	int a = 10;

​	float a = 20.00f;

​	long a = 100L;

​	System.out.println(a);//打印值就会报错，因为计算机不知道你要使用那个值



机器语言 - 0101010

汇编   符号语言   sun a + b;

c语言 print（"nihao"）；

int a = 10;



java: 标识符 

int number = 100；

public static void add（）{

​	是打发斯蒂芬微服务

}

方法名，变量名    userName

类 QianTao

数据类型转换有两种方式：自动类型和强制类型



**算数运算符号**

java语言的算数运算符号： +  -  *  /  % 

运算： 

```java
 int a = 10 + 10; // 20
        int b = 10 - 10; // 0
        int c = 10 * 10; //100
        int d = 10 / 10; //1
        int e = 9 % 10; //0


        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
        System.out.println(e);
```





```java
char c1 = 257;
char c2 = 'a';
```



**字符串拼接操作：**

```java
public static void main(String[] args) {
        //字符串的拼接 +
        //""号是字符串  '' 号是字符
        System.out.println("易"+"远"+"鹏");
        System.out.println("易远鹏"+1555348080);
        
        //数值和字符+操作会拼接
        //数值和数值+操作就是运算
        System.out.println(10+10+"元"); //20元
        System.out.println("欠费"+10+10+"元");
    }
```



**赋值运算符号：**

= 和+= ，*=，/=, -=

```java

       //运算赋值
        int b = 10;
        a += b;
        System.out.println(a);

        //原型：
        int c = 10;
        int m = 20;
        c = c + m;
        System.out.println(c);

```



**关系运算符号：** 

==   a == b ,判断a 和b 是否相同， 相同为ture ，不相同为false

!=    a != b  ,判断a 和b 是否不相等， 如果不相等返回true ，否则返回false

```java
>  
>= 
<  
<= 
```



#### **三元运算符：**（三目运算符）



**结构：**

```
关系表达式 ? 表达式1 : 表达式2;
a>b ? true : false;
```



练习题：定义三个int 类型的数据，a = 10 ; b = 20; c = 8,用三目判断他们的最大值（最小值）

```java
int a = 10;
        int b = 20;
        int c = 8;
        int max =0;

       // max = a < b ? a : b;
        //max = max < c ? max : c ;

       // System.out.println(max);


        //三目运算符嵌套
        max = a > b ? (a > c ? a : c) : (b > c ? b : c);
        System.out.println(max);
```





#### 1.数据输入

键盘输入

需要用到Scanner这个类

步骤1：导包

 import  java.util.Scanner ;

步骤2：创建对象

Scanner sc = new Scanner(System.in);

步骤3：调用对象的方法

int num = sc.nextInt();



#### 2.分支结构

java有三种结构：顺序结构，分支结构，循环结构

```java
//分支结构

        int a = 90;
        int b = 10;

        if (a > b){
            System.out.println("a不大于b");
        }else{
            System.out.println("a大于b");
        }
        //
```

**switch语句**

结构：

```
switch(表达式){
	case 值1:
		语句体1；
		break；
	case 值2:
		语句体2；
		break；
}
用法：在确定值的范围的时候就可以用
```

```java
int a = 5;

        switch(a){
            case 1:
                System.out.println(1);
                break;//跳出switch语句，跳出循环
            case 2:
                System.out.println(2);
                break;
            case 3:
                System.out.println(3);
                break;
            default:
                System.out.println("输入错误");
                break;
```



```
break;的作用//跳出switch语句和跳出循环
```







#### 3.循环语句

for循环：结构

```java
for(初始化语句;条件语句;条件控制语句){
	循环体语句
}
实例：
for(int i = 0; i < 10; i++){
	System.out.println("循环10次");
}
```



do..while循环：结构

```
do{
	语句块；
}while(条件表达式);
实例：
int a = 0;
do{
	System.out.println("我要循环了");
	a++;
}while(a < 5);
```



while循环：结构

```
while(条件语句){
	语句块
}
实例：
int a = 0;
while(a < 10){
	System.out.println("我要循环10次");
	a++;
}
```



#### 4.跳转控制语句：

**跳转控制语句的使用是基于条件控制语句（if switch）的**（有两个）

**continue**  跳过某次循环体的执行，继续下一次的执行

**break** 终止循环体的执行，也就是说结束当前整个循环





**总结**：各种循环语句的应用场景。for循环知道循环的次数，while和do while循环不知道循环的次数时使用



#### 5.随机数类Random

步骤1：导包

 import  java.util.Random ;

步骤2：创建对象

Random ra = new Random();

步骤3：调用对象的方法

int number = ra.nextInt(10); 

10 获取数据得范围是 0 - 10

```java
		Random ra = new Random();

        for (int i = 0; i < 100; i++) {
            int number = ra.nextInt(100)+1; //0 - 10 但是不包含10
            System.out.println(number);
        }
```





