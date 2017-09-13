# 二分查找

---

什么是二分查找，比如说当我们去图书馆去查看书籍，书籍都是按照书籍英文的首字母大小写进行排序，如果我们需要找到一本关于PHP的书籍，那么就会去看 与字母“P” 附近的位置，进行查找，这就是二分法。

### 二分查找的重点：

1、必须是有序列表

2、查找对的时候返回查找元素的位置

3、没有找到的时候返回null

4、**对数的了解**

### 二分法的时间复杂度

$$\log_2 n$$ 相当于多少个2乘级等于n

### PHP代码实现

```
<?php

$arr = [1,3,5,8,9,100,105,107,109,158,201,202,203,204,230,241,300];
$searchNumber = 201;

function binarySearch($searchNumber,$arr) {
    #最低位置
    $low = 0;
    #最高位置
    $high = count($arr);
    #中间位置
    while ($low <= $high) {

      $middle = floor(($low + $high) / 2);
      #取中间值
      $guess = $arr[$middle];
      #判断如果中间值 等于猜的数，直接返回该位置
      if($guess ==  $searchNumber) {
          return $middle;
      #判断如果中间位置的数值小于要查找的数值
      } elseif ($guess > $searchNumber) {
          $high = $middle - 1;
      } else {
          $low = $middle + 1;
      }

    }

}


echo binarySearch($searchNumber,$arr);
```



