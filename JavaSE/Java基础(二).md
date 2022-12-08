# 网络基础

## 网络相关概念

![image-20220728153138034](E:\大学\学习资料\笔记\pictures\image-20220728153138034.png)

![image-20220728153834986](E:\大学\学习资料\笔记\pictures\image-20220728153834986.png)

![image-20220728154056223](E:\大学\学习资料\笔记\pictures\image-20220728154056223.png)

![image-20220728154729827](E:\大学\学习资料\笔记\pictures\image-20220728154729827.png)

![image-20220728154755900](E:\大学\学习资料\笔记\pictures\image-20220728154755900.png)

![image-20220728160552123](E:\大学\学习资料\笔记\pictures\image-20220728160552123.png)

![image-20220728161400735](E:\大学\学习资料\笔记\pictures\image-20220728161400735.png)

![image-20220728161551578](E:\大学\学习资料\笔记\pictures\image-20220728161551578.png)

## InetAddress类

![image-20220728161834509](E:\大学\学习资料\笔记\pictures\image-20220728161834509.png)

![image-20220728162907082](E:\大学\学习资料\笔记\pictures\image-20220728162907082.png)

```java
public class API_ {
    public static void main(String[] args) throws UnknownHostException {

        //1.获取本机的InetAdress对象
        InetAddress localHost = InetAddress.getLocalHost();
        System.out.println(localHost);//LAPTOP-WKN/192.168.3.43

        //2.根据指定主机名 获取InetAddress对象
        InetAddress host1 = InetAddress.getByName("LAPTOP-WKN");
        System.out.println(host1);//LAPTOP-WKN/192.168.3.43

        //3.根据域名返回InetAddress对象，比如 www.baidu.com
        InetAddress host2 = InetAddress.getByName("www.baidu.com");
        System.out.println(host2);//www.baidu.com/36.152.44.95

        //4.通过InetAddress对象，获取对应的地址
        System.out.println(host2.getHostAddress());//36.152.44.96

        //5.通过InetAddress对象，获取对应刀的主机名/或者域名
        System.out.println(host2.getHostName());//www.baidu.com
    }
}
```

## Socket

![image-20220728162954365](E:\大学\学习资料\笔记\pictures\image-20220728162954365-16589969955641.png)

![image-20220728163358403](E:\大学\学习资料\笔记\pictures\image-20220728163358403-16589972392013.png)

![image-20220728163542224](E:\大学\学习资料\笔记\pictures\image-20220728163542224.png)

TCP编程（可靠）

UDP编程（不可靠）

![image-20220728163409966](E:\大学\学习资料\笔记\pictures\image-20220728163409966.png)

### TCP网络通信编程

#### 字节流

![image-20220728163716997](E:\大学\学习资料\笔记\pictures\image-20220728163716997.png)

![image-20220728164036550](E:\大学\学习资料\笔记\pictures\image-20220728164036550-16589976375585.png)

 ![image-20220728165216965](E:\大学\学习资料\笔记\pictures\image-20220728165216965.png)

服务端

![image-20220728165242268](E:\大学\学习资料\笔记\pictures\image-20220728165242268.png)![image-20220728165316560](E:\大学\学习资料\笔记\pictures\image-20220728165316560.png)

```java
public class Socket_Server {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(9000);
        System.out.println("服务器准备中，等待连接");
        Socket socket = serverSocket.accept();
        InputStream inputStream = socket.getInputStream();
        System.out.println("服务器连接成功");
        byte[] bytes = new byte[1024];
        int readLine = 0;
        while ((readLine = inputStream.read(bytes)) != -1){
            System.out.println(new String(bytes,0,readLine));
        }
        System.out.println("服务器接收完毕");
        inputStream.close();
        socket.close();
        System.out.println("服务器已关闭");
    }
}
```

客户端

![image-20220728165404114](E:\大学\学习资料\笔记\pictures\image-20220728165404114.png)

```java
public class Socket_User {
    public static void main(String[] args) throws IOException {
        Socket socket = new Socket(InetAddress.getLocalHost(),9000);
        OutputStream outputStream = socket.getOutputStream();
        System.out.println("客户端连接服务器成功");
        outputStream.write("hello".getBytes());
        System.out.println("客户端发送完毕");
        outputStream.close();
        socket.close();
        System.out.println("客户端已关闭");
    }
}
```

![image-20220728165455003](E:\大学\学习资料\笔记\pictures\image-20220728165455003.png)

![image-20220728185616864](E:\大学\学习资料\笔记\pictures\image-20220728185616864.png)

![image-20220728190224892](E:\大学\学习资料\笔记\pictures\image-20220728190224892.png)

![image-20220728190307291](E:\大学\学习资料\笔记\pictures\image-20220728190307291.png)

客户端

```java
public class Socket_Client02 {
    public static void main(String[] args) throws IOException {
        Socket socket = new Socket(InetAddress.getLocalHost(),9000);
        OutputStream outputStream = socket.getOutputStream();
        System.out.println("客户端连接服务器成功");

        outputStream.write("hello,Server".getBytes());
        socket.shutdownOutput();
        System.out.println("客户端发送完毕");

        InputStream inputStream = socket.getInputStream();
        byte[] bytes = new byte[1024];
        int readLine = 0;
        while ((readLine = inputStream.read(bytes)) != -1){
            System.out.println(new String(bytes,0,readLine));
        }
        System.out.println("客户端接收完毕");

        outputStream.close();
        socket.close();
        System.out.println("客户端已关闭");
    }
}
```

服务端

```java
public class Socket_Server02 {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(9000);
        System.out.println("服务器准备中，等待连接");
        Socket socket = serverSocket.accept();
        InputStream inputStream = socket.getInputStream();
        System.out.println("服务器连接成功");

        byte[] bytes = new byte[1024];
        int readLine = 0;
        while ((readLine = inputStream.read(bytes)) != -1){
            System.out.println(new String(bytes,0,readLine));
        }
        System.out.println("服务器接收完毕");

        OutputStream outputStream = socket.getOutputStream();
        outputStream.write("hello,Clent".getBytes());
        socket.shutdownOutput();
        System.out.println("服务器发送完毕");

        inputStream.close();
        socket.close();
        System.out.println("服务器已关闭");
    }
}
```

#### 字符流

![image-20220728191338178](E:\大学\学习资料\笔记\pictures\image-20220728191338178.png)

![image-20220728191708234](E:\大学\学习资料\笔记\pictures\image-20220728191708234.png)

![image-20220728222729961](E:\大学\学习资料\笔记\pictures\image-20220728222729961.png)

客户端

```java
public class Socket_Client03 {
    public static void main(String[] args) throws IOException {
        //连接服务端
        Socket socket = new Socket(InetAddress.getLocalHost(),9000);
        System.out.println("连接服务端成功");
        //发送消息
        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
        bufferedWriter.write("你好，服务端");
        bufferedWriter.newLine();
        bufferedWriter.flush();
        //接受服务端消息
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        System.out.println(bufferedReader.readLine());
        //关闭流
        bufferedReader.close();
        bufferedWriter.close();
        socket.close();
        System.out.println("客户端已关闭");
    }
}
```

服务端

```java
public class Socket_Server03 {
    public static void main(String[] args) throws IOException {
        //开始监听
        ServerSocket serverSocket = new ServerSocket(9000);
        System.out.println("服务器已经开始监听，等待连接");
        //接受客户端消息
        Socket socket = serverSocket.accept();
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        System.out.println(bufferedReader.readLine());
        //发送消息
        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
        bufferedWriter.write("你好，客户端");
        bufferedWriter.newLine();
        bufferedWriter.flush();
        //关闭流
        bufferedWriter.close();
        bufferedReader.close();
        socket.close();
        System.out.println("服务端已关闭");
    }
}
```

#### 上传文件

![image-20220730122351776](E:\大学\学习资料\笔记\pictures\image-20220730122351776.png)

![image-20220730122340582](E:\大学\学习资料\笔记\pictures\image-20220730122340582.png)

Client

```java
public class UploadClient {
    public static void main(String[] args) throws Exception {
        Socket socket = new Socket(InetAddress.getLocalHost(),8888);
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream("C:\\Users\\12518\\Desktop\\壁纸头像\\眼镜.png"));
        byte[] content = StreamUtils.streamToByteArray(bis);

        BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
        bos.write(content);
        bos.flush();
        socket.shutdownOutput();

        InputStream is = socket.getInputStream();
        String message = StreamUtils.streamToString(is);
        System.out.println(message);
        
        socket.close();
        bos.close();
        is.close();
        bis.close();
    }
}
```

Server

```java
public class UploadServer {
    public static void main(String[] args) throws Exception {
        ServerSocket serverSocket = new ServerSocket(8888);
        Socket socket = serverSocket.accept();

        BufferedInputStream bis = new BufferedInputStream(socket.getInputStream());
        byte[] content = StreamUtils.streamToByteArray(bis);

        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("D:\\WorkSpace\\JavaProject\\Fighting\\src\\Internet\\Upload\\copy.png"));
        bos.write(content);
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
        bw.write("收到图片");
        bw.flush();
        socket.shutdownOutput();

        bos.close();
        bis.close();
        socket.close();
        bw.close();
        serverSocket.close();
    }
}
```

### UDP网络编程（了解）

基本概念

![image-20220730194840029](E:\大学\学习资料\笔记\pictures\image-20220730194840029.png)

![image-20220730195419000](E:\大学\学习资料\笔记\pictures\image-20220730195419000.png)

基本流程

![image-20220730195438625](E:\大学\学习资料\笔记\pictures\image-20220730195438625.png)

![image-20220730195751108](E:\大学\学习资料\笔记\pictures\image-20220730195751108.png)

Receiver

![image-20220730200427398](E:\大学\学习资料\笔记\pictures\image-20220730200427398.png)![image-20220730200502325](E:\大学\学习资料\笔记\pictures\image-20220730200502325.png)

Sender

![image-20220730201335895](E:\大学\学习资料\笔记\pictures\image-20220730201335895.png)

## netstar指令

![image-20220730175333898](E:\大学\学习资料\笔记\pictures\image-20220730175333898.png)

![image-20220730193236639](E:\大学\学习资料\笔记\pictures\image-20220730193236639-16591807582051.png)

![image-20220730194225427](E:\大学\学习资料\笔记\pictures\image-20220730194225427.png)

![image-20220730194733984](E:\大学\学习资料\笔记\pictures\image-20220730194733984.png)

![image-20220730194739850](E:\大学\学习资料\笔记\pictures\image-20220730194739850.png)

![image-20220730194754519](E:\大学\学习资料\笔记\pictures\image-20220730194754519.png)

# 项目开发流程

![image-20220801161437625](E:\大学\学习资料\笔记\pictures\image-20220801161437625.png)

![image-20220801162629271](E:\大学\学习资料\笔记\pictures\image-20220801162629271.png)

## 多用户即时通讯系统

![image-20220801162933726](E:\大学\学习资料\笔记\pictures\image-20220801162933726.png)

![image-20220801164409507](E:\大学\学习资料\笔记\pictures\image-20220801164409507.png)

# 反射

## 介绍

![image-20220801222536496](E:\大学\学习资料\笔记\pictures\image-20220801222536496.png)

![image-20220801223553024](E:\大学\学习资料\笔记\pictures\image-20220801223553024.png)

![image-20220801223637583](E:\大学\学习资料\笔记\pictures\image-20220801223637583-16593645984751.png)

![image-20220801224300124](E:\大学\学习资料\笔记\pictures\image-20220801224300124.png)

## 反射机制

![image-20220803141102630](E:\大学\学习资料\笔记\pictures\image-20220803141102630.png)

![image-20220803141738749](E:\大学\学习资料\笔记\pictures\image-20220803141738749.png)

Java程序计算机三阶段

![image-20220803145253075](E:\大学\学习资料\笔记\pictures\image-20220803145253075-16595095741751.png)

反射机制

![image-20220803145619067](E:\大学\学习资料\笔记\pictures\image-20220803145619067.png)

## 反射相关主要的类

![image-20220803150023968](E:\大学\学习资料\笔记\pictures\image-20220803150023968.png)

![image-20220803150619144](E:\大学\学习资料\笔记\pictures\image-20220803150619144.png)

反射优点和缺点

![image-20220803174720181](E:\大学\学习资料\笔记\pictures\image-20220803174720181.png)

反射优化

![image-20220803175345668](E:\大学\学习资料\笔记\pictures\image-20220803175345668.png)

![image-20220803175638820](E:\大学\学习资料\笔记\pictures\image-20220803175638820.png)

## Class类

![image-20220803175757723](E:\大学\学习资料\笔记\pictures\image-20220803175757723.png)

###  常用方法

![image-20220803211421994](E:\大学\学习资料\笔记\pictures\image-20220803211421994.png)

![image-20220803212402924](E:\大学\学习资料\笔记\pictures\image-20220803212402924.png)

![image-20220803211950733](E:\大学\学习资料\笔记\pictures\image-20220803211950733.png)![image-20220803212341377](E:\大学\学习资料\笔记\pictures\image-20220803212341377.png)

### 获取Class对象

![image-20220804221350133](E:\大学\学习资料\笔记\pictures\image-20220804221350133.png)

![image-20220804221533601](E:\大学\学习资料\笔记\pictures\image-20220804221533601.png)

![image-20220804221908000](E:\大学\学习资料\笔记\pictures\image-20220804221908000-16596227490181.png)

```java
public class GetClass_ {
    public static void main(String[] args) throws ClassNotFoundException {

        //1. Class.forName
        String classAllPath = "com.hspedu.Car"; //通过读取配置文件获取
        Class<?> cls1 = Class.forName(classAllPath);
        System.out.println(cls1);

        //2. 类名.class , 应用场景: 用于参数传递
        Class cls2 = Car.class;
        System.out.println(cls2);

        //3. 对象.getClass(), 应用场景，有对象实例
        Car car = new Car();
        Class cls3 = car.getClass();
        System.out.println(cls3);

        //4. 通过类加载器【4种】来获取到类的Class对象
        //(1)先得到类加载器 car
        ClassLoader classLoader = car.getClass().getClassLoader();
        //(2)通过类加载器得到Class对象
        Class cls4 = classLoader.loadClass(classAllPath);
        System.out.println(cls4);

        //cls1 , cls2 , cls3 , cls4 其实是同一个对象
        System.out.println(cls1.hashCode());
        System.out.println(cls2.hashCode());
        System.out.println(cls3.hashCode());
        System.out.println(cls4.hashCode());

        //5. 基本数据(int, char,boolean,float,double,byte,long,short) 按如下方式得到Class类对象
        Class<Integer> integerClass = int.class;
        Class<Character> characterClass = char.class;
        Class<Boolean> booleanClass = boolean.class;
        System.out.println(integerClass);//int

        //6. 基本数据类型对应的包装类，可以通过 .TYPE 得到Class类对象
        Class<Integer> type1 = Integer.TYPE;
        Class<Character> type2 = Character.TYPE; //其它包装类BOOLEAN, DOUBLE, LONG,BYTE等待
        System.out.println(type1);

        System.out.println(integerClass.hashCode());//?
        System.out.println(type1.hashCode());//?

    }
}
```

![image-20220806201218712](E:\大学\学习资料\笔记\pictures\image-20220806201218712.png)

## 类加载

![image-20220806203450310](E:\大学\学习资料\笔记\pictures\image-20220806203450310.png)

![image-20220806205040424](E:\大学\学习资料\笔记\pictures\image-20220806205040424-16597902413821.png)

![image-20220806205253639](E:\大学\学习资料\笔记\pictures\image-20220806205253639.png)

![image-20220806205524308](E:\大学\学习资料\笔记\pictures\image-20220806205524308.png)

### 1.加载

![image-20220806210206920](E:\大学\学习资料\笔记\pictures\image-20220806210206920.png)

### 2.验证

![image-20220806210337596](E:\大学\学习资料\笔记\pictures\image-20220806210337596.png)

### 3.准备

![image-20220806210442619](E:\大学\学习资料\笔记\pictures\image-20220806210442619.png)

![image-20220806211315353](E:\大学\学习资料\笔记\pictures\image-20220806211315353.png)

### 4.解析

![image-20220806211940850](E:\大学\学习资料\笔记\pictures\image-20220806211940850.png)

### 5.初始化

![image-20220806212006173](E:\大学\学习资料\笔记\pictures\image-20220806212006173.png)

![image-20220806212439014](E:\大学\学习资料\笔记\pictures\image-20220806212439014.png)

## 通过反射获取类的结构信息

![image-20220806213801459](E:\大学\学习资料\笔记\pictures\image-20220806213801459.png)

![image-20220806213823519](E:\大学\学习资料\笔记\pictures\image-20220806213823519.png)

![image-20220806214108520](E:\大学\学习资料\笔记\pictures\image-20220806214108520.png)

![image-20220806214147213](E:\大学\学习资料\笔记\pictures\image-20220806214147213.png)

## 通过反射创建对象

![image-20220817203243394](E:\大学\学习资料\笔记\pictures\image-20220817203243394.png)

```java
public class ReflecCreateInstance {
    public static void main(String[] args) throws ClassNotFoundException, IllegalAccessException, InstantiationException, NoSuchMethodException, InvocationTargetException {

        //1. 先获取到User类的Class对象
        Class<?> userClass = Class.forName("com.hspedu.reflection.User");
        //2. 通过public的无参构造器创建实例
        Object o = userClass.newInstance();
        System.out.println(o);
        //3. 通过public的有参构造器创建实例
        /*
            constructor 对象就是
            public User(String name) {//public的有参构造器
                this.name = name;
            }
         */
        //3.1 先得到对应构造器
        Constructor<?> constructor = userClass.getConstructor(String.class);
        //3.2 创建实例，并传入实参
        Object hsp = constructor.newInstance("hsp");
        System.out.println("hsp=" + hsp);
        //4. 通过非public的有参构造器创建实例
        //4.1 得到private的构造器对象
        Constructor<?> constructor1 = userClass.getDeclaredConstructor(int.class, String.class);
        //4.2 创建实例
        //暴破【暴力破解】 , 使用反射可以访问private构造器/方法/属性, 反射面前，都是纸老虎
        constructor1.setAccessible(true);
        Object user2 = constructor1.newInstance(100, "张三丰");
        System.out.println("user2=" + user2);
    }
}

class User { //User类
    private int age = 10;
    private String name = "韩顺平教育";

    public User() {//无参 public
    }

    public User(String name) {//public的有参构造器
        this.name = name;
    }

    private User(int age, String name) {//private 有参构造器
        this.age = age;
        this.name = name;
    }

    public String toString() {
        return "User [age=" + age + ", name=" + name + "]";
    }
}

```

## 通过反射操作属性

![image-20220817210438681](E:\大学\学习资料\笔记\pictures\image-20220817210438681.png)

```java
public class ReflecAccessProperty {
    public static void main(String[] args) throws ClassNotFoundException, IllegalAccessException, InstantiationException, NoSuchFieldException {

        //1. 得到Student类对应的 Class对象
        Class<?> stuClass = Class.forName("com.hspedu.reflection.Student");
        //2. 创建对象
        Object o = stuClass.newInstance();//o 的运行类型就是Student
        System.out.println(o.getClass());//Student
        //3. 使用反射得到age 属性对象
        Field age = stuClass.getField("age");
        age.set(o, 88);//通过反射来操作属性
        System.out.println(o);//
        System.out.println(age.get(o));//返回age属性的值

        //4. 使用反射操作name 属性
        Field name = stuClass.getDeclaredField("name");
        //对name 进行暴破, 可以操作private 属性
        name.setAccessible(true);
        //name.set(o, "老韩");
        name.set(null, "老韩~");//因为name是static属性，因此 o 也可以写出null
        System.out.println(o);
        System.out.println(name.get(o)); //获取属性值
        System.out.println(name.get(null));//获取属性值, 要求name是static

    }
}

class Student {//类
    public int age;
    private static String name;

    public Student() {//构造器
    }

    public String toString() {
        return "Student [age=" + age + ", name=" + name + "]";
    }
}
```



## 通过反射操作方法

![image-20220817214318111](E:\大学\学习资料\笔记\pictures\image-20220817214318111.png)

```java
public class ReflecAccessMethod {
    public static void main(String[] args) throws ClassNotFoundException, NoSuchMethodException, IllegalAccessException, InstantiationException, InvocationTargetException {

        //1. 得到Boss类对应的Class对象
        Class<?> bossCls = Class.forName("com.hspedu.reflection.Boss");
        //2. 创建对象
        Object o = bossCls.newInstance();
        //3. 调用public的hi方法
        //Method hi = bossCls.getMethod("hi", String.class);//OK
        //3.1 得到hi方法对象
        Method hi = bossCls.getDeclaredMethod("hi", String.class);//OK
        //3.2 调用
        hi.invoke(o, "韩顺平教育~");

        //4. 调用private static 方法
        //4.1 得到 say 方法对象
        Method say = bossCls.getDeclaredMethod("say", int.class, String.class, char.class);
        //4.2 因为say方法是private, 所以需要暴破，原理和前面讲的构造器和属性一样
        say.setAccessible(true);
        System.out.println(say.invoke(o, 100, "张三", '男'));
        //4.3 因为say方法是static的，还可以这样调用 ，可以传入null
        System.out.println(say.invoke(null, 200, "李四", '女'));

        //5. 在反射中，如果方法有返回值，统一返回Object , 但是他运行类型和方法定义的返回类型一致
        Object reVal = say.invoke(null, 300, "王五", '男');
        System.out.println("reVal 的运行类型=" + reVal.getClass());//String


        //在演示一个返回的案例
        Method m1 = bossCls.getDeclaredMethod("m1");
        Object reVal2 = m1.invoke(o);
        System.out.println("reVal2的运行类型=" + reVal2.getClass());//Monster


    }
}

class Monster {}
class Boss {//类
    public int age;
    private static String name;

    public Boss() {//构造器
    }

    public Monster m1() {
        return new Monster();
    }

    private static String say(int n, String s, char c) {//静态方法
        return n + " " + s + " " + c;
    }

    public void hi(String s) {//普通public方法
        System.out.println("hi " + s);
    }
}

```

# MySQL数据库

## 简单原理

![image-20220818130934907](E:\大学\学习资料\笔记\pictures\image-20220818130934907.png)

## 命令行连接MySQL

![image-20220818175257024](E:\大学\学习资料\笔记\pictures\image-20220818175257024.png)

![image-20220818175418558](E:\大学\学习资料\笔记\pictures\image-20220818175418558.png)

## 图形化管理界面

NaviCat  SQLyog

## 数据库三层结构

![image-20220818181933039](E:\大学\学习资料\笔记\pictures\image-20220818181933039.png)

![image-20220818181905635](E:\大学\学习资料\笔记\pictures\image-20220818181905635.png)

![image-20220818182056439](E:\大学\学习资料\笔记\pictures\image-20220818182056439.png)

## 数据库语句分类

![image-20220818182203708](E:\大学\学习资料\笔记\pictures\image-20220818182203708.png)

