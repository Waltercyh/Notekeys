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
2. [两数之和](https://leetcode.cn/problems/two-sum/)：重点是在list中查询已知值的复杂度为O(n)，通过hashtable降低为O(1)，并且通过hashtable存放从值到index的映射。
3. [字母异位词分组](https://leetcode.cn/problems/group-anagrams/description/?envType=study-plan-v2&envId=top-100-liked): 两个不一样的对象但具有同样的特征，第一反应通过哈希表建立映射，降低复杂度，如何对这个特征建模则是需要注意的。dict是一种很好的存放特征到对象的映射的数据结构。
4. [最长连续序列](https://leetcode.cn/problems/longest-consecutive-sequence/description/?envType=study-plan-v2&envId=top-100-liked): 思路很简单，通过首元素往下遍历，找下一个数是否存在就行。两个注意点：1.首元素怎么选：肯定是他的上一个数不在的，否则就会重复地找；2.如何降低找这个行为的时间复杂度：使用哈希表（set）。

## 用一个随机函数生成另一个:
1.[leetcode470](https://leetcode-cn.com/problems/implement-rand10-using-rand7/submissions/)
通过多次运行给定的随机函数生成足够多的均匀样本,从中以新随机函数的尺度划分.例如,通过两次rand7可以生成1到49(记住不是简单相乘,这样不是均匀的, 是(a-1)*scale1 + b).然后从中截取.多的可以扔掉,重新运行,也可以用于下次随机数生成.

## 单调栈
1. [柱形图最大面积](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/): 需要判断每个高度点上左侧比它小的位置,需要一个栈存位置, 且满足坐标和高度递增.重点在于,i位置入栈前,栈内比height[i]高的都可以pop,因为它们不再可能成为i右侧的选项(height[i]更小).
2. 


## 回溯/遍历/组合
1. [组合数](https://leetcode-cn.com/problems/combination-sum-iii/submissions/) 组合可以看作dfs.
2. [单词搜索](https://leetcode.cn/problems/word-search/description/?envType=study-plan-v2&envId=top-100-liked) 注意这题和腐烂的橘子那一题的区别。这题是搜索一个单词，代表一条路径，路径的题不可用广度搜索，因为广度搜索时同层同时遍历，就没有路径的概念了，无法规定同层的另一个元素的时序，而应该用回溯（类似于dfs）。而腐烂的橘子本身是传播，橘子间没有差异，故同层搜索没有问题，可以用bfs。


## 二叉树
1. [路径总和](https://leetcode.cn/problems/path-sum-iii/submissions/507317100/?envType=study-plan-v2&envId=top-100-liked) 前缀和本身不难想，关键是在求前缀和的过程中把之前节点的和存下来，并查找，记住查找优先考虑hashmap(dict).


## 数组两边偏序的转化
1. [发糖](https://leetcode-cn.com/problems/candy/submissions/)  要求比两边高,可以从左到右和从右到左各遍历一次,先分立地求出解,再求max.这样就将两边的偏序分拆成了两个子问题.


## 状态机
1. [字符串转换整数 (atoi)](https://leetcode-cn.com/problems/string-to-integer-atoi/): 这种有多个情况, 且每个情况之间转换固定, 可以建模成状态机, 简洁明了.

## 贪心算法
1. [跳跃游戏II](https://leetcode.cn/problems/jump-game-ii/solutions/230241/tiao-yue-you-xi-ii-by-leetcode-solution/?envType=study-plan-v2&envId=top-100-liked)：每次记录当前可达位置的最大可达位置，作为下次可达的最远位置。比较巧妙的是，不需要记录最大可达位置的起始位置，因为最大可达位置是当前可达位置共用的，所以只要到当前可达的位置最大值就加1，而当前可达位置的最大值就是上一步的最大可达位置，因此走到最大可达位置后更新下一步的最大位置为当前最大可达位置，然后step+1就行。
