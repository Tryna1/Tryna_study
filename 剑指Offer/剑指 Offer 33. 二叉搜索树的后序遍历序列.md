**题意：** 输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。


**题解：** 通过后序遍历来划分左右子树，然后判断左子树中的元素是否都小于根，以及右子树中的元素是否都大于根。

```java
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        return dfs(postorder, 0, postorder.length - 1);
    }

    public boolean dfs(int[] postorder, int left, int right) {
        if(left >= right) return true;
        int i = left;
        while(postorder[i] < postorder[right]) i++;
        int m = i;
        while(postorder[i] > postorder[right]) i++;
        return i == right && dfs(postorder, left, m - 1) && dfs(postorder, m, right - 1); 
    }
}
```