### 创建数据库

![image-20220818221831800](E:\大学\学习资料\笔记\pictures\image-20220818221831800.png)

```mysql
#创建一个名称为db02的数据库。[图形化和指令演示]
#使用指令创建数据库
CREATE DATABASE db02;
#删除数据库指令
DROP DATABASE db02;
#创建一个使用utf8字符集，并带校对规则的db03数据库
CREATE DATABASE db03 CHARACTER SET utf8 COLLATE utf8_bin
```

### 查看删除数据库

![image-20220818221759072](E:\大学\学习资料\笔记\pictures\image-20220818221759072.png)

```mysql
#查看当前数据库服务器中的所有数据库
SHOW DATABASES
#查看前面创建的db01数据库的定义信息
SHOW CREATE DATABASE db01
#老师说明在创建数据库，表的时候，为了规避关键字，可以使用反引号解决
CREATE DATABASE `CREATE`
```

### 备恢复数据库

![image-20220818223131217](E:\大学\学习资料\笔记\pictures\image-20220818223131217.png)

![image-20220818223711060](E:\大学\学习资料\笔记\pictures\image-20220818223711060.png)

![image-20220819115800929](E:\大学\学习资料\笔记\pictures\image-20220819115800929.png)

```mysql
#备份db01 为beifen.sql，在Dos下执行mysqldump指令 其实在mysql安装目录\bin
mysqldump -u root -p -B db01 > d:\\beifen.sql
#删除db01
DROP DATABASE db01;
#恢复数据库db01(注意:进入mysql命令行再执行)
source d:\\beifen.sql

#或者直接将benfen.sql的内容放到查询编辑器中执行
-- MySQL dump 10.13  Distrib 5.7.19, for Win64 (x86_64)
--
-- Host: localhost    Database: db01
-- ------------------------------------------------------
-- Server version	5.7.19

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Current Database: `db01`
--

CREATE DATABASE /*!32312 IF NOT EXISTS*/ `db01` /*!40100 DEFAULT CHARACTER SET utf8 */;

USE `db01`;

--
-- Table structure for table `users`
--

DROP TABLE IF EXISTS `users`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `users` (
  `id` int(11) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `address` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `users`
--

LOCK TABLES `users` WRITE;
/*!40000 ALTER TABLE `users` DISABLE KEYS */;
INSERT INTO `users` VALUES (1,'张三','北京'),(2,'李四','江苏');
/*!40000 ALTER TABLE `users` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2022-08-19 11:54:46
```

### 创建表

![image-20220819121220212](E:\大学\学习资料\笔记\pictures\image-20220819121220212.png)

```mysql
#指令创建表
CREATE TABLE `user` (
	id INT,
	`name` VARCHAR(255),
	`birthday` DATE)
	CHARACTER SET utf8 COLLATE utf8_bin ENGINE INNODB;
```

### MySQL常用数据类型

![image-20220819122151839](E:\大学\学习资料\笔记\pictures\image-20220819122151839.png)

![image-20220819122531716](E:\大学\学习资料\笔记\pictures\image-20220819122531716.png)

![image-20220819123138673](E:\大学\学习资料\笔记\pictures\image-20220819123138673.png)

红字表示经常用的列类型

![image-20220819123255881](E:\大学\学习资料\笔记\pictures\image-20220819123255881.png)![image-20220819123335345](E:\大学\学习资料\笔记\pictures\image-20220819123335345.png)

#### 整型

![image-20220819123603950](E:\大学\学习资料\笔记\pictures\image-20220819123603950.png)

![image-20220819123941767](E:\大学\学习资料\笔记\pictures\image-20220819123941767.png)

#### bit类型

![image-20220819155142713](E:\大学\学习资料\笔记\pictures\image-20220819155142713.png)

#### 小数

![image-20220819155600597](E:\大学\学习资料\笔记\pictures\image-20220819155600597.png)

#### 字符串

![image-20220819160217460](E:\大学\学习资料\笔记\pictures\image-20220819160217460.png)

![image-20220819160707970](E:\大学\学习资料\笔记\pictures\image-20220819160707970-16608964288951.png)

![image-20220819160754838](E:\大学\学习资料\笔记\pictures\image-20220819160754838-16608964757543.png)

![image-20220819161442146](E:\大学\学习资料\笔记\pictures\image-20220819161442146.png)

![image-20220819161554412](E:\大学\学习资料\笔记\pictures\image-20220819161554412.png)

![image-20220819161604268](E:\大学\学习资料\笔记\pictures\image-20220819161604268.png)

#### 日期类型

![image-20220819161900943](E:\大学\学习资料\笔记\pictures\image-20220819161900943.png)

浅浅创建一个表 浅浅添加一个数据 浅浅查询一下

```mysql
CREATE TABLE `emp`(
	id INT,
	`name` VARCHAR(32),
	sex CHAR(1),
	birthday DATE,
	entry_date DATETIME,
	job VARCHAR(255),
	Salary DOUBLE,
	`resume` TEXT)CHARSET utf8 COLLATE utf8_bin;
	
INSERT INTO `emp`
	VALUES(10,'wkn','男','2001-7-6','2021-7-10 11:11:12','niubi',5000,'牛逼');
	
SELECT * FROM `emp`;
```

### 修改表

![image-20220819182905063](E:\大学\学习资料\笔记\pictures\image-20220819182905063.png)

```mysql
#修改表的操作练习

#员工表emp的上增加一个image列，varchar类型(要求在resume后面)
ALTER TABLE `emp`
	ADD image VARCHAR(30) NOT NULL DEFAULT ''
	AFTER `RESUME`;
	
#显示表结构，查看表的所有列
DESC employee;

#修改改job列，使其长度为60
ALTER TABLE employee
	MODIFY job VARCHAR(60) NOT NULL DEFAULT '';
	
#删除sex列	
ALTER TABLE `emp`
	DROP sex;
	
#表名改为employee
RENAME TABLE`emp` TO employee;

#修改表的字符集为utf8
ALTER TABLE employee 
	CHARACTER SET utf8;

#列名name修改为user name
ALTER TABLE employee 
	CHANGE `name` user_name VARCHAR(32) NOT NULL DEFAULT ''
```

### CRUD语句

create read update delete

![image-20220819184836117](E:\大学\学习资料\笔记\pictures\image-20220819184836117.png)

#### Insert添加

![image-20220819184956350](E:\大学\学习资料\笔记\pictures\image-20220819184956350.png)

```mysql
INSERT INTO goods (id,goods_name,price)
	VALUES(10,'华为',5000);
INSERT INTO goods (id,goods_name,price)
	VALUES(10,'iPhone',6000);
INSERT INTO goods (id,goods_name,price)
	VALUES(10,'小米',2000),(11,'samsung',5500);
SELECT * FROM goods;
```

注意事项

![image-20220819221220816](E:\大学\学习资料\笔记\pictures\image-20220819221220816.png)

```mysql
-- 1.插入的数据应与字段的数据类型相同。
--       比如 把 'abc' 添加到 int 类型会错误
INSERT INTO `goods` (id, goods_name, price) 
	VALUES('韩顺平', '小米手机', 2000);
-- 2. 数据的长度应在列的规定范围内，例如：不能将一个长度为80的字符串加入到长度为40的列中。
INSERT INTO `goods` (id, goods_name, price) 
	VALUES(40, 'vovo手机vovo手机vovo手机vovo手机vovo手机', 3000);
-- 3. 在values中列出的数据位置必须与被加入的列的排列位置相对应。
INSERT INTO `goods` (id, goods_name, price)  -- 不对
	VALUES('vovo手机',40, 2000);
-- 4. 字符和日期型数据应包含在单引号中。
INSERT INTO `goods` (id, goods_name, price) 
	VALUES(40, vovo手机, 3000); -- 错误的 vovo手机 应该 'vovo手机'
-- 5. 列可以插入空值[前提是该字段允许为空]，insert into table value(null)
INSERT INTO `goods` (id, goods_name, price) 
	VALUES(40, 'vovo手机', NULL);
-- 6. insert into tab_name (列名..)  values (),(),()  形式添加多条记录
INSERT INTO `goods` (id, goods_name, price) 
	VALUES(50, '三星手机', 2300),(60, '海尔手机', 1800);
-- 7. 如果是给表中的所有字段添加数据，可以不写前面的字段名称
INSERT INTO `goods`   
	VALUES(70, 'IBM手机', 5000);
-- 8. 默认值的使用，当不给某个字段值时，如果有默认值就会添加默认值，否则报错
      -- 如果某个列 没有指定 not null ,那么当添加数据时，没有给定值，则会默认给null
      -- 如果我们希望指定某个列的默认值，可以在创建表时指定
INSERT INTO `goods` (id, goods_name)   
	VALUES(80, '格力手机');

SELECT * FROM goods;

INSERT INTO `goods2` (id, goods_name)   
	VALUES(10, '顺平手机');
SELECT * FROM goods2;
```

#### Update修改

![image-20220820134250289](E:\大学\学习资料\笔记\pictures\image-20220820134250289.png)

使用细节

![image-20220820135047469](E:\大学\学习资料\笔记\pictures\image-20220820135047469.png)

```mysql
SELECT * FROM employee
#将所有员工薪水修改为5000
UPDATE employee SET Salary = 5000;
#将姓名为wkn的员工薪水修改为20000
UPDATE employee SET Salary = 20000
		WHERE user_name = 'wkn';
#将姓名为wkn的员工薪水原有基础上加10000
UPDATE employee SET Salary = Salary + 10000
		WHERE user_name = 'wkn';
#修改多个列
UPDATE employee SET Salary = Salary + 10000,job = 'lihai'
		WHERE user_name = 'wkn';
```

#### Delete删除

![image-20220820135458360](E:\大学\学习资料\笔记\pictures\image-20220820135458360-16609748992961.png)

```mysql
#删除表中名为xiaoming的数据
DELETE FROM employee
	WHERE user_name = 'xiaoming';
#删除表中所有数据
DELETE FROM employee;
```

使用细节

![image-20220820141720620](E:\大学\学习资料\笔记\pictures\image-20220820141720620.png)

#### Select单表查询

##### 基本语法

![](E:\大学\学习资料\笔记\pictures\image-20220820142323137.png)

```mysql
#查询表中所有学生信息
SELECT * FROM student;
#查询表中所有学生的姓名和对应的英语成绩
SELECT `name`,english FROM student;
#过滤表中重复数据
SELECT DISTINCT english FROM student;
#一定要每一个字段的数据都相同才会去重
SELECT DISTINCT `name`,english FROM student;
```

![image-20220820155634889](E:\大学\学习资料\笔记\pictures\image-20220820155634889.png)

```mysql
#统计学生总分 
SELECT `name`,(chinese+english+math) FROM student;
#每个学生总分加十分
SELECT `name`,(chinese+english+math+10) FROM student;
#使用别名表示学生分数
SELECT `name` AS `姓名`,(chinese+english+math) AS `总成绩` FROM student;
```

##### where子句中常用运算符

![image-20220820160809662](E:\大学\学习资料\笔记\pictures\image-20220820160809662.png)

```mysql
SELECT * FROM student
	WHERE math > 60 AND id > 3;
	
SELECT * FROM student
	WHERE english > chinese;
	
SELECT * FROM student
	WHERE (chinese+math+english) > 250 
	AND math < chinese  AND `name` LIKE '%胡';
```

```mysql
#区间查找
SELECT `name` FROM student
	WHERE english >= 70 AND english <= 90;
	
SELECT `name` FROM student
	WHERE math BETWEEN 70 AND 90;
#具体查找
SELECT `name` FROM student
	WHERE (chinese+english+math) IN (270,294)
SELECT `name` FROM student
	WHERE (chinese+english+math) = 270 OR (chinese+english+math) = 294
#姓查找
SELECT * FROM student
	WHERE `name` LIKE '吴%' OR `name` LIKE '张%';
#
SELECT `name` FROM student
	WHERE chinese - math > 30;
```

##### Order By排序

![image-20220820172306439](E:\大学\学习资料\笔记\pictures\image-20220820172306439.png)

```mysql
SELECT `name`,(chinese+math+english) AS total_score FROM student
	ORDER BY total_score;

SELECT `name`,(chinese+math+english) AS total_score FROM student
	ORDER BY total_score DESC;
```

##### 分页查询

![image-20220827192906654](E:\大学\学习资料\笔记\pictures\image-20220827192906654.png)

```mysql
-- 分页查询
-- 按雇员的id号升序取出， 每页显示3条记录，请分别显示 第1页，第2页，第3页

-- 第1页
SELECT * FROM emp 
	ORDER BY empno 
	LIMIT 0, 3;
-- 第2页
SELECT * FROM emp 
	ORDER BY empno 
	LIMIT 3, 3;
-- 第3页
SELECT * FROM emp 
	ORDER BY empno 
	LIMIT 6, 3;
-- 推导一个公式 
SELECT * FROM emp
	ORDER BY empno 
	LIMIT 每页显示记录数 * (第几页-1) , 每页显示记录数
	
-- 测试
SELECT job, COUNT(*) FROM emp GROUP BY  job;
-- 显示雇员总数，以及获得补助的雇员数
SELECT COUNT(*) FROM emp  WHERE mgr IS NOT NULL;
SELECT MAX(sal) - MIN(sal) FROM emp;
```

#### Select函数

##### 合计/统计函数count

![image-20220820175256681](E:\大学\学习资料\笔记\pictures\image-20220820175256681.png)

![image-20220820175727736](E:\大学\学习资料\笔记\pictures\image-20220820175727736.png)

```mysql
SELECT COUNT(*) FROM student;
SELECT COUNT(`name`) FROM student;
```

##### 合计/统计函数sum

![image-20220820220906382](E:\大学\学习资料\笔记\pictures\image-20220820220906382.png)

```mysql
SELECT SUM(math) FROM student;
SELECT SUM(chinese+math+english) FROM student;
SELECT SUM(math),SUM(chinese),SUM(english) FROM student;
SELECT SUM(chinese+math+english)/COUNT(*) AS average_score FROM student;
```

##### 合计/统计函数avg

![image-20220820220931539](E:\大学\学习资料\笔记\pictures\image-20220820220931539.png)

```mysql
SELECT AVG(chinese+math+english) AS average_score FROM student;
```

##### 合计/统计函数max/min

![image-20220820221026433](E:\大学\学习资料\笔记\pictures\image-20220820221026433-16610046274396.png)

```mysql
SELECT MIN(chinese+math+english) FROM student;
```

##### 分组统计函数group by+having

![image-20220822113025946](E:\大学\学习资料\笔记\pictures\image-20220822113025946.png)

![image-20220822114933853](E:\大学\学习资料\笔记\pictures\image-20220822114933853.png)

```mysql
-- 按照部分来分组查询
SELECT AVG(sal), MAX(sal) , deptno 
	FROM  emp GROUP BY deptno; 
-- 使用数学方法，对小数点进行处理
SELECT FORMAT(AVG(sal),2), MAX(sal) , deptno 
	FROM  emp GROUP BY deptno; 

-- ?显示每个部门的每种岗位的平均工资和最低工资
-- 老师分析 1. 显示每个部门的平均工资和最低工资
--          2. 显示每个部门的每种岗位的平均工资和最低工资
SELECT AVG(sal), MIN(sal) , deptno, job 
	FROM  emp GROUP BY deptno, job; 

-- ?显示平均工资低于2000的部门号和它的平均工资 // 别名

-- 老师分析 [写sql语句的思路是化繁为简,各个击破]
-- 1. 显示各个部门的平均工资和部门号
-- 2. 在1的结果基础上，进行过滤，保留 AVG(sal) < 2000
-- 3. 使用别名进行过滤 

SELECT AVG(sal), deptno 
	FROM emp GROUP BY deptno
		HAVING AVG(sal) < 2000;
-- 使用别名		
SELECT AVG(sal) AS avg_sal, deptno 
	FROM emp GROUP BY deptno
		HAVING avg_sal < 2000;
```

##### 字符串函数

![image-20220822123107912](E:\大学\学习资料\笔记\pictures\image-20220822123107912.png)

```mysql
-- 演示字符串相关函数的使用  ， 使用emp表来演示
-- CHARSET(str)	返回字串字符集
SELECT CHARSET(ename) FROM emp;
-- CONCAT (string2  [,... ])	连接字串, 将多个列拼接成一列
SELECT CONCAT(ename, ' 工作是 ', job) FROM emp;

-- INSTR (string ,substring )	返回substring在string中出现的位置,没有返回0
-- dual 亚元表, 系统表 可以作为测试表使用
SELECT INSTR('hanshunping', 'ping') FROM DUAL; 

-- UCASE (string2 )	转换成大写
SELECT UCASE(ename) FROM emp;

-- LCASE (string2 )	转换成小写

SELECT LCASE(ename) FROM emp;
-- LEFT (string2 ,length )	从string2中的左边起取length个字符
-- RIGHT (string2 ,length )	从string2中的右边起取length个字符
SELECT LEFT(ename, 2) FROM emp;

-- LENGTH (string )	string长度[按照字节]
SELECT LENGTH(ename) FROM emp;
-- REPLACE (str ,search_str ,replace_str ) 	
-- 在str中用replace_str替换search_str
-- 如果是manager 就替换成 经理
SELECT ename, REPLACE(job,'MANAGER', '经理')  FROM emp;

-- STRCMP (string1 ,string2 )	逐字符比较两字串大小
SELECT STRCMP('hsp', 'hsp') FROM DUAL;
-- SUBSTRING (str , position  [,length ])	
-- 从str的position开始【从1开始计算】,取length个字符
-- 从ename 列的第一个位置开始取出2个字符
SELECT SUBSTRING(ename, 1, 2) FROM emp;

-- LTRIM (string2 ) RTRIM (string2 )  TRIM(string)
-- 去除前端空格或后端空格
SELECT LTRIM('  韩顺平教育') FROM DUAL;
SELECT RTRIM('韩顺平教育   ') FROM DUAL;
SELECT TRIM('    韩顺平教育   ') FROM DUAL;

-- 练习: 以首字母小写的方式显示所有员工emp表的姓名
-- 方法1 
-- 思路先取出ename 的第一个字符，转成小写的
-- 把他和后面的字符串进行拼接输出即可

SELECT CONCAT(LCASE(SUBSTRING(ename,1,1)),  SUBSTRING(ename,2)) AS new_name
	FROM emp;  

SELECT CONCAT(LCASE(LEFT(ename,1)),  SUBSTRING(ename,2)) AS new_name
	FROM emp; 
```

![image-20220822124844271](E:\大学\学习资料\笔记\pictures\image-20220822124844271.png)

```mysql
-- 演示数学相关函数

-- ABS(num)	绝对值
SELECT ABS(-10) FROM DUAL;
-- BIN (decimal_number )十进制转二进制
SELECT BIN(10) FROM DUAL;
-- CEILING (number2 )	向上取整, 得到比num2 大的最小整数
SELECT CEILING(-1.1) FROM DUAL;

-- CONV(number2,from_base,to_base)	进制转换
-- 下面的含义是 8 是十进制的8, 转成 2进制输出
SELECT CONV(8, 10, 2) FROM DUAL;
-- 下面的含义是 16 是16进制的8, 转成 10 进制输出
SELECT CONV(16, 16, 10) FROM DUAL;

-- FLOOR (number2 )	向下取整,得到比 num2 小的最大整数
SELECT FLOOR(-1.1) FROM DUAL;

-- FORMAT (number,decimal_places )	保留小数位数(四舍五入)
SELECT FORMAT(78.125458,2) FROM DUAL;

-- HEX (DecimalNumber )	转十六进制

-- LEAST (number , number2  [,..])	求最小值
SELECT LEAST(0,1, -10, 4) FROM DUAL;
-- MOD (numerator ,denominator )	求余
SELECT MOD(10, 3) FROM DUAL;

-- RAND([seed])	RAND([seed]) 返回随机数 其范围为 0 ≤ v ≤ 1.0
-- 老韩说明
-- 1. 如果使用 rand() 每次返回不同的随机数 ，在 0 ≤ v ≤ 1.0
-- 2. 如果使用 rand(seed) 返回随机数, 范围 0 ≤ v ≤ 1.0, 如果seed不变，
--    该随机数也不变了
SELECT RAND() FROM DUAL;

SELECT CURRENT_TIMESTAMP() FROM DUAL;
```

##### 时间日期相关函数

![image-20220825202837804](E:\大学\学习资料\笔记\pictures\image-20220825202837804-16614305184201.png)

![image-20220825203100892](E:\大学\学习资料\笔记\pictures\image-20220825203100892.png)

![image-20220825204551128](E:\大学\学习资料\笔记\pictures\image-20220825204551128.png)

```mysql
-- 日期时间相关函数

-- CURRENT_DATE (  )	当前日期
SELECT CURRENT_DATE() FROM DUAL;
-- CURRENT_TIME (  )	当前时间
SELECT CURRENT_TIME()  FROM DUAL;
-- CURRENT_TIMESTAMP (  ) 当前时间戳
SELECT CURRENT_TIMESTAMP()  FROM DUAL;

-- 创建测试表 信息表
CREATE TABLE mes(
	id INT , 
	content VARCHAR(30), 
	send_time DATETIME);
	
	
-- 添加一条记录
INSERT INTO mes 
	VALUES(1, '北京新闻', CURRENT_TIMESTAMP()); 
INSERT INTO mes VALUES(2, '上海新闻', NOW());
INSERT INTO mes VALUES(3, '广州新闻', NOW());

SELECT * FROM mes;
SELECT NOW() FROM DUAL;

-- 上应用实例
-- 显示所有新闻信息，发布日期只显示 日期，不用显示时间.
SELECT id, content, DATE(send_time) 
	FROM mes;
-- 请查询在10分钟内发布的新闻, 思路一定要梳理一下.
SELECT * 
	FROM mes
	WHERE DATE_ADD(send_time, INTERVAL 10 MINUTE) >= NOW()

SELECT * 
	FROM mes
	WHERE send_time >= DATE_SUB(NOW(), INTERVAL 10 MINUTE) 

-- 请在mysql 的sql语句中求出 2011-11-11 和 1990-1-1 相差多少天
SELECT DATEDIFF('2011-11-11', '1990-01-01') FROM DUAL;
-- 请用mysql 的sql语句求出你活了多少天? [练习] 1986-11-11 出生
SELECT DATEDIFF(NOW(), '1986-11-11') FROM DUAL;
-- 如果你能活80岁，求出你还能活多少天.[练习] 1986-11-11 出生
-- 先求出活80岁 时, 是什么日期 X
-- 然后在使用 datediff(x, now()); 1986-11-11->datetime
-- INTERVAL 80 YEAR ： YEAR 可以是 年月日，时分秒
-- '1986-11-11' 可以date,datetime timestamp 
SELECT DATEDIFF(DATE_ADD('1986-11-11', INTERVAL 80 YEAR), NOW()) 
	FROM DUAL;
	
SELECT TIMEDIFF('10:11:11', '06:10:10') FROM DUAL;

-- YEAR|Month|DAY| DATE (datetime )
SELECT YEAR(NOW()) FROM DUAL;
SELECT MONTH(NOW()) FROM DUAL;
SELECT DAY(NOW()) FROM DUAL;
SELECT MONTH('2013-11-10') FROM DUAL;
-- unix_timestamp() : 返回的是1970-1-1 到现在的秒数
SELECT UNIX_TIMESTAMP() FROM DUAL;
-- FROM_UNIXTIME() : 可以把一个unix_timestamp 秒数[时间戳]，转成指定格式的日期
-- %Y-%m-%d 格式是规定好的，表示年月日
-- 意义：在开发中，可以存放一个整数，然后表示时间，通过FROM_UNIXTIME转换
--   
SELECT FROM_UNIXTIME(1618483484, '%Y-%m-%d') FROM DUAL;
SELECT FROM_UNIXTIME(1618483100, '%Y-%m-%d %H:%i:%s') FROM DUAL;
```

