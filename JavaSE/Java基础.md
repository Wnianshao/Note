JAVA学习笔记

# JAVA开发注意事项

1 计算机基础很重要，很重要
2 选择适合自己的语言，不纠结，不同语言适用场景不同，不同语言逻辑语法大同小异，触类旁通，推荐学JAVA，简单上手并好就业一些
3 动手写代码非常重要，光看不练白搭
4 懂了和会用不一样，会应用才是真的懂了
5 学习要有笔记、思维导图或代码记录，有自己的想法积累或总结，长期以往就会把精华学进脑内，就会知道怎么解决问题或者知道解决问题需要用哪段代码，最后就有了自己的学习方法
6 不要全部死记硬背，不变的语法，结构等需要背下来，其他功能性的内容知道在哪或者怎么找到解决办法就行了，实在理解不了就硬背然后实践中理解
7 报错一定不要逃避，这是提高自己能力的重要方法，排除错误才会提升能力也会避免犯错
8 不要闭门造车，敢于交流分享，交流分享技术很重要，不要让自己成为井底之蛙，很多问题别人也许有特别好的解决办法，不怕嘲笑，都是过来人，越战越勇！
9 不要跟风新技术，学习技术要建立体系，要有精通的技术和竞争力，用有限的时间做高效的事，定好学习目标和方向
10 别让收藏夹吃灰，别让磁盘充满也不学习，资源在精不在多，同上，规划好学习目标
11 学编程同性别无关，职场中女生有劣势，做好职业规划
12 学编程和专业无关，技术和业务逻辑分离，都重要
13  数学不好不是学不好编程的借口，绝大多数程序员不需要用到高深的数学知识，除非是算法、大数据等方向
树立目标，前进就是进步

# 基础

1、以class组成

2、执行入口为main方法。有固定格式：

public static void main(String[] args){

}

3.严格区分大小写

4、一个文件最多只有一个public类，public类必须按该类名命名

5、main方法也可以卸、载非public类中，然后指定运行非public类。

## 1.变量

![image-20211219134044734](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219134044734.png)

![image-20211219134247247](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219134247247.png)

## 2.基本数据类型

![image-20211219134454981](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219134454981.png)



![image-20211219132743639](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219132743639.png)

![image-20211219133101376](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219133101376.png)

![image-20211219140010861](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219140010861.png)

![image-20211219152328338](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219152328338.png)

![image-20211219152734547](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219152734547.png)

![image-20211219153029703](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219153029703.png)

![image-20211219153408170](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219153408170.png)

![image-20211219154050820](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219154050820.png)

## 3.运算符

### 算数运算符

![image-20211219154651193](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219154651193.png)

### 关系运算符

![image-20211219154841121](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219154841121.png)

![image-20211219154906721](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219154906721.png)

![image-20211219155130902](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219155130902.png)

## 4.标识符

![image-20211219155223015](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219155223015.png)

![image-20211219155255578](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219155255578.png)

## 5.键盘输入语句

![image-20211219155510105](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219155510105.png)

![image-20211219155546508](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219155546508.png)

## 6.数组（Array）

### 数组的使用

动态初始化

1、int a[] = new int[5]

2、int[]a  ;

​      a = new int[5];

静态初始化

int a[] = {2,3,4,5,6,7,8,9}

int a[] = new int[]{2,3,4,5,6,7,8,9}

### 数组的拷贝

new a;

new b;

 for(int i=0;i<n;i++){

b[i] = a[i];

}

### 数组的反转

1、找规律反转



2、倒序遍历

### 数组的添加

静态添加（末尾）

1、定义初始数组

2、定义一个新的数组，大小为arr.length+1

3、遍历arr数组，依次将arr的元素拷贝到arrNew数组

4、将4赋给arrNew的最后一个元素

5、让arr指向arrNEW

动态添加

char key 

判断key break

### 查找

顺序查找



二分查找

### 二维数组

静态初始化

int[] [] arr = {{0,0,0},{1,1,1},{2,2,2}}

动态初始化

int a[] [] = new int [2] [3]

int[]    x[] 也是二维数组

二维数组实际上是由多个一维数组组成的。

String[] strs = {"a","b"};

