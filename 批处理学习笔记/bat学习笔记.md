## 批处理笔记



### 一、一个基础的批处理程序

@echo off  //打开关闭显示文件路径

Echo "hello world"  //打印

pause //等待手动关闭 不加pause就执行完自动关闭

```bat
@echo off 
Echo "hello world"  
pause 
```



### 二、批处理运算操作

#### 1、算数运算

**加减乘除**

命令模式： set /a 1+3

**文本模式**

set /a  计算

echo 输出

```bat
@echo off

set /a num = 1 +2
set /a a = 1*3
echo %num%
echo %a% 

pause
```

优先级（）

小括号优先级比 +-*/要高



#### **2、重定向运算**

```c
文件流的方向从左到右
>  把内容写入文本如果没有就创建一个，会覆盖原有的内容
>> 把内容写入文本如果没有就创建一个，追加状态在原有的内容上
文本文件内容查看 type     
< 和什么原理一样，右边的内容覆盖到左边的文件
<< 右边的内容追加到左边的文件

关系运算 < 小于 >大于 关系运算
```



#### **3、多命令运算** 

&& 具有短路与，第一个命令错误那么就不会执行第二个命令不会执行

|| 短路 第一个命令执行成功 ，那么就不会执行第二个命令

**管道符号**   

|     A |B     a 命令的输出内容将会作为b命令的输入来执行

```c
命令dir查看文件目录内容
文件路径\a> dir | find ".txt" //查找.txt的文件  
文件路径\a> find "查找内容" 指定文件 
find可以查询文件的字符窜
find /? 可以看到命令的介绍和参数
find /c 显示包含字符窜的行数
find /v 显示所有未包含指定字符窜的行
find /n  显示行号
```



```
命令：netstat -an 查看网络端口
netstat -an | find "筛选的类型"
```



### 三、批处理基本指令

#### 1、命令格式

命令 子命令 参数 操作 选项

命令帮助信息查看 /? /help获取详细的帮助信息

```
命令有子命令有参数 操作和选项
net /?  查看命令net的语法
net user /? 查看net子命令user的语法
```

#### 2、批处理文件 参数传递

**.bat文件接受参数使用 %num**

```
net user pass pass /add   pass是我们的参数
动态形式
net user %1 %2 /add  %1和%2是我们的参数变量

```

**注释符号**

```
rem 注释符号
```

#### **3、炫酷的命令提示符**

```
颜色命令
color /? 查看color使用信息
color设置前景色和背景色
标题命令
title /? 可查看使用信息
title 设置命令提示符窗口的标题
```

#### 4、时间相关的命令

```
date 获取日期
time 获取时间分钟
date /T 显示
time /T 显示
指令 /? 查看基本信息
```

#### 5、启动命令

```
start /?  启动一个单独的窗口以运行指定的程序或命令
start /B 不启动隐藏窗口
```

####  6、调用其他bat文件

```c
call  可以调用对应的bat文件中的内容，但是
call 文件名  可以调用其他.bat文件，但是不能传递参数
```

#### 7、任务列表查看命令

```c
tasklist  该工具显示在本地或远程机械上当前运行的进程列表
tasklist \S 192.168.0.0 \u用户名 \P密码  \s指定连接到的远程系统
```

#### 8、任务关闭命令

```
taskkill  使用该工具按照进程 ID(PID)或者映像名称终止任务

```

#### 9、文件夹结构查看命令

```
tree 以表的形式展示当前文件夹或者指定文件夹的内容
```

#### 10、关机命令

```
  shutdown /i 关闭局域网计算机打开GUI可视化界面执行远程主机的关机操作
  shutdown -p 关闭本地计算器
```

#### 11、计划任务命令

```c
at win10不支持啦
每天执行    
at 22:00/every:M,T,W,Th,F,S,Su C:\abc.exe
    
改成了schtasks    
```

#### 12、批处理环境变量

```
set 可以查看和使用环境系统变量，方便我们使用路径
```





### 四、文件夹或文件相关的命令

#### 1、目录浏览

```
dir 展现现在目录下的文件
dir \a 隐藏目录，一般都是配置文件
```

![](F:\笔记\批处理学习笔记\QQ截图20220925140545.png)

#### 2、目录新建与删除

```
mkdir  创建目录
rmdir  删除目录
\Q\S 删除根本目录不需要确认
```

#### 3、目录切换

```
cd 打开目录
cd.. 返回上一级

rd 文件名 删除目录
```

#### 4、目录重命名

```
ren rename缩写
```

#### 5、目录复制

```
copy 文件1 文件2   1 ---》2
```

#### 6、文件删除

```
del 文件删除命令用来删除一个或多个文件
```

#### 7、文件剪切命令

```c
move 移动文件并重命名文件和目录
move D:\a\2.bat D:\ 将文件1 剪切到文件目录2
move 1.bat test.bat 将文件1 剪切并重命名为test
```









### 五、网络相关命令

#### 1、用户操作命令

