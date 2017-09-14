# 冒泡排序



```
<?php

$arr = [10,31,2,1,356,1123,456,117,21123,5677,11,8];

function bubbling($arr) {
    for($i = 0 , $len = count($arr) -1 ; $i < $len ; $i++) {
      for($k =  $i ,$len = count($arr); $k < $len ; $k++) {
        if ($arr[$i] < $arr[$k+1]) {
            $temp = $arr[$i];
            $arr[$i] = $arr[$k+1];
            $arr[$k+1] = $temp;
        }
      }
    }
    return $arr;
}

print_r(bubbling($arr));
```



