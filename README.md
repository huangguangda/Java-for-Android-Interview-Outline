# Java for Android
android-Required Interview Outline 欢迎Star，follow

# 平时操作电脑:
   如果在电脑中的某一个文件夹存储了1000部电影,某一天你想看电影,寻找很麻烦.在该文件夹中的文件是不能同名.
   上述存在的问题:
         1):电影太多,太繁杂,不方便管理.
         2):在同一个文件夹中,电影不能同名.
# 解决问题:
    在该文件夹中建立几个子文件夹:爱情,喜剧,动作,惊悚,教学,龙哥....
--------------------------------------------------------------------------------
    在编程世界中,咱们也不应该把所有的Java文件,全部放在同一个文件夹中.
    此时,解决该问题,我们也类似于建立多个文件夹,只不过在Java中,我们把这种文件夹称之为,包(package).
--------------------------------------------------------------------------------
一般的,同一个模块的Java文件,同一种功能的Java文件存在在相同包中,类似于其他语言的命名空间.
--------------------------------------------------------------------------------

# 建立包的语法:
 在Java文件的最开始位置(第一行):
 package 包名.子包.子包.子包;
 package 域名倒写.项目模块名称.组件名称;
          如:com.taobao.shopping.util;
          如:com._520it.crm.util;
             com._520it.pss.util;
# 注意: 
1):包名得符合标识符规范(若域名以数字打头,可以使用下划线隔开.)
2):企业开发,一般使用企业的域名倒写.www.taobao.com--->com.taotao
3):包名都是用小写字母组成.


```
public class UDPClient{
 public static void main(String[] args){
  try{
   DatagramSocket socket = new DatagramSocket(4567);
   InetAddress serverAddress = InetAddress.getByName("1..3.3.");
   String str = "hell";
   byte data[] = str.getBytes();
   DatagramPacket packet = new DatagramPacket(data,data.length,serverAddress,4567);
   socket.send(packet);
   }catch(Exception e){
   e.printStackTrace();
   }
}
```
```
public class SocketActivity extends Activity{
	private Button startButton = null;

	public void onCreate(Bundle savedInstanceState){
	 super.onCreate(savedInstanceState);
	 setContentView(R.layout.main);
	 startButton = (Button)findViewById(R.id.startListener);
	 startButton.setOnClickListener(new StartSocketListener());
	}

	classs StrartSocketListener implementns OnClickListener{
	 public void onClick(View v){
	   new ServerThread().start();
	 }
	}

	class ServerThread extends Thread{
	public void run(){
	 try{
	 
	  DatagramSocket socket = new DatagramSocket(4567);
	  
	  byte data[] = new byte[1024];
	  
	  DatagramPacket packet = new DatagramPacket(data,data.length);
	  
	  socket.receive(packet);
	  
	  System.out.println(packet.getLength());
	  
	  }catch(Exception e){
	   e.printStackTrace();
	   }
	   }
}
```
```
public class TCPClient{
 public static void main(String[] args){
  try{
   Socket socket = new Socket("192.1683.1.1",4567);
   InputStream inputStream = new FileIputStream("C:/text.txt");
   OutputStream outputStream = socket.getOutputStream();
   byte buffer[] = new byte[1024*4];
   int temp = 0;
   while( (temp = inputStream.read(buffer)) != -1 ){
    outputStream.write(buffer,0,temp);
    }
    outputStream.flush();
    }catch(Exception e){
    e.printStackTrace();
    }
   }
}
```
```
public class SocketActivity extends Activity{
	private Button startButton = null;

	public void onCreate(Bundle savedInstanceState){
	 super.onCreate(savedInstanceState);
	 setContentView(R.layout.main);
	 startButton = (Button)findViewById(R.id.startListener);
	 startButton.setOnClickListener(new StartSocketListener());
	}

	classs StrartSocketListener implementns OnClickListener{
	 public void onClick(View v){
	   new ServerThread().start();
	 }
	}

	class ServerThread extends Thread{
	 public void run(){
	 //声明一个ServerSocket对象
	  ServerSocket serverSocket = null;
	  try{
	  //创建一个ServerSocket对象，并让这个Socket在4567端口监听
	   serverSocket = new ServerSocket(4567);
	   Socket socket = serverSocket.accept();

	   InputStream inputStream = socket.getInputStream();
	   byte[] buffer = new byte[1024*4];
	   int temp = 0;
	   while( (temp = inputStream.read(buffer)) != -1 ){
	    System.out.println(new String(buffer, 0, temp));
	   }
	  }catch(IOException e){
	   e.printStackTrace();
	  }
	  finally{
	   try{
	    serverSocket.close();
	   }catch(IOException e){
        e.printStackTrace();
	   }
	  }
	 }
	}
}
```
# 局部变量的初始化和在JVM中的运行机制:
局部变量定义后，必须显示初始化后才能使用，因为系统不会为局部变量执行初始化操作。
这就意味着，定义局部变量后，系统并未为这个变量分配内存空间。

