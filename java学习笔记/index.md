# Java学习笔记


### Java集合框架

![集合框架体系](https://www.runoob.com/wp-content/uploads/2014/01/java-coll.png)

导入包  `import java.util.*;`



#### ArrayList

##### 一、定义一个ArrayList

```java
//默认创建一个ArrayList集合
List<String> list = new ArrayList<>();
//创建一个初始化长度为100的ArrayList集合
List<String> initlist = new ArrayList<>(100);
//将其他类型的集合转为ArrayList
List<String> setList = new ArrayList<>(new HashSet());
```

##### 二、ArrayList常用方法

1. `add(E element)`

2. `set(int index, E element)`

因为ArrayList底层是由数组实现的，set实现非常简单，调用 `set(4, "4")` 通过传入的数字下标找到对应的位置，替换其中的元素，前提也需要首先判断传入的数组下标是否越界。

3. `get(int index)`

4. `remove(int index)`
5. `remove(Object o)`
6. 其他方法

`size()` : 获取集合长度，通过定义在ArrayList中的私有变量size得到

`isEmpty()`：是否为空，通过定义在ArrayList中的私有变量size得到

`contains(Object o)`：是否包含某个元素，通过遍历底层数组elementData，通过equals或==进行判断

`clear()`：集合清空，通过遍历底层数组elementData，设置为null

7. ArrayList的遍历

```java
List<String> list=new ArrayList<String>();
list.add("Hello");
list.add("World");
list.add("HAHAHAHA");
//第一种遍历方法使用 For-Each 遍历 List
for (String str : list) {            //也可以改写 for(int i=0;i<list.size();i++) 这种形式
  System.out.println(str);
}

//第二种遍历，把链表变为数组相关的内容进行遍历
String[] strArray=new String[list.size()];
list.toArray(strArray);
for(int i=0;i<strArray.length;i++) //这里也可以改写为  for(String str:strArray) 这种形式
{
  System.out.println(strArray[i]);
}

//第三种遍历 使用迭代器进行相关遍历

Iterator<String> ite=list.iterator();
while(ite.hasNext())//判断下一个元素之后有值
{
  System.out.println(ite.next());
}
```

#### HashMap

##### 一、定义一个HashMap

`Map<String, String> map = new HashMap<>();`

##### 二、HashMap常用方法

1. `public V put(K key, V value)` :插入键值对数据
2. `public V get(Object key)` :根据键值获取键值对值数据
3. `public int size()` :获取Map中键值对的个数
4. `public boolean containsKey(Object key)` :判断Map集合中是否包含键为key的键值对
5. `boolean containsValue(Object value)` :判断Map集合中是否包含值为value的键值对
6. `public boolean isEmpty()` :判断Map集合中是否没有任何键值对
7. `public V remove(Object key)` :根据键值删除Map中键值对
8. `public void clear()` :清空Map集合中所有的键值对
9. HashMap的遍历

```java
Map<String, String> map = new HashMap<String, String>();
map.put("1", "value1");
map.put("2", "value2");
map.put("3", "value3");

//第一种：普遍使用，二次取值
System.out.println("通过Map.keySet遍历key和value：");
for (String key : map.keySet()) {
  System.out.println("key= "+ key + " and value= " + map.get(key));
}

//第二种
System.out.println("通过Map.entrySet使用iterator遍历key和value：");
Iterator<Map.Entry<String, String>> it = map.entrySet().iterator();
while (it.hasNext()) {
  Map.Entry<String, String> entry = it.next();
  System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
}

//第三种：推荐，尤其是容量大时
System.out.println("通过Map.entrySet遍历key和value");
for (Map.Entry<String, String> entry : map.entrySet()) {
  System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
}

//第四种
System.out.println("通过Map.values()遍历所有的value，但不能遍历key");
for (String v : map.values()) {
  System.out.println("value= " + v);
}
```



### Java多线程

Java 给多线程编程提供了内置的支持。 一条线程指的是进程中一个单一顺序的控制流，一个进程中可以并发多个线程，每条线程并行执行不同的任务。

多线程是多任务的一种特别的形式，但多线程使用了更小的资源开销。

这里定义和线程相关的另一个术语 - 进程：一个进程包括由操作系统分配的内存空间，包含一个或多个线程。一个线程不能独立的存在，它必须是进程的一部分。一个进程一直运行，直到所有的非守护线程都结束运行后才能结束。

多线程能满足程序员编写高效率的程序来达到充分利用 CPU 的目的。

#### 一个线程的生命周期

线程是一个动态执行的过程，它也有一个从产生到死亡的过程。

下图显示了一个线程完整的生命周期。

![线程的生命周期](https://www.runoob.com/wp-content/uploads/2014/01/java-thread.jpg)

- 新建状态：

  使用 **new** 关键字和 **Thread** 类或其子类建立一个线程对象后，该线程对象就处于新建状态。它保持这个状态直到程序 **start()** 这个线程。

- 就绪状态：

  当线程对象调用了start()方法之后，该线程就进入就绪状态。就绪状态的线程处于就绪队列中，要等待JVM里线程调度器的调度。

- 运行状态：

  如果就绪状态的线程获取 CPU 资源，就可以执行 **run()**，此时线程便处于运行状态。处于运行状态的线程最为复杂，它可以变为阻塞状态、就绪状态和死亡状态。

- 阻塞状态：

  如果一个线程执行了sleep（睡眠）、suspend（挂起）等方法，失去所占用资源之后，该线程就从运行状态进入阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就绪状态。可以分为三种： 

  等待阻塞：运行状态中的线程执行 wait() 方法，使线程进入到等待阻塞状态。

  同步阻塞：线程在获取 synchronized 同步锁失败(因为同步锁被其他线程占用)。

  其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O 请求时，线程就会进入到阻塞状态。当sleep() 状态超时，join() 等待线程终止或超时，或者 I/O 处理完毕，线程重新转入就绪状态。

- 死亡状态：

  一个运行状态的线程完成任务或者其他终止条件发生时，该线程就切换到终止状态。

#### 线程的优先级

每一个 Java 线程都有一个优先级，这样有助于操作系统确定线程的调度顺序。

Java 线程的优先级是一个整数，其取值范围是 1 （Thread.MIN_PRIORITY ） - 10 （Thread.MAX_PRIORITY ）。

默认情况下，每一个线程都会分配一个优先级 NORM_PRIORITY（5）。

具有较高优先级的线程对程序更重要，并且应该在低优先级的线程之前分配处理器资源。但是，线程优先级不能保证线程执行的顺序，而且非常依赖于平台。

#### Thread 方法

| 序号 | 方法描述                                                     |
| :--: | :----------------------------------------------------------- |
|  1   | **public void start()**<br/>使该线程开始执行；**==Java==** 虚拟机调用该线程的 run 方法。 |
|  2   | **public void run()**<br/>如果该线程是使用独立的 Runnable 运行对象构造的，则调用该 Runnable 对象的 run 方法；否则，该方法不执行任何操作并返回。 |
|  3   | **public final void setName(String name)**<br/>改变线程名称，使之与参数 name 相同。 |
|  4   | **public final void setPriority(int priority)**<br/> 更改线程的优先级。 |
|  5   | **public final void setDaemon(boolean on)**<br/>将该线程标记为守护线程或用户线程。 |
|  6   | **public final void join(long millisec)**<br/>等待该线程终止的时间最长为 millis 毫秒。 |
|  7   | **public void interrupt()**<br/>中断线程。                   |
|  8   | **public final boolean isAlive()**<br/>测试线程是否处于活动状态。 |

测试线程是否处于活动状态。 上述方法是被Thread对象调用的。下面的方法是Thread类的静态方法。

| 序号 | 方法描述                                                     |
| :--: | :----------------------------------------------------------- |
|  1   | **public static void yield()**<br/>暂停当前正在执行的线程对象，并执行其他线程。 |
|  2   | **public static void sleep(long millisec)**<br/>在指定的毫秒数内让当前正在执行的线程休眠（暂停执行），此操作受到系统计时器和调度程序精度和准确性的影响。 |
|  3   | **public static boolean holdsLock(Object x)**<br/>当且仅当当前线程在指定的对象上保持监视器锁时，才返回 true。 |
|  4   | **public static Thread currentThread()**<br/>返回对当前正在执行的线程对象的引用。 |
|  5   | **public static void dumpStack()**<br/>将当前线程的堆栈跟踪打印至标准错误流。 |



#### 创建一个线程

Java 提供了三种创建线程的方法：

- 通过实现 Runnable 接口；
- 通过继承 Thread 类本身；
- 通过 Callable 和 Future 创建线程。

##### 通过实现Runnable 接口来创建线程

创建一个线程，最简单的方法是创建一个实现 Runnable 接口的类。

为了实现 Runnable，一个类只需要执行一个方法调用 run()，声明如下：

`public void run()`

你可以重写该方法，重要的是理解的 run() 可以调用其他方法，使用其他类，并声明变量，就像主线程一样。

在创建一个实现 Runnable 接口的类之后，你可以在类中实例化一个线程对象。

Thread 定义了几个构造方法，下面的这个是我们经常使用的：

`Thread(Runnable threadOb,String threadName);`

这里，threadOb 是一个实现 Runnable 接口的类的实例，并且 threadName 指定新线程的名字。

新线程创建之后，你调用它的 start() 方法它才会运行。

`void start();`

下面是一个创建线程并开始让它执行的实例：

```java
class RunnableDemo implements Runnable {
   private Thread t;
   private String threadName;
   
   RunnableDemo( String name) {
      threadName = name;
      System.out.println("Creating " +  threadName );
   }
   
   public void run() {
      System.out.println("Running " +  threadName );
      try {
         for(int i = 4; i > 0; i--) {
            System.out.println("Thread: " + threadName + ", " + i);
            // 让线程睡眠一会
            Thread.sleep(50);
         }
      }catch (InterruptedException e) {
         System.out.println("Thread " +  threadName + " interrupted.");
      }
      System.out.println("Thread " +  threadName + " exiting.");
   }
   
   public void start () {
      System.out.println("Starting " +  threadName );
      if (t == null) {
         t = new Thread (this, threadName);
         t.start ();
      }
   }
}
 
public class TestThread {
 
   public static void main(String args[]) {
      RunnableDemo R1 = new RunnableDemo( "Thread-1");
      R1.start();
      
      RunnableDemo R2 = new RunnableDemo( "Thread-2");
      R2.start();
   }   
}
```

##### 通过继承Thread来创建线程

创建一个线程的第二种方法是创建一个新的类，该类继承 Thread 类，然后创建一个该类的实例。

继承类必须重写 run() 方法，该方法是新线程的入口点。它也必须调用 start() 方法才能执行。

该方法尽管被列为一种多线程实现方式，但是本质上也是实现了 Runnable 接口的一个实例。

```java
class ThreadDemo extends Thread {
   private Thread t;
   private String threadName;
   
   ThreadDemo( String name) {
      threadName = name;
      System.out.println("Creating " +  threadName );
   }
   
   public void run() {
      System.out.println("Running " +  threadName );
      try {
         for(int i = 4; i > 0; i--) {
            System.out.println("Thread: " + threadName + ", " + i);
            // 让线程睡眠一会
            Thread.sleep(50);
         }
      }catch (InterruptedException e) {
         System.out.println("Thread " +  threadName + " interrupted.");
      }
      System.out.println("Thread " +  threadName + " exiting.");
   }
   
   public void start () {
      System.out.println("Starting " +  threadName );
      if (t == null) {
         t = new Thread (this, threadName);
         t.start ();
      }
   }
}
 
public class TestThread {
 
   public static void main(String args[]) {
      ThreadDemo T1 = new ThreadDemo( "Thread-1");
      T1.start();
      
      ThreadDemo T2 = new ThreadDemo( "Thread-2");
      T2.start();
   }   
}
```

##### 通过Callable和Future创建线程

- 1. 创建 Callable 接口的实现类，并实现 call() 方法，该 call() 方法将作为线程执行体，并且有返回值。
- 2. 创建 Callable 实现类的实例，使用 FutureTask 类来包装 Callable 对象，该 FutureTask 对象封装了该 Callable 对象的 call() 方法的返回值。
- 3. 使用 FutureTask 对象作为 Thread 对象的 target 创建并启动新线程。
- 4. 调用 FutureTask 对象的 get() 方法来获得子线程执行结束后的返回值。

```java
public class CallableThreadTest implements Callable<Integer> {
    public static void main(String[] args)  
    {  
        CallableThreadTest ctt = new CallableThreadTest();  
        FutureTask<Integer> ft = new FutureTask<>(ctt);  
        for(int i = 0;i < 100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" 的循环变量i的值"+i);  
            if(i==20)  
            {  
                new Thread(ft,"有返回值的线程").start();  
            }  
        }  
        try  
        {  
            System.out.println("子线程的返回值："+ft.get());  
        } catch (InterruptedException e)  
        {  
            e.printStackTrace();  
        } catch (ExecutionException e)  
        {  
            e.printStackTrace();  
        }  
  
    }
    @Override  
    public Integer call() throws Exception  
    {  
        int i = 0;  
        for(;i<100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" "+i);  
        }  
        return i;  
    }  
}
```

##### 创建线程的三种方式的对比

- 1. 采用实现 Runnable、Callable 接口的方式创建多线程时，线程类只是实现了 Runnable 接口或 Callable 接口，还可以继承其他类。
- 2. 使用继承 Thread 类的方式创建多线程时，编写简单，如果需要访问当前线程，则无需使用 Thread.currentThread() 方法，直接使用 this 即可获得当前线程。

#### 线程的几个主要概念

在多线程编程时，你需要了解以下几个概念：

- 线程同步
- 线程间通信
- 线程死锁
- 线程控制：挂起、停止和恢复

#### 多线程的使用

有效利用多线程的关键是理解程序是并发执行而不是串行执行的。例如：程序中有两个子系统需要并发执行，这时候就需要利用多线程编程。

通过对多线程的使用，可以编写出非常高效的程序。不过请注意，如果你创建太多的线程，程序执行的效率实际上是降低了，而不是提升了。

请记住，上下文的切换开销也很重要，如果你创建了太多的线程，CPU 花费在上下文的切换的时间将多于执行程序的时间！


