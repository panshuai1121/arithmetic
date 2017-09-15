## 快速排序（优雅代码的典范）

**分而治之**，可能遇到使用任何已知算法都无法解决的问题，不应因此放弃，而是应该尝试使用掌握各种问题得解决方法，来找出解决问题的答案，快速排序采用分而治之的策略。

divide and conquer，D&C  **一种著名得递归式问题解决办法**。

分治算法是基于多分枝递归的一种算法设计模式。分治算法递归地把一个大问题分解为多个类型相同的子问题，直到这些子问题足够的简单能被直接解决。最后把这些子问题的解结合起来就能得到原始问题的解。

根据这个定义，我们可以很明显的知道，对于D&C问题，我们解决它需要两步，一是要找到递归式；二是要根据递归式能找到最后的答案

## 原理：

1、先找到一个基准值

2、创建两个分区、大于基准值 小于基准值

3、对于两个分区进行排序

4、小数组 + 基准值 + 大数组

5、**选择排序的速度与基准有关， 最好的状态下它得运行速度是 O\(n log n\)  最糟糕的情况是 O\(n^2\)**



```
<?php

$arr = [40,9,71,61,53,57,59,94,13,15];

function quickSort($arr) {
  if (count($arr) < 2) {
      return $arr;
  }
  //基准值
  $standard = $arr[0];
  $sort_left = [];
  $sort_right = [];
  for ($i = 1 ; $i < count($arr); $i++) {
      if ($arr[0] > $arr[$i]) {
          $sort_left[] = $arr[$i];
      } else {
          $sort_right[] = $arr[$i];
      }
  }
  $sortLeft = quickSort($sort_left);
  $sortRight = quickSort($sort_right);
  return array_merge($sortLeft,[$standard],$sortRight);

}

print_r(quickSort($arr));
```



