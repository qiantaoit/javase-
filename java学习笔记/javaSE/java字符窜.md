

# java字符窜笔记

### API&字符窜

**API（**Application Programma Interface）：应用程序编程接口

**简单理解**：API就是别人已经写好的东西，我们不需要自己编写，直接使用即可。

**Scanner 键盘录入**

**Random s随机数**



**API和API帮助文档**

**API**： 目前是JDK中提化的各种功能的java类

这些类将底层的实现封装起来，我们不需要关心这些类是如和实现的，还需要学习类的使用即可。

**API帮助文档**：帮助开发人员更好的使用API和查询API的一个工具。







### 开发常用字符窜

**认真学！编程不会字符窜开发就要凉一半**



### 1.String

String概述

java.lang.String 类代表字符串，java程序中所有字符串文字（例如：“abc"） 都为此类的对象。

**注意点**：字符串的内容是不会发生改变的，他的对象在创建后不能被更改。

**总结：**

1. String是java定义好的一个类。定义在java.lang包中，所有使用的时候不需要导包。
2.  java程序中的所有的字符串文字，都被实现为此类的对象。
3.  字符串不可变， 它们的值在创建后不能被更改

一,**创建String对象的两种方法：**

1. **直接赋值  String name = "字符串"；**

2. **new 使用构造方法赋值（如下表：）**

	| 构造方法                         | 说明                             |
	| -------------------------------- | -------------------------------- |
	| public String()                  | 创建空白字符串，不包含如何内容   |
	| public String（String original） | 根据传入的字符串，创建字符串对象 |
	| public String(char[] chs)        | 根据字符数组，创建字符串对象     |
	| public String(byte[] chs)        | 根据字节数组，创建字符串对象     |

	掌握最后两个构造方法

​		1.字符数组操作

​        2.字节数组操作

```java
//传递一个字符数组，根据字符数组的内容再创建一个新的字符串对象
char[] chs = {a,b,c,d};
String s1 = new String(chs);
sout(s1); //abcd
```

```java
//传递一个字节数组，根据字符数组的内容再创建一个新的字符串对象
byte[] bytes = {97,98,99,100};
String s1 = new String(bytes);
sout(s1); //abcd
```





**二、不同字符串赋值方法的内存有什么不同**



1、**直接赋值**

**StringTable（串池）**：是一块java内存的空间，用于存放字符串的

jdk7以前串池是在方法区里面的，

String s1 = "abc" 只有这种方法才会在串池开辟空间

![](img\串池的内存原理.png)

**串池里面相同的字符串是共用**,**当使用双引号直接赋值时，系统会检查该字符串在串池中是否存在。不存在：创建新的。存在：复用**



**2、new 赋值（这里使用字符数组为例）**

![](img\获取字符串对象的内存图.png)

**两种方法不同点**：直接赋值是开辟一个串池里面内容共有，new赋值是给每个对象开辟一个空间放入字符串











**三、java的常用方法（比较字符串）**



***==号比较原理：***

**基本数据类型**：比较的是数据值

**引用数据类型**：比较的是地址值

```java
String s1 = "abc";
String s2 = "abc";
System.out.println(s1 == s2); //true
//这里的s1和s2是直接赋值，他的字符串在串池里面，因为两个是相同的字符串是共用的所以地址是一个
```

```java
String s1 = new String("abc"); //对象赋值
String s2 = "abc";//直接赋值
//s1 是通过对象赋值的开辟了一块堆空间来存储字符串
//s2 是通过直接赋值的方式，会在串池开辟框架放字符串
//由此可见两种字符串的地址不一样，==做比较的话用地址来比
```



*如果只要比较内容怎么办呢？*

这里就可以使用字符串比较方法（不用导包）

| 字符串比较方法                           |                                    |
| ---------------------------------------- | ---------------------------------- |
| boolean equals（要比较的字符串）         | 完全一样结果才是true，否则false    |
| boolean equalslgnoreCase(要比较的字符串) | 忽略大小写的比较（可以用于验证码） |

**细节问题：**