直到程序为这个变量赋值时，系统才会为局部变量分配内存，并将初始值保存到该内存中。

局部变量不属于任何类或实例，因此它总是保存在其所在方法的栈内存中。

   基本数据局部变量：直接把这个变量的值保存到该变量所对应的内存中。
   
   引用数据局部变量：这个变量内存中存的是堆中的一块内存空间的地址值,通过该地址引用到该变量实际引用堆里的的对象。
   
栈内存中的变量无需系统垃圾回收，其往往随方法或代码块的运行结束而结束。

栈中的运算速度远远快于堆内存.

变量的分类和初始值:
变量因定义的位置不同,分为成员变量和局部变量.

成员变量: 直接定义在类的花括号中的变量.又称之为,字段(Field),有人把成员变量称之为属性,这是错的.

           使用static修饰:     类成员变量.
           没有使用static修饰: 实例成员变量.
	   
局部变量: 变量除了成员变量,其他就是局部变量.

           1):直接定义在方法中的变量.
           2):方法的形式参数.
           3):代码块({})中的变量.
	   
成员变量都有初始化值,局部变量没有初始化值.
使用局部变量,必须先赋值.成员变量的默认初始值如右图.
在Java中,只有final修饰符,可以修饰局部变量,其他的都不能修饰局部变量.
-----------------------------------------------------------------------------
# 变量的作用域和生命周期:

   当一个变量被定义的时候,它作用域就已经确定了.
   成员变量:在整个类中有效.
   局部变量:只在当前定义的{}中有效.

类成员和实例成员的访问:
------------------------------------------------
类  成员:使用static修饰的成员变量/方法,属于类,所以可以直接使用类名访问.
实例成员:没有使用static修饰的成员变量/方法,属于对象.必须使用对象来访问.
----------------------------------------------------------------------------------
访问规则:

    1):静态方法只能访问静态的成员变量/方法,不能访问非静态的成员变量/方法(属于对象).
               静态成员优先于对象存在.
	       
    2):非静态方法可以访问非静态成员变量/方法,也可以访问静态的成员变量/方法.
               因为底层使用对象访问的.
	       
    3):对象可以访问静态成员,但是不推荐,因为底层依然使用类名在调用.
    
    4):类可以访问静态成员,类不能访问非静态成员(成员变量/方法).
-----------------------------------------------------------------------------------
一般的,在开发中类成员如何使用:

    一般的,在开发中工具类的工具方法都使用static修饰,如此的好处,直接使用工具类名.方法就可以调用,使用更加简单.
    
   数组的工具类:java.util.Arrays中的工具方法.
   
   一般的,若静态方法需要访问一个成员变量,此时才把成员变量使用static修饰.


类是用来描述多个对象共同的状态和行为的,就拿人的姓名.
---------------------------------------------------------------
现在,我想描述一类事物的状态和行为,比如:人类,有总人数的状态,有毁灭的行为.

可能有人认为,毁灭是一个行为,那么可以在Person类中,定义一个方法(destory),若想毁灭人类,则调用该方法即可.但是新的问题又来了?到底谁来调用destory方法?
   
   春哥.destory();
   凤姐.destory();

都不对的,因为他们只能表示自己,不能表示人类.
----------------------------------------------------------------

我们平时在类中定义的成员变量和方法,都是对象的状态和行为.
那如何表示,一类事物的状态和行为呢?不是某一个个体(对象)的.

 此时,为了解决该问题,咱们得学习一个修饰符:static.
-----------------------------------------------------------------
static可以修饰成员变量(字段),可以修饰方法等,就表明该字段或该方法属于类,而不属于某一个对象.
-----------------------------------------------------------------

