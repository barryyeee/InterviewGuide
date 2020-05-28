# 二叉树路径总和

描述：给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

```java
/*递归方法*/
class Solution {
    private List<List<Integer>> res = new ArrayList<>();
    private List<Integer> out = new ArrayList<>();
    
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        helper(root, sum);
        return res;
    }
    private void helper(TreeNode root, int sum) {
        if (root == null) return;
        out.add(root.val);
        if (root.val == sum && root.right == null && root.left == null) 
            res.add(new ArrayList<>(out));
        helper(root.left, sum - root.val);
        helper(root.right, sum - root.val);
        out.remove(out.size() - 1);
    }
}
```

```java
/*非递归方法*/
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> res = new ArrayList<>();
        if (root == null) return res;
        
        List<TreeNode> stack = new ArrayList<>();
        TreeNode p = root, pre = null;
        int val = 0;
        while (p != null || !stack.isEmpty()) {
            if (p != null) {
                stack.add(p);
                val += p.val;
                p = p.left;
            }
            else {
                TreeNode tmp = stack.get(stack.size() - 1);
                if (tmp.right == null && tmp.left == null && val == sum) {
                    List<Integer> out = new ArrayList<>();
                    for (TreeNode node : stack) 
                        out.add(node.val);
                    res.add(out);
                }
                if (tmp.right != null && pre != tmp.right)
                    p = tmp.right;
                else {
                    pre = tmp;
                    val -= tmp.val;
                    stack.remove(tmp);
                }
            }
        }
        return res;
    }
}
```

ps. 因为二叉树的数据结构是需要自定义的，所以实际面试时面试官并没有要求我运行，他仅让我写出代码然后叙述一下思路。

LeetCode链接：  
https://leetcode-cn.com/problems/path-sum-ii/