```java
import java.util.Scanner;

public class String01 {
    public static void main(String[] args) {
        //1.假设录入一个abc
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个字符串");
        String str1= sc.next(); //abc
        //2.代码中再次定义一个字符串abc
        String str2 = "abc";
        //3.用 == 比较他们的地址能一样吗
        System.out.println(str1 == str2); //false 不一样
    }
}

```

**代码总结：键盘录入最终返回的内容是new出来的。以后要比较字符串就使用字符串比较方法**



**用户登录判断：**

```java
 import java.util.Scanner;

public class String02 {
    public static void main(String[] args) {
        //已知用户名和密码，请用程序实现模拟用户登录
        //总给三次机会，登录之后，给出相应的提示

        String userName = "abc";//用户名
        String passWord = "123";//密码

        for (int i =1;i <= 3;i++){
        //需要用户输入密码和用户名
             Scanner sc = new Scanner(System.in);
             System.out.println("请输入用户名：");
            String newName = sc.next();
            System.out.println("请输入密码：");
            String newPass = sc.next();

            //判断输入密码正确，并判断失败3次之后禁止再输入
            if (userName.equals(newName) && passWord.equals(newPass)){
                 System.out.println("用户登陆成功！");

            }else{
                System.out.println("用户登录失败");
            //count++;
            }
            if (i == 3){
                System.out.println("密码错误3次不能在输入了！");
            }
    }

    }
}

```



**遍历字符串：**

需要用到的方法：

| public char charAt（int index） | 根据所有返回字符   |
| ------------------------------- | ------------------ |
| public int length（）           | 返回此字符串的长度 |

数组的长度：数组名.length

字符串的长度：字符串对象.length() 

```java
import java.util.Scanner;

public class String03 {
    public static void main(String[] args) {
        //需求：键盘录入一个字符串，使用程序实现控制台遍历字符串
        //1、键盘录入字符串
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入字符串");
        String str = sc.next();

        //遍历
        for (int i = 0; i < str.length(); i++) {
            char c = str.charAt(i); //str.charAt(i)这个方法通过索引返回改索引处的字符
            System.out.println(c);
        }
    }
}

```



**统计字符次数：**

```java
import java.util.Scanner;

public class String04 {
    public static void main(String[] args) {
        //键盘录入一个字符串，统计该字符串中大小写字母字符，小写字母字符，数组字符出现的次数

        //1键盘录入一个字符串
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个字符串");
        String str = sc.next();

        //2.统计计数器
        int bigCount = 0;
        int smallCount = 0;
        int numberCount = 0;
        for (int i = 0; i < str.length(); i++) {
            // i 依次表示字符串的每个索引
            char c = str.charAt(i);

            //得到每个字符的索引了就判断他的几种情况
            if(c >= 'a' && c <= 'z'){ //这段判断包含了所有的英文字母小写
                //char类型的变量在参与计算时候自动类型提示为int 查询ascii码表
                //判断小写
                smallCount++;
            }else if(c >= 'A' && c <= 'Z'){
                //判断大写
                bigCount++;
            }else if (c >= '0' && c <= '9'){
                //数字
                numberCount++;
            }
        }
        System.out.println("小写字母有："+smallCount+"\t大写字母有："+bigCount+"\t数字有："+numberCount);
    }
}

```



**字符串拼接：**

```java
public class String05 {
    public static void main(String[] args) {
        //拼接字符串
        //定义一个方法，把int 数组中的数据按照指定的格式 拼接成一个字符串返回
        //调用该方法，并在控制台输出结果
        //int[] arr= {1,2,3}  显示为  [123]
        int[] arr = {1,2,3,4,5,6,7};
        String s = arrToString(arr);
        System.out.println(s);
    }
    //遍历数组并把数组拼接成字符串
    //需要数组

    public static String arrToString(int[] arr){
        //数据校验数组不能空
        if (arr == null){
            return "";
        }
        if(arr.length == 0){
            return "[]";
        }
        

      
        //当代码执行到这里表示不是null不是空
		  String result = "[";
        for (int i = 0; i < arr.length; i++) {
            // i索引 arr[i] 元素
            if (i == arr.length-1){
                //如果是最后一个元素就直接拼接
                result = result + arr[i];
            }else{
                //最后一个元素之前的所有元素后面拼接一个“，”
                result = result + arr[i]+", ";
            }

        }

        return result+"]";
    }
}

```