类成员(static修饰成员)的特点:

   1):随着类被加载进JVM而同时也最初始化和在内存中分配空间.
   
   2):优先于对象存在.(对象是通过new出来的.)
   
   3):被该类的所有对象所共享.
        该状态/行为是整个人类的,那么每一个人都是拥有该状态/行为的. 
	
   4):直接使用类名调用即可.
      人类毁灭:  Person.destory();
        


我们在创建Student对象,代码如下:
Student s1 = new Student();

其实我们在创建对象的时候,都是调用构造方法,构造函数/构造器/构造子.
--------------------------------------------------------
构造器:主要用于创建对象并返回对象和初始化对象数据.
--------------------------------------------------------

# 构造器的特点:
    类都有一个默认构造器,当不显示的定义构造器的时候,编译器会在编译的时候,提供一个默认构造器.
    1):构造器的名字必须和当前所在类的类名相同.
    
    2):不需要定义返回值类型,更加不能使用void作为返回.构造器的目的在于创建和返回当前类的对象,即使要编写返回类型,也应该是当前类名,如:Student Student(){},既然和当前类名相同,就规定统统省略.
    
    3):构造器中不需要使用return来返回当前构造的对象.
-------------------------------------------------------
# 默认构造器:
     1):无参数,无方法体.
     
     2):构造器的访问修饰符和当前类的修饰符相同(是否有public).
     
     3):一旦在类中显示地提供了构造器,则默认的构造器就不再提供了.
     
     推论: 一个类至少有一个构造器(即使没有自定义,编译器也会创建一个默认的).
-----------------------------------------
```
public class Student{
     默认的构造器
     public Student(){}
}
---------------
class Student{
     默认的构造器
     Student(){}
}
```
-------------------------------------------------------
方法的重载:

在同一个类中,方法同名,但是参数列表不同.
            解决了相同的功能方法,因为参数列表不同,而带来参数名不同的问题.
构造器重载:

          不同类的构造器是不相同的. 对于构造器重载来说,肯定是在同一个类中,并且构造器都是和类名相同.
          所以在同一个类中的多个构造器就必须参数列表不同(参数类型,参数个数,参数顺序).
-------------------------------------------------------
Student(){}
Student(String name){}
Student(String name,int age){}
  上述的构造器就是重载关系.

# 对象的创建和使用:
   在程序中,必须先有类,再有对象(先得有模板,再有根据模板制造出来的个体).
   
   1):创建对象    :类 对象名 = new 类名();
   
   2):对象调用方法:对象名.方法名([实参]);
   
   3):对象操作字段
          赋值:   对象名.变量 = 值;
          取值:   变量 = 对象名.变量;
	  
   4):打印对象:
         默认输出:Servant@659e0bfd,对象的类型@十六进制的hashCode,
          和数组一样,看不到对象中的数据,期待我们讲解Object类.
	  
   5):比较对象:
          每次new,都会在堆内存开辟新的内存空间.
          而"==",在比较引用类型的时候,比较的是引用的内存地址值.
	  
   6):对象的生命周期.
          从使用new在堆中开辟内存开始,到垃圾回收期回收之间.
          垃圾:内存中的某一块空间没有被某一个变量所引用.
          垃圾产生时,不一定运行GC,GC是自行调度,程序员控制不了.
	  
   7):匿名对象.
          没有名字的对象,就是创建对象时,没有赋给一个变量.
          new Servant();创建一个匿名对象
          只在堆中开辟内存空间,不会被栈中的变量所引用.
	  
       特点:匿名对象只能使用一次,就是刚刚创建的这一次.


# 对象:

对象是人们要进行研究任何事物，一切事物都可以认为是对象。
对象具有状态和行为:
对象具有状态，比如姓名,年龄,性别等。

对象还有行为，比如吃饭,睡觉,写代码等。
-----------------------------------------------------------------------------------------------------
类(类型):

具有相同特性（数据元素）和行为（功能）的多个对象的抽象就是类。因此，对象的抽象是类，类的具体化就是对象，也可以说类的实例是对象，类实际上就是一种数据类型。

类具有特性，对象的状态，用成员变量来描述。

类具有功能，对象的行为，用方法来描述。