Stirng strs[] = new String[]{"a",b","c"};







































# 面向对象(OOP)



## 7.类和对象

### 属性/成员变量

1.可以是基本数据类型，也可以是数组

2.有访问修饰符（控制属性访问范围）

public（默认）、protecter、private

3.属性有默认值0、false

### 创建对象形式

1.先声明再创建

Person preson；

preson = new Person();

2.直接创建

Person person = new Person();

### 类和对象内存分配机制

JAVA内存的结构分析

1、栈：一般存放基本数据类型

2、堆：存放对象（Cat cat，数组等）

3、方法区：常量池（常量、比如字符串），类加载信息

4、示意图[Cat(name,age,price)]

JAVA常见对象流程

1、先加载Person类信息

2、在堆中分配空间，进行默认初始化

3、把地址赋给对象

4、进行指定初始化

### 成员方法

1、当程序执行方法时，就会开辟一个独立的空间（栈空间）

2、当方法执行完毕，或者执行到return语句时，就会返回到调用方法的地方

3、返回后，继续执行和后面的代码

好处：

1、提高代码的复用性

2、可以将实现的细节封装起来，然后供其他用户来调用即可

注意事项 

1、一个方法最多一个返回值

2、返回多个值？：public int[] getshuzu(int n1,int n2){

​					int [] arr = new int[2];arr[0] = 1;arr[1]= 2;

​					return arr;		

}

3、方法传入的值为实参，方法中的为形参

4、类中方法也可以调用方法

5、一个类也可以调用另一个类的方法（跨类调用和访问修饰符和包还有关系）

**parameter --> 参数**

6、基本数据类型形参任何变化不影响实参（在栈里）

​		引用数据类型形参传递的是地址，变化时实参也变化（在堆里）（int[] [] arrry,Person p）

 **row 行 column列**

p = null (不改变)

p = new Person(不改变)

7、方法递归调用

栈中 先进后出

一定要有一个递归条件，避免死循环

8、方法重载

允许多个同名方法的存在，但要求形参列表不一致、

System.out.print() 典型重载例子

好处：减轻起名和记名的麻烦

细节：方法名一样、 形参必须不同（形参类型或个数或顺序，至少一样不同，参数名无要求）、返回类型无要求

9、可变参数

将同一个类中多个同名同功能但参数个数不同的方法，封装成一个方法

public int sum(int... nums){

​	int res = 0;

​	for(int i=0;i< num.length;i++){

​		res+=i

}

}(可接受0到多个参数,nums可以当作数组来使用 )

细节：实参可以是0或者任意多个

可变 参数的实参可以是数组，本质就数组

可变参数可以和普通类型一起放在形参列表，但必须保证可变参数在最后

最后只能有一个可变参数

### 作用域

全局变量、局部变量

全局变量有默认值（可以不赋值）、局部变量必须先赋值

属性如果不复制，有默认值

**细节**：属性和局部变量可以重名，访问时遵循就近原则

在同一个作用域中，两个局部变量不能重名

作用域范围：全局变量：可以被本类使用，或其它类使用（通过对象调用）

局部变量：只能在本类对应的方法中使用

修饰符：全局变量/属性可以加修饰符

局部变量不可以加修饰符

### 构造方法/构造器

1、构造器没有返回值

2、方法名和类名必须一样

3、参数列表和成员方法一样的规则

4、构造器的调用由系统完成

作用：完成对新对象的初始化

**细节**：一个类可以构造器重载（例：一个构造姓名、一个构造年龄）

如果没有定义构造器，系统会自动给类生成一个无参构造器

一旦定义了自己的构造器，默认构造器会被覆盖（除非显式定义一下）

流程分析：

1、1、先加载Person类信息（只加载一次）

2、在堆中分配空间（地址），进行默认初始化

3、把地址赋给对象

4、进行指定初始化（对象初始化 0 null）、（显式初始化）、（构造器初始化）

5、在对象在堆中的地址返回给p，（p是引用对象）

### this关键字

this.name当前对象的属性（哪个对象调用，this就指向哪个对象）

细节：this关键字可以用来访问本类属性、方法、构造器

this用于区分当前类的属性和局部变量

访问成员方法的语法：this.方法名（参数列表）

访问构造器的语法：this(参数列表)，只能在构造器中使用（必须在构造器中第一条语句）

this不能在类定义的外部使用，只能在类定义的方法中使用

### 包

1、作用

区分相同名字的类(import com.tencent.practice.user)

控制访问范围 

很好地管理类

2、本质

创建不同地文件夹来保存类文件

3、命名规则

只能包含数字、字符、下划线、小圆点、不能以数字开头，不能时关键字或保留字

4、com.公司名.项目名.业务模块名

com.tencent.practice.user

5、细节：

java.lang.*默认引入

import java.util.Scanner 系统提供的工具包

import java,util.*导入包内所有类

Arrays类 Arrays.sort()自动排序

包必须放在导入类的最上面

一个类中最多只有一个package

建议需要哪个类就导入哪个类

### 访问修饰符

1、公开级别：用public修饰、对外公开

2、受保护级别：用proteced修饰，对于子类和同一个包中的类公开

3、默认级别：没有修饰符号，向同一个包的类公开

4、私有级别：用private修饰，只有类本身可以访问，不对外公开

面向对象的三大特征：封装、继承、多态

### 封装

好处：隐藏实现细节

可以对数据进行验证、保证安全合理

实现步骤：（三步）

1、将属性私有化private

2、提供一个公共给的（public）set方法，用于对属性判断并赋值

public void setXxx（类型 参数名）{

​           //加入数据验证的业务逻辑

​              属性 = 参数名

}

3、提供一个公共的（public）get方法，用于获取属性的值

public 数据类型 gerXxx（）{//权限判断

​	return xx；

}

### 继承

代码复用性提高、扩展性提高

两个类的属性和方法有很多是相同的

​            A（父类、基类、超类）

​				[共有属性]

​				[共有方法]

​     B（子类、派生类）     C（子类）

D（子类、派生类）

​		[特有属性]

​		[特有方法]

class 子类 extends 父类{

​	子类会自动拥有父类定义的属性和方法

}

**细节：**私有属性和方法不能在子类直接访问，要通过公共的方法去访问

创建子类对象时，子类必须调用父类的构造器，完成父类的初始化（如果父类没有提供无参构造器，子类的构造器中会默认用super()调用父类的无参构造器完成对父类初始化的工作，否则编译不会通过）

如果希望指定去调用父类构造器，则显示的调用一下：super(参数列表)

super在使用时，必须放在构造器第一行,只能在构造器中使用

super()和Tthis()都只能放在构造器第一行，因此这两个方法不能共存在一个构造器

object(顶级父类)是所有类的基类

子类最多继承一个父类，java是单继承机制

不能滥用继承

**本质：**

当子类对象创建好后，建立查找的关系 

（1）首先看子类是否有该属性

（2）如果子类有这个属性，并且可以访问，则返回信息

（3）如果子类没有这个属性，就看父类有没有这个属性（如果父类有该属性，并且可以访问，就返回信息）

（4）如果父类没有按照（3）的规则，继续找商机父类，直至Objects

super（参数）：调用父类中的某一个构造函数（应该为构造函数中的第一条语句）。

this（参数）：调用本类中另一种形式的构造函数（应该为构造函数中的第一条语句）。

![image-20211112114438655](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211112114438655.png)

#### super关键字

用于访问父类的属性、方法、构造器

1、访问父类的非私有属性

super.属性名

2、访问父类非私有的方法

super.方法名（参数列表）

细节：

调用父类构造器的好处：分工明确、父类属性由父类初始化，子类属性由子类初始化

子类父类重名成员，必须用super调用父类（先在本类找，如果有就调用，如果没用去父类找，层层向上）

super访问遵循就近原则

![image-20211112155721791](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211112155721791.png)

#### 方法重写

子类一个方法和父类一个方法名称返回类型参数都一样，就说子类覆盖了父类的方法

![image-20211112164227488](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211112164227488.png)

### 多态

方法或对象具有多种形态，是OOP的第三大特征，是建立在分装和继承基础之上多态具体体现。

1、方法的多态

重写和重载就体现出多态

2、对象的多态

**重要**

![image-20211112170258827](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211112170258827.png)

Animal animal = new Dog():[animal 编译类型是Animal，运行类型Dog]

animal = new Cat（）[animal的运行类型变成了Cat，编译类型仍然是Animal]

通过getClass（）来查看运行类型

**细节**：

多态的前提：两个对象（类）存在继承关系

多态的向上转型:

本质：父类的引用指向了子类的对象

语法：父类类型   引用名 = new 子类类型（）；

特点：编译类型看左边、运行类型看右边

​			可以调用父类的所有成员（需遵守访问权限），不能调用子类中的特有成员。

编译的时候按父类标准编译，运行的时候按子类的标准运行

运行规则：从子类开始，向上寻找

多态的向下转型：

语法：子类类型 引用名 = （子类类型）父类引用

只能强转父类的引用，不能强转父类的对象

要求父类的引用必须指向的是当前目标类型的对象

向下转型后，可以调用子类类型中所有成员

属性没有重写之说

instanceof 比较操作符：判断对象的运行 类型是否为XX类型或XX类型的子类型

属性看编译类型，运行看方法类型,，属性没有重写之说

#### Java的动态绑定机制

当调用对象方法的时候，该方法会和该对象的内存地址/运行类型绑定

当调用对象属性时，没有动态绑定机制，哪里声明，哪里使用

#### 多态数组

![image-20211216202636879](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216202636879.png)

多态数组调用子类方法

![image-20211216203332621](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216203332621.png)

#### 多态参数

![image-20220307145541797](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220307145541797.png)

#### Object类详解

##### 比较运算符

== 和 equals 方法对比

== ：既可以判断基本类型、又可以判断引用类型

==：判断基本类型，判断的是值是否相等

==：判断引用类型， 判断的是地址是否相等

 euqals：只能判断引用类型（可重写）                                                                                                                                                                                 Stirng、Integer类的equals方法被重写了，变成了比较值是否相

##### hasCode方法:

![image-20211114194435887](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211114194435887.png)

##### toString方法

   全类名+@+哈希值的十六进制

例：return getClass().getName+"@"+Intefer.toHexString(hasCode)

​           包名+类名+@+哈希值（16进制  ）

一般会重写toString方法

当我们输出对象时，toString方法会默认调用，比如syso（Monster）；就会默认调用toString

##### finalize方法

1、对象被回收时，系统自动调用该对象的finalize方法。 

2、当某个对象没有任何引用时，jvm就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁前用finalize方法

3、垃圾回收机制的调用，是由系统来决定（即有自己的GC），也可以通过System.gc（）主动触发垃圾回收机制 

## 8.断点调试(debug)

每个变量的值

出现异常

追示源码 跳入方法 跳出方法

动态断点，可以跳过不需要的过程    

## 项目小练习2——房屋出租系统  

使用分层思想

![image-20220309174315606](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220309174315606.png)

## 9.静态变量与静态方法

### 类变量(静态变量)(static)

![image-20220311174018807](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220311174018807.png)

public static int count = 0;

类变量随着类的加载而创建，没有对象仍然可以使用

类变量可以通过    类.变量  直接访问（满足访问权限）

静态变量被对象共享，不影响对静态变量的使用

访问修饰符 static 数据类型 变量名;

访问方式：类名.类变量名 （推荐）   对象名.类变量名

**细节**

类访问不能直接访问非静态成员变量

static类变量，在类加载时就生成了，没有创建对象实例也可以通过类.类变量名访问

### 类方法

访问修饰符 static 数据返回类型 方法名（）{ }

1.当方法使用static后，该方法就是静态方法

2.静态方法就可以访问静态属性/变量

【不涉及相关成员时，使用静态方法】

【不创建实例时，当作工具来使用】

【自己写方法的时候】【Math类、Arrays类】

细节

类方法中不允许使用和对象有关的关键字，比如this、super（不可以使用非静态变量）

类方法（静态方法）中只能访问静态变量或静态方法

（非静态方法）普通成员方法，既可以访问普通变量方法，也可以访问静态变量方法（必须遵守访问权限）



###   main方法

mian方法虚拟机调用，所以必须为public

java虚拟机在执行main方法时不必创建对象，所以该方法法必须是static

该方法接收String类型的数组参数，该数组中保存执行Java命令时传递给所运行类型的参数

java执行的程序 [参数1，参数2，参数3]

可以直接调用main方法所在类的静态方法或静态属性。

但是，不能直接访问该类中的非静态成员，必须创建类的一个实例对象后，才能通过这个对象去访问类中的静态成员

![image-20220311221049256](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220311221049256.png)

在IDEA中动态传入main方法参数

![image-20220311221421475](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220311221421475.png)

## 10.代码块

![image-20211216212907394](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216212907394.png)

![image-20211216213034948](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216213034948.png)

代码块调用优先于构造器 调用构造器的时候就会调用代码块

创建子类对象实例，父类也会被加载，而且，父类先被加载，子类后被加载

类被加载的三中情况：创建对象实例时（new）

​										创建子类对象实例时，父类也会被加载

​									使用类的静态变量时（静态属性，静态方法）

static代码块，是在类加载时被执行的，而且只会执行一次

普通代码块，是在new对象时，被调用，而且是每创建一个对象，就调用一次

![image-20211216213637761](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216213637761.png)

![image-20211216224409558](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216224409558.png)

![image-20211216224807201](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216224807201.png)

1.静态代码块和静态属性初始化按顺序执行

2.普通代码块和普通属性初始化按顺序执行 

![image-20220313133023538](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313133023538.png)



继承中的代码块

![image-20211216230046804](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216230046804.png)



![](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216230526151.png)

## 11.单例设计模式

23种设计模式

1.单例（单个实例）

![image-20220313140945542](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313140945542.png)

饿汉式

![image-20220313141300267](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313141300267.png)

```java
public class girlfriend {
	public static void main(String[] agrs) {
		System.out.println(girl.getGrifriend());
		
	}
}


class girl{
	private String name;
	private int age;
	
	//2.在类的内部直接创建
	private static girl girlfriend = new girl("小红",20);
	
	//1.将构造器私有化
	private girl(String name,int age) {
		this.name = name;
		this.age = age;
	}
	
	//3.提供一个公共方法，返回girl
	public static girl getGrifriend() {
		return girlfriend;
	}
	public String toString() {
		return girlfriend.name + girlfriend.age;
	}
	
}
```

懒汉式

![image-20220313155454884](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313155454884.png)





饿汉式VS懒汉式

```java
public class girl_lanhan {
	public static void main(String[] args) {
		System.out.println(girlfriend.getGirlfriend());
	}
}
class girlfriend{
	private String name;
	private int age;
	private static girlfriend girl1;
	
	private girlfriend(String name,int age) {
		this.name = name;
		this.age = age;
	}
	
	public static girlfriend getGirlfriend() {
		if (girl1 == null) {
			girl1 = new girlfriend("小红",20);
		}
		return girl1;
	}
	public String toString() {
		return girl1.name + girl1.age;
	}
}

```

![image-20220313160038432](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313160038432.png)

![image-20220313160459914](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313160459914.png)

## 12.final关键字

![image-20211216212203808](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216212203808.png)



![image-20211216212654711](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216212654711.png)

定义、构造器、代码块赋值

![image-20220313170302431](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313170302431.png)

静态变量是在类加载时就创建，所以final修饰的静态变量不能在构造器中复制

![image-20220313170530833](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220313170530833.png)

![image-20211216232948431](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216232948431.png)

![image-20211216233154533](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216233154533.png)

可以直接类名.变量名



## 13.抽象类

![image-20211216233953510](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216233953510.png)

一般来说，抽象类会被继承，由其子类来实现方法。

![image-20211216234051426](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216234051426.png)

细节：

1.不能被实例化

![image-20211216234320647](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216234320647.png)

![image-20211216234424500](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216234424500.png)

![image-20211216234743350](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211216234743350.png)

### 抽象类——模板设计模式

![image-20211217002034968](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217002034968.png)

### 接口

![image-20211217100915924](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217100915924.png)

![image-20211217101204458](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217101204458.png)

![image-20211217101250134](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217101250134.png)

**细节**:

1.不能new 一个接口 

2.接口中所有方法都是public

3.普通类接口的子类必须实现所有方法（快捷键alt+enter）

4.abstract 类 impleements 接口{

​	可以不实现接口方法

}

![image-20211217102235218](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217102235218.png)

5.一个类可以同时实现多个接口

![image-20211217102931198](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217102931198.png)

6.![image-20220315154158469](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220315154158469.png)

7.接口名.属性名

8.接口可以继承接口，但不能继承类

9.接口之只能用public或者默认的

### 接口VS继承

![image-20211217104343265](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217104343265.png)

实现接口是Java对单继承机制的一个补充



![image-20211217105700237](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217105700237.png)



![image-20211217105745990](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217105745990.png)

```java
public class e_vs_i {
	public static void main(String[] args) {
		littleMonkey a = new littleMonkey();
		a.clime();
		a.fly();
		a.swim();
	}
}

class Monkey{
	public void clime() {
		System.out.println("i can climb");
	}
}


interface fish{
	public void swim();
}

interface bird{
	public void fly();
}

class littleMonkey extends Monkey implements fish,bird{

	@Override
	public void fly() {
		// TODO Auto-generated method stub
		System.out.println("i can fly");
	}

	@Override
	public void swim() {
		// TODO Auto-generated method stub
		System.out.println("i can swim");
	}
	
}

```

### 接口的多态

![image-20211217112115474](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217112115474.png)

![image-20220315161432361](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220315161432361.png)

接口与继承的多态类似

![image-20220315161802047](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220315161802047.png)



### 内部类

类的五大成员：属性、方法、构造器、代码块、内部类

![image-20211218130707719](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218130707719.png)

![image-20211217113126341](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217113126341.png)

![image-20211217113450279](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217113450279.png)

内部类的分类

![](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217113647149.png)

#### 局部内部类

```java
class Outer02{
	private int n = 100;
    public void m1(){ 
        class Inner{
            public vod f1(){
                System.out.println("n1 = " + n1)
            }
        }
    }
}
```

![image-20211218102718263](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218102718263.png)

记住：![image-20211217114842076](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211217114842076.png)

#### 匿名内部类

```java
public class niming {
	public static void main(String[] args) {
		Matrix muti = new Matrix() {
			public void say() {
				System.out.println("i'm not the one");
			}
		};
		Mofeisi fucck = new Mofeisi() {
     //由于是匿名内部类 相当于fucck继承了Mofeisi接口：fucck implements Mofeisi
			public void foresee() {
				System.out.println(new Matrix().leo + "" + " is the one");
			}
		};
		muti.say();
		fucck.foresee();
	}

}
class Matrix{
	String leo = "leo";
	public void say() {
		System.out.println("i'm the one");
	}
}
interface Mofeisi{
	void foresee();
}
```

![image-20220325154517198](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220325154517198.png)

![image-20220325155222926](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220325155222926.png)

![image-20220325155503438](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220325155503438.png)

细节：匿名内部类语法比较奇特，匿名内部类既是一个类的定义，同时本身也是一个对象，既有类的特征，也有创建你对象的特征

![image-20220327131309452](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327131309452.png)

![image-20220327131544378](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327131544378.png)

![image-20220327131607816](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327131607816.png)

最佳实践：当作实参直接传递，简洁高效

![image-20220327133700835](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327133700835.png)

```java
public class naozhong {
	public static void main() {
		CellPhone cellPhone = new CellPhone();
		cellPhone.alarmClock(new Bell(){
			public void ring() {
				System.out.println("懒猪起床了");
			}
		});
		cellPhone.alarmClock(new Bell(){
			public void ring() {
				System.out.println("上课了");
			}
		});
	}
}
interface Bell{
	 void ring();
}
class CellPhone{
	public void alarmClock(Bell bell) {
		bell.ring();
	}
}
```

#### 成员内部类

![image-20220327135826743](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327135826743.png)

![image-20220327140204962](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327140204962.png)

6、![image-20220327140828215](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327140828215.png)

 ![image-20220327141021067](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327141021067.png)

```java
public class chengyuan {
	public static void main(String[] args) {
		//创建对象方式一
		Outer outer = new Outer();
		Outer.Inter oo1 = outer.new Inter();
		oo1.say();
		//创建对象方式二
		outer.getInter();
		Outer.Inter oo2 = outer.getInter();
		oo2.say();
		
	}

}
class Outer{
	class Inter{
		public void say() {
			System.out.println("nihao,shijie");
		}
	}
	public Inter getInter() {
		return new Inter();
	}

```

#### 静态内部类

![image-20220327141117656](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327141117656.png)

![image-20220327141417539](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327141417539.png) 

```java
public class jingtaineibu {
	public static void main(String[] args) {
        
		Sunshine.Rainy s = new Sunshine.Rainy();
		
		Sunshine.Rainy s2 = Sunshine.getRainy();
		s.say();
		s2.say();
	}

}
class Sunshine {
	static class Rainy{
		public void say() {
			System.out.println("");
		}
	}
	public static Rainy getRainy() {
		return new Rainy();
	}
}
```

####  总结

![image-20220327145849823](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327145849823.png)

# 枚举和注解

## 枚举

![image-20220327182711623](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327182711623.png)

枚举类，把具体的对象一个一个列举出来

![image-20220327182910476](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327182910476.png)

枚举两种方式：自定义枚举、使用enum关键字来实现枚举类

自定义枚举

1将构造器私有化，防止直接new

2去掉setXXX相关方法，防止属性被修改

3在Season内部，直接创建固定的对象

4优化，可以加入final修饰符

![image-20220327183339283](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327183339283.png)

```java
public class Meijufangfa1 {
	public static void main(String[] args) {
		System.out.println(Season.SPRING);
	}

}
class Season{
	private String name;	//季节
	private String des;		//季节特征
	private Season(String name,String des) {
		this.name = name;
		this.des = des;
	}
	public static final Season SPRING = new Season("春天","温暖");
	public static final Season SUMMER = new Season("夏天","炎热");
	public static final Season AUTUAM = new Season("秋天","凉爽");
	public static final Season WINTER = new Season("冬天","寒冷");
	
	public String toString() {
		return "季节："+ this.name + " " + "特征：" + this.des;
	}
}

```

使用enum关键字来实现枚举类

1使用关键字enum替代class

2public static final Season SPRING = new Season("春天","温暖")直接使用

SPRING("春天","温暖")解读 常量名(实参列表)

3如果有多个常量（对象），使用,号间隔即可

4如果使用enum来实现枚举，要求将定义的常量对象，写在前面

```java
public class Meijufangfa1 {
	public static void main(String[] args) {
		System.out.println(Season.SPRING); 
	}

}
enum Season{
	SPRING("春天","温暖"),SUMMER("夏天","炎热"),AUTUAM("秋天","凉爽"),WINTER("冬天","寒冷");
	private String name;	//季节
	private String des;		//季节特征
	private Season(String name,String des) {
		this.name = name;
		this.des = des;
	}
	
	
	public String toString() {
		return "季节："+ this.name + " " + "特征：" + this.des;
	}
}
```

注意事项

![image-20220327210201262](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327210201262.png) 1是一个final类型的类，且继承自Enum类

3使用无参构造器创建常量对象SPRING()/SPRING

枚举常用方法使用

![image-20220327212146153](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327212146153.png)

### 补充：增强for循环

![image-20220327212903334](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327212903334.png)

```java
public class Meijufangfa1 {
	public static void main(String[] args) {
		System.out.println(Season.SPRING); 
		Season autumn = Season.AUTUMN;
		//输出枚举对象的名字
		System.out.println(autumn.name());
		//ordinal()输出的是该枚举对象的次序（编号从0开始）
		System.out.println(autumn.ordinal());
		//从反编译看出values方法，返回Season[]
		//含有定义的所有枚举对象
		Season[] values = Season.values();
		for(Season season: values) {//增强for循环
			System.out.println(season);
		}
		//valueOf 将字符串转换成枚举对象，要求字符串必须为已有的常量名
		Season autumn1 = Season.valueOf("AUTUMN");
		System.out.println(autumn1);
		//compareTo:比较两个枚举常量，比较的是编号
		//前一个编号-后一个编号
		System.out.println(Season.AUTUMN.compareTo(Season.SPRING));
	
	}

}
```

enum实现接口

![image-20220327215426023](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220327215426023.png)

## 注解

![image-20220517150157104](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517150157104.png)

![image-20220517150216201](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517150216201.png)

### Override

![image-20220517150347142](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517150347142.png)

1.重写了父类的fly方法

2.如果没有写，也会重写父类

3.如果你写了@Override注解，编译器会去检查该方法是否真的重写了父类的方法，如果的确重写了，则编译通过，如果没有构成重写，则编译错误

![image-20220517150939148](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517150939148.png)

### Deprecated

![image-20220517151222008](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517151222008.png)

![image-20220517151206257](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517151206257.png)

过度作用

### SuppressWarnings

1.不希望看到这些警告时，可以使用SuppressWarnings注解来抑制警告信息

![image-20220517152117782](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517152117782.png)

3.可以指定的警告类型有。。

4.作用范围与放置的位置有关

### 元注解

![image-20220517152741509](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517152741509.png)

![image-20220517152957256](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220517152957256.png)



# 异常处理

![image-20211218144320414](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218144320414.png)



```java
public class Exception01 {
    public static void main(String[] args) {
        int num1 = 10;
        int num2 = 0;

        try {
            int res= num1 / num2;
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
        System.out.println("程序正在运行");

    }
```

![image-20211218144635641](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218144635641.png)

## 异常体系图

![image-20211218150601751](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218150601751.png)

![image-20220524180328340](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524180328340.png)

## 常见运行异常

![image-20211218150850036](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218150850036.png)

##   常见的编译异常 

![image-20211218151508961](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218151508961.png)

## 异常处理方式

![image-20220524192012031](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524192012031.png)

### try-catch-finally

![image-20211219172334833](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172334833.png)

### throws

![image-20211219172400987](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172400987.png)

![image-20211219172431598](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172431598.png)

### try-catch具体演示

![image-20211219172525291](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172525291.png)

![image-20211219172655346](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172655346.png)

![image-20211219172620044](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172620044.png)

![image-20220524195428263](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524195428263.png)

### throws

![image-20211219172727103](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172727103.png)

![image-20220524201221821](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524201221821.png)

![image-20211219172823631](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219172823631.png)

### 自定义异常

![image-20220524202814049](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524202814049.png)

### throw和throws的区别

![image-20220524203334107](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220524203334107.png)

```java
public class homework01 {
    public static void main(String[] args) {
        //验证输入参数的个树
        try {
            if (args.length != 2) {
                throw new ArrayIndexOutOfBoundsException("参数个数不对");
            }
            int n1 = Integer.parseInt(args[0]);
            int n2 = Integer.parseInt(args[1]);
            double res = cal(n1, n2);

            System.out.println(res);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println(e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("参数格式不对 ");
        } catch (ArithmeticException e) {
            System.out.println("出现除0异常");
        }

    }
    //编写除法
    public static double cal(int n1,int n2){
        return n1/n2;
}
}
```



# 常用类

## 包装类

![image-20211218142733152](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218142733152.png)

### Boolean包装类

![image-20211218185629163](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218185629163.png)

### Character包装类

![image-20211218185708570](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218185708570.png)

### Number包装类

![image-20211218190100590](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218190100590.png)

### 包装类转换

#### 包装类和基本类型数据转换

![image-20211218190216606](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211218190216606.png)

```java
public class Wapper {
    public static void main(String[] args) {
        //JDK5前
        //手动装箱 int->Integer
        int n1 = 100;
        Integer integer = new Integer(n1);
        Integer integer1 = Integer.valueOf(n1);
        //手动拆箱
        //Integer->int
        int i = integer.intValue();

        //JDK5后
        //自动装箱
        int n2 = 200;
        Integer integer2 = n2;
        //自动拆箱
        int n3 = integer2;
    }
}

```

题目

![image-20211219131853537](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219131853537.png)

#### 包装类型和String类型相互转换

```java
public class 转换 {
    public static void main(String[] args) {
        //包装类转String\
        Integer i = 100;
        //方式1
        String str1 = i + "";//仅仅是赋一个新变量
        //方式2
        String str = i.toString();
        String str3 = String.valueOf(i);

        //String转包装类
        //使用自动装箱
        String str4 = "123456";
        Integer i2 = Integer.parseInt(str4);
        //使用构造器
        Integer i3 = new Integer(str4);

    }
}
```

#### Integer类和Character类的常用方法

![image-20211219132419879](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219132419879.png)

经典面试题

![image-20211219160321349](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219160321349.png)

![image-20211219160500204](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219160500204.png)

只要有基本数据类型，就是判断的值是否相等

![image-20220525205542801](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220525205542801.png)

### String类

实现串行化Serializable：可以在网络传输

![image-20211219161814662](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219161814662.png)

#### String类的注意事项

![image-20211219162504308](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219162504308.png)

#### String创建方式

![image-20211219162527898](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219162527898.png)

![image-20211219162547066](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219162547066.png)



![image-20211219162949929](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219162949929.png)

#### 字符串特性+习题

![image-20211219164244455](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219164244455.png)

![image-20211219164321408](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219164321408.png)

![image-20211219164639471](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219164639471.png)

String类常用方法

![image-20220526153904046](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220526153904046.png)

![image-20211219165000392](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165000392.png)

```java
public class zifuchuan {
    public static void main(String[] args) {
            String s1 = "asd";
            String s2 = "ASd";
        System.out.println(s1.equals(s2));//F
        System.out.println(s1.equalsIgnoreCase(s2));//T
        System.out.println(s1.length());//3
        System.out.println(s1.indexOf("s"));//1
        System.out.println(s2.lastIndexOf("S"));//1
        String s3 = s1.substring(0,2);
        System.out.println(s3);//as
        System.out.println(s1.charAt(0));//a
    }
}
```

![image-20220526160303739](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220526160303739.png)

```java
public class zifuchuan {
    public static void main(String[] args) {
        String s1 = "你好世界";
        String s2 = "你好中国";
        String s3 = "xiaoxie";
        String s4 = "DAXIE";
        String s5 = "锄禾日当午|汗滴禾下土@谁知盘中餐;粒粒皆辛苦";
        System.out.println(s3.toUpperCase());
        System.out.println(s1.concat(s2) );
        System.out.println(s4.toLowerCase(Locale.ROOT));
        System.out.println(s1.replace("你好","hello"));

        //转换成字符数组
        char[] zifu = s3.toCharArray();
        for(char c : zifu){
            System.out.println(c);
        }
        //split用法
        String[] poem = s5.split("[|,@;]");
        for(String s : poem){
            System.out.println(s);
        }

        // compareTo 比较两个字符串的大小，如果前者大,//则返回正数，后者大，则返回负数，如果相等，返回0//老韩解读
        // (1)如果长度相同，并且每个字符也相同，就返回0
        // (2〕如果长度相同或者不相同，但是在进行比较时，可以区分大小l/
        //        就返回if (c1 != c2){
        //    return c1 - c2;
        // (3)如果前面的部分都相同，就返回 str1.len - str2.lenl
        System.out.println(s1.compareTo(s2));
        //在对字符串进行分割时，如果有特殊字符，需要加入转义符\

        //format格式字符串
        int num = 15;
        System.out.printf("num = %d\n",num);
        System.out.println(String.format("num = %d",num));
    }
}
```

#### format输出

![image-20220526163626031](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220526163626031.png)

### StringBuffer类

![image-20211219165115471](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165115471.png)

![image-20211219165148368](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165148368.png)

![image-20211219165339244](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165339244.png)

![image-20220526195346313](E:\大学\学习资料\笔记\pictures\image-20220526195346313.png)

#### StringBuffer类构造器

![image-20211219165634894](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165634894.png)

#### String ->StringBuffer

![image-20211219165721318](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165721318.png)

#### StringBuffer -> String

![image-20211219165852027](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165852027.png)

#### StringBuffer常用方法

![image-20211219165919786](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219165919786.png)

![image-20211219170106463](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170106463.png)

![image-20211219170144815](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170144815.png)

![image-20211219170211427](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170211427.png)

![image-20211219170243399](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170243399.png)

#### 练习 将钱的数目每三位加一个逗号

```java
public class TrunToMoney {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String price = scanner.next();//123456.78
        StringBuffer money = new StringBuffer(price);
        if(price.indexOf(".") == -1){
            for(int i = price.length()-3;i > 0;i-=3){
                money.insert(i,",");
            }
        }else{
            for(int i = price.indexOf(".")-3;i > 0;i-=3){
                money.insert(i,",");
            }
        }
        System.out.println(money);
    }
}
```

### StringBuilder类

#### 基本介绍

![image-20211219170340694](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170340694.png)

![image-20220526211550660](E:\大学\学习资料\笔记\pictures\image-20220526211550660.png)

![image-20220526211843874](E:\大学\学习资料\笔记\pictures\image-20220526211843874.png)

#### String vs StiringBuffer vs StringBuilder

![image-20211219170648262](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170648262.png)

![image-20211219170740516](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170740516.png)

### Math类

#### 常用方法

```java
public class Mathlei {
    public static void main(String[] args) {
        //1.abs绝对值
        int abs = java.lang.Math.abs(-9);
        System.out.println(abs);//9
        //2.pow求幂
        double pow = Math.pow(-3.5,4);
        System.out.println(pow);//
        //3.ceil向上取整,返回>=该参数的最小整数
        double ceil = Math.ceil(-3.00001);
        System.out.println(ceil);//-3.0
        //4.floor向下取整,返回<=该参数的最大整数
        double floor = Math.floor(-4.999);
        System.out.println(floor);//-5.0
        //5.round四舍五入 Math.floor(该参数+0.5)
        long round = Math.round(-5.001);
        System.out.println(round);//-5
        //6.sqrt求开方
        double sqrt = Math.sqrt(-9.0);
        System.out.println(sqrt);//NaN
        //7.random随机数
        //random 返回的是 0<= x < 1 之间的一个随即小数
        //Math.random() * (b-a) 返回的是 0<= 数 <b-a
        //取整的时候double 转 int 只转前面部分
        //例如 取10 - 12的随机数
        for(int i = 0;i < 10;i++){
            System.out.println((int)(Math.random() * (12-10+1) + 10));
        }
        //8.max.min 返回最大值，最小值
        double min = Math.min(2.3,5.9);
        int max = Math.max(65,78); 
    }
}
```

### Arrays类

![image-20211219170856504](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219170856504.png)

![image-20220527144511353](E:\大学\学习资料\笔记\pictures\image-20220527144511353.png)

sort排序底层逻辑

![image-20220527160348824](E:\大学\学习资料\笔记\pictures\image-20220527160348824.png)

![image-20220527171208647](E:\大学\学习资料\笔记\pictures\image-20220527171208647.png)

![image-20220527171247256](E:\大学\学习资料\笔记\pictures\image-20220527171247256.png)

```java
public class 排序 {
    public static void main(String[] args) {
        Integer[] arr = new Integer[]{0,9,6,49,-1,-9,-8};
        System.out.println(Arrays.toString(arr));
        //默认升序排列
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
        Arrays.sort(arr, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1;
            }
        });
        System.out.println(Arrays.toString(arr));
    }
}
```

![image-20220527162639241](E:\大学\学习资料\笔记\pictures\image-20220527162639241.png)

![image-20220527162924709](E:\大学\学习资料\笔记\pictures\image-20220527162924709.png)

![image-20220527163055438](E:\大学\学习资料\笔记\pictures\image-20220527163055438.png)

![image-20220527163137583](E:\大学\学习资料\笔记\pictures\image-20220527163137583.png)

![image-20220527164030840](E:\大学\学习资料\笔记\pictures\image-20220527164030840.png)

排序练习

```java
@SuppressWarnings("all")
public class Main {
    public static void main(String[] args) {
        Book[] books = new Book[4];
        books[0] = new Book("红楼梦",100);
        books[1] = new Book("金瓶梅新版", 90);
        books[2] = new Book("青年文摘2022", 5);
        books[3] = new Book("java从入门到放弃", 300);

        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book o1, Book o2) {
                return o2.getPrice() - o1.getPrice() ;
            }});
        System.out.println(Arrays.toString(books));

        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book o1, Book o2) {
                return o1.getPrice() - o2.getPrice();
            }
        });
        System.out.println(Arrays.toString(books));

        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book o1, Book o2) {
                return o1.getLength() - o2.getLength();
            }
        });
        System.out.println(Arrays.toString(books));
    }
}
```

![image-20220527171544152](E:\大学\学习资料\笔记\pictures\image-20220527171544152.png)

### System类

#### 常见方法

![image-20220527171755432](E:\大学\学习资料\笔记\pictures\image-20220527171755432.png)

![image-20220527175044209](E:\大学\学习资料\笔记\pictures\image-20220527175044209.png)

![image-20220527175600777](E:\大学\学习资料\笔记\pictures\image-20220527175600777.png)

### 大数据处理方案（BigInteger & BigDecimal）

#### 应用场景

![image-20220527175856118](E:\大学\学习资料\笔记\pictures\image-20220527175856118.png)

#### 方法

![image-20220527180239980](E:\大学\学习资料\笔记\pictures\image-20220527180239980.png)

#### 整数加减乘除

![image-20220527180423305](E:\大学\学习资料\笔记\pictures\image-20220527180423305.png)

![image-20220527180803549](E:\大学\学习资料\笔记\pictures\image-20220527180803549.png)

### 日期类

#### Date类 

![image-20220527201121624](E:\大学\学习资料\笔记\pictures\image-20220527201121624.png)

![image-20220527203050248](E:\大学\学习资料\笔记\pictures\image-20220527203050248.png)

![image-20220527203114896](E:\大学\学习资料\笔记\pictures\image-20220527203114896.png)

![image-20220527203133525](E:\大学\学习资料\笔记\pictures\image-20220527203133525.png)

```java
public class Date_lei {
    public static void main(String[] args) {
        Date d1 = new Date();
        System.out.println(d1);

        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss E");
        String format = sdf.format(d1);
        System.out.println(format);
    }
}
```

#### Calendar类

![image-20220527204220193](E:\大学\学习资料\笔记\pictures\image-20220527204220193.png)

![image-20220527204552892](E:\大学\学习资料\笔记\pictures\image-20220527204552892.png)

![image-20220527205009499](E:\大学\学习资料\笔记\pictures\image-20220527205009499.png)

#### 第三代日期类

![image-20220527205147232](E:\大学\学习资料\笔记\pictures\image-20220527205147232.png)

![image-20220527205203988](E:\大学\学习资料\笔记\pictures\image-20220527205203988.png)

![image-20220527205619042](E:\大学\学习资料\笔记\pictures\image-20220527205619042.png)

![image-20220527205856082](E:\大学\学习资料\笔记\pictures\image-20220527205856082.png)

![image-20220527210128304](E:\大学\学习资料\笔记\pictures\image-20220527210128304.png)

![image-20220527210307016](E:\大学\学习资料\笔记\pictures\image-20220527210307016.png)

![image-20220527210635734](E:\大学\学习资料\笔记\pictures\image-20220527210635734.png)



# 集合

## 理解和好处

![image-20220514150734375](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514150734375.png)

## 集合的框架体系

![image-20220514150949761](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514150949761.png)

 ![image-20220514203410792](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514203410792.png)



![image-20220514204526088](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514204526088.png)

## Collection接口常用方法

### 增删改查

![image-20220514210113232](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514210113232.png)



```java
public class Test {
    public static void main(String[] args) {
        List list = new ArrayList();
//        add:添加单个元素
        list.add("jack");
        list.add(10);//list.add(new Integer(10))
        list.add(true);
        System.out.println("list = " + list);
//        remove:删除指定元素
        list.remove(0);//删除第一个元素
        list.remove(true);//指定删除某一葛元素
        list.remove(new Integer(10));
        System.out.println("list = " + list);
//        contains:查找元素是否存在
        list.add("jack");
        System.out.println(list.contains("jack"));
//        size:获取元素个数
        System.out.println(list.size());
//        isEmpty:判断是否为空
        System.out.println(list.isEmpty());
//        clear:清空
        list.clear();
        System.out.println("list = " + list);
//        addAll:添加多个元素
        list.add("jack");
        list.add("nihao");
        List list2 = new ArrayList();
        list2.addAll(list);
        System.out.println("list2 = " + list2);
//        containsAll:查找多个元素是否都存在
        System.out.println(list2.containsAll(list));
//        removeAll:删除多个元素
        list.removeAll(list2);
        System.out.println(list);
//        说明:以ArrayList实现类来演示.

    }
}
```

### 遍历元素方式1

![image-20220514213027934](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514213027934.png)

 ![image-20220514215746616](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514215746616.png)



```java
public class Test1 {
    public static void main(String[] args) {
        Collection col = new ArrayList();

        col.add(new Book("三国演义","罗贯中",10.1));
        col.add(new Book("西游记","吴承恩",5.1));
        col.add(new Book("红楼梦","",34.6));

        // System.out.println( "col=" + col);
        //希望能够遍历col集合
        //1.先得到col对应得迭代器
        Iterator iterator = col.iterator();
        //2.使用while循环遍历
        while(iterator.hasNext()){
            //返回下一个元素，类型是Object
            Object next = iterator.next();
            System.out.println("obj = " + next);
        }
        //快捷键，快速生成itit
        //显示所有快捷键得跨界见 ctrl + j
        while (iterator.hasNext()) {
            Object obj =  iterator.next();
            System.out.println("aj=" + obj);
        }
        //3.当退出while循环后，这时iterator迭代器指向最后得元素
        iterator.next();//抛出一场NoSuch。。。
        //4.如果想再次遍历，重置迭代器
        iterator = col.iterator();
        while (iterator.hasNext()) {
            Object next =  iterator.next();
            System.out.println(next);
        }
    }
}

class Book{
    String name;
    String author;
    double price;

    public Book(String name, String author, double price) {
        this.name = name;
        this.author = author;
        this.price = price;
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", author='" + author + '\'' +
                ", price=" + price +
                '}';
    }
}
```

### 遍历元素方式2

![image-20220514221020538](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220514221020538.png)

```java
public class Test3 {
    public static void main(String[] args) {
        Collection col = new ArrayList();

        col.add(new Book("三国演义","罗贯中",10.1));
        col.add(new Book("西游记","吴承恩",5.1));
        col.add(new Book("红楼梦","",34.6));

        //使用增强for
        //底层仍然是迭代器
        //理解成简化版得 迭代器遍历
        //快捷方式 I
        
        for(Object book : col){
            System.out.println("book=" + book);
        }
    }
}
```

### 遍历练习

```java
public class practice {
    public static void main(String[] args) {
        Collection col = new ArrayList();

        col.add(new Dog("dog1",15));
        col.add(new Dog("dog2",16));
        col.add(new Dog("dog3",17));


        //  迭代器遍历
        System.out.println("迭代器遍历");
        Iterator iterator = col.iterator();
        while(iterator.hasNext()){
            Object list = iterator.next();
            System.out.println(list);
        }
        //for增强遍历
        System.out.println("for增强遍历");
        for(Object dog : col){
            System.out.println(dog);
        }

    }
}

class Dog{
    private String name;
    private int age;

    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

## List接口常用方法

<img src="C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220515165347602.png" alt="image-20220515165347602" style="zoom:67%;" />

```java
public class list_ {
    public static void main(String[] args) {
//      List集合类中元素有序(即添加顺序和取出顺序一致)、且可重复[案例]
        List list = new ArrayList();
        list.add("jack");
        list.add("jim");
        list.add("wkn");
        list.add("wkn");
        System.out.println("list=" + list);
        //List集合中的每个元素都有其对应的顺序索引，即支持索引
        //索引是从0开始的
        System.out.println(list.get(1));
    }
}
```

### 增删改查

![image-20220515192329764](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220515192329764.png)

```java
public class ListMethod {
    public static void main(String[] args) {
        List list = new ArrayList();
        list.add("wkn");
        list.add("h");
        //add(int index, Object ele):在index位置插入els元素
        list.add(1,"ljw");
        System.out.println(list);
        //boolean addAll(int index, Collection eles):在index位置开始将eles中的所有元素添加进来
        List list2 = new ArrayList();
        list2.add("111");
        list2.add("222");
        list2.addAll(2,list);
        System.out.println(list2);
        //get
        //indexOf(Object obj):返回obj在集合中首次出现的位置
        //lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
        list.add("wkn");
        System.out.println(list);
        System.out.println(list.indexOf("wkn"));
        System.out.println(list.lastIndexOf("wkn"));
        //remove(int index):移除指定index位置的元素，并返回此元素
        System.out.println(list);
        list.remove(0);
        System.out.println(list);
        //set(int index, Object ele):设置指定index位置的元素ele，相当于是替换
        list.set(2,"sxy");
        //subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合
        //  fromIndex<=  <toIndex
        System.out.println(list2);
        System.out.println( list2.subList(1,3));
    }
}

```

### 遍历方式3种

![image-20220515203028871](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220515203028871.png)

```java
public class ListPractice {
    public static void main(String[] args) {
        List list = new ArrayList();
        for(int i = 1;i <= 5;i++){
            list.add(i);
        }
        System.out.println(list);
        //迭代器遍历
        Iterator iterator = list.iterator();
        while (iterator.hasNext()) {
            Object num =  iterator.next();
            System.out.println(num);
        }
        //for增强便利
        for (Object o : list) {
            System.out.println(o);
        }
        //普通方法
        for(int i=0;i < list.size();i++){
            Object object = list.get(i);
            System.out.println(object);
        }
    }
}
```

### List排序

```java
public class Listp2 {
    public static void main(String[] args) {
        List list = new ArrayList();
        list.add(new Book("红楼梦","曹雪芹",10));
        list.add(new Book("西游记","吴承恩",10));
        list.add(new Book("水浒传","施耐庵" ,9));
        list.add(new Book("三国","罗贯中",80));
        list.add(new Book("西游记","吴承恩",10));

        //对集合进行排序
        sort(list);
        for (Object o :list) {
            System.out.println(o);
        }

    }
    public static void sort(List list){

        int listsize = list.size();
        for(int i = 0; i < listsize-1;i++){
            for(int j = 0;j < listsize - 1 - i;j++){
                Book book1 = (Book)list.get(j);
                Book book2 = (Book)list.get(j+1);
                if(book1.getPrice() > book2.getPrice()){
                    list.set(j, book2);
                    list.set(j+1, book1);
                }
            }
        }
    }
}
class Book{
    private String name;
    private String author;
    private double price;

    public Book(String name, String author, double price) {
        this.name = name;
        this.author = author;
        this.price = price;
    }

    @Override
    public String toString() {
        return "名称：" + name + "\t\t作者：" + author + "\t\t价格：" + price;
    }

    public String getName() {
        return name;
    }

    public String getAuthor() {
        return author;
    }

    public double getPrice() {
        return price;
    }
}
```

### ArrayList底层结构和源码解析

![image-20220515213030610](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220515213030610.png)

![image-20220515213147555](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220515213147555.png)

![image-20220516111302972](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516111302972.png)

![image-20220516111320699](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516111320699.png)

![image-20220516111353514](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516111353514.png)

![image-20220516111858485](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516111858485.png)

![image-20220516114526259](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516114526259.png)

### Vector底层源码结构和源码剖析

![image-20220516153448448](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516153448448.png)

![image-20220516153644906](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516153644906.png)

### LinkList底层结构

![image-20220516162245779](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516162245779.png)

 ![image-20220516162504040](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516162504040.png )

 ![image-20220516164735141](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516164735141.png)

## Set接口和常用方法

![image-20220516164938194](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516164938194.png)

![image-20220516165125566](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516165125566.png)

```java
public class set {
    public static void main(String[] args) {
        Set set = new HashSet();
        set.add("niu");
        set.add("bi");
        set.add("li");
        set.add("hai");
        set.add(null);
        set.add(null);
        System.out.println(set);
        //set接口实现类的对象（set接口对象）不能存放重复元素
        //set接口对象存放数据无序（添加顺序取出顺序不一致,但固定）
        //遍历1 使用迭代器
        Iterator iterator = set.iterator();
        while(iterator.hasNext()){
            Object o = iterator.next();
            System.out.println(o);
        }
        //遍历2 增强for循环
        for(Object o : set){
            System.out.println(o);
        }
    }
}
```

### HasSet

![image-20220516170712230](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516170712230.png)

 注意

![image-20220607154300193](E:\大学\学习资料\笔记\pictures\image-20220607154300193.png)

HashSet底层机制

![image-20220516174904787](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516174904787.png)

源码解读

![image-20220607160212216](E:\大学\学习资料\笔记\pictures\image-20220607160212216.png)

第一个add

![image-20220607160155662](E:\大学\学习资料\笔记\pictures\image-20220607160155662.png)

![image-20220607160237177](E:\大学\学习资料\笔记\pictures\image-20220607160237177.png)

![image-20220607160402059](E:\大学\学习资料\笔记\pictures\image-20220607160402059.png)

第二个add

![image-20220607205324511](E:\大学\学习资料\笔记\pictures\image-20220607205324511.png)

![image-20220607205518296](E:\大学\学习资料\笔记\pictures\image-20220607205518296.png)

![image-20220607195413653](E:\大学\学习资料\笔记\pictures\image-20220607195413653.png)

![image-20220607195932939](E:\大学\学习资料\笔记\pictures\image-20220607195932939.png)

![image-20220607200755617](E:\大学\学习资料\笔记\pictures\image-20220607200755617.png)

### TreeSet

可排序

![image-20220709173601938](E:\大学\学习资料\笔记\pictures\image-20220709173601938.png)

 treeset必须实现Comparator接口，不然会报错

### LinkedHashSet

![image-20220705174139245](E:\大学\学习资料\笔记\pictures\image-20220705174139245.png)

 ![image-20220705174502396](E:\大学\学习资料\笔记\pictures\image-20220705174502396.png)



## Map接口和常用方法

![image-20220516182238043](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516182238043.png)

```java
public class MapMethod {
    public static void main(String[] args) {
        Map map = new HashMap();
        //添加put k-v
        map.put(1,"ni");
        map.put(2,"shi");
        map.put(3,"hao");
        map.put(4,"ren");
        System.out.println(map);
        //当有相同的k，就等价于替换
        map.put(4,"shushu");
        System.out.println(map);
        //获取k对应的v
        System.out.println(map.get(1));
    }
}
```

![image-20220516195516978](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516195516978.png)

当把HashMap$Node对象存放到entrySet对象，这样方便遍历，提供了getKey()和getValue()方法

![image-20220705182123940](E:\大学\学习资料\笔记\pictures\image-20220705182123940.png)

### Map常用方法

![image-20220516200437364](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516200437364.png)

![image-20220516200450477](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516200450477.png)

```java
public class MapMethod {
    public static void main(String[] args) {
        Map s = new HashMap();
        //put 添加k-v
        s.put(1,"ni");
        s.put(2,"hao");
        s.put(null,"shi");
        s.put(4,"jie");
        s.put("as","sad");
        System.out.println(s);
        //remove 根据k 删除v
        s.remove("as");
        System.out.println(s);
        //get 根据k 获取v
        System.out.println(s.get(4));
        //size 获取元素个数
        System.out.println(s.size());
        //isEmpty 判断个数是否为0
        System.out.println(s.isEmpty());
        //clear 清除
        s.clear();
        System.out.println(s);
        //containsKey 查找键是否存在
        System.out.println(s.containsKey(2));

    }
}
```

### Map遍历六大方式

![image-20220516202717042](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20220516202717042.png)

```java
public class MapAll {
    public static void main(String[] args) {
        Map map = new HashMap();
        //put 添加k-v
        map.put(1,"ni");
        map.put(2,"hao");
        map.put(null,"shi");
        map.put(4,"jie");
        map.put("as","sad");
        System.out.println(map);
        //第一组 先取出所有的key，通过key 取出对应的value
        Set keyset = map.keySet();
        //(1)增强for
        for (Object key : keyset) {
            System.out.println(key + ":" + map.get(key));
        }
        //(2)迭代器
        Iterator iterator = keyset.iterator();
        while(iterator.hasNext()){
            Object key = iterator.next();
            System.out.println(key + ":" + map.get(key));
        }
        //第二组 把所有的values取出
        Collection values = map.values();
        //可以使用所有Colltion使用的遍历方法
        //(1)增强for
        //(2)迭代器
        //第三组 通过EntrySet来获取k-v
        Set entrySet = map.entrySet();
        //(1)增强for
        for (Object entry : entrySet) {
            //将entry 转成 Map.Entry
            Map.Entry m = (Map.Entry)entry;
            System.out.println(m.getKey() + ":" + m.getValue());
        }
        //(2)迭代器
        Iterator iterator1 = entrySet.iterator();
        while (iterator.hasNext()) {
            Object entry =  iterator.next();
            //向下转型
            Map.Entry m = (Map.Entry)entry;
            System.out.println(m.getKey() + ":" + m.getValue());
        }


    }
}
```

### HashMap小结

![image-20220708011019773](E:\大学\学习资料\笔记\pictures\image-20220708011019773.png)

### TreeMap

先封装到entry对象

然后再添加，调用Comparatpr

### HashTable

![image-20220708012000979](E:\大学\学习资料\笔记\pictures\image-20220708012000979.png)

### Properties

![image-20220708012757220](E:\大学\学习资料\笔记\pictures\image-20220708012757220.png)

## 总结

![image-20220709172720639](E:\大学\学习资料\笔记\pictures\image-20220709172720639.png)

## Collections工具类

![image-20220709192927645](E:\大学\学习资料\笔记\pictures\image-20220709192927645.png)

```java
package Set;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

/**
 * @author wkn
 * @version 1.0
 **/
public class Collecttionssss {
    public static void main(String[] args) {
        List list = new ArrayList();

        list.add("ni");
        list.add("hao");
        list.add("niu");
        list.add("bi");
        System.out.println(list);
        //reverse(List):反转List中元素的顺序
        Collections.reverse(list);
        System.out.println(list);
        //shuffle(List):对List集合元素进行随机排序
        Collections.shuffle(list);
        System.out.println(list);
        //sort(List):根据元素的自然顺序进行升序排序
        Collections.sort(list);
        System.out.println(list);
        //sort(List,Comparator):根据指定顺序排序
        Collections.sort(list, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                return ((String)o2).length() - ((String)o1).length();
            }
        });
        System.out.println(list);
        //swap(list,int,int):将指定list集合中的i和j元素进行交换
        Collections.swap(list,0,3);
        System.out.println(list);
    }
}
```

![image-20220710221625623](E:\大学\学习资料\笔记\pictures\image-20220710221625623.png)

```java

        Collections.sort(list);
        System.out.println(list);
        //Object max(Collection):根据元素自然顺序，返回给定集合中的最大元素
        System.out.println(Collections.max(list));
        //Object min(Collection):根据。。返回最小
        System.out.println(Collections.min(list));
        //int frequency(Collection,Object):返回指定集合中指定元素出现次数
        System.out.println(Collections.frequency(list,"ni"));
        //void copy(list dest,list srt):将src中的内容复制到dest中

        for(int i=0;i < list.size();i++){
            list1.add("111");
        }
        Collections.copy(list,list1);
        System.out.println(list);
        //boolean replaceAll(List list,Object oldVal, Object newVal):使用新值替换List对象的所有旧值
        Collections.replaceAll(list,"111","666");
        System.out.println(list);
