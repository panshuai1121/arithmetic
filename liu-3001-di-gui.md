# 递归

递归最简单的理解就是自己调用自己本身，如果使用循环可能程序的性能很高，如果使用递归程序上更便于理解。

## 一、基线条件和递归条件

基线条件（base case）：函数不在自己调用自己的条件 ，避免死循环

递归条件（recursive case）：函数调用自己

```
#写一个倒计时 3....2...1

function countDown($i) {
    if ($i <= 0) { //基线条件
        return;
    } else {        //递归条件
      print $i;
      countDown($i - 1);
    }

}
countDown(3);
```

```
$arr = [1,5,4];

function arrSum(&$arr) {
    if (count($arr) == 0) {
       return ;
    }
    $x = array_pop($arr);
    return $x + arrSum($arr);
}
echo arrSum($arr);
```