-----------------------------------------------------------------------------------------------------
什么是类：类是对象的类型/模板。创建一个对象，就是使用一个类作为构建该对象的基础。
-----------------------------------------------------------------------------------------------------
在编程的世界:是先有类,再有对象,对象是根据类创建出来的.


面向对象的优势和特点:
---------------------------------------------------------
面向对象更加符合我们常规的思维方式，稳定性好，可重用性强，易于开发大型软件产品，有良好的可维护性。

当然上述例子仅仅只是说明了面向对象的一个特征——封装。除此之外面向对象还有两大特征，我们在具体讲解到的时候再做分析。

三大特征：

封装(Encapsulation)；
继承(Inheritance)；
多态(Polymorphism)；

封装是指将对象的实现细节隐藏起来，然后通过公共的方法来向外暴露该对象的功能。

继承是面向对象实现软件复用的重要手段，当子类继承父类后，子类是一种特殊的父类，能直接或间接获得父类里的成员。

多态是可以直接把子类对象赋给父类变量，但是运行时依然表现出子类的行为特征，这意味着同一类型的对象在运行时可能表现出不同的行为特征。

注意：
千万不要误解为面向对象一定就优于面向过程的设计.
     面向对象是基于面向过程的,永远不可能取代面向过程.


# 面向过程(PO)：

一种较早的编程思想，顾名思义该思想是站在过程的角度思考问题，强调的就是功能行为,功能的执行过程,即先干啥,后干啥。而每一个功能我们都使用函数(类似于方法)把这些步骤一步一步实现，使用的时候依次调用函数就可以了。

说人话:提倡和注重的:每一个功能都使用函数来完成,在使用某一个功能的时候,就挨着挨着调用函数即可.

案例：设计购物、做饭、吃饭，洗碗、以及写代码的程序。

面向过程最大的问题在于随着系统的膨胀，面向过程将无法应付，最终导致系统的崩溃。为了解决这一种软件危机，我们提出面向对象思想。

面向对象(OO)：一种基于面向过程的新的编程思想，顾名思义该思想是站在对象的角度思考问题，我们把多个功能合理的放到不同对象里，强调的是具备某些功能的对象。

具备某种功能的实体，称为对象.

								
# Java自带数组工具类Arrays		

既然常用的功能,大家都会使用到,所以SUN公司的科学家们把数组的操作方法,已经封装到Arrays类中.
------------------------------------------------------------
Arrays类:在java.util包中.
-------------------------------------------------------------
int binarySearch(type[] arr,type key)	使用二分法查找数组里某元素并返回其索引，若找不到返回负数.

void sort(type[] arr)	使用调优后的快速法对指定数组排序。

String toString(type[] arr)	返回指定数组内容的字符串表示形式。

public static type[] copyOf(type[] original, int newLength)	复制指定的数组，截取或用 0 填充（如有必要），以使副本具有指定的长度。


# 排序的分类：

选择排序（直接选择排序、堆排序）

交换排序(冒泡排序、快速排序)

插入排序（直接插入排序、二分法插入排序、Shell排序）

归并排序等。

# 方法的可变参数:
     传统的做法,在方法调用的时候, 传递一个数组:

     从正确与否的角度,是没问题的.但是,若单价过多,咱们就得先把多个单价数据先封装到数组中,再传递给getTotalPrice方法.
     但是,我觉得不爽!
     
     我期望,直接在方法中传递多个实际参数,而没必要先创建一个数组,再传递.

此时声明数组的参数,应该使用可变参数形式.

以前:
static  double getTotalPrice(double[] nums)

现在:
static  double getTotalPrice(double ... nums)

通过反编译可以发现: 其实:
 static  double getTotalPrice(double ... nums)编译之后,
 
在字节码中,其实就是:
static  double getTotalPrice(double[] nums)
--------------------------------------------------------------

得出结论:可变参数就是,方法的数组参数.
注意: 为了避免歧义,语法规定,可变参数必须作为方法的最后一个参数.

源:
int[] src = {1,3,5,7,9,11};

目标:
int[] dest = new int[10];

需求:把src数组中指定的几个元素拷贝到dest数组中.
----------------------------------------------------------
参数:

src :源,从哪个数组中拷贝数据

dest:目标,把数据拷贝到哪一个数组中

