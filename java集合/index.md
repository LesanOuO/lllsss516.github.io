# Java集合


[API](https://www.runoob.com/manual/jdk11api/java.base/java/util/package-summary.html)

![img](https://images2017.cnblogs.com/blog/1182892/201711/1182892-20171122101159430-391005054.jpg)

**Collection** 接口的接口 对象的集合（单列集合） 
├——-**List** 接口：元素按进入先后有序保存，可重复 
│—————-├ **LinkedList** 接口实现类， 链表， 插入删除， 没有同步， 线程不安全 
│—————-├ **ArrayList** 接口实现类， 数组， 随机访问， 没有同步， 线程不安全 
│—————-└ **Vector** 接口实现类 数组， 同步， 线程安全 
│ ———————-└ **Stack** 是Vector类的实现类 
└——-**Set** 接口： 仅接收一次，不可重复，并做内部排序 
├—————-└**HashSet** 使用hash表（数组）存储元素 
│————————└ **LinkedHashSet** 链表维护元素的插入次序 
└ —————-**TreeSet** 底层实现为二叉树，元素排好序

**Map** 接口 键值对的集合 （双列集合） 
├———**Hashtable** 接口实现类， 同步， 线程安全 
├———**HashMap** 接口实现类 ，没有同步， 线程不安全- 
│—————–├ **LinkedHashMap** 双向链表和哈希表实现 
│—————–└ **WeakHashMap** 
├ ——–**TreeMap** 红黑树对所有的key进行排序 
└———**IdentifyHashMap**

### HashSet

HashSet 基于 HashMap 来实现的，是一个不允许有重复元素的集合。

HashSet 允许有 null 值。

HashSet 是无序的，即不会记录插入的顺序。

HashSet 不是线程安全的， 如果多个线程尝试同时修改 HashSet，则最终结果是不确定的。 您必须在多线程访问时显式同步对 HashSet 的并发访问。

HashSet 实现了 Set 接口。

HashSet 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```
import java.util.HashSet; // 引入 HashSet 类
```

以下实例我们创建一个 HashSet 对象 sites，用于保存字符串元素：

```
HashSet<String> sites = new HashSet<String>();
```

部分方法：

```java
HashSet<String> sites = new HashSet<String>();
sites.add("Google");
sites.contains("Taobao");
sites.remove("Taobao");
sites.clear();
for (String i : sites) {
	System.out.println(i);
}
```

### HashMap

HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。

HashMap 实现了 Map 接口，根据键的 HashCode 值存储数据，具有很快的访问速度，最多允许一条记录的键为 null，不支持线程同步。

HashMap 是无序的，即不会记录插入的顺序。

HashMap 继承于AbstractMap，实现了 Map、Cloneable、java.io.Serializable 接口。

HashMap 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```
import java.util.HashMap; // 引入 HashMap 类
```

以下实例我们创建一个 HashMap 对象 Sites， 整型（Integer）的 key 和字符串（String）类型的 value：

```
HashMap<Integer, String> Sites = new HashMap<Integer, String>();
```

部分方法：

```java
// 创建 HashMap 对象 Sites
HashMap<Integer, String> Sites = new HashMap<Integer, String>();
// 添加键值对
Sites.put(1, "Google");
Sites.get(3);
Sites.remove(4);
// 输出 key 和 value
for (Integer i : Sites.keySet()) {
  System.out.println("key: " + i + " value: " + Sites.get(i));
}
// 返回所有 value 值
for(String value: Sites.values()) {
  // 输出每一个value
  System.out.print(value + ", ");
}
```

Java HashMap 常用方法列表如下：

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [clear()](https://www.runoob.com/java/java-hashmap-clear.html) | 删除 hashMap 中的所有键/值对                                 |
| [clone()](https://www.runoob.com/java/java-hashmap-clone.html) | 复制一份 hashMap                                             |
| [isEmpty()](https://www.runoob.com/java/java-hashmap-isempty.html) | 判断 hashMap 是否为空                                        |
| [size()](https://www.runoob.com/java/java-hashmap-size.html) | 计算 hashMap 中键/值对的数量                                 |
| [put()](https://www.runoob.com/java/java-hashmap-put.html)   | 将键/值对添加到 hashMap 中                                   |
| [putAll()](https://www.runoob.com/java/java-hashmap-putall.html) | 将所有键/值对添加到 hashMap 中                               |
| [putIfAbsent()](https://www.runoob.com/java/java-hashmap-putifabsent.html) | 如果 hashMap 中不存在指定的键，则将指定的键/值对插入到 hashMap 中。 |
| [remove()](https://www.runoob.com/java/java-hashmap-remove.html) | 删除 hashMap 中指定键 key 的映射关系                         |
| [containsKey()](https://www.runoob.com/java/java-hashmap-containskey.html) | 检查 hashMap 中是否存在指定的 key 对应的映射关系。           |
| [containsValue()](https://www.runoob.com/java/java-hashmap-containsvalue.html) | 检查 hashMap 中是否存在指定的 value 对应的映射关系。         |
| [replace()](https://www.runoob.com/java/java-hashmap-replace.html) | 替换 hashMap 中是指定的 key 对应的 value。                   |
| [replaceAll()](https://www.runoob.com/java/java-hashmap-replaceall.html) | 将 hashMap 中的所有映射关系替换成给定的函数所执行的结果。    |
| [get()](https://www.runoob.com/java/java-hashmap-get.html)   | 获取指定 key 对应对 value                                    |
| [getOrDefault()](https://www.runoob.com/java/java-hashmap-getordefault.html) | 获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值 |
| [forEach()](https://www.runoob.com/java/java-hashmap-foreach.html) | 对 hashMap 中的每个映射执行指定的操作。                      |
| [entrySet()](https://www.runoob.com/java/java-hashmap-entryset.html) | 返回 hashMap 中所有映射项的集合集合视图。                    |
| [keySet](https://www.runoob.com/java/java-hashmap-keyset.html)() | 返回 hashMap 中所有 key 组成的集合视图。                     |
| [values()](https://www.runoob.com/java/java-hashmap-values.html) | 返回 hashMap 中存在的所有 value 值。                         |
| [merge()](https://www.runoob.com/java/java-hashmap-merge.html) | 添加键值对到 hashMap 中                                      |
| [compute()](https://www.runoob.com/java/java-hashmap-compute.html) | 对 hashMap 中指定 key 的值进行重新计算                       |
| [computeIfAbsent()](https://www.runoob.com/java/java-hashmap-computeifabsent.html) | 对 hashMap 中指定 key 的值进行重新计算，如果不存在这个 key，则添加到 hasMap 中 |
| [computeIfPresent()](https://www.runoob.com/java/java-hashmap-computeifpresent.html) | 对 hashMap 中指定 key 的值进行重新计算，前提是该 key 存在于 hashMap 中。 |


