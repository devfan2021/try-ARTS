## 1.Algorithm

[1941]&nbsp;&nbsp;[Check if All Characters Have Equal Number of Occurrences](https://leetcode.com/problems/check-if-all-characters-have-equal-number-of-occurrences/description/)

**Easy** &nbsp;&nbsp; **Hash Table** &nbsp;&nbsp; **String** &nbsp;&nbsp; **Counting**

Given a string s, return true if s is a good string, or false otherwise.

A string s is good if all the characters that appear in s have the same number of occurrences (i.e., the same frequency).

Example1:

```
Input: s = "abacbc"
Output: true
Explanation: The characters that appear in s are 'a', 'b', and 'c'. All characters occur 2 times in s.
```

Example1:

```
Input: s = "aaabb"
Output: false
Explanation: The characters that appear in s are 'a' and 'b'.
'a' occurs 3 times while 'b' occurs 2 times, which is not the same number of times.
```

Constraints:

```
1 <= s.length <= 1000
s consists of lowercase English letters.
```

**解答**
本题可以采用常规的方法和基于 hashtab 的方式进行处理

##### (1).常规解法, 1层循环，时间复杂度 O(n)

```
func areOccurrencesEqual(s string) bool {
  if len(s) == 0 {
  return false
 }

 hashMap := make(map[rune]int, 0)
 for _, v := range s {
  hashMap[v] = hashMap[v] + 1
 }

 count := -1
 for _, v := range hashMap {
  if count == -1 {
   count = v
  }
  if count != v {
   return false
  }
 }
 return true
}
```

## 2.Review

* [CQRS](https://martinfowler.com/bliki/CQRS.html)
* [Clarified CQRS](https://udidahan.com/2009/12/09/clarified-cqrs/)
* [Pattern: Command Query Responsibility Segregation (CQRS)](https://microservices.io/patterns/data/cqrs.html)
* [QRS pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs)

## 3.Tip

本周一个比较大的收获就是使用Draw.io将新接手的系统在原先产品的流程图上重新进行优化，主要包括一些几部分：
(1). 加入缺失的关联系统，缺失的流程，使系统达到了一个相对完善的闭环流程
(2). 对流程图中的图标进行重新布局，调整整体的布局及连线
(3). 增加图例说明，将图例变小，使之成为整个图的辅助部分

从整个工作的流程来说有以下几大收获：
(1). 画图的过程使得自己对系统的整个流程有新的认识，方便快速熟悉接手的系统
(2). 稍微花点功夫，就可以将图调整的非常完美：比如统一图块的大小，连线方式，图块的对齐与布局等
(3). 做事是一个迭代的过程，在迭代的过程中你会发现更优雅的方案

## 4.Share

* [科技爱好者周刊（第195期）：你做过不在乎结果的项目吗？](https://mp.weixin.qq.com/s/4adHFTc_EOrbsUVPp-8ibg)
阮一峰老师的这期周刊中有个关于《你做过不在乎结果的项目吗？》是值得非常反思的一个问题，之前自己也不停尝试去学习或者做一些新的东西，但是往往都半途而废；摘录文中阮老师的话：
“不管多么忙，还是应该留出一点时间，放在自己的兴趣项目上面，哪怕得不到任何结果”，原因有两个：
（1）兴趣项目可以大大提升你的技术水平。
（2）兴趣项目可以塑造一个人。
兴趣项目就有这个作用，让你认识自己、塑造自己，壮大追求梦想的决心。
