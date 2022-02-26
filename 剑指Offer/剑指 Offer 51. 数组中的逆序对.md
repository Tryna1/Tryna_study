**题意：** 在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。


**题解：** 利用归并排序，在排序成有序序列的时候计算逆序对的数量，分为左右两个数组，当左数组中当前元素大于右数组中当前元素时，贡献加左数组剩余数组元素数量。

```java
class Solution {
    int[] nums, tmp;
    public int reversePairs(int[] nums) {
        this.nums = nums;
        tmp = new int[nums.length];
        return mergeSort(0, nums.length - 1);
    }

    public int mergeSort(int l, int r) {
        if(l >= r) return 0;
        int mid = (l + r) >> 1;
        int res = mergeSort(l, mid) + mergeSort(mid + 1, r);

        int i = l, j = mid + 1;
        for(int k = l; k <= r; k++) {
            tmp[k] = nums[k];
        } 
        for(int k = l; k <= r; k++) {
            if(i == mid + 1)
                nums[k] = tmp[j++];
            else if(j == r + 1 || tmp[i] <= tmp[j])
                nums[k] = tmp[i++];
            else {
                nums[k] = tmp[j++];
                res += mid - i + 1;
            }
        }
        return res;
    }
}
```