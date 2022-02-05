## 1.Algorithm

[1]&nbsp;&nbsp;[Two Sum](https://leetcode.com/problems/two-sum/description/)

**Easy** &nbsp;&nbsp; **array** &nbsp;&nbsp; **hash-table**

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

**解答**
本题可以采用常规的方法和基于 hashtab 的方式进行处理(题目描述中已经定义不存在重复的数据)

##### (1).常规解法, 2 层循环，时间复杂度 O(n\*n)

```

```

##### (2).基于 Hash，算术运算, 改成 1 层循环，时间复杂度 O(n)， 用空间换时间的思路

```

```

## 2.Review
* [HTAP(Hybird transaction/analytical processing)](https://en.wikipedia.org/wiki/Hybrid_transactional/analytical_processing)
* [How We Build an HTAP Database That Simplifies Your Data Platform](https://en.pingcap.com/blog/how-we-build-an-htap-database-that-simplifies-your-data-platform/)
* [The Past, Present, and Future of TiDB as an HTAP Database](https://pingcap.medium.com/the-past-present-and-future-of-tidb-as-an-htap-database-b9fa96ecd1c7)
* [Making an HTAP Database a Reality: What I Learned From PingCAP’s VLDB Paper](https://medium.com/swlh/making-an-htap-database-a-reality-what-i-learned-from-pingcaps-vldb-paper-6d249c930a11)

## 3.Tip

## 4.Share