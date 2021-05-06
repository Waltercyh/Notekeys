# Notekeys

## 动态规划
1. 最大子序和：f(i)代表包含num[i]的最大子序，f(i) = max(f(i-1)+num[i], num[i])，考虑 nums[i] 单独成为一段还是加入f(i−1) 对应的那一段
2. [编辑距离](https://leetcode-cn.com/problems/edit-distance/submissions/):首先：插入A和删除B等价。则可以全部转换为加入和替换。后续为常规解法。


## 哈希
1. [同构字符串](https://leetcode-cn.com/problems/isomorphic-strings/):构建两个哈希表，将已配对的部分存入，后续check当前出现的字符是否已配对，未配对则加入，已配对则判断是否符合。