srcPos:从源数组中的哪一个位置开始拷贝.

destPos:在目标数组中开始存放的位置.

length:拷贝几个元素

void arraycope(int[]src,int srcPos,int[] dest,int destPos,int length){...}

调用:
arraycope(src,1,dest,3,4);
----------------------------------------------------------

上述的数组元素拷贝只能运用于int类型数组,我们在开发中会遇到各自数据类型的数组.
 有人就想:有多少数据类型就重载多少次arraycope方法,不就OK了吗?
 
----解决方案:如此常用的一个功能,Java的大神们早就设计好了,并且把该功能方法存放在System类中.

基本使用:
     System.arraycopy(src,1,dest,3,4);
     可以拷贝任意类型是数组元素.


数组,用于存储数据,好比就是容器.

int[] num1= new int[]{1,3,5,7,9};

此时num1数组,存储了1,3,5,7,9这5个数字.

int[] num2 =new int[]{2,4,6,8,0};

能不能把定义一个新的容器,可以存储num1和num2数组呢?
---------------------------------------------------->
一维数组: 就是数组,数组中的每一个元素都是一个值.

二维数组: 数组中的数组,数组中的每一个元素都是一个数组.(可以表示二维空间(行/竖))

三维数组: 数组中的每一个元素都是一个二维数组.

 int[][] =  new int[][]{num1,num2};
--------------------------------------------
 int[][] =  new int[][]{
                           {1,3,5,7,9},
                           {2,4,6,8,0}
 };


# 方法参数的值传递机制(by value):
   方法被调用时，方法里的参数是以值传递的方式传递的。

所谓值传递，就是将实际参数的副本传入方法，而参数本身不受影响。


案例描述:请对以下的代码进行优化:
```
for (int i = 0; i < 1000; i++) {

    for (int j = 0; j < 100; j++){  

        for (int k = 0; k < 10; k++){  

              循环体代码

        }

    }

}
```
从给出的代码可知，不论如何优化，循环体代码执行的次数都是相同的，该部分不存在优化的可能。那么，代码的优化只能从循环变量i、j、k的实例化、初始化、比较、自增次数等方面的耗时上进行分析。

```
for (int i = 0; i < 10; i++) {

    for (int j = 0; j < 100; j++){  

        for (int k = 0; k < 1000; k++){  

              循环体代码

        }

    }
```

# 三大循环语句都一样,仅仅只是语法结构上不一样而已.

把while循环和for循环转换.
提示：

三大循环，是可以互换的，一般情况下，要是指定次数的循环，选用for循环要方便点。

# 三大循环之for循环:
语法:
```
for(初始化语句;boolean表达式;循环之后的操作语句)
{
   循环体
}
```

初始化语句:定义变量,赋初始值;
boolean表达式:判断条件,若条件为true,则进入循环体,若为false,则跳过循环.
循环之后的操作语句: 变量的自增/自减操作.

执行顺序:
      1):初始化语句.
      2):boolean表达式:
           true: GOTO 3
           false:跳过循环,不执行循环体
      3):执行循环体.
      4):循环之后的操作语句, GOTO 2.

# 三大循环之while循环:
```
语法:
while(boolean表达式)
{
     若boolean表达式结果为true,则执行这里.循环体
}
```
注意:先判断boolean表达式.

# 三大循环之do while循环:
语法:
```
do
{
   循环体
}while(boolean表达式);
```
注意: do while,不管boolean表达式对与错,先执行一次循环体.
     即使boolean表达式为false,do while也会执行一次.
     推论: 无论条件如何,dowhile至少会执行一次.

# 顺序结构:
如果代码里没有流程控制，程序是按照书写的格式从上而下一行一行执行的，
一条语句执行完之后继续执行下一条语句，中间没有判断和跳转，直到程序的结束

# 第一种结构:
if(boolean条件)
{
      代码/当boolean条件结果为true的时候,就执行这里的代码.
}
明天不下雨,我们就去公园.

# 注意:
  1):不能写出:if(boolean条件);{}
  2):若if的语句只有一句话,其实可以省略{},即是如此,也必须得写{}.
  3):对于boolean类型的表达式,不要使用 boolean表达式==true的写法.

