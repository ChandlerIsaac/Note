# 数组

## 两数之和（1）

> https://leetcode.cn/problems/two-sum/

### 题解一（self）

使用简单的双层循环遍历

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
            int ans[]={0,0};
        for(int i =0;i<nums.length;i++){
            for(int j = i+1;j<nums.length;j++){
                if(nums[i] + nums[j] == target){
                    ans[0] = i;
                    ans[1] = j;
                }
            }
        }
        return ans;
    }
}
```

### 题解二（官方）

> 使用哈希表  空间换时间

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> hashMap = new  HashMap<Integer,Integer>();  
        for(int i = 0;i<nums.length;i++){
            if(hashMap.containsKey(target - nums[i]))
                return new int[]{i,hashMap.get(target - nums[i])};
            hashMap.put(nums[i],i);
        }
        return new int[0];
}
}
```

# 字符串

## 回文数（9）

> https://leetcode.cn/problems/palindrome-number/

### 解法一（使用字符串）

```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0)return false;
        Integer num = (Integer)x;
        String s = num.toString();
        int i = 0,j=s.length()-1;
        while(i<j){
            char a = s.charAt(i);
            char b = s.charAt(j);
            if(a != b)
                return false;
            i++;
            j--;
        }
        return true;
    }
}
```

## ==最长公共前缀（14）==

>https://leetcode.cn/problems/longest-common-prefix/description/