```
net user 查看用户
net user 用户名 密码 /add  创建用户
net user 用户名 /delete   删除用户
```

#### 2、用户组操作命令

```
net localgroup  查看系统中的用户组
```

#### 3.网络联通检测命令

```
ping 
```

#### 4、网络连接命令

```
telnet 用于进行网络主机的管理，没有加密
telnet 192.169.0.0 连接任意的端口，发送信息

```

#### 5、路由信息的查看

```
tracert 这么命令可以探测本地主机和远程主机的ip地址
通常跳很多地址以后就到了网络主机的位置
```

#### 6、网络适配器的命令

```
ipconfig 可以获取网络适配器当中的信息
```

#### 7、ARP信息命令

```
arp 显示和修改地址解析协议(ARP)使用的“IP 到物理”地址转换表。
```



### 六、条件判断结构

#### 1、if—else

```bat
@echo off
rem 演示if-else结构  判断字符窜是否规定的字符窜

set v=hello

if %v%==hello  (echo ok)  else (echo no)

pause>nul
```

#### 2、文件存在判断exist

```bat
@echo off
rem 程序用来判断1.bat是否存在
if exist D:\a\1.bat  (echo ok) else (echo no)


pause>nul
```

#### 3、文件判断除

```bat
@echo off
if exist D:\a\abc.txt (
	echo 找到文件删除中！
	del D:\a\abc.txt
) else (
	echo 文件不存在！
)
pause>nul
```





### 七、循环结构

#### 1、遍历目录

```bat
for /d %%变量名 in (/*) do 具体操作
for 的/d开关用于遍历文件夹  	名称(路径 /*号代表当前路径) do 遍历完成后的操作
```

```bat
@echo off
rem for test
rem 遍历当前路径下的文件夹
for /d %%a in (*) do if %%a==1 rmdir %%a

rem 显示删掉的文件名
for /d %%a in (*) do echo %%a

pause>nul
```

#### 2、遍历文件夹目录里面的文件（和上面差不多）

```bat
for /r "目录路径" %%v in (匹配规则 例如*.py) do 执行操作 %%v
/r开关 指定具体的文件夹路径
文件可以保存到%%v变量当中，通过in () 去匹配文件类型
```

```bat
@echo off
for /r "D:\a\erm" %%v in (*.bat) do echo %%v

echo 删除所有*.bat文件

rem 删除所有的.bat文件
for /r "D:\a\erm" %%v in (*.bat) do del %%v

pause>nul
```

#### 3、遍历数字

```bat
for /L %%v in (start,step,end) do 具体操作
/L开关数字遍历 存放在%%v变量
in (开始数值,步长,结尾) 变量对应的范围
```

```bat
@echo off

rem %1是命令终端变量 
for /L %%v in (1,1,20) do ping %1.%%v

pause>nul
```

4、遍历文件内容

```bat
for /F %%v in (文件名) do 具体操作
/F 针对文件名进行内容遍历 
```

```bat
@echo off

for /f %%v in (ccc.txt) do echo %%v

pause>nul
```



### 八、Virus脚本分析 

#### 1、目录重复新建代码分析

利用goto语句重复进行新建（md）

```c
@echo off
rem 新建文件夹

cd C:\Users\itQt\Desktop

rem 创建文件
rem 打开文件

:loop
md Virus
cd Virus
goto loop

pause
exit
```



### 九、编程实例

#### 1、计算机信息展示

思路：

1.使用bat文件保存计算机具体内容到指定文件

2.本地开启http服务，将指定文件放在根目录下，通过浏览器访问txt

```bat
@echo off
rem 重定向文本，echo.是空格的意思
echo. > log.txt

echo Log File >> log.txt
echo.>> log.txt

rem 获取计算机用户名%username%
echo User : %username% >>log.txt

rem 时间日期
Date /t >> log.txt
Time /t >>log.txt
echo. >> log.txt
echo Process Ran by %username% >> log.txt
echo. >> log.txt

rem 显示系统进程
tasklist >> log.txt

echo Network Activities >> log.txt

rem 显示每个协议的统计信息
netstat -s >> log.txt
exit
```



#### 2、交互操作

使用跳转语局 goto跳转到代码块

```bat
@echo off

echo 1.a
echo 2.b
echo 3.c
echo 4.d

rem  set /p opt从标准输入中接受数据到opt

:first
echo 请选择：
set /p opt=
if %opt%==1 goto one
if %opt%==2 goto two
if %opt%==3 goto three
if %opt%==4 goto four
echo 请输入可用的选项
goto first

:one
echo 你选择了1
pause>nul
exit

:tow
echo 你选择了2
pause>nul
exit

:three
echo 你选择了3
pause>nul
exit

:four
echo 你选择了4
pause>nul
exit

rem pause>nul  把等待信息设为空，不可见
```



#### 3、计划执行

at 命令win10已经弃用

#### 4、BAT转EXE程序

**Bat to Exe Concerter工具**