# if语句的第二种结构:if-else语句.
```
如果......,否则......
if(boolean条件)
{
      当boolean条件结果为true的时候,就执行这里的代码.
}
else 
{
      当boolean条件结果为false的时候,就执行这里的代码.
}
```
------------------------------
if-else结构和三元运算符的区别:

 1):一个是结构,一个运算表达式.
 2):运算表达式的是必须得有一个结果的.
 3):从功能上,从语义上是相同的.
 
------------------------------
不能单独使用else,必须先有if,再有else.

需求:考试成绩大于90分，就打印优，如果大于80分，打印良，如果大于70分，打印中，其他情况打印多多努力。对于这个案例，如何解决.
```
if语句的第三种结构:if-elseif-else语句.
if(boolean条件1)
{
      当条件1为true的时候,执行这里.
}
else if(boolean条件2)
{
      当条件2为true的时候,执行这里
}
else if(boolean条件3)
{
      当条件3为true的时候,执行这里
}
else 
{
      上述所有条件,都不满足,就执行这里.
}
```

# switch的语法分析以及注意:

  1):switch中的表达式的结果/类型,必须是整数类型.
      整数类型:byte,short,char,int.没有long.
      从Java7开始,switch也支持String类型.
      
  2):switch语句,一旦找到入口,就会进入,并执行功能语句,后面的case不再判断,除非语句break,或return或则执行完成,才会停下来-----穿透.
  
  3):default表示,当case中的值都不成立的时候,才执行,一般的放在最后.
-----------------------------------------------------------------------
if和switch都是选择语句/条件语句,那到底什么时候选择使用if,什么时候选择使用switch.
分析各自的优缺点:

1): 对于所有的条件语句,if都可以完成.
2): swtich语句,只能正对于结果为数值的情况做判断.
3): 当if中条件的结果是数值的时候,使用switch更简单.

100：继续  客户端应当继续发送请求。客户端应当继续发送请求的剩余部分，或者如果请求已经完成，忽略这个响应。  

101： 转换协议  在发送完这个响应最后的空行后，服务器将会切换到在Upgrade 消息头中定义的那些协议。只有在切换新的协议更有好处的时候才应该采取类似措施。  
102：继续处理   由WebDAV（RFC 2518）扩展的状态码，代表处理将被继续执行。  

200：请求成功      处理方式：获得响应的内容，进行处理  

201：请求完成，结果是创建了新资源。新创建资源的URI可在响应的实体中得到    处理方式：爬虫中不会遇到  

202：请求被接受，但处理尚未完成    处理方式：阻塞等待  

204：服务器端已经实现了请求，但是没有返回新的信 息。如果客户是用户代理，则无须为此更新自身的文档视图。    处理方式：丢弃 

300：该状态码不被HTTP/1.0的应用程序直接使用， 只是作为3XX类型回应的默认解释。存在多个可用的被请求资源。    处理方式：若程序中能够处理，则进行进一步处理，如果程序中不能处理，则丢弃  

301：请求到的资源都会分配一个永久的URL，这样就可以在将来通过该URL来访问此资源    处理方式：重定向到分配的URL  

302：请求到的资源在一个不同的URL处临时保存     处理方式：重定向到临时的URL  

304：请求的资源未更新     处理方式：丢弃  

400：非法请求     处理方式：丢弃  

401：未授权     处理方式：丢弃  

403：禁止     处理方式：丢弃  

404：没有找到     处理方式：丢弃  

500：服务器内部错误  服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理。一般来说，这个问题都会在服务器端的源代码出现错误时出现。 

501：服务器无法识别  服务器不支持当前请求所需要的某个功能。当服务器无法识别请求的方法，并且无法支持其对任何资源的请求。  

502：错误网关  作为网关或者代理工作的服务器尝试执行请求时，从上游服务器接收到无效的响应。  

503：服务出错   由于临时的服务器维护或者过载，服务器当前无法处理请求。这个状况是临时的，并且将在一段时间以后恢复。

# 操作系统

管理和控制计算机硬件与软件资源的计算机程序，是直接运行在“裸机”上的最基本的系统软件，任何其他软件都必须在操作系统的支持下才能运行。