##### 加密和系统函数

![image-20220825205232493](E:\大学\学习资料\笔记\pictures\image-20220825205232493.png)

``` mysql
-- 演示加密函数和系统函数

-- USER()	查询用户
-- 可以查看登录到mysql的有哪些用户，以及登录的IP
SELECT USER() FROM DUAL; -- 用户@IP地址
-- DATABASE()	查询当前使用数据库名称
SELECT DATABASE();

-- MD5(str)	为字符串算出一个 MD5 32的字符串，常用(用户密码)加密
-- root 密码是 hsp -> 加密md5 -> 在数据库中存放的是加密后的密码
SELECT MD5('hsp') FROM DUAL;
SELECT LENGTH(MD5('hsp')) FROM DUAL;

-- 演示用户表，存放密码时，是md5
CREATE TABLE hsp_user
	(id INT , 
	`name` VARCHAR(32) NOT NULL DEFAULT '', 
	pwd CHAR(32) NOT NULL DEFAULT '');
INSERT INTO hsp_user 
	VALUES(100, '韩顺平', MD5('hsp'));
SELECT * FROM hsp_user; -- csdn

SELECT * FROM hsp_user  -- SQL注入问题
	WHERE `name`='韩顺平' AND pwd = MD5('hsp')  


-- PASSWORD(str) -- 加密函数, MySQL数据库的用户密码就是 PASSWORD函数加密

SELECT PASSWORD('hsp') FROM DUAL; -- 数据库的 *81220D972A52D4C51BB1C37518A2613706220DAC


-- select * from mysql.user \G 	从原文密码str 计算并返回密码字符串
-- 通常用于对mysql数据库的用户密码加密
-- mysql.user 表示 数据库.表 
SELECT * FROM mysql.user
```

##### 流程控制函数

![image-20220826153724959](E:\大学\学习资料\笔记\pictures\image-20220826153724959.png)

```mysql
# 演示流程控制语句

# IF(expr1,expr2,expr3)	如果expr1为True ,则返回 expr2 否则返回 expr3
SELECT IF(TRUE, '北京', '上海') FROM DUAL;
# IFNULL(expr1,expr2)	如果expr1不为空NULL,则返回expr1,否则返回expr2
SELECT IFNULL( NULL, '韩顺平教育') FROM DUAL;
# SELECT CASE WHEN expr1 THEN expr2 WHEN expr3 THEN expr4 ELSE expr5 END; [类似多重分支.]
# 如果expr1 为TRUE,则返回expr2,如果expr2 为t, 返回 expr4, 否则返回 expr5

SELECT CASE 
	WHEN TRUE THEN 'jack'  -- jack
	WHEN FALSE THEN 'tom' 
	ELSE 'mary' END

-- 1. 查询emp 表, 如果 comm 是null , 则显示0.0
--    老师说明，判断是否为null 要使用 is null, 判断不为空 使用 is not
SELECT ename, IF(comm IS NULL , 0.0, comm)
	FROM emp;
SELECT ename, IFNULL(comm, 0.0)
	FROM emp;
-- 2. 如果emp 表的 job 是 CLERK 则显示 职员， 如果是 MANAGER 则显示经理
--     如果是 SALESMAN 则显示 销售人员，其它正常显示

SELECT ename, (SELECT CASE 
		WHEN job = 'CLERK' THEN '职员' 
		WHEN job = 'MANAGER' THEN '经理'
		WHEN job = 'SALESMAN' THEN '销售人员' 
		ELSE job END) AS 'job'
	FROM emp; 

SELECT * FROM emp;
SELECT * FROM dept;
SELECT * FROM salgrade;
```

#### Select多表查询

![image-20220827213101721](E:\大学\学习资料\笔记\pictures\image-20220827213101721.png)

![image-20220827214334989](E:\大学\学习资料\笔记\pictures\image-20220827214334989.png)

```mysql
SELECT dname,job,sal,dept.`deptno` FROM dept,emp
	WHERE dept.deptno = emp.deptno
```

![image-20220827214735567](E:\大学\学习资料\笔记\pictures\image-20220827214735567.png)

```mysql
SELECT ename,sal,grade FROM emp,salgrade
	WHERE sal BETWEEN losal AND hisal
```

自连接

```mysql
-- 多表查询的 自连接

-- 思考题: 显示公司员工名字和他的上级的名字

-- 老韩分析： 员工名字 在emp, 上级的名字的名字 emp
-- 员工和上级是通过 emp表的 mgr 列关联
-- 这里老师小结：
-- 自连接的特点 1. 把同一张表当做两张表使用
--               2. 需要给表取别名 表名  表别名 
-- 		       3. 列名不明确，可以指定列的别名 列名 as 列的别名		
SELECT worker.ename AS '职员名' ,  boss.ename AS '上级名'
	FROM emp worker, emp boss
	WHERE worker.mgr = boss.empno;
SELECT * FROM emp;
```

#### Select子查询

![image-20220831171303978](E:\大学\学习资料\笔记\pictures\image-20220831171303978.png)

```mysql
-- 子查询的演示
-- 请思考：如何显示与SMITH同一部门的所有员工?
/*
	1. 先查询到 SMITH的部门号得到
	2. 把上面的select 语句当做一个子查询来使用
*/
SELECT deptno 
	FROM emp 
	WHERE ename = 'SMITH'

-- 下面的答案.	
SELECT * 
	FROM emp
	WHERE deptno = (
		SELECT deptno 
		FROM emp 
		WHERE ename = 'SMITH'
	)

-- 课堂练习:如何查询和部门10的工作相同的雇员的
-- 名字、岗位、工资、部门号, 但是不含10号部门自己的雇员.

/*
	1. 查询到10号部门有哪些工作
	2. 把上面查询的结果当做子查询使用
*/
select distinct job 
	from emp 
	where deptno = 10;
	
--  下面语句完整

select ename, job, sal, deptno
	from emp
	where job in (
		SELECT DISTINCT job 
		FROM emp 
		WHERE deptno = 10
	) and deptno != 10 
```

##### 临时表

![image-20220831185533015](E:\大学\学习资料\笔记\pictures\image-20220831185533015.png)

##### all-any

![image-20220831173048007](E:\大学\学习资料\笔记\pictures\image-20220831173048007.png)

![image-20220831173233580](E:\大学\学习资料\笔记\pictures\image-20220831173233580.png)

```mysql
-- all 和 any的使用

-- 请思考:显示工资比部门30的所有员工的工资高的员工的姓名、工资和部门号

SELECT ename, sal, deptno
	FROM emp
	WHERE sal > ALL(
		SELECT sal 
			FROM emp
			WHERE deptno = 30
		) 
-- 可以这样写
SELECT ename, sal, deptno
	FROM emp
	WHERE sal > (
		SELECT MAX(sal) 
			FROM emp
			WHERE deptno = 30
		) 

-- 请思考:如何显示工资比部门30的其中一个员工的工资高的员工的姓名、工资和部门号

SELECT ename, sal, deptno
	FROM emp
	WHERE sal > any(
		SELECT sal 
			FROM emp
			WHERE deptno = 30
		)

 SELECT ename, sal, deptno
	FROM emp
	WHERE sal > (
		SELECT min(sal) 
			FROM emp
			WHERE deptno = 30
		)


-- 查询ecshop中各个类别中，价格最高的商品

-- 查询 商品表
-- 先得到 各个类别中，价格最高的商品 max + group by cat_id, 当做临时表
-- 把子查询当做一张临时表可以解决很多很多复杂的查询

select cat_id , max(shop_price) 
	from ecs_goods
	group by cat_id
	
	
-- 这个最后答案	
select goods_id, ecs_goods.cat_id, goods_name, shop_price 
	from (
		SELECT cat_id , MAX(shop_price) as max_price
		FROM ecs_goods
		GROUP BY cat_id
	) temp , ecs_goods
	where  temp.cat_id = ecs_goods.cat_id 
	and temp.max_price = ecs_goods.shop_price 
```

##### 多列子查询

![image-20220831173351535](E:\大学\学习资料\笔记\pictures\image-20220831173351535.png)

```mysql
SELECT chinese,english 
	FROM student
	WHERE `name` = '小帅';
SELECT * 
	FROM student 
	WHERE (chinese,english) = (
	SELECT chinese,english 
	FROM student
	WHERE `name` = '小帅'
	) AND `name` != '小帅' 
```

### 表复制和表去重

![image-20220902181142363](E:\大学\学习资料\笔记\pictures\image-20220902181142363.png)

```mysql
-- 表的复制
-- 为了对某个sql语句进行效率测试，我们需要海量数据时，可以使用此法为表创建海量数据

CREATE TABLE my_tab01 
	( id INT,
	  `name` VARCHAR(32),
	  sal DOUBLE,
	  job VARCHAR(32),
	  deptno INT);
DESC my_tab01
SELECT * FROM my_tab01;

-- 演示如何自我复制
-- 1. 先把emp 表的记录复制到 my_tab01
INSERT INTO my_tab01 
	(id, `name`, sal, job,deptno)
	SELECT empno, ename, sal, job, deptno FROM emp;
-- 2. 自我复制
INSERT INTO my_tab01
	SELECT * FROM my_tab01;
SELECT COUNT(*) FROM my_tab01;

-- 如何删除掉一张表重复记录
-- 1. 先创建一张表 my_tab02, 
-- 2. 让 my_tab02 有重复的记录

CREATE TABLE my_tab02 LIKE emp; -- 这个语句 把emp表的结构(列)，复制到my_tab02

desc my_tab02;

insert into my_tab02
	select * from emp;
select * from my_tab02;
-- 3. 考虑去重 my_tab02的记录
/*
	思路 
	(1) 先创建一张临时表 my_tmp , 该表的结构和 my_tab02一样
	(2) 把my_tmp 的记录 通过 distinct 关键字 处理后 把记录复制到 my_tmp
	(3) 清除掉 my_tab02 记录
	(4) 把 my_tmp 表的记录复制到 my_tab02
	(5) drop 掉 临时表my_tmp
*/
-- (1) 先创建一张临时表 my_tmp , 该表的结构和 my_tab02一样

create table my_tmp like my_tab02
-- (2) 把my_tmp 的记录 通过 distinct 关键字 处理后 把记录复制到 my_tmp
insert into my_tmp 
	select distinct * from my_tab02;

-- (3) 清除掉 my_tab02 记录
delete from my_tab02;
-- (4) 把 my_tmp 表的记录复制到 my_tab02
insert into my_tab02
	select * from my_tmp;
-- (5) drop 掉 临时表my_tmp
drop table my_tmp;

select * from my_tab02;
```

### 合并查询

![image-20220902181914487](E:\大学\学习资料\笔记\pictures\image-20220902181914487.png)

![image-20220902182144939](E:\大学\学习资料\笔记\pictures\image-20220902182144939.png)

```mysql
-- 合并查询

SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5

SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3

-- union all 就是将两个查询结果合并，不会去重
SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5
UNION ALL
SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3

-- union  就是将两个查询结果合并，会去重
SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5
UNION 
SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3
```

### MySQL表外连接

![image-20220902182745256](E:\大学\学习资料\笔记\pictures\image-20220902182745256.png)

![image-20220902182932448](E:\大学\学习资料\笔记\pictures\image-20220902182932448.png)

```mysql
-- 外连接

-- 比如：列出部门名称和这些部门的员工名称和工作，
-- 同时要求 显示出那些没有员工的部门。

-- 使用我们学习过的多表查询的SQL， 看看效果如何?

SELECT dname, ename, job 
	FROM emp, dept
	WHERE emp.deptno = dept.deptno
	ORDER BY dname
SELECT * FROM dept;

SELECT * FROM emp;


-- 创建 stu
/*
id  name   
1   Jack
2   Tom
3   Kity
4   nono

*/
CREATE TABLE stu (
	id INT,
	`name` VARCHAR(32));
INSERT INTO stu VALUES(1, 'jack'),(2,'tom'),(3, 'kity'),(4, 'nono');
SELECT * FROM stu;
-- 创建 exam
/*
id   grade
1    56
2    76
11   8

*/
CREATE TABLE exam(
	id INT,
	grade INT);
INSERT INTO exam VALUES(1, 56),(2,76),(11, 8);
SELECT * FROM exam;

-- 使用左连接
-- （显示所有人的成绩，如果没有成绩，也要显示该人的姓名和id号,成绩显示为空）

SELECT `name`, stu.id, grade
	FROM stu, exam
	WHERE stu.id = exam.id;
	
-- 改成左外连接
SELECT `name`, stu.id, grade
	FROM stu LEFT JOIN exam
	ON stu.id = exam.id;
	
	
-- 使用右外连接（显示所有成绩，如果没有名字匹配，显示空)
-- 即：右边的表(exam) 和左表没有匹配的记录，也会把右表的记录显示出来
SELECT `name`, stu.id, grade
	FROM stu RIGHT JOIN exam
	ON stu.id = exam.id;

-- 列出部门名称和这些部门的员工信息(名字和工作)，
-- 同时列出那些没有员工的部门名。5min
-- 使用左外连接实现
SELECT dname, ename, job
	FROM dept LEFT JOIN emp
	ON dept.deptno = emp.deptno
	
-- 使用右外连接实现

SELECT dname, ename, job
	FROM emp RIGHT JOIN dept
	ON dept.deptno = emp.deptno

```

### MySQL约束

![image-20220902204907261](E:\大学\学习资料\笔记\pictures\image-20220902204907261.png)

#### primary key主键

![image-20220902205012828](E:\大学\学习资料\笔记\pictures\image-20220902205012828.png)

![image-20220902205816956](E:\大学\学习资料\笔记\pictures\image-20220902205816956.png)

```mysql
-- 主键使用

-- id	name 	email
CREATE TABLE t17
	(id INT PRIMARY KEY, -- 表示id列是主键 
	`name` VARCHAR(32),
	email VARCHAR(32));
	
-- 主键列的值是不可以重复
INSERT INTO t17
	VALUES(1, 'jack', 'jack@sohu.com');
INSERT INTO t17
	VALUES(2, 'tom', 'tom@sohu.com');

INSERT INTO t17
	VALUES(1, 'hsp', 'hsp@sohu.com');
	
SELECT * FROM t17;

-- 主键使用的细节讨论
-- primary key不能重复而且不能为 null。
INSERT INTO t17
	VALUES(NULL, 'hsp', 'hsp@sohu.com');
-- 一张表最多只能有一个主键, 但可以是复合主键(比如 id+name)
CREATE TABLE t18
	(id INT PRIMARY KEY, -- 表示id列是主键 
	`name` VARCHAR(32), PRIMARY KEY -- 错误的
	email VARCHAR(32));
-- 演示复合主键 (id 和 name 做成复合主键)
CREATE TABLE t18
	(id INT , 
	`name` VARCHAR(32), 
	email VARCHAR(32),
	PRIMARY KEY (id, `name`) -- 这里就是复合主键
	);

INSERT INTO t18
	VALUES(1, 'tom', 'tom@sohu.com');
INSERT INTO t18
	VALUES(1, 'jack', 'jack@sohu.com');
INSERT INTO t18
	VALUES(1, 'tom', 'xx@sohu.com'); -- 这里就违反了复合主键
SELECT * FROM t18;

-- 主键的指定方式 有两种 
-- 1. 直接在字段名后指定：字段名  primakry key
-- 2. 在表定义最后写 primary key(列名); 
CREATE TABLE t19
	(id INT , 
	`name` VARCHAR(32) PRIMARY KEY, 
	email VARCHAR(32)
	);

CREATE TABLE t20
	(id INT , 
	`name` VARCHAR(32) , 
	email VARCHAR(32),
	PRIMARY KEY(`name`) -- 在表定义最后写 primary key(列名)
	);
 
-- 使用desc 表名，可以看到primary key的情况

DESC t20 -- 查看 t20表的结果，显示约束的情况
DESC t18
```

#### not null非空

![image-20220902210001455](E:\大学\学习资料\笔记\pictures\image-20220902210001455.png)

#### unique唯一

![image-20220902210022472](E:\大学\学习资料\笔记\pictures\image-20220902210022472.png)

#### foreign key外键

![image-20220902210450311](E:\大学\学习资料\笔记\pictures\image-20220902210450311.png)

![image-20220902212703641](E:\大学\学习资料\笔记\pictures\image-20220902212703641.png)

![image-20220902213341280](E:\大学\学习资料\笔记\pictures\image-20220902213341280.png)

```mysql
-- 外键演示

-- 创建 主表 my_class
CREATE TABLE my_class (
	id INT PRIMARY KEY , -- 班级编号
	`name` VARCHAR(32) NOT NULL DEFAULT '');

-- 创建 从表 my_stu
CREATE TABLE my_stu (
	id INT PRIMARY KEY , -- 学生编号
	`name` VARCHAR(32) NOT NULL DEFAULT '',
	class_id INT , -- 学生所在班级的编号
	-- 下面指定外键关系
	FOREIGN KEY (class_id) REFERENCES my_class(id))
-- 测试数据
INSERT INTO my_class 
	VALUES(100, 'java'), (200, 'web');
INSERT INTO my_class 
	VALUES(300, 'php');
	
SELECT * FROM my_class;
INSERT INTO my_stu 
	VALUES(1, 'tom', 100);
INSERT INTO my_stu 
	VALUES(2, 'jack', 200);
INSERT INTO my_stu 
	VALUES(3, 'hsp', 300);
INSERT INTO my_stu 
	VALUES(4, 'mary', 400); -- 这里会失败...因为400班级不存在

INSERT INTO my_stu 
	VALUES(5, 'king', NULL); -- 可以, 外键 没有写 not null
SELECT * FROM my_class;

-- 一旦建立主外键的关系，数据不能随意删除了
DELETE FROM my_class
	WHERE id = 100; 

```

#### check

![image-20220902214117107](E:\大学\学习资料\笔记\pictures\image-20220902214117107.png)

```mysql
-- 演示check的使用
-- mysql5.7目前还不支持check ,只做语法校验，但不会生效
-- 了解 
-- 学习 oracle, sql server, 这两个数据库是真的生效.

-- 测试
CREATE TABLE t23 (
	id INT PRIMARY KEY,
	`name` VARCHAR(32) ,
	sex VARCHAR(6) CHECK (sex IN('man','woman')),
	sal DOUBLE CHECK ( sal > 1000 AND sal < 2000)
	);
	
-- 添加数据
INSERT INTO t23 
	VALUES(1, 'jack', 'mid', 1);
SELECT * FROM t23;
```

### MySQL自增长

![image-20220904201827180](E:\大学\学习资料\笔记\pictures\image-20220904201827180.png)

![image-20220904202417312](E:\大学\学习资料\笔记\pictures\image-20220904202417312.png)

```mysql
-- 演示自增长的使用
-- 创建表
CREATE TABLE t24
	(id INT PRIMARY KEY AUTO_INCREMENT,
	 email VARCHAR(32)NOT NULL DEFAULT '',
	 `name` VARCHAR(32)NOT NULL DEFAULT ''); 
DESC t24
-- 测试自增长的使用
INSERT INTO t24
	VALUES(NULL, 'tom@qq.com', 'tom');

INSERT INTO t24
	(email, `name`) VALUES('hsp@sohu.com', 'hsp');

SELECT * FROM t24;

-- 修改默认的自增长开始值
ALTER TABLE t25 AUTO_INCREMENT = 100
CREATE TABLE t25
	(id INT PRIMARY KEY AUTO_INCREMENT,
	 email VARCHAR(32)NOT NULL DEFAULT '',
	 `name` VARCHAR(32)NOT NULL DEFAULT ''); 
INSERT INTO t25
	VALUES(NULL, 'mary@qq.com', 'mary');
INSERT INTO t25
	VALUES(666, 'hsp@qq.com', 'hsp');
SELECT * FROM t25;

CREATE DATABASE tmp;
CREATE TABLE dept( /*部门表*/
deptno MEDIUMINT   UNSIGNED  NOT NULL  DEFAULT 0,
dname VARCHAR(20)  NOT NULL  DEFAULT "",
loc VARCHAR(13) NOT NULL DEFAULT ""
) ;

#创建表EMP雇员
CREATE TABLE emp
(empno  MEDIUMINT UNSIGNED  NOT NULL  DEFAULT 0, /*编号*/
ename VARCHAR(20) NOT NULL DEFAULT "", /*名字*/
job VARCHAR(9) NOT NULL DEFAULT "",/*工作*/
mgr MEDIUMINT UNSIGNED NOT NULL DEFAULT 0,/*上级编号*/
hiredate DATE NOT NULL,/*入职时间*/
sal DECIMAL(7,2)  NOT NULL,/*薪水*/
comm DECIMAL(7,2) NOT NULL,/*红利*/
deptno MEDIUMINT UNSIGNED NOT NULL DEFAULT 0 /*部门编号*/
) ;

#工资级别表
CREATE TABLE salgrade
(
grade MEDIUMINT UNSIGNED NOT NULL DEFAULT 0,
losal DECIMAL(17,2)  NOT NULL,
hisal DECIMAL(17,2)  NOT NULL
);

#测试数据
INSERT INTO salgrade VALUES (1,700,1200);
INSERT INTO salgrade VALUES (2,1201,1400);
INSERT INTO salgrade VALUES (3,1401,2000);
INSERT INTO salgrade VALUES (4,2001,3000);
INSERT INTO salgrade VALUES (5,3001,9999);	

```

### MySQL索引

![image-20220904203533168](E:\大学\学习资料\笔记\pictures\image-20220904203533168.png)

```mysql
-- 在没有创建索引时，我们的查询一条记录
SELECT * 
	FROM emp 
	WHERE empno = 1234567 
-- 使用索引来优化一下， 体验索引的牛

-- 在没有创建索引前 , emp.ibd 文件大小 是 524m
-- 创建索引后 emp.ibd 文件大小 是 655m [索引本身也会占用空间.]
-- 创建ename列索引,emp.ibd 文件大小 是 827m

-- empno_index 索引名称 
-- ON emp (empno) : 表示在 emp表的 empno列创建索引
CREATE INDEX empno_index ON emp (empno)

-- 创建索引后， 查询的速度如何

SELECT * 
	FROM emp 
	WHERE empno = 1234578 -- 0.003s 原来是4.5s


-- 创建索引后，只对创建了索引的列有效 
SELECT * 
	FROM emp 
	WHERE ename = 'PjDlwy' -- 没有在ename创建索引时，时间4.7s

CREATE INDEX ename_index ON emp (ename) -- 在ename上创建索引
```

