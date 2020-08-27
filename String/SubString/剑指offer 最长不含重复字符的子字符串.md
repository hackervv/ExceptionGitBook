#### 剑指offer 最长不含重复字符的子字符串

------

【难度】 ⭐  ⭐ 

【题目】

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

###### 解法一：滑动窗口加hashmap

1.  如果字符串为空，直接返回0。声明子串的头索引为head，返回结果res，用于记录字符对应位置的字典hp。
2.  从头开始循环字符串s，tail作为子串结尾的索引。
3.  如果当前tail对应的字符存在字典，则表明已经出现了重复，**更新头节点到头节点和当前tail对应字符串索引的最大值**。
4.  将当前tail的字符存入字典hp，值为tail+1，更新res为res 和 当前首尾之差的最大值。
5.  循环结束，返回res。

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:
            return 0
        head, res = 0, 0
        hp = {}
        for tail in range(len(s)):
            if s[tail] in hp:
                head = max(head, hp.get(s[tail]))
            hp[s[tail]] = tail + 1
            res = max(res, tail - head + 1)
        return res
```