**字符串反转：**

```java
public class String06 {
    public static void main(String[] args) {
        //定义一个方法，实现字符串反转。
        //键盘录入一个字符串，调用该方法后，在控制台输出结果
        //例如：键盘录入 abc ，输出结果 cba

        String result = reverser("abcdefghijkmln");
        System.out.println(result);

    }
    //定义方法三问

    //我要干嘛    ---- 实现字符串反转
    //我干这件事需要什么才能完成？ --- 需要字符串
    //调用处是否需要继续使用方法的结果呢  --- 需要结果输出

    public  static String reverser(String str){
        //abc 变为 cba 通过字符串索引倒着遍历
        //遍历字符串的循环
        String reult = "";
        for (int i = str.length()-1; i >= 0; i--) {
            //i 依次表示字符串的索引
            char c = str.charAt(i);
            reult = reult + c; //倒序的字符串和reult拼接成一个型的字符串
        }
        return reult; //返回新的字符串
    }

}

```



**金额转换：**

```java
import java.util.Scanner;


    //案例：输入一个金额，转换成大写的中文金额
public class String07 {
    public static void main(String[] args) {
        //1.键盘录入一个金额
        Scanner sc = new Scanner(System.in);
        int money;
        while (true){
            System.out.println("请录入一个金额");
            money = sc.nextInt();
            if (money >= 0 && money <=9999999){
                //验证金额合法然后退出循环
                break;
            }else{
                System.out.println("金额无效");
            }
        }


        //定义一个变量用来表示签的大小
        String moneyStr = "";
        //2.得到，money的每一位数资 ，再转成中文
        while (true){//123
            //从右往左获取数据,因为右侧是个位
            int ge = money % 10; // (1)123 % 10 = 3; (3)12 % 10 = 2 (5)1 % 10 = 1
            String capitalNumber = getCapitalNumber(ge);
            //把转换之后的大写拼接到moneyStr当中
            moneyStr = capitalNumber + moneyStr;
            //第一次循环： “叁” + “”  = “叁”
            //第二次循环： "贰" + “叁” = ”贰叁“
            //从右往左拼

            //去掉刚刚获取得数据
            money = money / 10;  // (2)123 / 10 = 12  (4)12 / 10 = 1 (6) 1 / 10 = 0
            //如果数字上的每一位全部获取到，那么money记录的就是0 ，此时循环结束
            if (money == 0){ //最后退出循环
                break;
            }
        }



        //3.在前面补零，补齐7位
        int count = 7 - moneyStr.length();//

        for (int i = 0; i < count; i++) {
            moneyStr = "零" + moneyStr;
        }
        System.out.println(moneyStr);


        //4.插入单位
        //定义一个数组表示单位
        String[] arr = {"佰","拾","萬","仟","佰","拾","元"};

        //遍历moneyStr，把arr单位插入
        String result = "";
        for (int i = 0; i < moneyStr.length(); i++) {
            char c = moneyStr.charAt(i);
            //这样等同于插入啦
           //把单位和数字插入到result当中
            result = result + c + arr[i];
        }

        //打印
        System.out.println(result);
    }

    //定义一个方法把数字变成大写中午
    //1 --- 壹

    public static String getCapitalNumber(int number){
        //定义数组让数子和大写的中文去产生一个对应关系
        String[] arr = {"零","壹","贰","叁","肆","伍","陆","柒","捌","玖",};
        //返回结果
        return arr[number];
    }
}

```



**手机号屏蔽：**

![](F:\笔记\java学习笔记\javaSE\img\手机号屏蔽.png)



String substring(int beginIndext ,int endIndex) 截取字符串方法

注意：包头不包尾，包左不包右，只有返回值才是截取的小串

