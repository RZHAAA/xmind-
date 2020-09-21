# JVM探究

## java常见面试题：

请谈谈你对JVM的理解？java8虚拟和和之前的变化更新

什么是OOM

![1599999408584](C:\Users\RZH\AppData\Local\Temp\1599999408584.png)

![1599999486380](C:\Users\RZH\AppData\Local\Temp\1599999486380.png)

## JVM的位置

![1599999724269](C:\Users\RZH\AppData\Local\Temp\1599999724269.png)



##  JVM的体系结构

![1599999792462](C:\Users\RZH\AppData\Local\Temp\1599999792462.png)



![1599999839300](C:\Users\RZH\AppData\Local\Temp\1599999839300.png)

 

![1599999882527](C:\Users\RZH\AppData\Local\Temp\1599999882527.png)

JNI就是指的本地方法接口

jvm体系结构

![1600049205510](C:\Users\RZH\AppData\Local\Temp\1600049205510.png)

![1600000190618](C:\Users\RZH\AppData\Local\Temp\1600000190618.png)



## 类加载器：

加载class文件

虚拟机自带的加载器

启动类（根）加载器

扩展类加载器

应用程序加载器

![1600000608329](C:\Users\RZH\AppData\Local\Temp\1600000608329.png)



![1600000921776](C:\Users\RZH\AppData\Local\Temp\1600000921776.png)

双亲委派机制

所以说如果要重写一些类的话，必须把jvm改了，

![1600001598840](C:\Users\RZH\AppData\Local\Temp\1600001598840.png)



## JAVA沙箱机制

![1600002818535](C:\Users\RZH\AppData\Local\Temp\1600002818535.png)

![1600002837822](C:\Users\RZH\AppData\Local\Temp\1600002837822.png)

 ![1600002859784](C:\Users\RZH\AppData\Local\Temp\1600002859784.png)

 ![1600002887514](C:\Users\RZH\AppData\Local\Temp\1600002887514.png)

![1600002952416](C:\Users\RZH\AppData\Local\Temp\1600002952416.png)

 ![1600002974111](C:\Users\RZH\AppData\Local\Temp\1600002974111.png)

  Robot类，可以写外挂的。



## native关键字

![1600003665089](C:\Users\RZH\AppData\Local\Temp\1600003665089.png)

这个比较重要，容易唬住人

 ![1600003695699](C:\Users\RZH\AppData\Local\Temp\1600003695699.png)

![1600003756229](C:\Users\RZH\AppData\Local\Temp\1600003756229.png)

​    存储static，final，Class，常量池



## 栈：数据结构

![1600004971310](C:\Users\RZH\AppData\Local\Temp\1600004971310.png)





​	![1600004951689](C:\Users\RZH\AppData\Local\Temp\1600004951689.png)

![1600005181278](C:\Users\RZH\AppData\Local\Temp\1600005181278.png)

  

## 三种JVM

![1600005437720](C:\Users\RZH\AppData\Local\Temp\1600005437720.png)



## 堆

![1600005814326](C:\Users\RZH\AppData\Local\Temp\1600005814326.png)

 ![1600005862410](C:\Users\RZH\AppData\Local\Temp\1600005862410.png)



![1600006136481](C:\Users\RZH\AppData\Local\Temp\1600006136481.png)

 ![1600006162854](C:\Users\RZH\AppData\Local\Temp\1600006162854.png)

 

### 新生区和老年区



![1600009606556](C:\Users\RZH\AppData\Local\Temp\1600009606556.png)



经过研究，99%的对象都是临时对象



### 永久区 

![1600010185242](C:\Users\RZH\AppData\Local\Temp\1600010185242.png)

jdk1.8之后

![1600010269897](C:\Users\RZH\AppData\Local\Temp\1600010269897.png) 

元空间逻辑上存在，物理上不存在

![1600011005579](C:\Users\RZH\AppData\Local\Temp\1600011005579.png)

 s+=s+s.....问题



![1600056297043](C:\Users\RZH\AppData\Local\Temp\1600056297043.png)



先看大对象，再看线程

![1600056719977](C:\Users\RZH\AppData\Local\Temp\1600056719977.png)



![1600056790989](C:\Users\RZH\AppData\Local\Temp\1600056790989.png)

### GC垃圾回收

![1600063584332](C:\Users\RZH\AppData\Local\Temp\1600063584332.png)



JVM在进行GC时

新生代、幸存区、老年区

![1600064093705](C:\Users\RZH\AppData\Local\Temp\1600064093705.png)



![1600064624859](C:\Users\RZH\AppData\Local\Temp\1600064624859.png)

#### 引用计数法

![1600064734827](C:\Users\RZH\AppData\Local\Temp\1600064734827.png)

占用空间，并不高效，现在没有用这个算法了



#### 复制算法

![1600065414608](C:\Users\RZH\AppData\Local\Temp\1600065414608.png)



![1600065618484](C:\Users\RZH\AppData\Local\Temp\1600065618484.png)



好处：没有内存的碎片

坏处：浪费了内存空间：多了一半空间永远是空的to，假设对象100%存活（极端情况），则来回复制比较消耗系统资源

复制算法最佳使用场景：存活度比较低的区域，新生区。



#### 标记清除算法

![1600065896197](C:\Users\RZH\AppData\Local\Temp\1600065896197.png)



优点：不需要额外的空间！

缺点：两次扫描，严重浪费时间，会产生内存碎片。

#### 标记压缩：

![1600066061504](C:\Users\RZH\AppData\Local\Temp\1600066061504.png)



先多清除几次，再进行压缩，可以再进行优化



#### 总结

![1600066603871](C:\Users\RZH\AppData\Local\Temp\1600066603871.png)



JMM



![1600067456809](C:\Users\RZH\AppData\Local\Temp\1600067456809.png)

![1600067475933](C:\Users\RZH\AppData\Local\Temp\1600067475933.png)



![1600067746184](C:\Users\RZH\AppData\Local\Temp\1600067746184.png)













