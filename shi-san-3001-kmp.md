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