```

# 泛型

好处：

![image-20220712191502456](E:\大学\学习资料\笔记\pictures\image-20220712191502456.png)

![image-20220712192740911](E:\大学\学习资料\笔记\pictures\image-20220712192740911.png)

## 泛型说明

![image-20220712192944416](E:\大学\学习资料\笔记\pictures\image-20220712192944416.png)

泛型的作用:

（1）可以在类声明时通过一个标识表示类中某个属性的类型

（2）或者是某个方法的返回值的类型，或者是参数类型

![image-20220712194154439](E:\大学\学习资料\笔记\pictures\image-20220712194154439-16576261153441.png)

![image-20220712194238094](E:\大学\学习资料\笔记\pictures\image-20220712194238094.png)

## 泛型语法

![image-20220712195100949](E:\大学\学习资料\笔记\pictures\image-20220712195100949.png)

![image-20220712200647217](E:\大学\学习资料\笔记\pictures\image-20220712200647217.png)

```java
package FanXing;

import java.util.HashMap;
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

/**
 * @author wkn
 * @version 1.0
 **/
public class Test2 {
    public static void main(String[] args) {
        //1.HashSet
        Set<Student> set = new HashSet<Student>();
        set.add(new Student("john",12));
        set.add(new Student("Jim",15));
        //遍历
        for(Student stu:set){
            System.out.println(stu.getName());
        }
        Iterator<Student> iterator = set.iterator();
        while (iterator.hasNext()) {
            Student stu = iterator.next();
            System.out.println(stu);
        }

        //HashMap
        HashMap<String,Student> hashMap = new HashMap<String,Student>();
        hashMap.put("John",new Student("john",12));
        hashMap.put("Jim",new Student("Jim",15));
        //遍历
        Set<String> keyset = hashMap.keySet();
        for(String key:keyset){
            System.out.println("key = " + key + " value = " + hashMap.get(key));
        }
        Iterator<String> iterator1 = keyset.iterator();
        while (iterator1.hasNext()) {
            String key =  iterator1.next();
            System.out.println("key = " + key + " value = " + hashMap.get(key));
        }
    }
}

