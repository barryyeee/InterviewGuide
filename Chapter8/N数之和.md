# N数之和

描述：给定一个数组arr，从中选出n个数的和等于target

面试官问我这道题的时候我现场没有想出来，事后思考了一下，其实和全排列的本质相同，只是多了两个限制条件：选出n个数、和为target，仍然可以用回溯+剪枝来实现，记得考虑去重。

```java
class Solution {
    private List<List<Integer>> res = new ArrayList<>();
    
    public List<List<Integer>> calSum(int[] arr, int target, int n) {
        List<Integer> out = new ArrayList<>();
        Arrays.sort(arr); //先对数组进行排序，方便后续去重
        DFS(arr, target, n, out, 0);
        return res;
    }
    
    private void DFS(int[] arr, int target, int n, List<Integer> out, int cur) {
        /*递归出口*/
        if(target < 0 || out.size() > n || cur > arr.length) 
            return;
        /*符合条件的out加入结果集中*/
        else if(target == 0 && out.size() == n) {
            res.add(new ArrayList<>(out));
            return;
        }
        else {
            int pre = -1; //去重：递归进入的同一层函数，所选数字不能相同
            for(int i = cur; i < arr.length; i++) {
                if(pre != -1 && arr[pre] == arr[i]) continue; //跳过重复的数
                pre = i;
                out.add(arr[i]);
                countSum(arr, target - arr[i], n, out, i + 1);
                out.remove(out.size() - 1);
            }
        }
    }
}
```

后来在网上搜的时候，发现了另一种解法：利用二进制来进行标记与选择。比如数组中有4个数，要选出3个数使其和为target，相当于$$C_{4}^{3}$$，那么二进制1011就表示从4个数中选第1,3,4个数（剩下的3种情况为0111、1101、1110），选出数组中第1,3,4个数后，判断其和是否等于target，等于的话就加入结果集中。

长度为4的数组中可以有哪几种选择情况呢？因为n一定是一个正整数，所以总共有$$C_{4}^{1}+C_{4}^{2}+C_{4}^{3}+C_{4}^{4}=15$$种选择方案，对应就是n=1（二进制0001）到n=4（二进制1111）的所有可能，所以遍历的范围是$1\leq i\leq 15$，也就是$1\leq i< 16$，16可以通过位移运算1<<4得到，即上限bit = 1 << arr.length

该算法涉及一些位运算操作，比如按位与&和左移<<等，不过bit位移时有溢出风险，且算法时间复杂度为O(n)=2^n，数组过大时会超时或爆栈。但觉得使用二进制的思路很棒，还是分享一下。

```java
class Solution {
    public List<List<Integer>> calSum(int[] arr, int n, int target) {
        Arrays.sort(arr); //先对数组进行排序，方便后续去重
        List<List<Integer>> res = new ArrayList<>();
        int len = arr.length;
        int bit = 1 << len; //需遍历的二进制的上限
        for(int i = 1; i < bit; i++) {
            int sum = 0;
            List<Integer> out = new ArrayList<>();
            if(countOne(i) == n) {
                /*二进制选取数字的方案与数组中的数的映射*/
                for(int j = 0; j < len; j++) {
                    /*取出二进制中所有1映射的数组相应位置的数并计算它们的和*/
                    if((i & 1 << j) != 0) {
                        sum += arr[j];
                        out.add(arr[j]);
                    }
                }
                /*符合sum=target且不重复的结果加入结果集中*/
                if(sum == target && !res.contains(out)) res.add(out);
            }
        }
        return res;
    }
    /*计算二进制中有几个1*/
    private int countOne(int num) {
        int count = 0;
        while(num > 0) {
            num = num & (num - 1);
            count++;
        }
        return count;
    }
}
```