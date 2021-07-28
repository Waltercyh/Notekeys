# Notekeys

## 动态规划
1. 最大子序和：f(i)代表包含num[i]的最大子序，f(i) = max(f(i-1)+num[i], num[i])，考虑 nums[i] 单独成为一段还是加入f(i−1) 对应的那一段
2. [编辑距离](https://leetcode-cn.com/problems/edit-distance/submissions/):首先：插入A和删除B等价。则可以全部转换为加入和替换。后续为常规解法。

### 有个值得注意的地方！
~~~
[[0]*(len2+1)]*(len1+1) #当中每一列为赋值，改变一列会造成其他列改变，导致无法正确初始化边界值
[[0]*(len2+1) for _ in range(len1+1)] #应该像这样建立dp数组
~~~

## 链表
1. [回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/): 关键在于想要时间复杂度O(n),空间复杂度O(1).所以需要在原链表上进行操作.所有回文都可以转化为倒序是否相同.于是转化为反转后半链表,看前后是否相同.定位后半链表可以使用快慢指针.
2. [寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/): 看似是数组问题,其实可以建模成链表.有重复数等价于链表有环.故可以借助快慢指针.记住快慢指针在不同问题中,快指针的判断是不一样的.比如单链表中快指针虽然一次走两步,但是每走一步都要判断一下条件(会走完/要算差值步数),但是在环形链表中,快指针要严格一次走两步,才能满足2(a+b).


## 哈希
1. [同构字符串](https://leetcode-cn.com/problems/isomorphic-strings/):构建两个哈希表，将已配对的部分存入，后续check当前出现的字符是否已配对，未配对则加入，已配对则判断是否符合。

## 用一个随机函数生成另一个:
1.[leetcode470](https://leetcode-cn.com/problems/implement-rand10-using-rand7/submissions/)
通过多次运行给定的随机函数生成足够多的均匀样本,从中以新随机函数的尺度划分.例如,通过两次rand7可以生成1到49(记住不是简单相乘,这样不是均匀的, 是(a-1)*scale1 + b).然后从中截取.多的可以扔掉,重新运行,也可以用于下次随机数生成.

## 单调栈
1. [柱形图最大面积](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/): 需要判断每个高度点上左侧比它小的位置,需要一个栈存位置, 且满足坐标和高度递增.重点在于,i位置入栈前,栈内比height[i]高的都可以pop,因为它们不再可能成为i右侧的选项(height[i]更小).
