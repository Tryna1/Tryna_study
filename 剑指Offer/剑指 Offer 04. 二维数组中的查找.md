**题意：** 在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

**题解：** 我们要善于采用每一行和每一列都递增的条件。我们以右上角为起点，当当前元素的值大于`target`时，我们向下找才有可能找到答案；当当前元素的值小于`target`时，我们向左找才有可能找到答案。

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0)
            return false;
        int rows = matrix.length;
        int columns = matrix[0].length;
        int n = 0, m = columns - 1;
        while(true) {
            if(n >= rows || m < 0) break;
            if(matrix[n][m] > target)
                m--;
            else if(matrix[n][m] < target)
                n++;
            else return true;
        }
        return false;
    }
}
```