美国SUN(Stanford University Network)公司，在中国大陆的正式中文名为“太阳计算机系统（中国）有限公司”。
1982年，SUN公司诞生于美国斯坦福大学校园，并于1986年上市，在NASDAQ（纳斯达克：是全美证券商协会自动报价系统）的标识为SUNW，2007年改为JAVA。
2009年4月20日19点40分，美国数据软件巨头甲骨文公司（Oracle）宣布以74亿美元收购SUN公司，从此Java也有“干爹”了，在这个拼爹的时代，Java的发展前景不容置疑。

## Java语言特性
简单、面向对象、安全、跨平台、多线程、健壮、分布式等

## 什么是计算机语言:
生活中的两个人的交流主要是方式无非是采用一种都能够识别的语言，那么也就是说该语言是他们之间传递信息的媒介。

那么什么是计算机语言呢？计算机语言是指用于人与计算机之间通讯的一种特殊语言，是人与计算机之间传递信息的媒介。

那计算机怎么能读懂我们给它发出的的信息呢？此时就需要编写一套由字符、数字所组成并按照某种语法格式的一串串计算机指令，而这些计算机指令就是计算机语言。
软件就是由若干条计算机指令所组成的。

计算机语言分类:

①　机器语言：直接用二进制指令表达，指令是用0和1组成的一串代码，它们有一定的位数，并分成若干段，各段的编码表示不同的含义。

②　汇编语言：使用一些特殊的符号来代替机器语言的二进制码(又称符号语言)，计算机不能直接识别，需要用一种软件将汇编语言翻译成机器语言，汇编语言依赖于硬件体系，开发难度大。

③　高级语言：使用一定格式的自然语言进行编写源代码，通过编译器将源代码翻译成计算机直接识别的机器语言，之后再由计算机执行，不直接操作硬件，把繁琐的翻译操作交给编译器完成。

我们将学习的Java就属于高级语言范畴。

什么是编程:

前面说了计算机语言就是用来实现人和计算机通讯的，那为什么人要和计算机通讯呢，其原因就是为了让计算机帮我们完成一些人为起来比较复杂的工作。
那计算机怎么知道我们要它解决的问题是什么，怎么知道解决问题的具体的步骤是什么呢？此时我们就得通过编程语言去告诉计算机去，做什么，怎么做。这种人和计算机之间交流的过程，我们称之为编程。

举例:计算机例子/分页的例子。


在计算机内，有符号数有3种表示法：原码、反码和补码,所有数据的运算都是采用补码进行的。

正数的原码，反码，补码都相同，负数稍微复杂。

操作5(101)和-5的二进制。

正数5的二进制：101
  原码=101，反码=101，补码=101；
---------------------------------------
原码:

就是二进制表示法，即最高位为符号位，“0”表示正，“1”表示负，其余位表示数值的大小。

反码:

计算250的各个进制值。
十进制和二进制之间转换:
十进制--->二进制:（11111010）
对于整数部分，用被除数反复除以2，除第一次外，每次除以2均取前一次商的整数部分作被除数并依次记下每次的余数。另外，所得到的商的最后一位余数是所求二进制数的最高位。
二进制--->十进制:
进制数第0位的权值是2的0次方，第1位的权值是2的1次方，第2位的权值是2的2次方……公式：第N位 * 2的N次方,结果再相加.
-------------------------------------------------------------------------------
十进制和八进制之间转换:
十进制--->八进制:
10进制数转换成8进制的方法，和转换为2进制的方法类似，唯一变化：除数由2变成8。
八进制--->十进制:
进制数第0位的权值为8的0次方，第1位权值为8的1次方，第2位权值为8的2次方
-------------------------------------------------------------------------------
十进制和十六进制之间转换:
十进制--->十六进制:
10进制数转换成16进制的方法，和转换为2进制的方法类似，唯一变化：除数由2变成16。
十六进制--->十进制:
第0位的权值为16的0次方，第1位的权值为16的1次方，第2位的权值为16的2次方……
-------------------------------------------------------------------------------
二进制和八进制之间转换:
二进制和十六进制之间转换:
八进制和十六进制之间转换:

平台(硬件+OS)相关性:

我们称能够支持程序运行的硬件或软件环境为平台。

不同的平台都有其特有的指令格式，也就是说Win支持的指令格式和Linux支持的指令格式是不一样的，
进而导致了Windows的可执行文件不能在Linux平台上运行，反之Linux的可执行文件也无法再Windows上运行，把这种情况称为平台相关性。