```java
public class String08 {
    public static void main(String[] args) {
        //1.截取一个手机号码
        String phoneNumbre = "15519887123";
        System.out.println(phoneNumbre);
        //2.获取前面3位
        String start = phoneNumbre.substring(0,3);


        //3.截取手机号码后面4位
        String end = phoneNumbre.substring(7); //只有一个值默认截取末尾，

        //4.拼接
        String result = start + "****"+end;

        //5.打印结果
        System.out.println(result);
    }
}

```





**身份证号码内容提取：**

```java
public class String09 {
    public static void main(String[] args) {
        //1.定义一个字符串记录身份证号码
        String id = "520203202309232039";

        //2.获取出生年月日
        String year = id.substring(6,10);
        String month = id.substring(10,12);
        String day = id.substring(12,14);


        System.out.println("人物信息为：");
        System.out.println("出生年月日："+year+"年"+month+"月"+day+"日");


        //字符数字，转数字的方法
        //获取性别 单数男双女
        char gender = id.charAt(16);
        //利用ascii表进行转换
        //'0' ==== 48
        //'9' ==== 57

        //'9' = 57
        //'9' - 48 = 9 他们的差值刚好就等于一个数字9
        int num = gender - 48; //
        if (num % 2 == 0){
            System.out.println("性别：女");
        }else {
            System.out.println("性别：男");
        }
    }
}

```



**敏感词替换：**

使用到的方法

String replace(旧值，新值) 替换

**注意点**：只有返回值才是替换之后的结果

```java
public class String10 {
    public static void main(String[] args) {
        //1.获取到说的话
        String taik = "你玩得真他妈的好，下次别玩了，SB，CNM";

        //2.把里面的敏感词tmd替换
        //定义一个敏感词库
        String[] arr = {"TMD","他妈的","CNM","SB","GB"};

        //循环的到数组中的每一个敏感词
        for (int i = 0; i < arr.length; i++) {
           taik = taik.replace(arr[i],"***");
        }


        //3.打印结果
        System.out.println(taik);
    }
}

```





### 2.StringBuilder类

如果用以前的S = S +"abc" 这种方法拼接字符串，在处理10000个字符串的时候就会很慢

如果使用StringBuilder类速度就很快

```java
StringBuilder sb = new StringBuilder("");
for(int i =0;i < 100000;i++){
	sb.append("abc");
}
sout(sb);
```



**StringBuilder 可以看成一个容器，创建之后里面的内容是可变的**

**作用**：提高字符串的操作效率



1、下面这种方法拼接，每拼接一次就好产生一个串池里新字符串，非常站内存

![](img\字符串拼接01.png)

2.这种方法把字符串都放入一个容器里面就是拼接好的字符串

![](img\字符串拼接类02.png)



##### **StringBuilder构造方法**

| 方法名                           | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| public StringBuilder()           | 创建一个空白可变字符串对象，不包含任何内容 |
| public StringBuilder(String str) | 根据字符串的内容，来创建可变字符串对象     |

**StringBuilder常用方法**

| 方法名                                | 说明                     |
| ------------------------------------- | ------------------------ |
| public StringBuilder append(任意类型) | 添加数据，并返回对象本身 |
| public StringBuilder reverse()        | 反转容器中的内容         |

|                          |                                                         |
| ------------------------ | ------------------------------------------------------- |
| public int length()      | 返回长度（字符出现的个数）                              |
| public String toString() | 通过toString()就可以实现把StringBuilder对象转换为String |



### 3.StringJoiner

**StringJoiner概述**

StringJoiner跟StringBuilder一样，也可以看成是一种容器，创建之后里面的内容是可变的。

**作用：**提高字符串的操作效率，而且代码编写特别简洁，但是目前市场上很少有人用

**JDK8开始出现的**



##### StringJoiner的构造方法

| 方法名                                            | 说明                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| public StringJoiner(间隔符号)                     | 创建一个StringJoiner对象，指定拼接时的间隔符号               |
| public StringJoiner(间隔符号，开始符号，结束符号) | 创建一个StringJoiner对象，指定拼接时的间隔符号，开始符号，结束符号 |



**StringJoiner成员方法**