#### 索引的原理

![image-20220904214420700](E:\大学\学习资料\笔记\pictures\image-20220904214420700.png)

![image-20220904214327867](E:\大学\学习资料\笔记\pictures\image-20220904214327867.png)

#### 增删改查索引

![image-20220904214934105](E:\大学\学习资料\笔记\pictures\image-20220904214934105.png)

![image-20220904215756780](E:\大学\学习资料\笔记\pictures\image-20220904215756780.png)

![image-20220904215820097](E:\大学\学习资料\笔记\pictures\image-20220904215820097.png)

```mysql
-- 演示mysql的索引的使用
-- 创建索引
CREATE TABLE t25 (
	id INT ,
	`name` VARCHAR(32));
	
-- 查询表是否有索引
SHOW INDEXES FROM t25;
-- 添加索引
-- 添加唯一索引 
CREATE UNIQUE INDEX id_index ON t25 (id);
-- 添加普通索引方式1
CREATE INDEX id_index ON t25 (id);
-- 如何选择 
-- 1. 如果某列的值，是不会重复的，则优先考虑使用unique索引, 否则使用普通索引
-- 添加普通索引方式2
ALTER TABLE t25 ADD INDEX id_index (id)

-- 添加主键索引
CREATE TABLE t26 (
	id INT ,
	`name` VARCHAR(32));
ALTER TABLE t26 ADD PRIMARY KEY (id)

SHOW INDEX FROM t25

-- 删除索引
DROP INDEX id_index ON t25
-- 删除主键索引
ALTER TABLE t26 DROP PRIMARY KEY


-- 修改索引 ， 先删除，在添加新的索引

-- 查询索引
-- 1. 方式
SHOW INDEX FROM t25
-- 2. 方式
SHOW INDEXES FROM t25
-- 3. 方式
SHOW KEYS FROM t25
-- 4 方式
DESC t25
```

#### 索引应用场景

![image-20220904215950871](E:\大学\学习资料\笔记\pictures\image-20220904215950871-16622999930771.png)

### MySQL事务

![image-20220909123828482](E:\大学\学习资料\笔记\pictures\image-20220909123828482.png)

```mysql
-- 事务的一个重要的概念和具体操作
-- 看一个图[看示意图]
-- 演示
-- 1. 创建一张测试表
CREATE TABLE t27
	( id INT,
	  `name` VARCHAR(32));
-- 2. 开始事务
START TRANSACTION 
-- 3. 设置保存点
SAVEPOINT a
-- 执行dml 操作
INSERT INTO t27 VALUES(100, 'tom');
SELECT * FROM t27;

SAVEPOINT b
-- 执行dml操作
INSERT INTO t27 VALUES(200, 'jack');

-- 回退到 b
ROLLBACK TO b
-- 继续回退 a
ROLLBACK TO a
-- 如果这样, 表示直接回退到事务开始的状态.
ROLLBACK 
COMMIT
```

#### 事务理解

![image-20220909124604407](E:\大学\学习资料\笔记\pictures\image-20220909124604407.png)

![image-20220909131954741](E:\大学\学习资料\笔记\pictures\image-20220909131954741.png)

```mysql
-- 讨论 事务细节
-- 1. 如果不开始事务，默认情况下，dml操作是自动提交的，不能回滚
INSERT INTO t27 VALUES(300, 'milan'); -- 自动提交 commit

SELECT * FROM t27

-- 2. 如果开始一个事务，你没有创建保存点. 你可以执行 rollback，
-- 默认就是回退到你事务开始的状态
START TRANSACTION 
INSERT INTO t27 VALUES(400, 'king');
INSERT INTO t27 VALUES(500, 'scott');
ROLLBACK -- 表示直接回退到事务开始的的状态
COMMIT;

-- 3. 你也可以在这个事务中(还没有提交时), 创建多个保存点.比如: savepoint 	aaa;    
-- 执行 dml , savepoint  bbb

-- 4. 你可以在事务没有提交前，选择回退到哪个保存点
-- 5. InnoDB 存储引擎支持事务 , MyISAM 不支持
-- 6. 开始一个事务 start  transaction,    set autocommit=off;
```

#### 事务隔离级别

![image-20220912094604156](E:\大学\学习资料\笔记\pictures\image-20220912094604156.png)

![image-20220912094636216](E:\大学\学习资料\笔记\pictures\image-20220912094636216.png)

![image-20220912094916824](E:\大学\学习资料\笔记\pictures\image-20220912094916824.png)

![image-20220912095039493](E:\大学\学习资料\笔记\pictures\image-20220912095039493-1662947440591-1.png)

![image-20220912100946192](E:\大学\学习资料\笔记\pictures\image-20220912100946192.png)

![image-20220912101255152](E:\大学\学习资料\笔记\pictures\image-20220912101255152.png)

### MySQL存储引擎

![image-20220912101618422](E:\大学\学习资料\笔记\pictures\image-20220912101618422.png)

![image-20220912101946186](E:\大学\学习资料\笔记\pictures\image-20220912101946186.png)

![image-20220912102053678](E:\大学\学习资料\笔记\pictures\image-20220912102053678.png)

![image-20220912102313126](E:\大学\学习资料\笔记\pictures\image-20220912102313126.png)

![image-20220912103155643](E:\大学\学习资料\笔记\pictures\image-20220912103155643.png)

![image-20220912103249741](E:\大学\学习资料\笔记\pictures\image-20220912103249741-1662949970838-3.png)

### 视图

![image-20220912103424298](E:\大学\学习资料\笔记\pictures\image-20220912103424298.png)

![image-20220912103903465](E:\大学\学习资料\笔记\pictures\image-20220912103903465.png)

![image-20220912103952526](E:\大学\学习资料\笔记\pictures\image-20220912103952526.png)

![image-20220912104227918](E:\大学\学习资料\笔记\pictures\image-20220912104227918.png)

```mysql
-- 视图的使用
-- 创建一个视图emp_view01，只能查询emp表的(empno、ename, job 和 deptno ) 信息

-- 创建视图
CREATE VIEW emp_view01
	AS
	SELECT empno, ename, job, deptno FROM emp; 

-- 查看视图
DESC emp_view01

SELECT * FROM emp_view01;
SELECT empno, job  FROM emp_view01;

-- 查看创建视图的指令
SHOW CREATE VIEW emp_view01
-- 删除视图
DROP VIEW emp_view01;


-- 视图的细节

-- 1. 创建视图后，到数据库去看，对应视图只有一个视图结构文件(形式: 视图名.frm) 
-- 2. 视图的数据变化会影响到基表，基表的数据变化也会影响到视图[insert update delete ]

-- 修改视图 会影响到基表

UPDATE emp_view01 
	SET job = 'MANAGER' 
	WHERE empno = 7369
	
SELECT * FROM emp; -- 查询基表


SELECT * FROM emp_view01

-- 修改基本表， 会影响到视图

UPDATE emp 
	SET job = 'SALESMAN' 
	WHERE empno = 7369

-- 3. 视图中可以再使用视图 , 比如从emp_view01 视图中，选出empno,和ename做出新视图
DESC emp_view01

CREATE VIEW emp_view02
	AS
	SELECT empno, ename FROM emp_view01
	
SELECT * FROM emp_view02
```

![image-20220912115541384](E:\大学\学习资料\笔记\pictures\image-20220912115541384.png)

```mysql
-- 视图的课堂练习
-- 针对 emp ，dept , 和   salgrade 张三表.创建一个视图 emp_view03，
-- 可以显示雇员编号，雇员名，雇员部门名称和 薪水级别[即使用三张表，构建一个视图]

/*
	分析: 使用三表联合查询，得到结果
	将得到的结果，构建成视图
	  
*/
CREATE VIEW emp_view03
	AS
	SELECT empno, ename, dname, grade
	FROM emp, dept, salgrade
	WHERE emp.deptno = dept.deptno AND 
	(sal BETWEEN losal AND hisal) 

DESC emp_view03
SELECT * FROM emp_view03
```

### MySQL管理

![image-20220912185930197](E:\大学\学习资料\笔记\pictures\image-20220912185930197.png)

![image-20220912191426796](E:\大学\学习资料\笔记\pictures\image-20220912191426796.png)

![image-20220912192806945](E:\大学\学习资料\笔记\pictures\image-20220912192806945.png)

![image-20220912193851520](E:\大学\学习资料\笔记\pictures\image-20220912193851520.png)

```mysql
--  修改自己的密码, 没问题

SET PASSWORD = PASSWORD('abcdef')

-- 修改其他人的密码， 需要权限

SET PASSWORD FOR 'root'@'localhost' = PASSWORD('123456')
```

```mysql
-- Mysql用户的管理
-- 原因：当我们做项目开发时，可以根据不同的开发人员，赋给他相应的Mysql操作权限
-- 所以，Mysql数据库管理人员(root), 根据需要创建不同的用户，赋给相应的权限，供人员使用

-- 1. 创建新的用户
-- 解读 (1) 'hsp_edu'@'localhost' 表示用户的完整信息 'hsp_edu' 用户名 'localhost' 登录的IP
-- (2) 123456 密码, 但是注意 存放到 mysql.user表时，是password('123456') 加密后的密码
--     *6BB4837EB74329105EE4568DDA7DC67ED2CA2AD9
CREATE USER 'hsp_edu'@'localhost' IDENTIFIED BY '123456'

SELECT `host`, `user`, authentication_string  
	FROM mysql.user

-- 2. 删除用户
DROP USER 'hsp_edu'@'localhost'

-- 3. 登录

-- root 用户修改 hsp_edu@localhost 密码, 是可以成功.
SET PASSWORD FOR 'hsp_edu'@'localhost' = PASSWORD('123456')
```

![image-20220912194455524](E:\大学\学习资料\笔记\pictures\image-20220912194455524.png)

![image-20220912194628012](E:\大学\学习资料\笔记\pictures\image-20220912194628012.png)

![image-20220912195610371](E:\大学\学习资料\笔记\pictures\image-20220912195610371.png)

```mysql
-- 演示 用户权限的管理

-- 创建用户 shunping  密码 123 , 从本地登录
CREATE USER 'shunping'@'localhost' IDENTIFIED BY '123'

-- 使用root 用户创建 testdb  ,表 news
CREATE DATABASE testdb
CREATE TABLE news (
	id INT ,
	content VARCHAR(32));
-- 添加一条测试数据
INSERT INTO news VALUES(100, '北京新闻');
SELECT * FROM news;

-- 给 shunping 分配查看 news 表和 添加news的权限
GRANT SELECT , INSERT 
	ON testdb.news
	TO 'shunping'@'localhost'
	
-- 可以增加update权限
GRANT UPDATE  
	ON testdb.news
	TO 'shunping'@'localhost'
	
	
-- 修改 shunping的密码为 abc
SET PASSWORD FOR 'shunping'@'localhost' = PASSWORD('abc');

-- 回收 shunping 用户在 testdb.news 表的所有权限
REVOKE SELECT , UPDATE, INSERT ON testdb.news FROM 'shunping'@'localhost'
REVOKE ALL ON testdb.news FROM 'shunping'@'localhost'

-- 删除 shunping
DROP USER 'shunping'@'localhost'
```

![image-20220912195701693](E:\大学\学习资料\笔记\pictures\image-20220912195701693.png)

# JDBC和连接池

![image-20220914172259702](E:\大学\学习资料\笔记\pictures\image-20220914172259702.png)

![image-20220914173021802](E:\大学\学习资料\笔记\pictures\image-20220914173021802.png)

![image-20220914174906721](E:\大学\学习资料\笔记\pictures\image-20220914174906721.png)

![image-20220914175007330](E:\大学\学习资料\笔记\pictures\image-20220914175007330.png)

![image-20220914204044930](E:\大学\学习资料\笔记\pictures\image-20220914204044930.png)

## 注册驱动步骤

在项目下新建一个目录

![image-20220914205202803](E:\大学\学习资料\笔记\pictures\image-20220914205202803.png)

拷贝数据库驱动文件

![image-20220914205213749](E:\大学\学习资料\笔记\pictures\image-20220914205213749.png)

右击jar文件 add

![image-20220914205229043](E:\大学\学习资料\笔记\pictures\image-20220914205229043.png)

![image-20220914210252762](E:\大学\学习资料\笔记\pictures\image-20220914210252762.png)

```java
package com.hspedu.jdbc;

import com.mysql.jdbc.Driver;

import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 这是第一个Jdbc 程序，完成简单的操作
 */
public class Jdbc01 {
    public static void main(String[] args) throws SQLException {

        //前置工作： 在项目下创建一个文件夹比如 libs
        // 将 mysql.jar 拷贝到该目录下，点击 add to project ..加入到项目中
        //1. 注册驱动
        Driver driver = new Driver(); //创建driver对象

        //2. 得到连接
        // 老师解读
        //(1) jdbc:mysql:// 规定好表示协议，通过jdbc的方式连接mysql
        //(2) localhost 主机，可以是ip地址
        //(3) 3306 表示mysql监听的端口
        //(4) hsp_db02 连接到mysql dbms 的哪个数据库
        //(5) mysql的连接本质就是前面学过的socket连接
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        //将 用户名和密码放入到Properties 对象
        Properties properties = new Properties();
        //说明 user 和 password 是规定好，后面的值根据实际情况写
        properties.setProperty("user", "root");// 用户
        properties.setProperty("password", "hsp"); //密码
        Connection connect = driver.connect(url, properties);

        //3. 执行sql
        //String sql = "insert into actor values(null, '刘德华', '男', '1970-11-11', '110')";
        //String sql = "update actor set name='周星驰' where id = 1";
        String sql = "delete from actor where id = 1";
        //statement 用于执行静态SQL语句并返回其生成的结果的对象
        Statement statement = connect.createStatement();
        int rows = statement.executeUpdate(sql); // 如果是 dml语句，返回的就是影响行数

        System.out.println(rows > 0 ? "成功" : "失败");

        //4. 关闭连接资源
        statement.close();
        connect.close();

    }
}
```

## 获取数据库连接的五种方式

![image-20220914211324436](E:\大学\学习资料\笔记\pictures\image-20220914211324436.png)

![image-20220914214252769](E:\大学\学习资料\笔记\pictures\image-20220914214252769.png)

![image-20220914220154585](E:\大学\学习资料\笔记\pictures\image-20220914220154585.png)

![image-20220914220318287](E:\大学\学习资料\笔记\pictures\image-20220914220318287.png)

![image-20220914220906648](E:\大学\学习资料\笔记\pictures\image-20220914220906648.png)

![image-20220914220933466](E:\大学\学习资料\笔记\pictures\image-20220914220933466.png)

```java
package com.hspedu.jdbc;

import com.mysql.jdbc.Driver;
import org.junit.jupiter.api.Test;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 分析java 连接mysql的5中方式
 */
public class JdbcConn {

    //方式1
    @Test
    public void connect01() throws SQLException {
        Driver driver = new Driver(); //创建driver对象
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        //将 用户名和密码放入到Properties 对象
        Properties properties = new Properties();
        //说明 user 和 password 是规定好，后面的值根据实际情况写
        properties.setProperty("user", "root");// 用户
        properties.setProperty("password", "hsp"); //密码
        Connection connect = driver.connect(url, properties);
        System.out.println(connect);
    }

    //方式2
    @Test
    public void connect02() throws ClassNotFoundException, IllegalAccessException, InstantiationException, SQLException {
        //使用反射加载Driver类 , 动态加载，更加的灵活，减少依赖性
        Class<?> aClass = Class.forName("com.mysql.jdbc.Driver");
        Driver driver = (Driver)aClass.newInstance();

        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        //将 用户名和密码放入到Properties 对象
        Properties properties = new Properties();
        //说明 user 和 password 是规定好，后面的值根据实际情况写
        properties.setProperty("user", "root");// 用户
        properties.setProperty("password", "hsp"); //密码

        Connection connect = driver.connect(url, properties);
        System.out.println("方式2=" + connect);

    }

    //方式3 使用DriverManager 替代 driver 进行统一管理
    @Test
    public void connect03() throws IllegalAccessException, InstantiationException, ClassNotFoundException, SQLException {

        //使用反射加载Driver
        Class<?> aClass = Class.forName("com.mysql.jdbc.Driver");
        Driver driver = (Driver) aClass.newInstance();

        //创建url 和 user 和 password
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        String user = "root";
        String password = "hsp";

        DriverManager.registerDriver(driver);//注册Driver驱动

        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println("第三种方式=" + connection);
    }

    //方式4: 使用Class.forName 自动完成注册驱动，简化代码
    //这种方式获取连接是使用的最多，推荐使用
    @Test
    public void connect04() throws ClassNotFoundException, SQLException {
        //使用反射加载了 Driver类
        //在加载 Driver类时，完成注册
        /*
            源码: 1. 静态代码块，在类加载时，会执行一次.
            2. DriverManager.registerDriver(new Driver());
            3. 因此注册driver的工作已经完成
            static {
                try {
                    DriverManager.registerDriver(new Driver());
                } catch (SQLException var1) {
                    throw new RuntimeException("Can't register driver!");
                }
            }
         */
        Class.forName("com.mysql.jdbc.Driver");

        //创建url 和 user 和 password
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        String user = "root";
        String password = "hsp";
        Connection connection = DriverManager.getConnection(url, user, password);

        System.out.println("第4种方式~ " + connection);

    }

    //方式5 , 在方式4的基础上改进，增加配置文件，让连接mysql更加灵活
    @Test
    public void connect05() throws IOException, ClassNotFoundException, SQLException {

        //通过Properties对象获取配置文件的信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");

        Class.forName(driver);//建议写上

        Connection connection = DriverManager.getConnection(url, user, password);

        System.out.println("方式5 " + connection);


    }

} 

```

## ResultSet结果集

![image-20220916214423744](E:\大学\学习资料\笔记\pictures\image-20220916214423744.png)

![image-20220916220115658](E:\大学\学习资料\笔记\pictures\image-20220916220115658.png)

```java
package com.hspedu.jdbc.resultset_;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.sql.*;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示select 语句返回 ResultSet ,并取出结果
 */
@SuppressWarnings({"all"})
public class ResultSet_ {
    public static void main(String[] args) throws Exception {

        //通过Properties对象获取配置文件的信息


        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");

        //1. 注册驱动
        Class.forName(driver);//建议写上

        //2. 得到连接
        Connection connection = DriverManager.getConnection(url, user, password);

        //3. 得到Statement
        Statement statement = connection.createStatement();
        //4. 组织SqL
        String sql = "select id, name , sex, borndate from actor";
        //执行给定的SQL语句，该语句返回单个 ResultSet对象
        /*
        +----+-----------+-----+---------------------+
        | id | name      | sex | borndate            |
        +----+-----------+-----+---------------------+-------+
        |  4 | 刘德华    | 男  | 1970-12-12 00:00:00 |
        |  5 | jack      | 男  | 1990-11-11 00:00:00 |
        +----+-----------+-----+---------------------+-------+
         */
        /*
            老韩阅读debug 代码 resultSet 对象的结构


         */
        ResultSet resultSet = statement.executeQuery(sql);

        //5. 使用while取出数据
        while (resultSet.next()) { // 让光标向后移动，如果没有更多行，则返回false
            int id  = resultSet.getInt(1); //获取该行的第1列
            //int id1 = resultSet.getInt("id"); 通过列名来获取值, 推荐
            String name = resultSet.getString(2);//获取该行的第2列
            String sex = resultSet.getString(3);
            Date date = resultSet.getDate(4);

            System.out.println(id + "\t" + name + "\t" + sex + "\t" + date);
        }

        //6. 关闭连接
        resultSet.close();
        statement.close();
        connection.close();

    }
}
```

## SQL注入

![image-20220917104900268](E:\大学\学习资料\笔记\pictures\image-20220917104900268.png)

## PreparedStatement

![image-20220917105844593](E:\大学\学习资料\笔记\pictures\image-20220917105844593.png)

![image-20220917110200767](E:\大学\学习资料\笔记\pictures\image-20220917110200767.png)

```java
package com.hspedu.jdbc.preparedstatement_;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.sql.*;
import java.util.Properties;
import java.util.Scanner;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示PreparedStatement使用
 */
@SuppressWarnings({"all"})
public class PreparedStatement_ {
    public static void main(String[] args) throws Exception {

        //看 PreparedStatement类图

        Scanner scanner = new Scanner(System.in);

        //让用户输入管理员名和密码
        System.out.print("请输入管理员的名字: ");  //next(): 当接收到 空格或者 '就是表示结束
        String admin_name = scanner.nextLine(); // 老师说明，如果希望看到SQL注入，这里需要用nextLine
        System.out.print("请输入管理员的密码: ");
        String admin_pwd = scanner.nextLine();

        //通过Properties对象获取配置文件的信息

        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");

        //1. 注册驱动
        Class.forName(driver);//建议写上

        //2. 得到连接
        Connection connection = DriverManager.getConnection(url, user, password);

        //3. 得到PreparedStatement
        //3.1 组织SqL , Sql 语句的 ? 就相当于占位符
        String sql = "select name , pwd  from admin where name =? and pwd = ?";
        //3.2 preparedStatement 对象实现了 PreparedStatement 接口的实现类的对象
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        //3.3 给 ? 赋值
        preparedStatement.setString(1, admin_name);
        preparedStatement.setString(2, admin_pwd);

        //4. 执行 select 语句使用  executeQuery
        //   如果执行的是 dml(update, insert ,delete) executeUpdate()
        //   这里执行 executeQuery ,不要在写 sql

        ResultSet resultSet = preparedStatement.executeQuery(sql);
        if (resultSet.next()) { //如果查询到一条记录，则说明该管理存在
            System.out.println("恭喜， 登录成功");
        } else {
            System.out.println("对不起，登录失败");
        }

        //关闭连接
        resultSet.close();
        preparedStatement.close();
        connection.close();

    }
}
```