-编辑操作-----------------------------------------------------------------------------------------------------------

CTRL+C--------复制              		CTRL+X--------剪切                 	 CTRL+V--------粘贴

CTRL+A--------全选      	        CTRL+Z--------撤销            		      CTRL+S--------保存 

---基本操作-----------------------------------------------------------------------------------------------------------

【Win】+D  显示桌面                  【Win】+R  打开“运行"               【Win】+L  屏幕锁定

【Win】+E  打开“我的电脑”          	【Win】+F  搜索文件                  【ALT】+TAB  AB项目切换

先使用 【Win】+R 打开“运行窗口",输入: 

calc—>启动计算器      						mspaint—>打开画图板			

notepad—>打开记事本   				cmd—>CMD命令提示符    				截图工具

---常用命令-----------------------------------------------------------------------------------------------------------

盘符之间的切换: 盘符:回车,如进入E盘,  E:回车

进入指定目录   :cd will :cd javase\day01

目录的回退     :cd.. 回到上一级目录:cd\ 回到盘符根目录
清屏           :cls

进制也就是进位制，是人们规定的一种进位方法。 对于任何一种进制---X进制，就表示某一位置上的数运算时是逢X进一位。 十进制是逢十进一，十六进制是逢十六进一，二进制就是逢二进一，以此类推，x进制就是逢x进位。
---------------------------------------------------------
二进制:由两个基本数字0，1组成，运算规律是逢二进一.计算机都使用二进制表示数据.
八进制:由0、1、2、3、4、5、6、7组成,运算规律是逢八进一.
十进制:由0，1，2、3、4、5、6、7、8、9组成.
十六进制:由0～9以及A，B，C，D，E，F组成.
--------------------------------------------------------
二进制数系统中，位简记为b,也称为比特，每个二进制数字0或1就是一个位(bit)。
位是数据存储的最小单位，其中8 bit 就称为一个字节（Byte）
1B（byte，字节）= 8 bit；
1KB（Kibibyte，千字节）=1024B= 2^10 B；
1MB（Mebibyte，兆字节，百万字节，简称“兆”）=1024KB= 2^20 B；
1GB（Gigabyte，吉字节，十亿字节，又称“千兆”）=1024MB= 2^30 B；
1TB（Terabyte，万亿字节，太字节）=1024GB= 2^40 B；
1PB（Petabyte，千万亿字节，拍字节）=1024TB= 2^50 B；


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

## 体会

想想自己期望中的团队和同事具备哪些特质，然后让自己向着这些方面努力；
聪明，钻研，潜力，韧性
重视基础，重视基础，重视基础！
对技术的热情和热爱（真心感兴趣才能更可能走得更远），乐观&韧性（不管做什么都必然会有挫折，有成功和失败，坚持才是答案，哈哈），认知和思考的能力（是否形成了自己的认知体系，能层层剥茧找到事物的本质），勤奋（加班不是勤奋，思考上的懒惰才是真正的懒惰）。

> 1. 不知道就说不知道，不要绕和试图遮掩，大家都是做技术的，技术上的事，做没做过，会不会，一目了然。如果不懂装懂，绕来绕去，会让人觉得未来跟你合作会很累；2. 对知识型问题，就是那种知道就是知道不知道就是不知道的问题（比如中国有多少个省级行政区），直接说不知道就好了。但对于认知型、问题解决型之类的问题，一定要根据自己已有的知识和经验给出自己的思考和解决方案

## 重要的是这些：
(1) 如果你处理过，那你对细节是否了解，是否形成自己的一套方法论，是否总结了问题分类和常见解法跳出解决问题迈向避免问题等等，这能从侧面反映你的认知能力和钻研能力；
(2) 如果你没处理过，你能否根据已有的经验和知识给出不错的解决思路（侧面反映你的思考能力和举一反三的能力，以及解决新问题的能力）
(3) 另外，有一些不明确的点一定要和面试官确认，比如，现象的一些细节，线上环境的配置等等，不要做主观假设,这其实也是很重要的方面，如果你解决问题都是靠猜和主观假设，很难让人放心.

## 按照学Java基础5天，看一本书5天。10天Java基础就可以学完。看一个APP视频教程10天，谷歌官网看一遍2个月。行动，现在都上班了

未完待续！！！