class Student{
    private String name;
    private int age;

    public Student(String name,int age){
        this.name = name;
        this.age = age;
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

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

![image-20220712214927099](E:\大学\学习资料\笔记\pictures\image-20220712214927099.png)

### 注意事项和细节

![image-20220713143324386](E:\大学\学习资料\笔记\pictures\image-20220713143324386.png)

![image-20220713143709217](E:\大学\学习资料\笔记\pictures\image-20220713143709217.png)

![image-20220713143729772](E:\大学\学习资料\笔记\pictures\image-20220713143729772.png)

![image-20220713144011370](E:\大学\学习资料\笔记\pictures\image-20220713144011370.png)

等价于List<Object> = new ArrayList<>();

![image-20220713143922170](E:\大学\学习资料\笔记\pictures\image-20220713143922170.png)

## 自定义泛型

![image-20220713172808182](E:\大学\学习资料\笔记\pictures\image-20220713172808182.png)

![image-20220713185627484](E:\大学\学习资料\笔记\pictures\image-20220713185627484.png)

![image-20220713190438615](E:\大学\学习资料\笔记\pictures\image-20220713190438615.png)

![image-20220713190524647](E:\大学\学习资料\笔记\pictures\image-20220713190524647.png)

![image-20220713195810155](E:\大学\学习资料\笔记\pictures\image-20220713195810155.png)

## 泛型的继承和通配符

![image-20220713200021284](E:\大学\学习资料\笔记\pictures\image-20220713200021284.png)

![image-20220713195959851](E:\大学\学习资料\笔记\pictures\image-20220713195959851.png)

## 测试框架JUnit

![image-20220713200824197](E:\大学\学习资料\笔记\pictures\image-20220713200824197.png)

# Java绘图坐标体系

![image-20220714163258052](E:\大学\学习资料\笔记\pictures\image-20220714163258052.png)

![image-20220714163608638](E:\大学\学习资料\笔记\pictures\image-20220714163608638.png)

## 画一个圆

```java
package Draw;

import javax.swing.*;
import java.awt.*;

/**
 * @author wkn
 * @version 1.0
 **/
public class DrawCircle extends JFrame{
    private MyPannel myPannel = null;//先声明一个画板
    
    public DrawCircle(){//构造器中 创建画板、添加画报到JFrame框架并设置参数
        myPannel = new MyPannel();

        this.add(myPannel);
        this.setSize(1000,1000);
        this.setVisible(true);
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new DrawCircle();//创建类
    }
}

class MyPannel extends JPanel{

    @Override//重写paint方法，传入画笔类
    public void paint(Graphics g) {
        super.paint(g);

        g.drawOval(10,10,200,200);
    }

```

![image-20220714164615793](E:\大学\学习资料\笔记\pictures\image-20220714164615793.png)



![image-20220714165500682](E:\大学\学习资料\笔记\pictures\image-20220714165500682.png)

![image-20220714165522222](E:\大学\学习资料\笔记\pictures\image-20220714165522222.png)

![image-20220714165632549](E:\大学\学习资料\笔记\pictures\image-20220714165632549.png)

![image-20220714164927552](E:\大学\学习资料\笔记\pictures\image-20220714164927552.png)

## Graphics类

![image-20220714172647618](E:\大学\学习资料\笔记\pictures\image-20220714172647618.png)

![image-20220714174414275](E:\大学\学习资料\笔记\pictures\image-20220714174414275.png)

![image-20220714175713433](E:\大学\学习资料\笔记\pictures\image-20220714175713433.png)

# Java事件处理机制

![image-20220714210158787](E:\大学\学习资料\笔记\pictures\image-20220714210158787.png)

## 让小球上下移动

![image-20220714210518841](E:\大学\学习资料\笔记\pictures\image-20220714210518841.png)

![image-20220714210550002](E:\大学\学习资料\笔记\pictures\image-20220714210550002.png)

![image-20220714210559833](E:\大学\学习资料\笔记\pictures\image-20220714210559833.png)

![image-20220714210622258](E:\大学\学习资料\笔记\pictures\image-20220714210622258.png)

![image-20220714210841674](E:\大学\学习资料\笔记\pictures\image-20220714210841674.png)

![image-20220714211004577](E:\大学\学习资料\笔记\pictures\image-20220714211004577.png)

![image-20220714211422080](E:\大学\学习资料\笔记\pictures\image-20220714211422080.png)

## 说明

![image-20220714213348025](E:\大学\学习资料\笔记\pictures\image-20220714213348025.png)

![image-20220714213516672](E:\大学\学习资料\笔记\pictures\image-20220714213516672.png)

![image-20220714213605822](E:\大学\学习资料\笔记\pictures\image-20220714213605822-16578057671751.png)

![image-20220714213733798](E:\大学\学习资料\笔记\pictures\image-20220714213733798.png)

![image-20220714213838477](E:\大学\学习资料\笔记\pictures\image-20220714213838477.png)

# 线程（基础）

## 相关概念

![image-20220715112609391](E:\大学\学习资料\笔记\pictures\image-20220715112609391.png)

![image-20220715112703798](E:\大学\学习资料\笔记\pictures\image-20220715112703798.png)

![image-20220715113017085](E:\大学\学习资料\笔记\pictures\image-20220715113017085.png)

![image-20220715113201334](E:\大学\学习资料\笔记\pictures\image-20220715113201334.png)

![image-20220715113355390](E:\大学\学习资料\笔记\pictures\image-20220715113355390.png)

## 基本使用

![image-20220715114131253](E:\大学\学习资料\笔记\pictures\image-20220715114131253.png)

![image-20220715114221669](E:\大学\学习资料\笔记\pictures\image-20220715114221669.png)

### 1.继承Thread类

![image-20220715114509390](E:\大学\学习资料\笔记\pictures\image-20220715114509390.png)

```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class t1 {
    public static void main(String[] args) {
        Cat cat = new Cat();
        cat.start();
    }
}

class Cat extends Thread{

    int times = 0;
    @Override
    public void run() {
        while(true){
            System.out.println("nihao" + (++times) );

            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            if(times == 9){
                break;
            }
        }
    }
}
```

![image-20220715120302846](E:\大学\学习资料\笔记\pictures\image-20220715120302846.png)

主线程执行完毕，子线程仍然可以执行

![image-20220715120516724](E:\大学\学习资料\笔记\pictures\image-20220715120516724.png)

![image-20220715120625783](E:\大学\学习资料\笔记\pictures\image-20220715120625783.png)

start源码追析

![image-20220715121052319](E:\大学\学习资料\笔记\pictures\image-20220715121052319.png)

![image-20220715120959671](E:\大学\学习资料\笔记\pictures\image-20220715120959671.png)

![image-20220715121201087](E:\大学\学习资料\笔记\pictures\image-20220715121201087.png)

### 2.实现Runable接口

![image-20220715121337901](E:\大学\学习资料\笔记\pictures\image-20220715121337901.png)

```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class t2 {
    public static void main(String[] args) {
        sayhihi sayhihi = new sayhihi();
        Thread thread = new Thread(sayhihi);
        thread.start();

    }
}
class sayhihi implements Runnable{

    @Override
    public void run() {
        int time = 0;
        while (true) {
            System.out.println("666" + (++time) + "xiancheng=" + Thread.currentThread().getName());
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            if(time == 10){     
                break;
            }
        }
    }
}
```

### 3.多个线程使用

![image-20220715161016071](E:\大学\学习资料\笔记\pictures\image-20220715161016071.png)

![image-20220715191817148](E:\大学\学习资料\笔记\pictures\image-20220715191817148.png)

![image-20220715202059396](E:\大学\学习资料\笔记\pictures\image-20220715202059396.png)

```java
package XianCheng;
/**
 * @author wkn
 * @version 1.0
 **/
public class duoxiancheng {
    public static void main(String[] args) {
        T1 t1 = new T1();
        T2 t2 = new T2();
        Thread thread = new Thread(t1);
        Thread thread1 = new Thread(t2);

        thread.start();
        thread1.start();
    }
}

class T1 implements Runnable{

    @Override
    public void run() {
        while (true){
            System.out.println("我是1 "+Thread.currentThread().getName());
            try {
                Thread.sleep(800);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

class T2 implements Runnable{

    @Override
    public void run() {
        while (true){
            System.out.println("我是2 "+Thread.currentThread().getName());
            try {
                Thread.sleep(800);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

## Thread VS Runnable区别

![image-20220715202326183](E:\大学\学习资料\笔记\pictures\image-20220715202326183.png)

### 售票超卖问题

![image-20220715214255826](E:\大学\学习资料\笔记\pictures\image-20220715214255826.png)

## 线程终止

![image-20220715214722039](E:\大学\学习资料\笔记\pictures\image-20220715214722039.png)

![image-20220715215109219](E:\大学\学习资料\笔记\pictures\image-20220715215109219.png)

![image-20220715215157242](E:\大学\学习资料\笔记\pictures\image-20220715215157242.png)

```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class test2{
    public static void main(String[] args) {
        sayhihi sayhihi = new sayhihi();
        Thread thread33 = new Thread(sayhihi);
        thread33.start();
        System.out.println("main线程休眠10s");

        try {
            Thread.sleep(10 * 1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        sayhihi.setLoop(false);
    }
}
class sayhihi implements Runnable{

    boolean loop = true;
    @Override
    public void run() {
        int time = 0;
        while (loop) {
            System.out.println("666" + (++time) + "xiancheng=" + Thread.currentThread().getName());
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            if(time == 10){
                break;
            }
        }
    }

    public void setLoop(boolean loop) {
        this.loop = loop;
    }
}
```



## 线程常用方法

![image-20220715215349068](E:\大学\学习资料\笔记\pictures\image-20220715215349068.png)

![image-20220715222638742](E:\大学\学习资料\笔记\pictures\image-20220715222638742.png)

![image-20220715222945546](E:\大学\学习资料\笔记\pictures\image-20220715222945546.png)

![image-20220715223252878](E:\大学\学习资料\笔记\pictures\image-20220715223252878.png)

```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class Method {
    public static void main(String[] args) {
        Dog dog = new Dog();
        Thread thread = new Thread(dog);

        thread.setName("旺财");
        thread.setPriority(Thread.MIN_PRIORITY);
        System.out.println(thread.getPriority());
        thread.start();

        while (true) {
            try {
                Thread.sleep(5000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            thread.interrupt();
        }
    }
}

class Dog implements Runnable{

    boolean loop = true;
    @Override
    public void run() {
        int count = 0;
        while(loop){
            System.out.println(Thread.currentThread().getName()+"正在吃屎"+(++count));
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println(Thread.currentThread().getName()+"吃屎被打断");
            }
        }
    }
}
```

![image-20220715223606943](E:\大学\学习资料\笔记\pictures\image-20220715223606943.png)

join插队(一定成功)

![image-20220716162031340](E:\大学\学习资料\笔记\pictures\image-20220716162031340.png)

yield礼让(不一定成功)

![image-20220716162316911](E:\大学\学习资料\笔记\pictures\image-20220716162316911.png)

![image-20220716170620773](E:\大学\学习资料\笔记\pictures\image-20220716170620773.png)



```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class Xianchengchadui {
    public static void main(String[] args) throws InterruptedException {
        son_thread son = new son_thread();
//        Thread zhuxian = new Thread();
        Thread zixian = new Thread(son);

//        zhuxian.start();
        for(int i=1;i<=10;i++){
            Thread.sleep(1000);
            System.out.println("hi "+ i);
            if(i == 5){
                zixian.start();
                zixian.join();
            }
        }
        System.out.println("主线程结束");
    }
}

class son_thread implements Runnable{

    @Override
    public void run() {
        int count = 0;
        while (true){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("hello"+" "+ (++count));
            if(count == 10){
                System.out.println("子线程结束");
                break;
            }
        }
    }
}
```

![image-20220716171055932](E:\大学\学习资料\笔记\pictures\image-20220716171055932.png)

![image-20220716171458808](E:\大学\学习资料\笔记\pictures\image-20220716171458808.png)

## 线程的生命周期

![image-20220716171623758](E:\大学\学习资料\笔记\pictures\image-20220716171623758.png)

![image-20220716171743835](E:\大学\学习资料\笔记\pictures\image-20220716171743835.png)

![image-20220716172309038](E:\大学\学习资料\笔记\pictures\image-20220716172309038.png)

## 线程同步机制

![image-20220716172406132](E:\大学\学习资料\笔记\pictures\image-20220716172406132.png)

![image-20220716175402350](E:\大学\学习资料\笔记\pictures\image-20220716175402350.png)

```java
package XianCheng;

/**
 * @author wkn
 * @version 1.0
 **/
public class XianCheng_tongbu {
    public static void main(String[] args) {
        SaleTickets saleTickets = new SaleTickets();
        Thread thread = new Thread(saleTickets);
        Thread thread1 = new Thread(saleTickets);
        Thread thread2 = new Thread(saleTickets);

        thread.start();
        thread1.start();
        thread2.start();

        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("票已卖完");
    }
}

class SaleTickets implements Runnable{

    private static int tickets_num = 2000;
    private boolean loop = true;

    public synchronized void Sale() {
        if(tickets_num <=0 ){
            loop = false;
            return;
        }
             try {
                 Thread.sleep(1);
             } catch (InterruptedException e) {
                 e.printStackTrace();
             }
             tickets_num--;
             System.out.println(Thread.currentThread().getName() + "卖出," +"还剩" + tickets_num + "张");
    }
    @Override
    public void run() {
        while(loop) {
            Sale();
        }
    }
}

```

### 同步原理

![image-20220716231324902](E:\大学\学习资料\笔记\pictures\image-20220716231324902.png)

![image-20220716231425034](E:\大学\学习资料\笔记\pictures\image-20220716231425034.png)

![image-20220716231433399](E:\大学\学习资料\笔记\pictures\image-20220716231433399.png)

### 互斥锁

![image-20220716231512340](E:\大学\学习资料\笔记\pictures\image-20220716231512340.png)

![image-20220716231746455](E:\大学\学习资料\笔记\pictures\image-20220716231746455.png)

![image-20220716232006664](E:\大学\学习资料\笔记\pictures\image-20220716232006664.png)

![image-20220716232040526](E:\大学\学习资料\笔记\pictures\image-20220716232040526.png)

锁同一个对象

![image-20220716232131809](E:\大学\学习资料\笔记\pictures\image-20220716232131809.png)

![image-20220716232229262](C:\Users\12518\Desktop\语言\image-20220716232229262.png)

![image-20220716233118292](E:\大学\学习资料\笔记\pictures\image-20220716233118292.png)

![image-20220716233135106](E:\大学\学习资料\笔记\pictures\image-20220716233135106.png)

```java
//代码块版
class SaleTickets implements Runnable{

    private static int tickets_num = 2000;
    private boolean loop = true;

    public synchronized void Sale() {
        synchronized (this){
            if (tickets_num <= 0) {
                loop = false;
                return;
            }
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            tickets_num--;
            System.out.println(Thread.currentThread().getName() + "卖出," + "还剩" + tickets_num + "张");
        }
    }
    @Override
    public void run() {
        while(loop) {
            Sale();
        }
    }
}
```

### 线程死锁

![image-20220717091228919](E:\大学\学习资料\笔记\pictures\image-20220717091228919.png)

![image-20220717092857919](E:\大学\学习资料\笔记\pictures\image-20220717092857919.png)

###  释放锁

![image-20220717093717763](E:\大学\学习资料\笔记\pictures\image-20220717093717763.png)

![image-20220717093754895](E:\大学\学习资料\笔记\pictures\image-20220717093754895.png)

#  IO流 

![image-20211219173215409](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219173215409.png)

![image-20220722174209542](E:\大学\学习资料\笔记\pictures\image-20220722174209542.png)

![image-20211219190349334](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219190349334.png)



## 常用的文件操作

### 创建文件

![image-20211219190709150](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219190709150.png)

![image-20211219191018090](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219191018090.png)

![image-20211219191220049](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219191220049.png)

![image-20211219191558637](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219191558637.png) 

```java
import org.junit.jupiter.api.Test;

import java.io.File;
import java.io.IOException;

/**
 * @author wkn
 * @version 1.0
 **/
public class Creat_File {
    public static void main(String[] args) {

    }

    @Test
    //方式一 new File(String pathname)
    public void create01(){
        String filePath = "D:\\WorkSpace\\JavaProject\\IO\\src\\test1.txt";
        File file = new File(filePath);
        try {
            file.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    @Test
    //方式二 new File(File parent,String child)
    public void create02(){
        File parent = new File("D:\\WorkSpace\\JavaProject\\IO\\src");
        String child = "test2.txt";
        File file = new File(parent,child);
        try {
            file.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    @Test
    //方式三new File(String parent,String child)
    public void create03(){
        String parent = "D:\\WorkSpace\\JavaProject\\IO\\src";
        String child ="test3.txt";
        File file = new File(parent,child);
        try {
            file.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```



### 获取文件信息

![image-20211219192318180](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219192318180.png)

### 目录的操作和文件的删除

![image-20211219192756034](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219192756034.png)

#### 文件删除

![image-20220722212516640](E:\大学\学习资料\笔记\pictures\image-20220722212516640.png)

#### 目录删除

在Java编程中，目录也被当作文件

![image-20220722212724876](E:\大学\学习资料\笔记\pictures\image-20220722212724876.png)

#### 创建目录

一级目录用mkdir() 

多级目录用mkdirs()

![image-20211219193742052](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219193742052.png)

![image-20211219193921893](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219193921893.png)

## IO流原理

![image-20211219194356104](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219194356104.png)

![image-20211219194623513](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219194623513.png)

![image-20211219194831653](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219194831653.png)

![image-20220722213725039](E:\大学\学习资料\笔记\pictures\image-20220722213725039.png)

![image-20220722213745147](E:\大学\学习资料\笔记\pictures\image-20220722213745147.png)

## 字节流

![image-20211219200542535](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219200542535.png)

![image-20211219202834572](C:\Users\12518\AppData\Roaming\Typora\typora-user-images\image-20211219202834572.png)

### FileInputStream

![image-20220722214419442](E:\大学\学习资料\笔记\pictures\image-20220722214419442.png)

![image-20220724134900219](E:\大学\学习资料\笔记\pictures\image-20220724134900219.png)

```java
    @Test
    public void readFile() throws IOException {
        byte[] buf = new byte[8];
        int readLen = 0;
        FileInputStream fileInputStream = null;
        String path = "D:\\WorkSpace\\JavaProject\\IO\\src\\Input_Stream\\hello.txt";

        fileInputStream = new FileInputStream(path);
        while((readLen = fileInputStream.read(buf)) != -1){
            System.out.print(new String(buf,0,readLen));
        }
        fileInputStream.close();
    }
}
```

### FileOutputStream

![image-20220724163148199](E:\大学\学习资料\笔记\pictures\image-20220724163148199.png)

![image-20220724163343506](E:\大学\学习资料\笔记\pictures\image-20220724163343506.png)

```java
@Test
    public void writeFile() throws IOException {
        String path1 = "D:\\WorkSpace\\JavaProject\\IO\\src\\Output_Stream\\new1.txt";
        String path2 = "D:\\WorkSpace\\JavaProject\\IO\\src\\Output_Stream\\new2.txt";
        String content = "hello";
        //覆盖原来文本
        FileOutputStream file_fugai = new FileOutputStream(path1);
        //加入文本
        FileOutputStream file_jia = new FileOutputStream(path2,true);
        //三种写入文件方法
        file_fugai.write('S');
        file_fugai.write(content.getBytes());
        file_fugai.write(content.getBytes(),0,3);

        file_jia.write('S');
        file_jia.write(content.getBytes());
        file_jia.write(content.getBytes(),0,3);
    }
```

###  文件拷贝

![image-20220724201212064](E:\大学\学习资料\笔记\pictures\image-20220724201212064.png)

```java
public class FileCopy {
    public static void main(String[] args) throws IOException {
        String input_path = "D:\\WorkSpace\\JavaProject\\IO\\src\\Output_Stream\\莫名其妙.png";
        String output_path = "D:\\WorkSpace\\JavaProject\\IO\\src\\Output_Stream\\测试.png";

        FileInputStream fileInputStream = new FileInputStream(input_path);
        FileOutputStream fileOutputStream = new FileOutputStream(output_path);

        byte[] buf = new byte[8];
        int bytesize = 0;

        while((bytesize=fileInputStream.read(buf)) != -1){
            fileOutputStream.write(buf,0,bytesize);
        }
        if(fileInputStream != null){
            fileInputStream.close();
            System.out.println("拷贝完成");
        }
    }
}
```

## 字符流

![image-20220724210614967](E:\大学\学习资料\笔记\pictures\image-20220724210614967.png)

### FileReader

![image-20220724210707503](E:\大学\学习资料\笔记\pictures\image-20220724210707503.png)

```java
public class FileReader_ {
    public static void main(String[] args) throws IOException {
        String filePath = "D:\\WorkSpace\\JavaProject\\IO\\src\\Reader_\\test.txt";
        int data = 0;
        int readLen = 0;
        char[] buf = new char[8];
        FileReader fileReader = new FileReader(filePath);
//        System.out.println("一个一个字符读");
//        while ((data = fileReader.read()) != -1){
//            System.out.print((char)data);
//        }
        System.out.println("一个一个字符数组读");
        while((readLen = fileReader.read(buf)) != -1){
            System.out.print(new String(buf,0,readLen));
        }
        

        if(fileReader != null){
            fileReader.close();
        }
    }
}
```

### FileWriter

![image-20220724211016584](E:\大学\学习资料\笔记\pictures\image-20220724211016584.png)

![image-20220724212939371](E:\大学\学习资料\笔记\pictures\image-20220724212939371.png)

```java
public class FileWriter_ {
    public static void main(String[] args) throws IOException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\Writer_\\new1.txt";
        String filepath1 = "D:\\WorkSpace\\JavaProject\\IO\\src\\Writer_\\new2.txt";
        char[] chars = {'n','b'};
        String str = "撒大大伟大发生的郭文贵";

        FileWriter fileWriter = new FileWriter(filepath);
        FileWriter fileWriter1 = new FileWriter(filepath1,true);

        fileWriter.write('H');
        fileWriter1.write('S');
        fileWriter.write(chars,0,1);
        fileWriter1.write("你好世界".toCharArray(),0,2);
        fileWriter1.write(str);
        fileWriter.write(str,0,2);

        if(fileWriter != null){
            fileWriter.close();
        }
        if(fileWriter1 != null){
            fileWriter1.close();
        }
    }
}
```

## 节点流和处理流

![image-20220725171301383](E:\大学\学习资料\笔记\pictures\image-20220725171301383.png)

节点流和处理流一览图

![image-20220725172716912](E:\大学\学习资料\笔记\pictures\image-20220725172716912.png)

节点流

![image-20220725171545752](E:\大学\学习资料\笔记\pictures\image-20220725171545752.png)

处理流

![image-20220725171847120](E:\大学\学习资料\笔记\pictures\image-20220725171847120.png)

节点流和处理流的区别和联系

![image-20220725173020689](E:\大学\学习资料\笔记\pictures\image-20220725173020689.png)

![image-20220725184328371](E:\大学\学习资料\笔记\pictures\image-20220725184328371.png)

## 处理流

### 字符处理流

![image-20220725184457001](E:\大学\学习资料\笔记\pictures\image-20220725184457001.png)

#### BufferedReader

![image-20220725185017313](E:\大学\学习资料\笔记\pictures\image-20220725185017313.png)

```java
public class BufferedReader_ {
    public static void main(String[] args) throws IOException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\Reader_\\test.txt";
        BufferedReader bufferedReader = new BufferedReader(new FileReader(filepath));
        String line;
        while((line = bufferedReader.readLine()) != null){
            System.out.println(line);
        }
    }
}
```

#### BufferedWriter

![image-20220725210406013](E:\大学\学习资料\笔记\pictures\image-20220725210406013.png)

```java
public class BufferedWriter_ {
    public static void main(String[] args) throws IOException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\Writer_\\buf_new1.txt";
        String content = "你好世界";
        BufferedWriter bufferedWriter = new java.io.BufferedWriter(new FileWriter(filepath,true));
        bufferedWriter.write(content);
        bufferedWriter.newLine();//换行符
        bufferedWriter.write(content);
        bufferedWriter.close();
    }
}
```

![image-20220725210557754](E:\大学\学习资料\笔记\pictures\image-20220725210557754.png)

### 字节处理流

![image-20220725212512508](E:\大学\学习资料\笔记\pictures\image-20220725212512508.png)

#### BufferedInputStream

#### BufferedOutputStream

![image-20220725212632035](E:\大学\学习资料\笔记\pictures\image-20220725212632035.png)

```java
public class Buffered_stream_copy {
    public static void main(String[] args) throws IOException {
        String input_path = "D:\\WorkSpace\\JavaProject\\IO\\src\\Writer_\\莫名其妙.png";
        String output_path = "D:\\WorkSpace\\JavaProject\\IO\\src\\Writer_\\test_pic.png";

        BufferedInputStream bufferedInputStream = new BufferedInputStream(new FileInputStream(input_path));
        BufferedOutputStream bufferedOutputStream = new BufferedOutputStream(new FileOutputStream(output_path));

        int readlen = 0;
        byte[] buf = new byte[1024];

        while((readlen = bufferedInputStream.read(buf)) != -1){
            bufferedOutputStream.write(buf,0,readlen);
        }

        if(bufferedInputStream != null){
            bufferedInputStream.close();
        }
        if(bufferedOutputStream != null){
            bufferedOutputStream.close();
        }
    }
}
```

### 对象流

![image-20220725214153796](E:\大学\学习资料\笔记\pictures\image-20220725214153796.png)

![image-20220725215058145](E:\大学\学习资料\笔记\pictures\image-20220725215058145.png)

![image-20220725215253708](E:\大学\学习资料\笔记\pictures\image-20220725215253708.png)

![image-20220725215336660](E:\大学\学习资料\笔记\pictures\image-20220725215336660.png)

#### ObjectOutputStream

![image-20220725220215233](E:\大学\学习资料\笔记\pictures\image-20220725220215233.png)

![image-20220725222400163](E:\大学\学习资料\笔记\pictures\image-20220725222400163.png)

#### ObjectInputStream

![image-20220725222539621](E:\大学\学习资料\笔记\pictures\image-20220725222539621.png)

![image-20220725223310809](E:\大学\学习资料\笔记\pictures\image-20220725223310809-16587595929091.png)

```java
public class ObjectInputStream_ {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\Object_\\data.dat";
        ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream(filepath));

        System.out.println(objectInputStream.readInt());
        System.out.println(objectInputStream.readDouble());
        System.out.println(objectInputStream.readBoolean());
        Object person = objectInputStream.readObject();
        System.out.println(person);

        Person p = (Person)person;
        System.out.println(p.getName());
        objectInputStream.close();
    }
}
```

细节

![image-20220726105414755](E:\大学\学习资料\笔记\pictures\image-20220726105414755.png)

![image-20220726110327497](E:\大学\学习资料\笔记\pictures\image-20220726110327497.png)

![image-20220726110034304](E:\大学\学习资料\笔记\pictures\image-20220726110034304.png)

### 标准输入输出流

![image-20220726110421234](E:\大学\学习资料\笔记\pictures\image-20220726110421234.png)

![image-20220726110726056](E:\大学\学习资料\笔记\pictures\image-20220726110726056.png)

![image-20220726110635996](E:\大学\学习资料\笔记\pictures\image-20220726110635996.png)

### 转换流

![image-20220726110847402](E:\大学\学习资料\笔记\pictures\image-20220726110847402.png)

![image-20220726111251307](E:\大学\学习资料\笔记\pictures\image-20220726111251307.png)

#### InputStreamReader

![image-20220726111710469](E:\大学\学习资料\笔记\pictures\image-20220726111710469.png)

![image-20220726112123431](E:\大学\学习资料\笔记\pictures\image-20220726112123431.png)

```java
public class InputStreamReader_ {
    public static void main(String[] args) throws IOException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\zhuanhuan\\test.txt";
        String line;
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(new FileInputStream(filepath),"gbk"));

        line = bufferedReader.readLine();
        System.out.println(line);

        bufferedReader.close();
    }
}
```

#### OutPutStreamWriter

![image-20220726120404608](E:\大学\学习资料\笔记\pictures\image-20220726120404608.png)

```java
public class OutPutStreamWriter_ {
    public static void main(String[] args) throws IOException {
        String filepath = "D:\\WorkSpace\\JavaProject\\IO\\src\\zhuanhuan\\test_shuchu.txt";
        OutputStreamWriter outputStreamWriter = new OutputStreamWriter(new FileOutputStream(filepath),"gbk");
        outputStreamWriter.write("你好牛逼");
        outputStreamWriter.close();
    }
}
```

### 打印流

![image-20220726160528668](E:\大学\学习资料\笔记\pictures\image-20220726160528668.png)

#### PrintStream  

![image-20220726161304101](E:\大学\学习资料\笔记\pictures\image-20220726161304101.png)

![image-20220726161537388](E:\大学\学习资料\笔记\pictures\image-20220726161537388.png)

#### PrintWriter

![image-20220726162002375](E:\大学\学习资料\笔记\pictures\image-20220726162002375.png)

## Properties类

![image-20220726162109338](E:\大学\学习资料\笔记\pictures\image-20220726162109338.png)

### 传统方法

![image-20220726163739473](E:\大学\学习资料\笔记\pictures\image-20220726163739473.png)

### 使用Properties类

![image-20220726163830451](E:\大学\学习资料\笔记\pictures\image-20220726163830451.png)

![image-20220726163919204](E:\大学\学习资料\笔记\pictures\image-20220726163919204.png)

![image-20220726164258621](E:\大学\学习资料\笔记\pictures\image-20220726164258621.png)

读取

![image-20220726164238566](E:\大学\学习资料\笔记\pictures\image-20220726164238566-16588249594791.png)

```java
public class duqu {
    public static void main(String[] args) throws IOException {
        //创建对象
        Properties p = new Properties();
        //加载
        p.load(new FileReader("D:\\WorkSpace\\JavaProject\\IO\\src\\Properties_\\mysql.properties"));
        //打印到电脑屏幕
        p.list(System.out);
        //根据key获取值
        String user = p.getProperty("user");
        System.out.println(user);
    }
}
```

创建修改

![image-20220726164506486](E:\大学\学习资料\笔记\pictures\image-20220726164506486.png)

![image-20220726164936113](E:\大学\学习资料\笔记\pictures\image-20220726164936113.png)

```java
public class duqu {
    public static void main(String[] args) throws IOException {
        //创建对象
        Properties p = new Properties();
        //加载
        p.load(new FileReader("D:\\WorkSpace\\JavaProject\\IO\\src\\Properties_\\mysql.properties"));
        //打印到电脑屏幕
        p.list(System.out);
        //根据key获取值
        String user = p.getProperty("user");
        System.out.println(user);
    }
}
```

