#### 剑指offer 连续子数组的最大和

------

【难度】 ⭐ 

【题目】

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

###### 解法一：动态规划

1.  首先判断数组nums是否长度为1，如果为1，直接返回该第一位元素。
2.  取nums的长度计作n，申明动态规划状态数组dp切长度为n。
3.  从1到n开始循环数组nums并更新dp，**因为需要的是连续子数组的最大值，dp[i] 的值为dp[i-1]加上当前nums[i]和当前值nums[i]的最大值**。
4.  最后返回状态数组dp中的最大值。

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return nums[0]
        n = len(nums)
        dp = [0] * n
        for i in range(1, n):
            dp[i] = max(dp[i-1] + nums[i], nums[i])
        return max(dp)
```

