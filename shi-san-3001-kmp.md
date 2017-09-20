# 字符串匹配的KMP算法 {#page-title}

Knuth-Morris-Pratt算法 简称 KMP算法，是最常用的算法之一，它以三个发明者命名，起头的那个K就是著名科学家Donald Knuth

内容转载：[阮一峰](http://www.ruanyifeng.com/)

举例来说，有一个字符串"BBC ABCDAB ABCDABCDABDE"，我想知道，里面是否包含另一个字符串"ABCDABD"？

1、首先，字符串"BBC ABCDAB ABCDABCDABDE"的第一个字符与搜索词"ABCDABD"的第一个字符，进行比较。因为B与A不匹配，所以搜索词后移一位

![](http://image.beekka.com/blog/201305/bg2013050103.png)

2、B与A不匹配，搜索词再往后移

![](http://image.beekka.com/blog/201305/bg2013050104.png)

3、就这样，直到字符串有一个字符，与搜索词的第一个字符相同为止。

![](http://image.beekka.com/blog/201305/bg2013050105.png)

4、接着比较字符串和搜索词的下一个字符，还是相同。

![](http://image.beekka.com/blog/201305/bg2013050106.png)

5、直到字符串有一个字符，与搜索词对应的字符不相同为止。

![](http://image.beekka.com/blog/201305/bg2013050107.png)

6、这时，最自然的反应是，将搜索词整个后移一位，再从头逐个比较。这样做虽然可行，但是效率很差，因为你要把"搜索位置"移到已经比较过的位置，重比一遍。

![](http://image.beekka.com/blog/201305/bg2013050108.png)

7、一个基本事实是，当空格与D不匹配时，你其实知道前面六个字符是"ABCDAB"。KMP算法的想法是，设法利用这个已知信息，不要把"搜索位置"移回已经比较过的位置，继续把它向后移，这样就提高了效率

![](http://image.beekka.com/blog/201305/bg2013050107.png)

8、怎么做到这一点呢？可以针对搜索词，算出一张《部分匹配表》（Partial Match Table）。这张表是如何产生的，后面再介绍，这里只要会用就可以了

![](http://image.beekka.com/blog/201305/bg2013050109.png)

![](http://image.beekka.com/blog/201305/bg2013050107.png)

9、已知空格与D不匹配时，前面六个字符"ABCDAB"是匹配的。查表可知，最后一个匹配字符B对应的"部分匹配值"为2，因此按照下面的公式算出向后移动的位数：

```
　移动位数 = 已匹配的字符数 - 对应的部分匹配值
```

因为 6 - 2 等于4，所以将搜索词向后移动4位

10、

![](http://image.beekka.com/blog/201305/bg2013050110.png)

因为空格与Ｃ不匹配，搜索词还要继续往后移。这时，已匹配的字符数为2（"AB"），对应的"部分匹配值"为0。所以，移动位数 = 2 - 0，结果为 2，于是将搜索词向后移2位。

11、

![](http://image.beekka.com/blog/201305/bg2013050111.png)

