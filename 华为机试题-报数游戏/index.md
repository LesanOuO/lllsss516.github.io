# 华为机试题：报数游戏


在进行华为机试时遇到了报数游戏的编程题（约瑟夫环），但是看了很多网上的解题都非常长，于是经过不断的学习参考，有了下面这个解题方法，也不知道是不是最好的😭

**题目：**

100个人围成一圈，每个人有一个编码，编号从1开始到100.他们从1开始依次报数，报到为M的人自动退出圈圈，然后下一个人接着从1开始报数，直到剩余的人数小于M。请问最后剩余的人在原先的编号为多少？

例如：输入M=3时，输出为：“58，91”；输入M=4时，输出为： “34，45， 97”

**解答：**

```java
import java.util.*;

public class test {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        List list = new ArrayList<Integer>(100);
        for (int i = 1; i <= 100; i++) {
            list.add(i);
        }
        int i = 0;
        while (list.size() >= n) {
            i = (i + n - 1) % list.size();
            list.remove(i);
        }
        list.stream().forEach(System.out::println);
    }
}
```
