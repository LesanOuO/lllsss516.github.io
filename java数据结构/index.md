# Java数据结构


[API](https://www.runoob.com/manual/jdk11api/java.base/java/util/package-summary.html)

### Vector

Vector 类实现了一个动态数组。和 ArrayList 很相似，但是两者是不同的：

- Vector 是同步访问的。
- Vector 包含了许多传统的方法，这些方法不属于集合框架。

Vector 主要用在事先不知道数组的大小，或者只是需要一个可以改变大小的数组的情况。

Vector 类支持 4 种构造方法。

第一种构造方法创建一个默认的向量，默认大小为 10：

```
Vector()
```

第二种构造方法创建指定大小的向量。

```
Vector(int size)
```

第三种构造方法创建指定大小的向量，并且增量用 incr 指定。增量表示向量每次增加的元素数目。

```
Vector(int size,int incr)
```

第四种构造方法创建一个包含集合 c 元素的向量：

```
Vector(Collection c)
```

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | void add(int index, Object element)   在此向量的指定位置插入指定的元素。 |
| 2    | boolean add(Object o)   将指定元素添加到此向量的末尾。       |
| 3    | void clear() 从此向量中移除所有元素。                        |
| 4    | boolean contains(Object elem) 如果此向量包含指定的元素，则返回 true。 |
| 5    | Object get(int index) 返回向量中指定位置的元素。             |
| 6    | int indexOf(Object elem)  返回此向量中第一次出现的指定元素的索引，如果此向量不包含该元素，则返回 -1。 |
| 7    | boolean isEmpty() 测试此向量是否不包含组件。                 |
| 8    | int size()  返回此向量中的组件数。                           |

### Stack

栈是Vector的一个子类，它实现了一个标准的后进先出的栈。

堆栈只定义了默认构造函数，用来创建一个空栈。 堆栈除了包括由Vector定义的所有方法，也定义了自己的一些方法。

```
Stack()
```

除了由Vector定义的所有方法，自己也定义了一些方法：

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | boolean empty()  测试堆栈是否为空。                          |
| 2    | Object peek( ) 查看堆栈顶部的对象，但不从堆栈中移除它。      |
| 3    | Object pop( ) 移除堆栈顶部的对象，并作为此函数的值返回该对象。 |
| 4    | Object push(Object element) 把项压入堆栈顶部。               |
| 5    | int search(Object element) 返回对象在堆栈中的位置，以 1 为基数。 |

### ArrayList

ArrayList 类是一个可以动态修改的数组，与普通数组的区别就是它是没有固定大小的限制，我们可以添加或删除元素。

ArrayList 继承了 AbstractList ，并实现了 List 接口。

ArrayList 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```
import java.util.ArrayList; // 引入 ArrayList 类

ArrayList<E> objectName =new ArrayList<>();　 // 初始化
```

- **E**: 泛型数据类型，用于设置 objectName 的数据类型，**只能为引用数据类型**。
- **objectName**: 对象名。

ArrayList 是一个数组队列，提供了相关的添加、删除、修改、遍历等功能。

Java ArrayList 常用方法列表如下：

| 方法                                                         | 描述                                          |
| :----------------------------------------------------------- | :-------------------------------------------- |
| [add()](https://www.runoob.com/java/java-arraylist-add.html) | 将元素插入到指定位置的 arraylist 中           |
| [addAll()](https://www.runoob.com/java/java-arraylist-addall.html) | 添加集合中的所有元素到 arraylist 中           |
| [clear()](https://www.runoob.com/java/java-arraylist-clear.html) | 删除 arraylist 中的所有元素                   |
| [clone()](https://www.runoob.com/java/java-arraylist-clone.html) | 复制一份 arraylist                            |
| [contains()](https://www.runoob.com/java/java-arraylist-contains.html) | 判断元素是否在 arraylist                      |
| [get()](https://www.runoob.com/java/java-arraylist-get.html) | 通过索引值获取 arraylist 中的元素             |
| [indexOf()](https://www.runoob.com/java/java-arraylist-indexof.html) | 返回 arraylist 中元素的索引值                 |
| [removeAll()](https://www.runoob.com/java/java-arraylist-removeall.html) | 删除存在于指定集合中的 arraylist 里的所有元素 |
| [remove()](https://www.runoob.com/java/java-arraylist-remove.html) | 删除 arraylist 里的单个元素                   |
| [size()](https://www.runoob.com/java/java-arraylist-size.html) | 返回 arraylist 里元素数量                     |
| [isEmpty()](https://www.runoob.com/java/java-arraylist-isempty.html) | 判断 arraylist 是否为空                       |
| [subList()](https://www.runoob.com/java/java-arraylist-sublist.html) | 截取部分 arraylist 的元素                     |
| [set()](https://www.runoob.com/java/java-arraylist-set.html) | 替换 arraylist 中指定索引的元素               |
| [sort()](https://www.runoob.com/java/java-arraylist-sort.html) | 对 arraylist 元素进行排序                     |
| [toArray()](https://www.runoob.com/java/java-arraylist-toarray.html) | 将 arraylist 转换为数组                       |
| [toString()](https://www.runoob.com/java/java-arraylist-tostring.html) | 将 arraylist 转换为字符串                     |
| [ensureCapacity](https://www.runoob.com/java/java-arraylist-surecapacity.html)() | 设置指定容量大小的 arraylist                  |
| [lastIndexOf()](https://www.runoob.com/java/java-arraylist-lastindexof.html) | 返回指定元素在 arraylist 中最后一次出现的位置 |
| [retainAll()](https://www.runoob.com/java/java-arraylist-retainall.html) | 保留 arraylist 中在指定集合中也存在的那些元素 |
| [containsAll()](https://www.runoob.com/java/java-arraylist-containsall.html) | 查看 arraylist 是否包含指定集合中的所有元素   |
| [trimToSize()](https://www.runoob.com/java/java-arraylist-trimtosize.html) | 将 arraylist 中的容量调整为数组中的元素个数   |
| [removeRange()](https://www.runoob.com/java/java-arraylist-removerange.html) | 删除 arraylist 中指定索引之间存在的元素       |
| [replaceAll()](https://www.runoob.com/java/java-arraylist-replaceall.html) | 将给定的操作内容替换掉数组中每一个元素        |
| [removeIf()](https://www.runoob.com/java/java-arraylist-removeif.html) | 删除所有满足特定条件的 arraylist 元素         |
| [forEach()](https://www.runoob.com/java/java-arraylist-foreach.html) | 遍历 arraylist 中每一个元素并执行特定操作     |

### LinkedList

链表（Linked list）是一种常见的基础数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址。

链表可分为单向链表和双向链表。

一个单向链表包含两个值: 当前节点的值和一个指向下一个节点的链接。

![img](https://www.runoob.com/wp-content/uploads/2020/06/408px-Singly-linked-list.svg_.png)

一个双向链表有三个整数值: 数值、向后的节点链接、向前的节点链接。

![img](https://www.runoob.com/wp-content/uploads/2020/06/610px-Doubly-linked-list.svg_.png)

Java LinkedList（链表） 类似于 ArrayList，是一种常用的数据容器。

与 ArrayList 相比，LinkedList 的增加和删除对操作效率更高，而查找和修改的操作效率较低。

**以下情况使用 ArrayList :**

- 频繁访问列表中的某一个元素。
- 只需要在列表末尾进行添加和删除元素操作。

**以下情况使用 LinkedList :**

- 你需要通过循环迭代来访问列表中的某些元素。
- 需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。

LinkedList 继承了 AbstractSequentialList 类。

LinkedList 实现了 Queue 接口，可作为队列使用。

LinkedList 实现了 List 接口，可进行列表的相关操作。

LinkedList 实现了 Deque 接口，可作为队列使用。

LinkedList 实现了 Cloneable 接口，可实现克隆。

LinkedList 实现了 java.io.Serializable 接口，即可支持序列化，能通过序列化去传输。

### Queue

**Queue： 基本上，一个队列就是一个先入先出（FIFO）的数据结构**

**Queue接口与List、Set同一级别，都是继承了Collection接口。LinkedList实现了Deque接 口。**

![img](https://images2017.cnblogs.com/blog/1182892/201711/1182892-20171122100317930-842768608.png)

​		**add**    增加一个元索           如果队列已满，则抛出一个IIIegaISlabEepeplian异常
　　**remove**  移除并返回队列头部的元素  如果队列为空，则抛出一个NoSuchElementException异常
　　**element** 返回队列头部的元素       如果队列为空，则抛出一个NoSuchElementException异常
　　**offer**    添加一个元素并返回true    如果队列已满，则返回false
　　**poll**     移除并返问队列头部的元素  如果队列为空，则返回null
　　**peek**    返回队列头部的元素       如果队列为空，则返回null
　　**put**     添加一个元素           如果队列满，则阻塞
　　**take**    移除并返回队列头部的元素   如果队列为空，则阻塞

**remove、element、offer 、poll、peek 其实是属于Queue接口。**

### Comparator自定义排序

Comparator接口可以实现自定义排序，实现Comparator接口时，要重写compare方法： 
int compare(Object o1, Object o2) 返回一个基本类型的整型 
如果要按照升序排序,则o1 小于o2，返回-1（负数），相等返回0，01大于02返回1（正数） 
如果要按照降序排序,则o1 小于o2，返回1（正数），相等返回0，01大于02返回-1（负数）

```java
list.sort(new Comparator<Person>() {
        int flag=0;
        @Override
        public int compare(Person o1, Person o2) {
            int a=o1.getSex().compareTo(o2.getSex());
            if(a!=0&&a>0){
                return -1;
                    }
            else if(o1.getSex().equals(o2.getSex())){
                if(o1.getAge()<o2.getAge()){
                    return -1;
                }
                else if(o1.getAge()==o2.getAge()){
                    if(o1.getWeigth()<o2.getWeigth()){
                        return -1;
                    }
                    else if(o1.getWeigth()==o2.getWeigth()){
                        if(o1.getHeight()>o2.getHeight()){
                            return -1;
                        }
                        else if(o1.getHeight()==o2.getHeight()){
                            if(o1.getName().length()<o2.getName().length()){
                                return -1;
                            }
                        }
                    }
                }
            }
            return 1;
        }
    });
```


