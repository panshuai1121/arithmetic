# 选择排序

随着排序的进行，每次检查元素的个数越来越少，最后一次的检查只有一个，并非每次检查n个元素，第一次n-1，第二次n-2。。。和1，平局每次检查， 在表示的时候 大O会去掉常数 O\(n^2\)

思路：

1、需要有一个需要排序的数组

2、每一次进行比较时先取出数组中第一个数与下一个数进行比较，如果当前数比下一个数大，那么下一个数变成，当前数，并且记录最小数得索引位置

3、每次比较后把最小索引的数，放在新的数组当中

```
$arr = [17,13,1,7,9,0,11,24,61];

function findSmallNumber($arr) {
    $small = $arr[0];
    $smallIndex = 0;
    for ($i = $smallIndex; $i < count($arr); $i++) {
        if ($arr[$i] < $small) {
            $small = $arr[$i];
            $smallIndex =  $i;
        }
    }
    return $smallIndex;
}

function selectionSort($list) {
    $sorted = [];
    $len = count($list);
    for ($i = 0 ; $i < $len; $i++) {
        $index = findSmallNumber($list);
        $sorted[] = array_splice($list, $index, 1)[0];
    }
    return $sorted;
}
echo "<pre>";
print_r(selectionSort($arr));
```