```java
package com.hspedu.jdbc.preparedstatement_;

import java.io.FileInputStream;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.Properties;
import java.util.Scanner;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示PreparedStatement使用 dml语句
 */
@SuppressWarnings({"all"})
public class PreparedStatementDML_ {
    public static void main(String[] args) throws Exception {

        //看 PreparedStatement类图

        Scanner scanner = new Scanner(System.in);

        //让用户输入管理员名和密码
        System.out.print("请输删除管理员的名字: ");  //next(): 当接收到 空格或者 '就是表示结束
        String admin_name = scanner.nextLine(); // 老师说明，如果希望看到SQL注入，这里需要用nextLine
//        System.out.print("请输入管理员的新密码: ");
//        String admin_pwd = scanner.nextLine();

        //通过Properties对象获取配置文件的信息

        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");

        //1. 注册驱动
        Class.forName(driver);//建议写上

        //2. 得到连接
        Connection connection = DriverManager.getConnection(url, user, password);

        //3. 得到PreparedStatement
        //3.1 组织SqL , Sql 语句的 ? 就相当于占位符
        //添加记录
        //String sql = "insert into admin values(?, ?)";
        //String sql = "update admin set pwd = ? where name = ?";
        String sql = "delete from  admin where name = ?";
        //3.2 preparedStatement 对象实现了 PreparedStatement 接口的实现类的对象
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        //3.3 给 ? 赋值
        preparedStatement.setString(1, admin_name);

        //preparedStatement.setString(2, admin_name);

        //4. 执行 dml 语句使用  executeUpdate
        int rows = preparedStatement.executeUpdate();
        System.out.println(rows > 0 ? "执行成功" : "执行失败");
        //关闭连接
        preparedStatement.close();
        connection.close();


    }
}
```

## JDBC API

![image-20220917174358554](E:\大学\学习资料\笔记\pictures\image-20220917174358554.png)

![image-20220917174437643](E:\大学\学习资料\笔记\pictures\image-20220917174437643.png)

![image-20220917174448026](E:\大学\学习资料\笔记\pictures\image-20220917174448026.png)

## 封装JDBCUtils

![image-20220917174514738](E:\大学\学习资料\笔记\pictures\image-20220917174514738.png)

```java
package com.hspedu.jdbc.utils;

import java.io.FileInputStream;
import java.io.IOException;
import java.sql.*;
import java.util.Properties;

/*
 * 这是一个工具类，完成 mysql的连接和关闭资源
 */
public class JDBCUtils {
    //定义相关的属性(4个), 因为只需要一份，因此，我们做出static
    private static String user; //用户名
    private static String password; //密码
    private static String url; //url
    private static String driver; //驱动名

    //在static代码块去初始化
    static {

        try {
            Properties properties = new Properties();
            properties.load(new FileInputStream("src\\mysql.properties"));
            //读取相关的属性值
            user = properties.getProperty("user");
            password = properties.getProperty("password");
            url = properties.getProperty("url");
            driver = properties.getProperty("driver");
        } catch (IOException e) {
            //在实际开发中，我们可以这样处理
            //1. 将编译异常转成 运行异常
            //2. 调用者，可以选择捕获该异常，也可以选择默认处理该异常，比较方便.
            throw new RuntimeException(e);

        }
    }

    //连接数据库, 返回Connection
    public static Connection getConnection() {

        try {
            return DriverManager.getConnection(url, user, password);
        } catch (SQLException e) {
            //1. 将编译异常转成 运行异常
            //2. 调用者，可以选择捕获该异常，也可以选择默认处理该异常，比较方便.
            throw new RuntimeException(e);
        }
    }

    //关闭相关资源
    /*
        1. ResultSet 结果集
        2. Statement 或者 PreparedStatement
        3. Connection
        4. 如果需要关闭资源，就传入对象，否则传入 null
     */
    public static void close(ResultSet set, Statement statement, Connection connection) {

        //判断是否为null
        try {
            if (set != null) {
                set.close();
            }
            if (statement != null) {
                statement.close();
            }
            if (connection != null) {
                connection.close();
            }
        } catch (SQLException e) {
            //将编译异常转成运行异常抛出
            throw new RuntimeException(e);
        }

    }

}
```

```java
package com.hspedu.jdbc.utils;

import org.junit.jupiter.api.Test;

import java.sql.*;

/**
 * @author 韩顺平
 * @version 1.0
 * 该类演示如何使用JDBCUtils工具类，完成dml 和 select
 */
public class JDBCUtils_Use {


    @Test
    public void testSelect() {
        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "select * from actor where id = ?";
        PreparedStatement preparedStatement = null;
        ResultSet set = null;
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtils.getConnection();
            System.out.println(connection.getClass()); //com.mysql.jdbc.JDBC4Connection
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.setInt(1, 5);//给?号赋值
            //执行, 得到结果集
            set = preparedStatement.executeQuery();
            //遍历该结果集
            while (set.next()) {
                int id = set.getInt("id");
                String name = set.getString("name");
                String sex = set.getString("sex");
                Date borndate = set.getDate("borndate");
                String phone = set.getString("phone");
                System.out.println(id + "\t" + name + "\t" + sex + "\t" + borndate + "\t" + phone);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtils.close(set, preparedStatement, connection);
        }
    }

    @Test
    public void testDML() {//insert , update, delete

        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "update actor set name = ? where id = ?";
        // 测试 delete 和 insert ,自己玩.
        PreparedStatement preparedStatement = null;
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtils.getConnection();

            preparedStatement = connection.prepareStatement(sql);
            //给占位符赋值
            preparedStatement.setString(1, "周星驰");
            preparedStatement.setInt(2, 4);
            //执行
            preparedStatement.executeUpdate();
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtils.close(null, preparedStatement, connection);
        }
    }
}
```

## 事务

![image-20220919212729497](E:\大学\学习资料\笔记\pictures\image-20220919212729497.png)

```java
package com.hspedu.jdbc.transaction_;

import com.hspedu.jdbc.utils.JDBCUtils;
import org.junit.jupiter.api.Test;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示jdbc 中如何使用事务
 */
public class Transaction_ {

    //没有使用事务.
    @Test
    public void noTransaction() {

        //操作转账的业务
        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "update account set balance = balance - 100 where id = 1";
        String sql2 = "update account set balance = balance + 100 where id = 2";
        PreparedStatement preparedStatement = null;
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtils.getConnection(); // 在默认情况下，connection是默认自动提交
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.executeUpdate(); // 执行第1条sql

            int i = 1 / 0; //抛出异常
            preparedStatement = connection.prepareStatement(sql2);
            preparedStatement.executeUpdate(); // 执行第3条sql


        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtils.close(null, preparedStatement, connection);
        }
    }

    //事务来解决
    @Test
    public void useTransaction() {

        //操作转账的业务
        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "update account set balance = balance - 100 where id = 1";
        String sql2 = "update account set balance = balance + 100 where id = 2";
        PreparedStatement preparedStatement = null;
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtils.getConnection(); // 在默认情况下，connection是默认自动提交
            //将 connection 设置为不自动提交
            connection.setAutoCommit(false); //开启了事务
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.executeUpdate(); // 执行第1条sql

            int i = 1 / 0; //抛出异常
            preparedStatement = connection.prepareStatement(sql2);
            preparedStatement.executeUpdate(); // 执行第3条sql

            //这里提交事务
            connection.commit();

        } catch (SQLException e) {
            //这里我们可以进行回滚，即撤销执行的SQL
            //默认回滚到事务开始的状态.
            System.out.println("执行发生了异常，撤销执行的sql");
            try {
                connection.rollback();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtils.close(null, preparedStatement, connection);
        }
    }
}
```

## 批处理

![image-20220919221446209](E:\大学\学习资料\笔记\pictures\image-20220919221446209.png)

```java
package com.hspedu.jdbc.batch_;

import com.hspedu.jdbc.utils.JDBCUtils;
import org.junit.jupiter.api.Test;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示java的批处理
 */
public class Batch_ {

    //传统方法，添加5000条数据到admin2

    @Test
    public void noBatch() throws Exception {

        Connection connection = JDBCUtils.getConnection();
        String sql = "insert into admin2 values(null, ?, ?)";
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        System.out.println("开始执行");
        long start = System.currentTimeMillis();//开始时间
        for (int i = 0; i < 5000; i++) {//5000执行
            preparedStatement.setString(1, "jack" + i);
            preparedStatement.setString(2, "666");
            preparedStatement.executeUpdate();
        }
        long end = System.currentTimeMillis();
        System.out.println("传统的方式 耗时=" + (end - start));//传统的方式 耗时=10702
        //关闭连接
        JDBCUtils.close(null, preparedStatement, connection);
    }

    //使用批量方式添加数据
    @Test
    public void batch() throws Exception {

        Connection connection = JDBCUtils.getConnection();
        String sql = "insert into admin2 values(null, ?, ?)";
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        System.out.println("开始执行");
        long start = System.currentTimeMillis();//开始时间
        for (int i = 0; i < 5000; i++) {//5000执行
            preparedStatement.setString(1, "jack" + i);
            preparedStatement.setString(2, "666");
            //将sql 语句加入到批处理包中 -> 看源码
            /*
            //1. //第一就创建 ArrayList - elementData => Object[]
            //2. elementData => Object[] 就会存放我们预处理的sql语句
            //3. 当elementData满后,就按照1.5扩容
            //4. 当添加到指定的值后，就executeBatch
            //5. 批量处理会减少我们发送sql语句的网络开销，而且减少编译次数，因此效率提高
            public void addBatch() throws SQLException {
                synchronized(this.checkClosed().getConnectionMutex()) {
                    if (this.batchedArgs == null) {

                        this.batchedArgs = new ArrayList();
                    }

                    for(int i = 0; i < this.parameterValues.length; ++i) {
                        this.checkAllParametersSet(this.parameterValues[i], this.parameterStreams[i], i);
                    }

                    this.batchedArgs.add(new PreparedStatement.BatchParams(this.parameterValues, this.parameterStreams, this.isStream, this.streamLengths, this.isNull));
                }
            }

             */
            preparedStatement.addBatch();
            //当有1000条记录时，在批量执行
            if((i + 1) % 1000 == 0) {//满1000条sql
                preparedStatement.executeBatch();
                //清空一把
                preparedStatement.clearBatch();
            }
        }
        long end = System.currentTimeMillis();
        System.out.println("批量方式 耗时=" + (end - start));//批量方式 耗时=108
        //关闭连接
        JDBCUtils.close(null, preparedStatement, connection);
    }
}
```

## 数据库连接池

传统连接方式

![image-20220920101120055](E:\大学\学习资料\笔记\pictures\image-20220920101120055.png)

![image-20220920101140912](E:\大学\学习资料\笔记\pictures\image-20220920101140912.png)

数据库连接池

![image-20220920102018821](E:\大学\学习资料\笔记\pictures\image-20220920102018821.png)

![image-20220920113100404](E:\大学\学习资料\笔记\pictures\image-20220920113100404.png)

![image-20220920121254398](E:\大学\学习资料\笔记\pictures\image-20220920121254398.png)

### C3P0

连接方式一

```java
package com.hspedu.jdbc.datasource;


import com.mchange.v2.c3p0.ComboPooledDataSource;
import org.junit.jupiter.api.Test;
import java.io.FileInputStream;
import java.sql.Connection;
import java.sql.SQLException;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示c3p0的使用
 */
public class C3P0_ {

    //方式1： 相关参数，在程序中指定user, url , password等
    @Test
    public void testC3P0_01() throws Exception {

        //1. 创建一个数据源对象
        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();
        //2. 通过配置文件mysql.properties 获取相关连接的信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //读取相关的属性值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");

        //给数据源 comboPooledDataSource 设置相关的参数
        //注意：连接管理是由 comboPooledDataSource 来管理
        comboPooledDataSource.setDriverClass(driver);
        comboPooledDataSource.setJdbcUrl(url);
        comboPooledDataSource.setUser(user);
        comboPooledDataSource.setPassword(password);

        //设置初始化连接数
        comboPooledDataSource.setInitialPoolSize(10);
        //最大连接数
        comboPooledDataSource.setMaxPoolSize(50);
        //测试连接池的效率, 测试对mysql 5000次操作
        long start = System.currentTimeMillis();
        for (int i = 0; i < 5000; i++) {
            Connection connection = comboPooledDataSource.getConnection(); //这个方法就是从 DataSource 接口实现的
            //System.out.println("连接OK");
            connection.close();
        }
        long end = System.currentTimeMillis();
        //c3p0 5000连接mysql 耗时=391
        System.out.println("c3p0 5000连接mysql 耗时=" + (end - start));

    }
```

连接方式二

```java
//第二种方式 使用配置文件模板来完成

    //1. 将c3p0 提供的 c3p0.config.xml 拷贝到 src目录下
    //2. 该文件指定了连接数据库和连接池的相关参数
    @Test
    public void testC3P0_02() throws SQLException {

        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource("hsp_edu");

        //测试5000次连接mysql
        long start = System.currentTimeMillis();
        System.out.println("开始执行....");
        for (int i = 0; i < 500000; i++) {
            Connection connection = comboPooledDataSource.getConnection();
            //System.out.println("连接OK~");
            connection.close();
        }
        long end = System.currentTimeMillis();
        //c3p0的第二种方式 耗时=413
        System.out.println("c3p0的第二种方式(500000) 耗时=" + (end - start));//1917

    }
}
```

### Druid(德鲁伊)

```java
package com.hspedu.jdbc.datasource;

import com.alibaba.druid.pool.DruidDataSourceFactory;
import org.junit.jupiter.api.Test;

import javax.sql.DataSource;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.sql.Connection;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 测试druid的使用
 */
public class Druid_ {

    @Test
    public void testDruid() throws Exception {
        //1. 加入 Druid jar包
        //2. 加入 配置文件 druid.properties , 将该文件拷贝项目的src目录
        //3. 创建Properties对象, 读取配置文件
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\druid.properties"));

        //4. 创建一个指定参数的数据库连接池, Druid连接池
        DataSource dataSource =
                DruidDataSourceFactory.createDataSource(properties);

        long start = System.currentTimeMillis();
        for (int i = 0; i < 500000; i++) {
            Connection connection = dataSource.getConnection();
            System.out.println(connection.getClass());
            //System.out.println("连接成功!");
            connection.close();
        }
        long end = System.currentTimeMillis();
        //druid连接池 操作5000 耗时=412
        System.out.println("druid连接池 操作500000 耗时=" + (end - start));//539


    }
}
```

JBDCUtilsByDruid

```java
package com.hspedu.jdbc.datasource;

import com.alibaba.druid.pool.DruidDataSourceFactory;

import javax.sql.DataSource;
import java.io.FileInputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;

/**
 * @author 韩顺平
 * @version 1.0
 * 基于druid数据库连接池的工具类
 */
public class JDBCUtilsByDruid {

    private static DataSource ds;

    //在静态代码块完成 ds初始化
    static {
        Properties properties = new Properties();
        try {
            properties.load(new FileInputStream("src\\druid.properties"));
            ds = DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            e.printStackTrace();
        }

    }

    //编写getConnection方法
    public static Connection getConnection() throws SQLException {
        return ds.getConnection();
    }

    //关闭连接, 老师再次强调： 在数据库连接池技术中，close 不是真的断掉连接
    //而是把使用的Connection对象放回连接池
    public static void close(ResultSet resultSet, Statement statement, Connection connection) {

        try {
            if (resultSet != null) {
                resultSet.close();
            }
            if (statement != null) {
                statement.close();
            }
            if (connection != null) {
                connection.close();
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }
}
```

JDBCByDruid使用

```java
package com.hspedu.jdbc.datasource;


import org.junit.jupiter.api.Test;

import java.sql.*;
import java.util.ArrayList;

/**
 * @author 韩顺平
 * @version 1.0
 */
@SuppressWarnings({"all"})
public class JDBCUtilsByDruid_USE {

    @Test
    public void testSelect() {

        System.out.println("使用 druid方式完成");
        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "select * from actor where id >= ?";
        PreparedStatement preparedStatement = null;
        ResultSet set = null;
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtilsByDruid.getConnection();
            System.out.println(connection.getClass());//运行类型 com.alibaba.druid.pool.DruidPooledConnection
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.setInt(1, 1);//给?号赋值
            //执行, 得到结果集
            set = preparedStatement.executeQuery();

            //遍历该结果集
            while (set.next()) {
                int id = set.getInt("id");
                String name = set.getString("name");//getName()
                String sex = set.getString("sex");//getSex()
                Date borndate = set.getDate("borndate");
                String phone = set.getString("phone");
                System.out.println(id + "\t" + name + "\t" + sex + "\t" + borndate + "\t" + phone);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtilsByDruid.close(set, preparedStatement, connection);
        }
    }

    //使用老师的土方法来解决ResultSet =封装=> Arraylist
    @Test
    public ArrayList<Actor> testSelectToArrayList() {

        System.out.println("使用 druid方式完成");
        //1. 得到连接
        Connection connection = null;
        //2. 组织一个sql
        String sql = "select * from actor where id >= ?";
        PreparedStatement preparedStatement = null;
        ResultSet set = null;
        ArrayList<Actor> list = new ArrayList<>();//创建ArrayList对象,存放actor对象
        //3. 创建PreparedStatement 对象
        try {
            connection = JDBCUtilsByDruid.getConnection();
            System.out.println(connection.getClass());//运行类型 com.alibaba.druid.pool.DruidPooledConnection
            preparedStatement = connection.prepareStatement(sql);
            preparedStatement.setInt(1, 1);//给?号赋值
            //执行, 得到结果集
            set = preparedStatement.executeQuery();

            //遍历该结果集
            while (set.next()) {
                int id = set.getInt("id");
                String name = set.getString("name");//getName()
                String sex = set.getString("sex");//getSex()
                Date borndate = set.getDate("borndate");
                String phone = set.getString("phone");
                //把得到的resultset 的记录，封装到 Actor对象，放入到list集合
                list.add(new Actor(id, name, sex, borndate, phone));
            }

            System.out.println("list集合数据=" + list);
            for(Actor actor : list) {
                System.out.println("id=" + actor.getId() + "\t" + actor.getName());
            }

        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            //关闭资源
            JDBCUtilsByDruid.close(set, preparedStatement, connection);
        }
        //因为ArrayList 和 connection 没有任何关联，所以该集合可以复用.
        return  list;
    }
}
```

## Apache——DBUtils

问题引出，resultSet在Connection断开后无法使用

![image-20220923205937814](E:\大学\学习资料\笔记\pictures\image-20220923205937814.png)

土方法实现数据库存到集合

ArrayList -> ResultSet 

正式介绍

![image-20220923220224496](E:\大学\学习资料\笔记\pictures\image-20220923220224496.png)

```java
package com.hspedu.jdbc.datasource;


import org.apache.commons.dbutils.QueryRunner;
import org.apache.commons.dbutils.handlers.BeanHandler;
import org.apache.commons.dbutils.handlers.BeanListHandler;
import org.apache.commons.dbutils.handlers.ScalarHandler;
import org.junit.jupiter.api.Test;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

/**
 * @author 韩顺平
 * @version 1.0
 */
@SuppressWarnings({"all"})
public class DBUtils_USE {

    //使用apache-DBUtils 工具类 + druid 完成对表的crud操作
    @Test
    public void testQueryMany() throws SQLException { //返回结果是多行的情况

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();
        //4. 就可以执行相关的方法，返回ArrayList 结果集
        //String sql = "select * from actor where id >= ?";
        //   注意: sql 语句也可以查询部分列
        String sql = "select id, name from actor where id >= ?";
        // 老韩解读
        //(1) query 方法就是执行sql 语句，得到resultset ---封装到 --> ArrayList 集合中
        //(2) 返回集合
        //(3) connection: 连接
        //(4) sql : 执行的sql语句
        //(5) new BeanListHandler<>(Actor.class): 在将resultset -> Actor 对象 -> 封装到 ArrayList
        //    底层使用反射机制 去获取Actor 类的属性，然后进行封装
        //(6) 1 就是给 sql 语句中的? 赋值，可以有多个值，因为是可变参数Object... params
        //(7) 底层得到的resultset ,会在query 关闭, 关闭PreparedStatment
        /**
         * 分析 queryRunner.query方法:
         * public <T> T query(Connection conn, String sql, ResultSetHandler<T> rsh, Object... params) throws SQLException {
         *         PreparedStatement stmt = null;//定义PreparedStatement
         *         ResultSet rs = null;//接收返回的 ResultSet
         *         Object result = null;//返回ArrayList
         *
         *         try {
         *             stmt = this.prepareStatement(conn, sql);//创建PreparedStatement
         *             this.fillStatement(stmt, params);//对sql 进行 ? 赋值
         *             rs = this.wrap(stmt.executeQuery());//执行sql,返回resultset
         *             result = rsh.handle(rs);//返回的resultset --> arrayList[result] [使用到反射，对传入class对象处理]
         *         } catch (SQLException var33) {
         *             this.rethrow(var33, sql, params);
         *         } finally {
         *             try {
         *                 this.close(rs);//关闭resultset
         *             } finally {
         *                 this.close((Statement)stmt);//关闭preparedstatement对象
         *             }
         *         }
         *
         *         return result;
         *     }
         */
        List<Actor> list =
                queryRunner.query(connection, sql, new BeanListHandler<>(Actor.class), 1);
        System.out.println("输出集合的信息");
        for (Actor actor : list) {
            System.out.print(actor);
        }


        //释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }

    //演示 apache-dbutils + druid 完成 返回的结果是单行记录(单个对象)
    @Test
    public void testQuerySingle() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();
        //4. 就可以执行相关的方法，返回单个对象
        String sql = "select * from actor where id = ?";
        // 老韩解读
        // 因为我们返回的单行记录<--->单个对象 , 使用的Hander 是 BeanHandler
        Actor actor = queryRunner.query(connection, sql, new BeanHandler<>(Actor.class), 10);
        System.out.println(actor);

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }

    //演示apache-dbutils + druid 完成查询结果是单行单列-返回的就是object
    @Test
    public void testScalar() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();

        //4. 就可以执行相关的方法，返回单行单列 , 返回的就是Object
        String sql = "select name from actor where id = ?";
        //老师解读： 因为返回的是一个对象, 使用的handler 就是 ScalarHandler
        Object obj = queryRunner.query(connection, sql, new ScalarHandler(), 4);
        System.out.println(obj);

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);
    }

    //演示apache-dbutils + druid 完成 dml (update, insert ,delete)
    @Test
    public void testDML() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();

        //4. 这里组织sql 完成 update, insert delete
        //String sql = "update actor set name = ? where id = ?";
        //String sql = "insert into actor values(null, ?, ?, ?, ?)";
        String sql = "delete from actor where id = ?";

        //老韩解读
        //(1) 执行dml 操作是 queryRunner.update()
        //(2) 返回的值是受影响的行数 (affected: 受影响)
        //int affectedRow = queryRunner.update(connection, sql, "林青霞", "女", "1966-10-10", "116");
        int affectedRow = queryRunner.update(connection, sql, 1000 );
        System.out.println(affectedRow > 0 ? "执行成功" : "执行没有影响到表");

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }
}
```

Apache_Use

![image-20220924120541071](E:\大学\学习资料\笔记\pictures\image-20220924120541071.png)