| 方法名                               | 说明                                         |
| ------------------------------------ | -------------------------------------------- |
| public StringJoiner add (添加的内容) | 添加数据，返回对象本身                       |
| public int length()                  | 返回长度（字符串出现的个数）                 |
| public String toString()             | 返回一个字符串（该字符串就是拼接之后的字符） |

简单打印：

```java
package com.qt;

import java.util.StringJoiner;

public class StringJoinerDemo1 {
    public static void main(String[] args) {
        //创建一个对象，并指定间隔符号
        StringJoiner sj = new StringJoiner("---");

        //2.添加元素
        sj.add("add").add("bbb").add("ccc");
        System.out.println(sj); //add---bbb---ccc
    }
}

```



常用方法：

```java
package com.qt;

import java.util.StringJoiner;

public class StringJoinerDemo2 {
    public static void main(String[] args) {
        //1.创建对象
        StringJoiner sj = new StringJoiner(",","<",">");

        sj.add("aaa").add("bbb").add("ccc");

        int len = sj.length(); //返回结果为拼接完成后的长度
        System.out.println(len);

        System.out.println(sj);


        //toString()成员方法，返回拼接完成后的字符串
        String str = sj.toString();
        System.out.println(str); //<aaa,bbb,ccc>

    }
}

```





#### 总结：

1. **String ：**

	表示字符串的类，定义了很多操作字符串的方法

2. **StringBuilder** ：

	一个可变的操作字符串的容器

	可以高效的拼接字符串，还可以将容器里面的内容反转。（这是以后常用功能）

3. **StringJoiner：**

	JDK8出现的一个可变操作字符串的容器，可以高效，方便的拼接字符串

	在拼接时，可以指定间隔符合，开始符号，结束符号。





### 4.字符串原理

**拓展底层原理1：字符串存储的内存原理**

* 直接赋值会复用字符串常量池中的

* new出来的不会复用，而是开辟一个新的空间

	

**拓展底层原理2： ==号比较的到底是什么？**

* 基本数据类型比较数据值

* 引用数据类型比较地址值

	以后不会什么类型我们都使用equals()

	

**拓展底层原理3：字符串拼接的底层原理**

* **第一种情况无变量拼接**

	![](img\无变量字符串拼接.png)

![](img\无变量参与字符串拼接2.png)



* **第二种情况有变量参与**

	*JDK8以前字符串拼接有StringBuilder的参与*

​		![](img\JDK8以前的字符串拼接.png)

​	

JDK8以后字符串的拼接方式

![](img\JDK8以后字符串的拼接方式.png)

先去预估字符串的长度，然后创建一个数组。最后打印字符串

**结论：**不管怎么优化都还是浪费时间，用+拼接，会在底层创建多个对象性能



**拓展底层原理4：StringBuilder提高效率原理图**

String s1 = S2 + "c"; 参与运算的字符串，都是new出来的字符串

String s2 = "a"+ "b"+"c"; //这段代码会触发字符串的优化机制（创建数组拼接为abc）

![](img\字符串原理4.png)

**拓展底层原理5：StringBuilder**

* 默认创建一个长度为16的字节数组
* 添加的内容长度小于16，直接存
* 添加的内容大于16会扩容（原来的容量*2+2）

```java
package com.qt;

public class StringBuilderDemo1 {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        //容量：最大是多少
        //长度，已经装多少
        System.out.println(sb.capacity());//查看容量
        System.out.println(sb.length()); //内容长度

        sb.append("abc").append("cc");
        //
        System.out.println(sb.capacity()); //查看容量
        System.out.println(sb.length());  //内容长度


        sb.append("abcdefghijkmlnopqrxz");
        //因为字符串太长所以对象扩容了
        System.out.println(sb.capacity()); //查看容量
        System.out.println(sb.length()); //内容长度
    }
}

```

![](img\字符串原理小结3.png)

### 5.综合练习

![](img\字符串练习题1.png)



​								![](img\字符串练习题2.png)



### ToCharArray( )的用法，将字符串对象中的字符转换为一个字符数组



```java
String str = "abcde";

char[] ch =  str.ToCharArray( );
//把字符数组转换为字符串
String str2 = new String(arr)；
```

