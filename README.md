# Java for Android
android-Required Interview Outline 欢迎Star，follow
# 继承，封装，多态

## 什么是继承

继承是：子类得到父类所有的成员变量和方法，只支持单继承（即一个子类只能继承一个父类，1个父类可给多个子类继承，但接口可多继承），作用：提高代码的复用性，使得变化的系统有延续性。

## 什么是封装

封装是：封装了实现的细节，隐藏了对象的状态信息在内部，对外只提供接口和方法，进行交互，提高安全性，提高代码的复用性。

## 什么是多态

多态是：同一个类型的不同对象，对于同一个行为，具有多个不同表现形式，消除同一类型之间的耦合关系，使得对象具备多种表现形式。

# 基本类型
整数类型，浮点类型，字符类型，布尔类型，byte 1,short 2,int 4,long 8   floa 4t,double 8   char 2,boolean /

封装类：Byte , Short , Integer , Long , Float , Double , Char , Boolean

>Java的数据类型主要分为：基本数据类型，枚举类型和引用数据类型

## 面向过程(PO)：

一种较早的编程思想，顾名思义该思想是站在过程的角度思考问题，强调的就是功能行为,功能的执行过程,即先干啥,后干啥。而每一个功能我们都使用函数(类似于方法)把这些步骤一步一步实现，使用的时候依次调用函数就可以了。

### 说人话:
提倡和注重的:每一个功能都使用函数来完成,在使用某一个功能的时候,就挨着挨着调用函数即可.
案例：设计购物、做饭、吃饭，洗碗、以及写代码的程序。

>面向过程最大的问题在于**随着系统的膨胀**，面向过程将无法应付，最终导致系统的崩溃。为了解决这一种软件危机，我们提出面向对象思想。

## 面向对象(OO)：
一种基于面向过程的新的编程思想，顾名思义该思想是站在对象的角度思考问题，我们把多个功能合理的放到不同对象里，强调的是具备某些功能的对象。

具备某种功能的实体，称为对象.

## 深入浅出的排序算法-冒泡排序

> 什么是冒泡排序呢？

为什么这个排序要叫冒泡呢？为什么不叫其他名词呢？其实这个取名是根据排序算法的基本思路命名的，见名知意，冒泡排序，就是想泡泡在水里一样，在水里大的泡泡先浮出水面，就是大的先排出来，最小的最慢排出。

冒泡排序，是对排序的各个元素从头到尾依次进行相邻的大小比较，比如你是队长，在你的面前有一排人，你要将其进行排序，依次按照从小到大排序。

怎么理解最大的值被排除，你是队长，你对面前的一群人看不惯，进行排序，从左到右开始，第一个和第二个进行比较，大的那个就被挑出来，与第三个进行比较，接下来就是依次按照这个方法比较，就能把那个最大的值，最高的给挑出来不是，这就是第一轮的比较。

接下来，最大的就不用跟他比较了，上面所述，在排序时，你面前的人，是不能乱动的，一旦比较哪个大，两者就换位，如果第一比第二个小，就是第二个大时，两者不用换位，第二个就与第三个进行比较。

依照这个方法，两两比较，大的都被排到了最后，那么一旦排完，是不是都依照从小到大，（从低到高）的顺序在你面前排好了。
```
//第一轮
for(int index=0;index < arr.length-1; index++）{
//相邻两个比较
 if(arr[index] > arr[index+1]){
   int temp = arr[index];
   arr[index] = arr[index+1];
   arr[index+1] = temp;
 }
}

print(arr);

for(int index=0;index < arr.length-2;index++){
//这里arr.length-2,为什么比上一次多减了1呢？
//因为第一轮，把最大的排出来了，就不用比较了，少了一个人
 if(arr[index] > arr[index+1]){
   int temp = arr[index];
   arr[index] = arr[index+1];
   arr[index+1] = temp;
 }
}

print(arr);

for(int index=0;index < arr.length-3;index++){
 if(arr[index]>arr[index+1]){
   int temp = arr[index];
   arr[index] = arr[index+1];
   arr[index+1] = temp;
 }
}

print(arr);
```

### 优化

```
for(int num=1;num<arr.length;num++){

 for(int index=0;index<arr.length-num;index++){

   if(arr[index]>arr[index+1]){
     int temp = arr[index];
     arr[index] = arr[index+1];
     arr[index+1] = temp;
   }
 }
}
```

## 重点Android

首先你得学习通信技术，大部分都要和后台接口交互，通信技术有okhttp ，解析后台数据有fastjson，流行的通信技术，其次就是界面UI，Android灵活就在界面，界面的功能有很多，之前简书或则掘金上面的第三方界面，就是人家自己写好的自定义View，技术成熟时，你也可以开发自定义View。

### 交互数据的一个通信技术，okhttp

这个交互会用到你跟数据库联系，或则从网上下载数据

比平常用http通信简单很多

比如后台数据库有用户数据和信息，你要把数据获取下来放在你的界面上，就必须通过http请求下载并解析数据

第三方库，你只要下载到你源代码lib中引用一下，就可以用这些特效控件了

http://www.jianshu.com/p/658b56bec80f 

EventBus(事件处理)，xUtils(网络，图片，ORM)

下载百度地图  baidumapapi.jar和libBMapApiEngine.so放libs/armeabi
http://dev.baidu.com/wiki/static/imap/files/BaiduMapApi Lib Android 1.0.zip
申请API Key
地址: http://dev.baidu.com/wiki/static/impap/key

未完待续！！！