```java
package com.hspedu.jdbc.datasource;


import org.apache.commons.dbutils.QueryRunner;
import org.apache.commons.dbutils.handlers.BeanHandler;
import org.apache.commons.dbutils.handlers.BeanListHandler;
import org.apache.commons.dbutils.handlers.ScalarHandler;
import org.junit.jupiter.api.Test;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

/**
 * @author 韩顺平
 * @version 1.0
 */
@SuppressWarnings({"all"})
public class DBUtils_USE {

    //使用apache-DBUtils 工具类 + druid 完成对表的crud操作
    @Test
    public void testQueryMany() throws SQLException { //返回结果是多行的情况

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();
        //4. 就可以执行相关的方法，返回ArrayList 结果集
        //String sql = "select * from actor where id >= ?";
        //   注意: sql 语句也可以查询部分列
        String sql = "select id, name from actor where id >= ?";
        // 老韩解读
        //(1) query 方法就是执行sql 语句，得到resultset ---封装到 --> ArrayList 集合中
        //(2) 返回集合
        //(3) connection: 连接
        //(4) sql : 执行的sql语句
        //(5) new BeanListHandler<>(Actor.class): 在将resultset -> Actor 对象 -> 封装到 ArrayList
        //    底层使用反射机制 去获取Actor 类的属性，然后进行封装
        //(6) 1 就是给 sql 语句中的? 赋值，可以有多个值，因为是可变参数Object... params
        //(7) 底层得到的resultset ,会在query 关闭, 关闭PreparedStatment
        /**
         * 分析 queryRunner.query方法:
         * public <T> T query(Connection conn, String sql, ResultSetHandler<T> rsh, Object... params) throws SQLException {
         *         PreparedStatement stmt = null;//定义PreparedStatement
         *         ResultSet rs = null;//接收返回的 ResultSet
         *         Object result = null;//返回ArrayList
         *
         *         try {
         *             stmt = this.prepareStatement(conn, sql);//创建PreparedStatement
         *             this.fillStatement(stmt, params);//对sql 进行 ? 赋值
         *             rs = this.wrap(stmt.executeQuery());//执行sql,返回resultset
         *             result = rsh.handle(rs);//返回的resultset --> arrayList[result] [使用到反射，对传入class对象处理]
         *         } catch (SQLException var33) {
         *             this.rethrow(var33, sql, params);
         *         } finally {
         *             try {
         *                 this.close(rs);//关闭resultset
         *             } finally {
         *                 this.close((Statement)stmt);//关闭preparedstatement对象
         *             }
         *         }
         *
         *         return result;
         *     }
         */
        List<Actor> list =
                queryRunner.query(connection, sql, new BeanListHandler<>(Actor.class), 1);
        System.out.println("输出集合的信息");
        for (Actor actor : list) {
            System.out.print(actor);
        }


        //释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }

    //演示 apache-dbutils + druid 完成 返回的结果是单行记录(单个对象)
    @Test
    public void testQuerySingle() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();
        //4. 就可以执行相关的方法，返回单个对象
        String sql = "select * from actor where id = ?";
        // 老韩解读
        // 因为我们返回的单行记录<--->单个对象 , 使用的Hander 是 BeanHandler
        Actor actor = queryRunner.query(connection, sql, new BeanHandler<>(Actor.class), 10);
        System.out.println(actor);

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }

    //演示apache-dbutils + druid 完成查询结果是单行单列-返回的就是object
    @Test
    public void testScalar() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();

        //4. 就可以执行相关的方法，返回单行单列 , 返回的就是Object
        String sql = "select name from actor where id = ?";
        //老师解读： 因为返回的是一个对象, 使用的handler 就是 ScalarHandler
        Object obj = queryRunner.query(connection, sql, new ScalarHandler(), 4);
        System.out.println(obj);

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);
    }

    //演示apache-dbutils + druid 完成 dml (update, insert ,delete)
    @Test
    public void testDML() throws SQLException {

        //1. 得到 连接 (druid)
        Connection connection = JDBCUtilsByDruid.getConnection();
        //2. 使用 DBUtils 类和接口 , 先引入DBUtils 相关的jar , 加入到本Project
        //3. 创建 QueryRunner
        QueryRunner queryRunner = new QueryRunner();

        //4. 这里组织sql 完成 update, insert delete
        //String sql = "update actor set name = ? where id = ?";
        //String sql = "insert into actor values(null, ?, ?, ?, ?)";
        String sql = "delete from actor where id = ?";

        //老韩解读
        //(1) 执行dml 操作是 queryRunner.update()
        //(2) 返回的值是受影响的行数 (affected: 受影响)
        //int affectedRow = queryRunner.update(connection, sql, "林青霞", "女", "1966-10-10", "116");
        int affectedRow = queryRunner.update(connection, sql, 1000 );
        System.out.println(affectedRow > 0 ? "执行成功" : "执行没有影响到表");

        // 释放资源
        JDBCUtilsByDruid.close(null, null, connection);

    }
}
```

## Dao

![image-20220924175226049](E:\大学\学习资料\笔记\pictures\image-20220924175226049.png)

 

![image-20220925162313199](E:\大学\学习资料\笔记\pictures\image-20220925162313199.png)

![image-20220927133953192](E:\大学\学习资料\笔记\pictures\image-20220927133953192.png)

![image-20220925162345764](E:\大学\学习资料\笔记\pictures\image-20220925162345764.png)

![image-20220925162420269](E:\大学\学习资料\笔记\pictures\image-20220925162420269-1664258412185-1.png)

### BasicDao

```java
package com.hspedu.dao_.dao;

import com.hspedu.dao_.utils.JDBCUtilsByDruid;
import org.apache.commons.dbutils.QueryRunner;
import org.apache.commons.dbutils.handlers.BeanHandler;
import org.apache.commons.dbutils.handlers.BeanListHandler;
import org.apache.commons.dbutils.handlers.ScalarHandler;

import java.sql.Connection;
import java.sql.SQLException;
import java.util.List;

/**
 * @author 韩顺平
 * @version 1.0
 * 开发BasicDAO , 是其他DAO的父类
 */
public class BasicDAO<T> { //泛型指定具体类型

    private QueryRunner qr =  new QueryRunner();

    //开发通用的dml方法, 针对任意的表
    public int update(String sql, Object... parameters) {

        Connection connection = null;

        try {
            connection = JDBCUtilsByDruid.getConnection();
            int update = qr.update(connection, sql, parameters);
            return  update;
        } catch (SQLException e) {
           throw  new RuntimeException(e); //将编译异常->运行异常 ,抛出
        } finally {
            JDBCUtilsByDruid.close(null, null, connection);
        }

    }

    //返回多个对象(即查询的结果是多行), 针对任意表

    /**
     *
     * @param sql sql 语句，可以有 ?
     * @param clazz 传入一个类的Class对象 比如 Actor.class
     * @param parameters 传入 ? 的具体的值，可以是多个
     * @return 根据Actor.class 返回对应的 ArrayList 集合
     */
    public List<T> queryMulti(String sql, Class<T> clazz, Object... parameters) {

        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            return qr.query(connection, sql, new BeanListHandler<T>(clazz), parameters);

        } catch (SQLException e) {
            throw  new RuntimeException(e); //将编译异常->运行异常 ,抛出
        } finally {
            JDBCUtilsByDruid.close(null, null, connection);
        }

    }

    //查询单行结果 的通用方法
    public T querySingle(String sql, Class<T> clazz, Object... parameters) {

        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            return  qr.query(connection, sql, new BeanHandler<T>(clazz), parameters);

        } catch (SQLException e) {
            throw  new RuntimeException(e); //将编译异常->运行异常 ,抛出
        } finally {
            JDBCUtilsByDruid.close(null, null, connection);
        }
    }

    //查询单行单列的方法,即返回单值的方法

    public Object queryScalar(String sql, Object... parameters) {

        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            return  qr.query(connection, sql, new ScalarHandler(), parameters);

        } catch (SQLException e) {
            throw  new RuntimeException(e); //将编译异常->运行异常 ,抛出
        } finally {
            JDBCUtilsByDruid.close(null, null, connection);
        }
    }

}
```

### ActorDao

```JAVA
package com.hspedu.dao_.dao;

import com.hspedu.dao_.domain.Actor;

/**
 * @author 韩顺平
 * @version 1.0
 */
public class ActorDAO extends BasicDAO<Actor> {
    //1. 就有 BasicDAO 的方法
    //2. 根据业务需求，可以编写特有的方法.
}
```

### TestDao

```java
package com.hspedu.dao_.test;

import com.hspedu.dao_.dao.ActorDAO;
import com.hspedu.dao_.domain.Actor;
import org.junit.jupiter.api.Test;

import java.util.List;

/**
 * @author 韩顺平
 * @version 1.0
 */
public class TestDAO {

    //测试ActorDAO 对actor表crud操作
    @Test
    public void testActorDAO() {

        ActorDAO actorDAO = new ActorDAO();
        //1. 查询
        List<Actor> actors = actorDAO.queryMulti("select * from actor where id >= ?", Actor.class, 1);
        System.out.println("===查询结果===");
        for (Actor actor : actors) {
            System.out.println(actor);
        }

        //2. 查询单行记录
        Actor actor = actorDAO.querySingle("select * from actor where id = ?", Actor.class, 6);
        System.out.println("====查询单行结果====");
        System.out.println(actor);

        //3. 查询单行单列
        Object o = actorDAO.queryScalar("select name from actor where id = ?", 6);
        System.out.println("====查询单行单列值===");
        System.out.println(o);

        //4. dml操作  insert ,update, delete
        int update = actorDAO.update("insert into actor values(null, ?, ?, ?, ?)", "张无忌", "男", "2000-11-11", "999");

        System.out.println(update > 0 ? "执行成功" : "执行没有影响表");
    }
}
```

# 正则表达式

![image-20221010191103262](E:\大学\学习资料\笔记\pictures\image-20221010191103262.png)

基本介绍

![image-20221010191119727](E:\大学\学习资料\笔记\pictures\image-20221010191119727.png)

![image-20221010191536449](E:\大学\学习资料\笔记\pictures\image-20221010191536449.png)

```java
 //1. 先创建一个Pattern对象 ， 模式对象, 可以理解成就是一个正则表达式对象
        //Pattern pattern = Pattern.compile("[a-zA-Z]+");
        //Pattern pattern = Pattern.compile("[0-9]+");
        //Pattern pattern = Pattern.compile("([0-9]+)|([a-zA-Z]+)");
        //Pattern pattern = Pattern.compile("<a target=\"_blank\" title=\"(\\S*)\"");

        Pattern pattern = Pattern.compile("\\d+\\.\\d+\\.\\d+\\.\\d+");
        //2. 创建一个匹配器对象
        //理解： 就是 matcher 匹配器按照 pattern(模式/样式), 到 content 文本中去匹配
        //找到就返回true, 否则就返回false
        int no = 0;
        Matcher matcher = pattern.matcher(content);
        //3. 可以开始循环匹配
        while (matcher.find()) {
            //匹配内容，文本，放到 m.group(0)
            System.out.println("找到: " + (++no) + " " +matcher.group(0));
        }



    }
}
```

![image-20221010193153068](E:\大学\学习资料\笔记\pictures\image-20221010193153068.png)

```java
package com.hspedu.regexp;

import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
 * @author 韩顺平
 * @version 1.0
 * 分析java的正则表达式的底层实现(重要.)
 */
public class RegTheory {
    public static void main(String[] args) {

        String content = "1998年12月8日，第二代Java平台的企业版J2EE发布。1999年6月，Sun公司发布了" +
                "第二代Java平台（简称为Java2）的3个版本：J2ME（Java2 Micro Edition，Java2平台的微型" +
                "版），应用于移动、无线及有限资源的环境；J2SE（Java 2 Standard Edition，Java 2平台的" +
                "标准版），应用于桌面环境；J2EE（Java 2Enterprise Edition，Java 2平台的企业版），应" +
                "用3443于基于Java的应用服务器。Java 2平台的发布，是Java发展过程中最重要的一个" +
                "里程碑，标志着Java的应用开始普及9889 ";
        //目标：匹配所有四个数字
        //说明
        //1. \\d 表示一个任意的数字
        String regStr = "(\\d\\d)(\\d\\d)";
        //2. 创建模式对象[即正则表达式对象]
        Pattern pattern = Pattern.compile(regStr);
        //3. 创建匹配器
        //说明：创建匹配器matcher， 按照 正则表达式的规则 去匹配 content字符串
        Matcher matcher = pattern.matcher(content);

        //4.开始匹配
        /**
         *
         * matcher.find() 完成的任务 （考虑分组）
         * 什么是分组，比如  (\d\d)(\d\d) ,正则表达式中有() 表示分组,第1个()表示第1组,第2个()表示第2组...
         * 1. 根据指定的规则 ,定位满足规则的子字符串(比如(19)(98))
         * 2. 找到后，将 子字符串的开始的索引记录到 matcher对象的属性 int[] groups;
         *    2.1 groups[0] = 0 , 把该子字符串的结束的索引+1的值记录到 groups[1] = 4
         *    2.2 记录1组()匹配到的字符串 groups[2] = 0  groups[3] = 2
         *    2.3 记录2组()匹配到的字符串 groups[4] = 2  groups[5] = 4
         *    2.4.如果有更多的分组.....
         * 3. 同时记录oldLast 的值为 子字符串的结束的 索引+1的值即35, 即下次执行find时，就从35开始匹配
         *
         * matcher.group(0) 分析
         *
         * 源码:
         * public String group(int group) {
         *         if (first < 0)
         *             throw new IllegalStateException("No match found");
         *         if (group < 0 || group > groupCount())
         *             throw new IndexOutOfBoundsException("No group " + group);
         *         if ((groups[group*2] == -1) || (groups[group*2+1] == -1))
         *             return null;
         *         return getSubSequence(groups[group * 2], groups[group * 2 + 1]).toString();
         *     }
         *  1. 根据 groups[0]=31 和 groups[1]=35 的记录的位置，从content开始截取子字符串返回
         *     就是 [31,35) 包含 31 但是不包含索引为 35的位置
         *
         *  如果再次指向 find方法.仍然安上面分析来执行
         */
        while (matcher.find()) {
            //小结
            //1. 如果正则表达式有() 即分组
            //2. 取出匹配的字符串规则如下
            //3. group(0) 表示匹配到的子字符串
            //4. group(1) 表示匹配到的子字符串的第一组字串
            //5. group(2) 表示匹配到的子字符串的第2组字串
            //6. ... 但是分组的数不能越界.
            System.out.println("找到: " + matcher.group(0));
            System.out.println("第1组()匹配到的值=" + matcher.group(1));
            System.out.println("第2组()匹配到的值=" + matcher.group(2));


        }
    }
}     
```

## 语法

![image-20221010194301995](E:\大学\学习资料\笔记\pictures\image-20221010194301995.png)

### 元字符

#### 转义号

![image-20221010194354382](E:\大学\学习资料\笔记\pictures\image-20221010194354382.png)

```java
String content = "abc123()()$$$$#@@!";

        String str = "\\(";

        Pattern pattern = Pattern.compile(str);
        Matcher matcher = pattern.matcher(content);

        while(matcher.find()){
            System.out.println(matcher.group(0));
        }

// )
// )
```

#### 字符匹配符

![image-20221010194714086](E:\大学\学习资料\笔记\pictures\image-20221010194714086.png)

![image-20221010194820290](E:\大学\学习资料\笔记\pictures\image-20221010194820290.png)

![image-20221010195342114](E:\大学\学习资料\笔记\pictures\image-20221010195342114.png)

![image-20221010195916200](E:\大学\学习资料\笔记\pictures\image-20221010195916200.png)

![image-20221010200313014](E:\大学\学习资料\笔记\pictures\image-20221010200313014.png)

```java
package com.hspedu.regexp;

import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
 * @author 韩顺平
 * @version 1.0
 * 演示字符匹配符 的使用
 */
public class RegExp03 {
    public static void main(String[] args) {

        String content = "a11c8abc _ABCy @";
        //String regStr = "[a-z]";//匹配 a-z之间任意一个字符
        //String regStr = "[A-Z]";//匹配 A-Z之间任意一个字符
        //String regStr = "abc";//匹配 abc 字符串[默认区分大小写]
        //String regStr = "(?i)abc";//匹配 abc 字符串[不区分大小写]
        //String regStr = "[0-9]";//匹配 0-9 之间任意一个字符
        //String regStr = "[^a-z]";//匹配 不在 a-z之间任意一个字符
        //String regStr = "[^0-9]";//匹配 不在 0-9之间任意一个字符
        //String regStr = "[abcd]";//匹配 在 abcd中任意一个字符
        //String regStr = "\\D";//匹配 不在 0-9的任意一个字符
        //String regStr = "\\w";//匹配 大小写英文字母, 数字，下划线
        //String regStr = "\\W";//匹配 等价于 [^a-zA-Z0-9_]
        //\\s 匹配任何空白字符(空格,制表符等)
        //String regStr = "\\s";
        //\\S 匹配任何非空白字符 ,和\\s刚好相反
        //String regStr = "\\S";
        //.  匹配出 \n 之外的所有字符,如果要匹配.本身则需要使用 \\.
        String regStr = ".";

        //说明
        //1. 当创建Pattern对象时，指定 Pattern.CASE_INSENSITIVE, 表示匹配是不区分字母大小写.
        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/);
        Matcher matcher = pattern.matcher(content);


        while (matcher.find()) {
            System.out.println("找到 " + matcher.group(0));
        }
    }
}
```

#### 选择匹配符

![image-20221013200511483](E:\大学\学习资料\笔记\pictures\image-20221013200511483.png)

```java
String content = "hanshunping 韩 寒冷";
        String regStr = "han|韩|寒";

        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/);
        Matcher matcher = pattern.matcher(content);


        while (matcher.find()) {
            System.out.println("找到 " + matcher.group(0));
        }
```



#### 限定符

![image-20221013202331865](E:\大学\学习资料\笔记\pictures\image-20221013202331865.png)

![image-20221013202525831](E:\大学\学习资料\笔记\pictures\image-20221013202525831.png)        

![image-20221013204239593](E:\大学\学习资料\笔记\pictures\image-20221013204239593.png)

![image-20221013204320354](E:\大学\学习资料\笔记\pictures\image-20221013204320354.png)

![image-20221013204426209](E:\大学\学习资料\笔记\pictures\image-20221013204426209.png)

```java
String content = "a211111aaaaaahello";

        //a{3},1{4},\\d{2}
        //String regStr = "a{3}";// 表示匹配 aaa
        //String regStr = "1{4}";// 表示匹配 1111
        //String regStr = "\\d{2}";// 表示匹配 两位的任意数字字符

        //a{3,4},1{4,5},\\d{2,5}

        //细节：java匹配默认贪婪匹配，即尽可能匹配多的
        //String regStr = "a{3,4}"; //表示匹配 aaa 或者 aaaa
        //String regStr = "1{4,5}"; //表示匹配 1111 或者 11111
//String regStr = "\\d{2,5}"; //匹配2位数或者3,4,5


        //1+
        //String regStr = "1+"; //匹配一个1或者多个1
        //String regStr = "\\d+"; //匹配一个数字或者多个数字

        //1*
        //String regStr = "1*"; //匹配0个1或者多个1

        //演示?的使用, 遵守贪婪匹配
        String regStr = "a1?"; //匹配 a 或者 a1
        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/);
        Matcher matcher = pattern.matcher(content);
while (matcher.find()) {
            System.out.println("找到 " + matcher.group(0));
        }
```

### 定位符

![image-20221013205406221](E:\大学\学习资料\笔记\pictures\image-20221013205406221.png)

### 分组

![image-20221014133339347](E:\大学\学习资料\笔记\pictures\image-20221014133339347.png)

```java
		String content = "hanshunping s7789 nn1189han";

        //下面就是非命名分组
        //说明
        // 1. matcher.group(0) 得到匹配到的字符串
        // 2. matcher.group(1) 得到匹配到的字符串的第1个分组内容
        // 3. matcher.group(2) 得到匹配到的字符串的第2个分组内容

        //String regStr = "(\\d\\d)(\\d\\d)";//匹配4个数字的字符串

        //命名分组： 即可以给分组取名
        String regStr = "(?<g1>\\d\\d)(?<g2>\\d\\d)";//匹配4个数字的字符串

        Pattern pattern = Pattern.compile(regStr);
        Matcher matcher = pattern.matcher(content);

        while (matcher.find()) {
            System.out.println("找到=" + matcher.group(0));
            System.out.println("第1个分组内容=" + matcher.group(1));
            System.out.println("第1个分组内容[通过组名]=" + matcher.group("g1"));
            System.out.println("第2个分组内容=" + matcher.group(2));
            System.out.println("第2个分组内容[通过组名]=" + matcher.group("g2"));
```

![image-20221014133923192](E:\大学\学习资料\笔记\pictures\image-20221014133923192.png)

```java
String content = "hello韩顺平教育 jack韩顺平老师 韩顺平同学hello韩顺平学生";

//        找到 韩顺平教育 、韩顺平老师、韩顺平同学 子字符串
        //String regStr = "韩顺平教育|韩顺平老师|韩顺平同学";
        //上面的写法可以等价非捕获分组, 注意：不能 matcher.group(1)
        //String regStr = "韩顺平(?:教育|老师|同学)";

        //找到 韩顺平 这个关键字,但是要求只是查找韩顺平教育和 韩顺平老师 中包含有的韩顺平
        //下面也是非捕获分组，不能使用 matcher.group(1)
        //String regStr = "韩顺平(?=教育|老师)";

        //找到 韩顺平 这个关键字,但是要求只是查找 不是 (韩顺平教育 和 韩顺平老师) 中包含有的韩顺平
        //下面也是非捕获分组，不能使用 matcher.group(1)
        String regStr = "韩顺平(?!教育|老师)";

        Pattern pattern = Pattern.compile(regStr);
        Matcher matcher = pattern.matcher(content);
        while (matcher.find()) {
            System.out.println("找到: " + matcher.group(0));
        }
```

### 三大常用同类

![image-20221016172824663](E:\大学\学习资料\笔记\pictures\image-20221016172824663.png)

#### Pattern类

![image-20221016172906760](E:\大学\学习资料\笔记\pictures\image-20221016172906760.png)

#### Matchers

![image-20221016173326111](E:\大学\学习资料\笔记\pictures\image-20221016173326111.png)

![image-20221016173641644](E:\大学\学习资料\笔记\pictures\image-20221016173641644.png)

### 反向引用

![image-20221016173954482](E:\大学\学习资料\笔记\pictures\image-20221016173954482.png)

### 替换分割匹配

![image-20221017152211925](E:\大学\学习资料\笔记\pictures\image-20221017152211925.png)

# JDK8新特性

## Java8概述

- Java 8 (又称为jdk 1.8) 是Java 语言开发的一个主要版本。
- Java 8 是oracle公司于2014年3月发布，可以看成是自Java 5 以来最具革命性的版本。Java 8为Java语言、编译器、类库、开发工具与JVM带来了大量新特性。

