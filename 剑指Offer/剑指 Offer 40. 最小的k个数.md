**题意：** 输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

**题解：** 直接排序即可。

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        Arrays.sort(arr);
        int[] res = new int[k];
        for(int i = 0; i < k; i++)
            res[i] = arr[i];
        return res;
    }
}
```



**归并排序版**

```java
class Solution {
    int[] arr, tmp;
    public int[] getLeastNumbers(int[] arr, int k) {
        this.arr = arr;
        tmp = new int[arr.length];
        mergeSort(0, arr.length - 1);
        int[] res = new int[k];
        for(int i = 0; i < k; i++)
            res[i] = this.arr[i];
        return res;
    }

    public void mergeSort(int l, int r) {
        if(l >= r) return ;
        int mid = (l + r) >> 1;
        mergeSort(l, mid);
        mergeSort(mid + 1, r);
        int i = l, j = mid + 1;
        for(int k = l ; k <= r; k++)
            tmp[k] = arr[k];
        for(int k = l; k <= r; k++) {
            if(i == mid + 1)
                arr[k] = tmp[j++];
            else if(j == r + 1 || tmp[i] <= tmp[j])
                arr[k] = tmp[i++];
            else arr[k] = tmp[j++];
        }
    }

}
```

**快速排序版**

```java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        quickSort(arr, 0, arr.length - 1);
        return Arrays.copyOf(arr, k);
    }

    public void quickSort(int[] arr, int l, int r) {
        if(l >= r) return ;
        int i = l, j = r;
        while(i < j) {
            while(i < j && arr[l] <= arr[j]) j--;
            while(i < j && arr[l] >= arr[i]) i++;
            swap(arr, i, j);
        }
        swap(arr, i, l);
        quickSort(arr, l, i - 1);
        quickSort(arr, i + 1, r);
    }

    public void swap(int[] arr, int i, int j) {
        int tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
    }
}
```