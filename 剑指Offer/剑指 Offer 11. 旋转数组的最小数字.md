**题意：** 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。

给你一个可能存在 重复 元素值的数组 numbers ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一次旋转，该数组的最小值为1。  


**题解：** 很明显采用二分法。

* 当`numbers[mid] > numbers[r]`时，说明mid肯定在左排序数组中，所以mid以及mid左边的数字都不可能是最小值，所以令`l = mid + 1`
* 当`numbers[mid] < numbers[r]`时，说明mid肯定在右排序数组中，所以mid右边的数字肯定不是最小值，所以令`r = mid`
* 当`numbers[mid] == numbers[r]`时，无法确定mid在哪个数组中，只能把r排除掉，所以令`r = r - 1`


```java
class Solution {
    public int minArray(int[] numbers) {
        int l = 0, r = numbers.length - 1;
        int m = 0;
        while(l < r) {
            m = (l + r) >> 1;
            if(numbers[m] > numbers[r])
                l = m + 1;
            else if(numbers[m] < numbers[r])
                r = m;
            else r--;
        }
        return numbers[l];
    }
}
```