![img](https://img-blog.csdnimg.cn/img_convert/873337fa3d817235541f830b76bfc87e.png)

## Java8新特性的好处

- 速度更快
- 代码更少(增加了新的语法：Lambda 表达式)
- 强大的Stream API
- 便于并行
- 最大化减少空指针异常：Optional
- Nashorn引擎，允许在JVM上运行JS应用

## 并行流与串行流

并行流就是把一个内容分成多个数据块，并用不同的线程分别处理每个数据块的流。相比较串行的流，并行的流可以很大程度上提高程序的执行效率。

Java 8 中将并行进行了优化，我们可以很容易的对数据进行并行操作。[Stream](https://so.csdn.net/so/search?q=Stream&spm=1001.2101.3001.7020) API 可以声明性地通过parallel() 与sequential() 在并行流与顺序流之间进行切换。

## [Lambda](https://so.csdn.net/so/search?q=Lambda&spm=1001.2101.3001.7020)表达式

Lambda 是一个匿名函数，我们可以把Lambda [表达式](https://so.csdn.net/so/search?q=表达式&spm=1001.2101.3001.7020)理解为是一段可以传递的代码（将代码像数据一样进行传递）。使用它可以写出更简洁、更灵活的代码。作为一种更紧凑的代码风格，使Java的语言表达能力得到了提升。

### Lambda表达式使用举例

```java
import org.junit.Test;

import java.util.Comparator;

/**
 * Lambda表达式的使用举例
 */
public class LambdaTest {
    @Test
    public void test(){
        Runnable r1 = new Runnable() {
            @Override
            public void run() {
                System.out.println("长安欢迎您");
            }
        };
        r1.run();

        System.out.println("+++++++++++++++++++++++++|");

        Runnable r2 = () -> System.out.println("长安欢迎您");

        r2.run();
    }

    @Test
    public void test2(){
        Comparator<Integer> c1 = new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return Integer.compare(o1,o2);
            }
        };
        int compare1 = c1.compare(8,16);
        System.out.println(compare1);

        System.out.println("+++++++++++++++++++++++");

        //Lambda表达式的写法
        Comparator<Integer> c2 = (o1,o2) -> Integer.compare(o1,o2);

        int compare2 = c2.compare(28,35);
        System.out.println(compare2);

        System.out.println("+++++++++++++++++++++++++++");
        //方法引用
        Comparator<Integer> c3 = Integer :: compare;

        int compare3 = c3.compare(28,35);
        System.out.println(compare3);
    }
}

```

### 4.2、Lambda表达式语法的使用1

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.function.Consumer;

/**
 * Lambda表达式的使用
 *
 * 1.举例： (o1,o2) -> Integer.compare(o1,o2);
 * 2.格式：
 *      -> :lambda操作符 或 箭头操作符
 *      ->左边：lambda形参列表 （其实就是接口中的抽象方法的形参列表）
 *      ->右边：lambda体 （其实就是重写的抽象方法的方法体）
 *
 * 3.Lambda表达式的使用：（分为6种情况介绍）
 */
public class LambdaTest1 {

    //语法格式一：无参，无返回值
    @Test
    public void test(){
        Runnable r1 = new Runnable() {
            @Override
            public void run() {
                System.out.println("长安欢迎您");
            }
        };
        r1.run();

        System.out.println("+++++++++++++++++++++++++|");

        Runnable r2 = () -> System.out.println("长安欢迎您");

        r2.run();
    }

    //语法格式二：Lambda 需要一个参数，但是没有返回值。
    @Test
    public void test2(){
        Consumer<String> con = new Consumer<String>() {
            @Override
            public void accept(String s) {
                System.out.println(s);
            }
        };
        con.accept("善与恶的区别是什么？");

        System.out.println("+++++++++++++++++++");

        Consumer<String> c1 = (String s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");
    }

    //语法格式三：数据类型可以省略，因为可由编译器推断得出，称为“类型推断”
    @Test
    public void test3(){
        Consumer<String> c1 = (String s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = (s) -> {
            System.out.println(s);
        };
        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }

    @Test
    public void test4(){
        ArrayList<String> list = new ArrayList<>();//类型推断

        int[] arr = {1,2,3};//类型推断
    }
}
```

### 4.3、Lambda表达式语法的使用2

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.function.Consumer;

/**
 * Lambda表达式的使用
 *
 * 1.举例： (o1,o2) -> Integer.compare(o1,o2);
 * 2.格式：
 *      -> :lambda操作符 或 箭头操作符
 *      ->左边：lambda形参列表 （其实就是接口中的抽象方法的形参列表）
 *      ->右边：lambda体 （其实就是重写的抽象方法的方法体）
 *
 * 3.Lambda表达式的使用：（分为6种情况介绍）
 *
 *    总结：
 *    ->左边：lambda形参列表的参数类型可以省略(类型推断)；如果lambda形参列表只有一个参数，其一对()也可以省略
 *    ->右边：lambda体应该使用一对{}包裹；如果lambda体只有一条执行语句（可能是return语句），省略这一对{}和return关键字
 */
public class LambdaTest1 {

    //语法格式四：Lambda若只需要一个参数时，参数的小括号可以省略
    @Test
    public void test5(){
        Consumer<String> c1 = (s) -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = s -> {
            System.out.println(s);
        };
        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }

    //语法格式五：Lambda需要两个或以上的参数，多条执行语句，并且可以有返回值
    @Test
    public void test6(){
        Comparator<Integer> c1 = new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                System.out.println(o1);
                System.out.println(o2);
                return o1.compareTo(o2);
            }
        };
        System.out.println(c1.compare(15,23));

        System.out.println("\\\\\\\\\\\\\\\\\\\\\\\\\\");

        Comparator<Integer> com2 = (o1,o2) -> {
            System.out.println(o1);
            System.out.println(o2);
            return o1.compareTo(o2);
        };
        System.out.println(com2.compare(16,8));
    }

    //语法格式六：当Lambda体只有一条语句时，return与大括号若有，都可以省略
    @Test
    public void test7(){
        Comparator<Integer> c1 = (o1,o2) -> {
            return o1.compareTo(o2);
        };

        System.out.println(c1.compare(16,8));

        System.out.println("\\\\\\\\\\\\\\\\\\\\\\\\\\");

        Comparator<Integer> c2 = (o1,o2) -> o1.compareTo(o2);

        System.out.println(c2.compare(17,24));
    }

    @Test
    public void test8(){
        Consumer<String> c1 = s -> {
            System.out.println(s);
        };
        c1.accept("先天人性无善恶,后天人性有善恶。");

        System.out.println("---------------------");

        Consumer<String> c2 = s -> System.out.println(s);

        c2.accept("如果没有邪恶的话我们怎么会知道人世间的那些善良呢？");
    }
}
```

**3.2.1 语法格式一：无参，有返回值**

```java
Runnable r1 = () -> {System.out.println(“hello Lamdba!”)}
复制代码
```

**3.2.2 语法格式二：Lamdba需要一个参数，但没有返回值**

```java
Consumer<String> con = (String str) -> {System.out.println(str)}
复制代码
```

**3.2.3 语法格式三：数据类型可省略，因为可由编译器推断得出，称为类型推断**

```java
Consumer<String> con = (str) -> {System.out.println(str)}
复制代码
```

**3.2.4 语法格式四：Lamdba若只需要一个参数时，小括号可以省略**

```java
Consumer<String> con = str -> {System.out.println(str)}
复制代码
```

**3.2.5 语法格式五：Lamdba需要两个以上的参数，多条执行语句，并且可以有返回值**

```java
Comparator<Integer>com = (o1,o1) -> {
	Syste.out.println("Lamdba表达式使用");
    return Integer.compare(o1,o2);
}
复制代码
```

**3.2.6 语法格式六：当Lamdba体只有一条语句时，return和大括号若有，都可以省略**

```java
Comparator<Integer>com = (o1,o1) ->	Integer.compare(o1,o2);
```

## 05、函数式(Functional)接口

### 5.1、[函数式接口](https://so.csdn.net/so/search?q=函数式接口&spm=1001.2101.3001.7020)的介绍

```java
/*
 * 4.Lambda表达式的本质：作为函数式接口的实例
 *
 * 5. 如果一个接口中，只声明了一个抽象方法，则此接口就称为函数式接口。我们可以在一个接口上使用 @FunctionalInterface 注解，
 *   这样做可以检查它是否是一个函数式接口。
 *
 */

/**
 * 自定义函数式接口
 */
public interface MyInterFace {

    void method();

//    void method2();
    
}
```

- 在`java.util.function`包下定义了Java 8 的丰富的函数式接口
- Java从诞生日起就是一直倡导“一切皆对象”，在Java里面面向对象(OOP)编程是一切。但是随着python、scala等语言的兴起和新技术的挑战，Java不得不做出调整以便支持更加广泛的技术要求，也即java不但可以支持OOP还可以支持OOF（面向函数编程）
- 在函数式编程语言当中，函数被当做一等公民对待。在将函数作为一等公民的编程语言中，Lambda表达式的类型是函数。但是在Java8中，有所不同。在Java8中，Lambda表达式是对象，而不是函数，它们必须依附于一类特别的对象类型——函数式接口。
- 简单的说，在Java8中，Lambda表达式就是一个函数式接口的实例。这就是Lambda表达式和函数式接口的关系。也就是说，**只要一个对象是函数式接口的实例，那么该对象就可以用Lambda表达式来表示**。
- **所以以前用匿名实现类表示的现在都可以用Lambda表达式来写。**

### 5.2、Java内置的函数式接口介绍及使用举例

| 函数式接口                         | 参数类型 | 返回类型 | 用途                                                         |
| ---------------------------------- | -------- | -------- | ------------------------------------------------------------ |
| `Consumer` 消费型接口              | T        | void     | 对类型为T的对象应用操作，包含方法：`void accept(T t)`        |
| `Supplier` 供给型接口              | 无       | T        | 返回类型为T的对象，包含方法：`T get()`                       |
| `Function<T, R>`函数型接口         | T        | R        | 对类型为T的对象应用操作，并返回结果。结果是R类型的对象。包含方法：`R apply(T t)` |
| `Predicate`断定型接口              | T        | boolean  | 确定类型为T的对象是否满足某约束，并返回boolean 值。包含方法：`boolean test(T t)` |
| `BiFunction<T,U,R>`                | T, U     | R        | 对类型为T,U参数应用操作，返回R类型的结果。包含方法为：`Rapply(T t,U u)`; |
| `UnaryOperator`(Function子接口)    | T        | T        | 对类型为T的对象进行一元运算，并返回T类型的结果。包含方法为：`Tapply(T t)`; |
| `BinaryOperator`(BiFunction子接口) | T,T      | T        | 对类型为T的对象进行二元运算，并返回T类型的结果。包含方法为：`Tapply(T t1,T t2)`; |
| `BiConsumer<T,U>`                  | T,U      | void     | 对类型为T,U参数应用操作。包含方法为：`voidaccept(Tt,Uu)`     |
| `BiPredicate<T,U>`                 | T,U      | boolean  | 包含方法为：`booleantest(Tt,Uu)`                             |
| `ToIntFunction`                    | T        | int      | 计算`int`值的函数                                            |
| `ToLongFunction`                   | T        | long     | 计算`long`值的函数                                           |
| `ToDoubleFunction`                 | T        | double   | 计算`double`值的函数                                         |
| `IntFunction`                      | int      | R        | 参数为`int`类型的函数                                        |
| `LongFunction`                     | long     | R        | 参数为`long`类型的函数                                       |
| `DoubleFunction`                   | double   | R        | 参数为`double`类型的函数                                     |

```java
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;
import java.util.function.Predicate;

/**
 * java内置的4大核心函数式接口
 *
 * 消费型接口 Consumer<T>     void accept(T t)
 * 供给型接口 Supplier<T>     T get()
 * 函数型接口 Function<T,R>   R apply(T t)
 * 断定型接口 Predicate<T>    boolean test(T t)
 */
public class LambdaTest2 {

    public void happyTime(double money, Consumer<Double> con) {
        con.accept(money);
    }

    @Test
    public void test(){
        happyTime(30, new Consumer<Double>() {
            @Override
            public void accept(Double aDouble) {
                System.out.println("熬夜太累了，点个外卖，价格为：" + aDouble);
            }
        });
        System.out.println("+++++++++++++++++++++++++");

        //Lambda表达式写法
        happyTime(20,money -> System.out.println("熬夜太累了，吃口麻辣烫，价格为：" + money));
    }

    //根据给定的规则，过滤集合中的字符串。此规则由Predicate的方法决定
    public List<String> filterString(List<String> list, Predicate<String> pre){

        ArrayList<String> filterList = new ArrayList<>();
        for(String s : list){
            if(pre.test(s)){
                filterList.add(s);
            }
        }
        return filterList;

    }

    @Test
    public void test2(){
        List<String> list = Arrays.asList("长安","上京","江南","渝州","凉州","兖州");

        List<String> filterStrs = filterString(list, new Predicate<String>() {
            @Override
            public boolean test(String s) {
                return s.contains("州");
            }
        });

        System.out.println(filterStrs);

        List<String> filterStrs1 = filterString(list,s -> s.contains("州"));
        System.out.println(filterStrs1);
    }
}
123456789101112131415161718192021222324252627282930313233343536373839404142434445464748495051525354555657585960616263646566
```

## 06、方法引用与构造器引用

- 当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用！
- 方法引用可以看做是Lambda表达式深层次的表达。换句话说，方法引用就是Lambda表达式，也就是函数式接口的一个实例，通过方法的名字来指向一个方法，可以认为是Lambda表达式的一个语法糖。
- 要求：实现接口的抽象方法的参数列表和返回值类型，必须与方法引用的方法的参数列表和返回值类型保持一致！
- 格式：使用操作符“::” 将类(或对象) 与方法名分隔开来。
- 如下三种主要使用情况：
  - **对象::实例方法名**
  - **类::静态方法名**
  - **类::实例方法名**

### 6.1、方法引用的使用情况1

> 1、Employee类

```java
public class Employee {

	private int id;
	private String name;
	private int age;
	private double salary;

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
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

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public Employee() {
		System.out.println("Employee().....");
	}

	public Employee(int id) {
		this.id = id;
		System.out.println("Employee(int id).....");
	}

	public Employee(int id, String name) {
		this.id = id;
		this.name = name;
	}

	public Employee(int id, String name, int age, double salary) {

		this.id = id;
		this.name = name;
		this.age = age;
		this.salary = salary;
	}

	@Override
	public String toString() {
		return "Employee{" + "id=" + id + ", name='" + name + '\'' + ", age=" + age + ", salary=" + salary + '}';
	}

	@Override
	public boolean equals(Object o) {
		if (this == o)
			return true;
		if (o == null || getClass() != o.getClass())
			return false;

		Employee employee = (Employee) o;

		if (id != employee.id)
			return false;
		if (age != employee.age)
			return false;
		if (Double.compare(employee.salary, salary) != 0)
			return false;
		return name != null ? name.equals(employee.name) : employee.name == null;
	}

	@Override
	public int hashCode() {
		int result;
		long temp;
		result = id;
		result = 31 * result + (name != null ? name.hashCode() : 0);
		result = 31 * result + age;
		temp = Double.doubleToLongBits(salary);
		result = 31 * result + (int) (temp ^ (temp >>> 32));
		return result;
	}
}

```

> 2、测试类

```java
import org.junit.Test;

import java.io.PrintStream;
import java.util.Comparator;
import java.util.function.BiPredicate;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Supplier;

/**
 * 方法引用的使用
 *
 * 1.使用情境：当要传递给Lambda体的操作，已经有实现的方法了，可以使用方法引用！
 *
 * 2.方法引用，本质上就是Lambda表达式，而Lambda表达式作为函数式接口的实例。所以
 *   方法引用，也是函数式接口的实例。
 *
 * 3. 使用格式：  类(或对象) :: 方法名
 *
 * 4. 具体分为如下的三种情况：
 *    情况1     对象 :: 非静态方法
 *    情况2     类 :: 静态方法
 *
 *    情况3     类 :: 非静态方法
 *
 * 5. 方法引用使用的要求：要求接口中的抽象方法的形参列表和返回值类型与方法引用的方法的
 *    形参列表和返回值类型相同！（针对于情况1和情况2）
 */
public class MethodRefTest {
    
    // 情况一：对象 :: 实例方法
    //Consumer中的void accept(T t)
    //PrintStream中的void println(T t)
    @Test
    public void test() {
        Consumer<String> c1 = str -> System.out.println(str);
        c1.accept("兖州");

        System.out.println("+++++++++++++");
        PrintStream ps = System.out;
        Consumer<String> c2 = ps::println;
        c2.accept("xian");
    }

    //Supplier中的T get()
    //Employee中的String getName()
    @Test
    public void test2() {
        Employee emp = new Employee(004,"Nice",19,4200);

        Supplier<String> sk1 = () -> emp.getName();
        System.out.println(sk1.get());

        System.out.println("*******************");
        Supplier<String> sk2 = emp::getName;
        System.out.println(sk2.get());
    }
}
12345678910111213141516171819202122232425262728293031323334353637383940414243444546474849505152535455565758
```

### 6.2、方法引用的使用情况2

> 1、Employee类——同上

> 2、测试类

```java
import org.junit.Test;
import java.util.Comparator;
import java.util.function.Function;

public class MethodRefTest {

    // 情况二：类 :: 静态方法
    //Comparator中的int compare(T t1,T t2)
    //Integer中的int compare(T t1,T t2)
    @Test
    public void test3() {
        Comparator<Integer> com1 = (t1, t2) -> Integer.compare(t1,t2);
        System.out.println(com1.compare(21,20));

        System.out.println("+++++++++++++++");

        Comparator<Integer> com2 = Integer::compare;
        System.out.println(com2.compare(15,7));
    }

    //Function中的R apply(T t)
    //Math中的Long round(Double d)
    @Test
    public void test4() {
        Function<Double,Long> func = new Function<Double, Long>() {
            @Override
            public Long apply(Double d) {
                return Math.round(d);
            }
        };

        System.out.println("++++++++++++++++++");

        Function<Double,Long> func1 = d -> Math.round(d);
        System.out.println(func1.apply(14.1));

        System.out.println("++++++++++++++++++");

        Function<Double,Long> func2 = Math::round;
        System.out.println(func2.apply(17.4));
    }
}
123456789101112131415161718192021222324252627282930313233343536373839404142
```

### 6.2、方法引用的使用情况3

> 1、Employee类——同上

> 2、测试类

```java
import org.junit.Test;

import java.util.Comparator;
import java.util.function.BiPredicate;
import java.util.function.Function;

public class MethodRefTest {

    // 情况三：类 :: 实例方法  (有难度)
    // Comparator中的int comapre(T t1,T t2)
    // String中的int t1.compareTo(t2)
    @Test
    public void test5() {
        Comparator<String> com1 = (s1,s2) -> s1.compareTo(s2);
        System.out.println(com1.compare("abc","abd"));

        System.out.println("++++++++++++++++");

        Comparator<String> com2 = String :: compareTo;
        System.out.println(com2.compare("abd","abm"));
    }

    //BiPredicate中的boolean test(T t1, T t2);
    //String中的boolean t1.equals(t2)
    @Test
    public void test6() {
        BiPredicate<String,String> pre1 = (s1, s2) -> s1.equals(s2);
        System.out.println(pre1.test("MON","MON"));

        System.out.println("++++++++++++++++++++");
        
        BiPredicate<String,String> pre2 = String :: equals;
        System.out.println(pre2.test("MON","MON"));
    }

    // Function中的R apply(T t)
    // Employee中的String getName();
    @Test
    public void test7() {
        Employee employee = new Employee(007, "Ton", 21, 8000);

        Function<Employee,String> func1 = e -> e.getName();
        System.out.println(func1.apply(employee));

        System.out.println("++++++++++++++++++++++++");

        Function<Employee,String> f2 = Employee::getName;
        System.out.println(f2.apply(employee));
    }
}
1234567891011121314151617181920212223242526272829303132333435363738394041424344454647484950
```

### 6.4、构造器引用与[数组](https://so.csdn.net/so/search?q=数组&spm=1001.2101.3001.7020)引用的使用

> 格式：ClassName::new

与函数式接口相结合，自动与函数式接口中方法兼容。

可以把构造器引用赋值给定义的方法，要求构造器参数列表要与接口中抽象方法的参数列表一致！且方法的返回值即为构造器对应类的对象。

> 1、Employee类——同上

> 2、测试类

```java
import org.junit.Test;

import java.util.Arrays;
import java.util.function.BiFunction;
import java.util.function.Function;
import java.util.function.Supplier;

/**
 * 一、构造器引用
 *      和方法引用类似，函数式接口的抽象方法的形参列表和构造器的形参列表一致。
 *      抽象方法的返回值类型即为构造器所属的类的类型
 *
 * 二、数组引用
 *     可以把数组看做是一个特殊的类，则写法与构造器引用一致。 
 */
public class MethodRefTest {

    //构造器引用
    //Supplier中的T get()
    //Employee的空参构造器：Employee()
    @Test
    public void test() {
        Supplier<Employee> sup = new Supplier<Employee>() {
            @Override
            public Employee get() {
                return new Employee();
            }
        };
        System.out.println("+++++++++++++++++++");

        Supplier<Employee> sk1 = () -> new Employee();
        System.out.println(sk1.get());

        System.out.println("+++++++++++++++++++");

        Supplier<Employee> sk2 = Employee::new;
        System.out.println(sk2.get());
    }

    //Function中的R apply(T t)
    @Test
    public void test2() {
        Function<Integer, Employee> f1 = id -> new Employee(id);
        Employee employee = f1.apply(7793);
        System.out.println(employee);

        System.out.println("+++++++++++++++++++");

        Function<Integer, Employee> f2 = Employee::new;
        Employee employee1 = f2.apply(4545);
        System.out.println(employee1);
    }

    //BiFunction中的R apply(T t,U u)
    @Test
    public void test3() {
        BiFunction<Integer, String, Employee> f1 = (id, name) -> new Employee(id, name);
        System.out.println(f1.apply(2513, "Fruk"));

        System.out.println("*******************");

        BiFunction<Integer, String, Employee> f2 = Employee::new;
        System.out.println(f2.apply(9526, "Bon"));
    }

    //数组引用
    //Function中的R apply(T t)
    @Test
    public void test4() {
        Function<Integer, String[]> f1 = length -> new String[length];
        String[] arr1 = f1.apply(7);
        System.out.println(Arrays.toString(arr1));

        System.out.println("+++++++++++++++++++");

        Function<Integer, String[]> f2 = String[]::new;
        String[] arr2 = f2.apply(9);
        System.out.println(Arrays.toString(arr2));
    }
}
1234567891011121314151617181920212223242526272829303132333435363738394041424344454647484950515253545556575859606162636465666768697071727374757677787980
```

## 07、强大的Stream [API](https://so.csdn.net/so/search?q=API&spm=1001.2101.3001.7020)

### 7.1、Stream API的概述

- Java8中有两大最为重要的改变。第一个是Lambda 表达式；另外一个则是Stream API。
- Stream API ( `java.util.stream`)把真正的函数式编程风格引入到Java中。这是目前为止对Java类库最好的补充，因为Stream API可以极大提供Java程序员的生产力，让程序员写出高效率、干净、简洁的代码。
- Stream 是Java8 中处理集合的关键抽象概念，它可以指定你希望对集合进行的操作，可以执行非常复杂的查找、过滤和映射数据等操作。使用Stream API 对集合数据进行操作，就类似于使用SQL 执行的数据库查询。也可以使用Stream API 来并行执行操作。简言之，Stream API 提供了一种高效且易于使用的处理数据的方式。
- 为什么要使用Stream API
  - **实际开发中，项目中多数数据源都来自于Mysql，Oracle等。但现在数据源可以更多了，有MongDB，Radis等，而这些NoSQL的数据就需要Java层面去处理**。
  - **Stream 和Collection 集合的区别：Collection 是一种静态的内存数据结构，而Stream 是有关计算的。前者是主要面向内存，存储在内存中，后者主要是面向CPU，通过CPU 实现计算**。

```java
/**
 * 1.Stream关注的是对数据的运算，与CPU打交道
 *   集合关注的是数据的存储，与内存打交道
 *
 * 2.
 * ①Stream 自己不会存储元素。
 * ②Stream 不会改变源对象。相反，他们会返回一个持有结果的新Stream。
 * ③Stream 操作是延迟执行的。这意味着他们会等到需要结果的时候才执行
 *
 * 3.Stream 执行流程
 * ① Stream的实例化
 * ② 一系列的中间操作（过滤、映射、...)
 * ③ 终止操作
 *
 * 4.说明：
 * 4.1 一个中间操作链，对数据源的数据进行处理
 * 4.2 一旦执行终止操作，就执行中间操作链，并产生结果。之后，不会再被使用
 */
123456789101112131415161718
```

![img](https://img-blog.csdnimg.cn/img_convert/c4f4c62e55b8182fa7c99cd15a0d7de0.png)

### 7.2、Stream的实例化

> 1、EmployeeData类

```java
import java.util.ArrayList;
import java.util.List;
/**
 * 提供用于测试的数据
 */
public class EmployeeData {
	
	public static List<Employee> getEmployees(){
		List<Employee> list = new ArrayList<>();
		
		list.add(new Employee(1001, "马化腾", 34, 6000.38));
		list.add(new Employee(1002, "马云", 12, 9876.12));
		list.add(new Employee(1003, "刘强东", 33, 3000.82));
		list.add(new Employee(1004, "雷军", 26, 7657.37));
		list.add(new Employee(1005, "李彦宏", 65, 5555.32));
		list.add(new Employee(1006, "比尔盖茨", 42, 9500.43));
		list.add(new Employee(1007, "任正非", 26, 4333.32));
		list.add(new Employee(1008, "扎克伯格", 35, 2500.32));
		
		return list;
	}	
}
```

> 2、Employee类

```java
public class Employee {

	private int id;
	private String name;
	private int age;
	private double salary;

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
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

	public double getSalary() {
		return salary;
	}

	public void setSalary(double salary) {
		this.salary = salary;
	}

	public Employee() {
		System.out.println("Employee().....");
	}

	public Employee(int id) {
		this.id = id;
		System.out.println("Employee(int id).....");
	}

	public Employee(int id, String name) {
		this.id = id;
		this.name = name;
	}

	public Employee(int id, String name, int age, double salary) {

		this.id = id;
		this.name = name;
		this.age = age;
		this.salary = salary;
	}

	@Override
	public String toString() {
		return "Employee{" + "id=" + id + ", name='" + name + '\'' + ", age=" + age + ", salary=" + salary + '}';
	}

	@Override
	public boolean equals(Object o) {
		if (this == o)
			return true;
		if (o == null || getClass() != o.getClass())
			return false;

		Employee employee = (Employee) o;

		if (id != employee.id)
			return false;
		if (age != employee.age)
			return false;
		if (Double.compare(employee.salary, salary) != 0)
			return false;
		return name != null ? name.equals(employee.name) : employee.name == null;
	}

	@Override
	public int hashCode() {
		int result;
		long temp;
		result = id;
		result = 31 * result + (name != null ? name.hashCode() : 0);
		result = 31 * result + age;
		temp = Double.doubleToLongBits(salary);
		result = 31 * result + (int) (temp ^ (temp >>> 32));
		return result;
	}
}
```

> 3、测试类

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.stream.IntStream;
import java.util.stream.Stream;

/**
 * 测试Stream的实例化
 */
public class StreamAPITest {

    //创建 Stream方式一：通过集合
    @Test
    public void test(){
        List<Employee> employees = EmployeeData.getEmployees();

//        default Stream<E> stream() : 返回一个顺序流
        Stream<Employee> stream = employees.stream();

//        default Stream<E> parallelStream() : 返回一个并行流
        Stream<Employee> parallelStream = employees.parallelStream();
    }

    //创建 Stream方式二：通过数组
    @Test
    public void test2(){
        int[] arr = new int[]{1,2,3,4,5,6};
        //调用Arrays类的static <T> Stream<T> stream(T[] array): 返回一个流
        IntStream stream = Arrays.stream(arr);

        Employee e1 = new Employee(1001,"Hom");
        Employee e2 = new Employee(1002,"Nut");
        Employee[] arr1 = new Employee[]{e1,e2};

        Stream<Employee> stream1 = Arrays.stream(arr1);
    }
    //创建 Stream方式三：通过Stream的of()
    @Test
    public void test3(){
        Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5, 6);
    }

    //创建 Stream方式四：创建无限流
    @Test
    public void test4(){
//      迭代
//      public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f)
        //遍历前10个偶数
        Stream.iterate(0, t -> t + 2).limit(10).forEach(System.out::println);

//      生成
//      public static<T> Stream<T> generate(Supplier<T> s)
        Stream.generate(Math::random).limit(10).forEach(System.out::println);
    }
}
```

## 7.3、Stream的中间操作：筛选与切片

多个中间操作可以连接起来形成一个流水线，除非流水线上触发终止操作，否则中间操作不会执行任何的处理！而在终止操作时一次性全部处理，称为“惰性求值”。

| 方法                  | 描述                                                         |
| --------------------- | ------------------------------------------------------------ |
| `filter(Predicate p)` | 接收Lambda ，从流中排除某些元素                              |
| `distinct()`          | 筛选，通过流所生成元素的hashCode() 和equals() 去除重复元素   |
| `limit(long maxSize)` | 截断流，使其元素不超过给定数量                               |
| `skip(long n)`        | 跳过元素，返回一个扔掉了前n 个元素的流。若流中元素不足n 个，则返回一个空流。与`limit(n)`互补 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //1-筛选与切片
    @Test
    public void test(){
        List<Employee> list = EmployeeData.getEmployees();
//        filter(Predicate p)——接收 Lambda ， 从流中排除某些元素。
        Stream<Employee> stream = list.stream();
        //练习：查询员工表中薪资大于7000的员工信息
        stream.filter(e -> e.getSalary() > 7000).forEach(System.out::println);

        System.out.println("+++++++++++++++++++++++");
//        limit(n)——截断流，使其元素不超过给定数量。
        list.stream().limit(3).forEach(System.out::println);
        System.out.println("+++++++++++++++++++++++");

//        skip(n) —— 跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一个空流。与 limit(n) 互补
        list.stream().skip(3).forEach(System.out::println);

        System.out.println("+++++++++++++++++++++++");
//        distinct()——筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素

        list.add(new Employee(1013,"李飞",42,8500));
        list.add(new Employee(1013,"李飞",41,8200));
        list.add(new Employee(1013,"李飞",28,6000));
        list.add(new Employee(1013,"李飞",39,7800));
        list.add(new Employee(1013,"李飞",40,8000));

//        System.out.println(list);

        list.stream().distinct().forEach(System.out::println);
    }
}
```

## 7.4、Stream的中间操作：映射

| 方法                              | 描述                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `map(Function f)`                 | 接收一个函数作为参数，该函数会被应用到每个元素上，并将其映射成一个新的元素。 |
| `mapToDouble(ToDoubleFunction f)` | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的DoubleStream。 |
| `mapToInt(ToIntFunction f)`       | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的IntStream。 |
| `mapToLong(ToLongFunction f)`     | 接收一个函数作为参数，该函数会被应用到每个元素上，产生一个新的LongStream。 |
| `flatMap(Function f)`             | 接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //2-映射
    @Test
    public void test2(){
//        map(Function f)——接收一个函数作为参数，将元素转换成其他形式或提取信息，该函数会被应用到每个元素上，并将其映射成一个新的元素。
        List<String> list = Arrays.asList("aa", "bb", "cc", "dd");
        list.stream().map(str -> str.toUpperCase()).forEach(System.out::println);

//        练习1：获取员工姓名长度大于3的员工的姓名。
        List<Employee> employees = EmployeeData.getEmployees();
        Stream<String> namesStream = employees.stream().map(Employee::getName);
        namesStream.filter(name -> name.length() > 3).forEach(System.out::println);
        System.out.println();

        //练习2：
        Stream<Stream<Character>> streamStream = list.stream().map(StreamAPITest2::fromStringToStream);
        
        streamStream.forEach(s ->{
            s.forEach(System.out::println);
        });
        System.out.println("++++++++++++++++++++++");
//        flatMap(Function f)——接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流。
        Stream<Character> characterStream = list.stream().flatMap(StreamAPITest2::fromStringToStream);
        
        characterStream.forEach(System.out::println);
    }

    //将字符串中的多个字符构成的集合转换为对应的Stream的实例
    public static Stream<Character> fromStringToStream(String str){//aa
        ArrayList<Character> list = new ArrayList<>();
        for(Character c : str.toCharArray()){
            list.add(c);
        }
        return list.stream();
    }

    @Test
    public void test3(){
        ArrayList list1 = new ArrayList();
        list1.add(25);
        list1.add(33);
        list1.add(14);

        ArrayList list2 = new ArrayList();
        list2.add(51);
        list2.add(23);
        list2.add(61);

//        list1.add(list2);
        list1.addAll(list2);
        System.out.println(list1);
    }
}
```

## 7.5、Stream的中间操作：排序

| 方法                     | 描述                               |
| ------------------------ | ---------------------------------- |
| `sorted()`               | 产生一个新流，其中按自然顺序排序   |
| `sorted(Comparator com)` | 产生一个新流，其中按比较器顺序排序 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Stream;

/**
 * 测试Stream的中间操作
 */
public class StreamAPITest2 {

    //3-排序
    @Test
    public void test4(){
//        sorted()——自然排序
        List<Integer> list = Arrays.asList(25,45,36,12,85,64,72,-95,4);
        list.stream().sorted().forEach(System.out::println);
        //抛异常，原因:Employee没有实现Comparable接口
//        List<Employee> employees = EmployeeData.getEmployees();
//        employees.stream().sorted().forEach(System.out::println);


//        sorted(Comparator com)——定制排序

        List<Employee> employees = EmployeeData.getEmployees();
        employees.stream().sorted( (e1,e2) -> {

            int ageValue = Integer.compare(e1.getAge(),e2.getAge());
            if(ageValue != 0){
                return ageValue;
            }else{
                return -Double.compare(e1.getSalary(),e2.getSalary());
            }

        }).forEach(System.out::println);
    }
}
12345678910111213141516171819202122232425262728293031323334353637383940
```

## 7.6、Stream的终止操作：匹配与查找

- 终端操作会从流的流水线生成结果。其结果可以是任何不是流的值，例如：List、Integer，甚至是void 。
- 流进行了终止操作后，不能再次使用。

| 方法                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| `allMatch(Predicate p)`  | 检查是否匹配所有元素                                         |
| `anyMatch(Predicate p)`  | 检查是否至少匹配一个元素                                     |
| `noneMatch(Predicate p)` | 检查是否没有匹配所有元素                                     |
| `findFirst()`            | 返回第一个元素                                               |
| `findAny()`              | 返回当前流中的任意元素                                       |
| `count()`                | 返回流中元素总数                                             |
| `max(Comparator c)`      | 返回流中最大值                                               |
| `min(Comparator c)`      | 返回流中最小值                                               |
| `forEach(Consumer c)`    | 内部迭代(使用Collection 接口需要用户去做迭代，称为外部迭代。相反，Stream API 使用内部迭代——它帮你把迭代做了) |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.List;
import java.util.Optional;
import java.util.stream.Stream;

public class StreamAPITest3 {
    //1-匹配与查找
    @Test
    public void test(){
        List<Employee> employees = EmployeeData.getEmployees();

//        allMatch(Predicate p)——检查是否匹配所有元素。
//          练习：是否所有的员工的年龄都大于18
        boolean allMatch = employees.stream().allMatch(e -> e.getAge() > 23);
        System.out.println(allMatch);

//        anyMatch(Predicate p)——检查是否至少匹配一个元素。
//         练习：是否存在员工的工资大于 10000
        boolean anyMatch = employees.stream().anyMatch(e -> e.getSalary() > 9000);
        System.out.println(anyMatch);

//        noneMatch(Predicate p)——检查是否没有匹配的元素。
//          练习：是否存在员工姓“马”
        boolean noneMatch = employees.stream().noneMatch(e -> e.getName().startsWith("马"));
        System.out.println(noneMatch);
        
//        findFirst——返回第一个元素
        Optional<Employee> employee = employees.stream().findFirst();
        System.out.println(employee);
        
//        findAny——返回当前流中的任意元素
        Optional<Employee> employee1 = employees.parallelStream().findAny();
        System.out.println(employee1);
    }

    @Test
    public void test2(){
        List<Employee> employees = EmployeeData.getEmployees();
        
        // count——返回流中元素的总个数
        long count = employees.stream().filter(e -> e.getSalary() > 4500).count();
        System.out.println(count);
        
//        max(Comparator c)——返回流中最大值
//        练习：返回最高的工资：
        Stream<Double> salaryStream = employees.stream().map(e -> e.getSalary());
        Optional<Double> maxSalary = salaryStream.max(Double::compare);
        System.out.println(maxSalary);
        
//        min(Comparator c)——返回流中最小值
//        练习：返回最低工资的员工
        Optional<Employee> employee = employees.stream().min((e1, e2) -> Double.compare(e1.getSalary(), e2.getSalary()));
        System.out.println(employee);
        System.out.println();
        
//        forEach(Consumer c)——内部迭代
        employees.stream().forEach(System.out::println);

        //使用集合的遍历操作
        employees.forEach(System.out::println);
    }
}
1234567891011121314151617181920212223242526272829303132333435363738394041424344454647484950515253545556575859606162636465
```

## 7.7、Stream的终止操作：归约

| 方法                               | 描述                                                 |
| ---------------------------------- | ---------------------------------------------------- |
| `reduce(T iden, BinaryOperator b)` | 可以将流中元素反复结合起来，得到一个值。返回T        |
| `reduce(BinaryOperator b)`         | 可以将流中元素反复结合起来，得到一个值。返回Optional |

> 备注：map 和reduce 的连接通常称为map-reduce 模式，因Google 用它来进行网络搜索而出名。

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.stream.Stream;

public class StreamAPITest3 {

    //2-归约
    @Test
    public void test3(){
//        reduce(T identity, BinaryOperator)——可以将流中元素反复结合起来，得到一个值。返回 T
//        练习1：计算1-10的自然数的和
        List<Integer> list = Arrays.asList(72,25,32,34,43,56,81,15,29,71);
        Integer sum = list.stream().reduce(0, Integer::sum);
        System.out.println(sum);

//        reduce(BinaryOperator) ——可以将流中元素反复结合起来，得到一个值。返回 Optional<T>
//        练习2：计算公司所有员工工资的总和
        List<Employee> employees = EmployeeData.getEmployees();
        Stream<Double> salaryStream = employees.stream().map(Employee::getSalary);
//        Optional<Double> sumMoney = salaryStream.reduce(Double::sum);
        Optional<Double> sumMoney = salaryStream.reduce((d1,d2) -> d1 + d2);
        System.out.println(sumMoney.get());
    }
}
1234567891011121314151617181920212223242526272829
```

### 7.8、Stream的终止操作：收集

| 方法                   | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| `collect(Collector c)` | 将流转换为其他形式。接收一个Collector接口的实现，用于给Stream中元素做汇总的方法 |

```java
import github2.Employee;
import github2.EmployeeData;
import org.junit.Test;

import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.Set;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class StreamAPITest3 {

    //3-收集
    @Test
    public void test4() {
//        collect(Collector c)——将流转换为其他形式。接收一个 Collector接口的实现，用于给Stream中元素做汇总的方法
//        练习1：查找工资大于6000的员工，结果返回为一个List或Set

        List<Employee> employees = EmployeeData.getEmployees();
        List<Employee> employeeList = employees.stream().filter(e -> e.getSalary() > 6000).collect(Collectors.toList());

        employeeList.forEach(System.out::println);
        
        System.out.println("++++++++++++++++++");
        
        Set<Employee> employeeSet = employees.stream().filter(e -> e.getSalary() > 6000).collect(Collectors.toSet());

        employeeSet.forEach(System.out::println);
    }
}
12345678910111213141516171819202122232425262728293031
```

> `Collector` 接口中方法的实现决定了如何对流执行收集的操作(如收集到`List、Set、Map`)。
>
> `Collectors`实用类提供了很多静态方法，可以方便地创建常见收集器实例，具体方法与实例如下表：

![img](https://img-blog.csdnimg.cn/img_convert/bd29b1fd138291421630d2d542675cf7.png)
![img](https://img-blog.csdnimg.cn/img_convert/0d4c3b7ce571549e8940d8c9e8192df1.png)

## 08、Optional类

## 8.1、Optional类的介绍

到目前为止，臭名昭著的空指针异常是导致Java应用程序失败的最常见原因。以前，为了解决空指针异常，Google公司著名的Guava项目引入了Optional类，Guava通过使用检查空值的方式来防止代码污染，它鼓励程序员写更干净的代码。受到Google Guava的启发，Optional类已经成为Java 8类库的一部分。

- `Optional` 类(`java.util.Optional`) 是一个容器类，它可以保存类型T的值，代表这个值存在。或者仅仅保存`null`，表示这个值不存在。原来用`null` 表示一个值不存在，现`在Optional` 可以更好的表达这个概念。并且可以避免空指针异常。
- Optional类的Javadoc描述如下：这是一个可以为null的容器对象。如果值存在则`isPresent()`方法会返回`true`，调用`get()`方法会返回该对象。
- Optional提供很多有用的方法，这样我们就不用显式进行空值检测。
- 创建Optional类对象的方法：
  - `Optional.of(T t)`: 创建一个Optional 实例，t必须非空；
  - `Optional.empty()` : 创建一个空的Optional 实例
  - `Optional.ofNullable(T t`)：t可以为null
- 判断Optional容器中是否包含对象：
  - `boolean isPresent()` : 判断是否包含对象
  - `void ifPresent(Consumer<? super T> consumer)` ：如果有值，就执行Consumer接口的实现代码，并且该值会作为参数传给它。
- 获取Optional容器的对象：
  - `T get()`: 如果调用对象包含值，返回该值，否则抛异常
  - `T orElse(T other)` ：如果有值则将其返回，否则返回指定的other对象。
  - `T orElseGet(Supplier<? extends T> other)` ：如果有值则将其返回，否则返回由Supplier接口实现提供的对象。
  - `T orElseThrow(Supplier<? extends X> exceptionSupplier)` ：如果有值则将其返回，否则抛出由Supplier接口实现提供的异常。

> 1、Boy类

```java
public class Boy {
    private Girl girl;

    public Boy() {
    }

    public Boy(Girl girl) {
        this.girl = girl;
    }

    public Girl getGirl() {
        return girl;
    }

    public void setGirl(Girl girl) {
        this.girl = girl;
    }

    @Override
    public String toString() {
        return "Boy{" +
                "girl=" + girl +
                '}';
    }
}
12345678910111213141516171819202122232425
```

> 2、Girl类

```java
public class Girl {
    private String name;

    public Girl() {
    }

    public Girl(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Girl{" +
                "name='" + name + '\'' +
                '}';
    }
}
12345678910111213141516171819202122232425
```

> 3、测试类

```java
import org.junit.Test;
import java.util.Optional;

/**
 * Optional类：为了在程序中避免出现空指针异常而创建的。
 *
 * 常用的方法：ofNullable(T t)
 *           orElse(T t)
 */
public class OptionalTest {
    /**
     * Optional.of(T t) : 创建一个 Optional 实例，t必须非空；
     * Optional.empty() : 创建一个空的 Optional 实例
     * Optional.ofNullable(T t)：t可以为null
     */
    @Test
    public void test(){
        Girl girl = new Girl();
//        girl = null;
        //of(T t):保证t是非空的
        Optional<Girl> optionalGirl = Optional.of(girl);
    }

    @Test
    public void test2(){
        Girl girl = new Girl();
//        girl = null;
        //ofNullable(T t)：t可以为null
        Optional<Girl> optionalGirl = Optional.ofNullable(girl);
        System.out.println(optionalGirl);
        //orElse(T t1):如果单前的Optional内部封装的t是非空的，则返回内部的t.
        //如果内部的t是空的，则返回orElse()方法中的参数t1.
        Girl girl1 = optionalGirl.orElse(new Girl(""));
        System.out.println(girl1);
    }
}
123456789101112131415161718192021222324252627282930313233343536
```

## 8.2、Optional类的使用举例

> 1、测试类

```java
import org.junit.Test;
import java.util.Optional;

/**
 * Optional类：为了在程序中避免出现空指针异常而创建的。
 *
 * 常用的方法：ofNullable(T t)
 *           orElse(T t)
 */
public class OptionalTest {

    @Test
    public void test3(){
        Boy boy = new Boy();
        boy = null;
        String girlName = getGirlName(boy);
        System.out.println(girlName);
    }

    private String getGirlName(Boy boy) {
        return boy.getGirl().getName();
    }

    //优化以后的getGirlName():
    public String getGirlName1(Boy boy){
        if(boy != null){
            Girl girl = boy.getGirl();
            if(girl != null){
                return girl.getName();
            }
        }
        return null;
    }

    @Test
    public void test4(){
        Boy boy = new Boy();
        boy = null;
        String girlName = getGirlName1(boy);
        System.out.println(girlName);
    }

    //使用Optional类的getGirlName():
    public String getGirlName2(Boy boy){

        Optional<Boy> boyOptional = Optional.ofNullable(boy);
        //此时的boy1一定非空
        Boy boy1 = boyOptional.orElse(new Boy(new Girl("朱淑贞")));

        Girl girl = boy1.getGirl();

        Optional<Girl> girlOptional = Optional.ofNullable(girl);
        //girl1一定非空
        Girl girl1 = girlOptional.orElse(new Girl("阿青"));

        return girl1.getName();
    }

    @Test
    public void test5(){
        Boy boy = null;
        boy = new Boy();
        boy = new Boy(new Girl("李清照"));
        String girlName = getGirlName2(boy);
        System.out.println(girlName);
    }
}
```
