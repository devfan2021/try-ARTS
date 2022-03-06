## 1.Algorithm

[91]&nbsp;&nbsp;[Decode Ways](https://leetcode.com/problems/decode-ways/description/)

**Easy** &nbsp;&nbsp; **String** &nbsp;&nbsp; **Dynamic Programming**

A message containing letters from A-Z can be encoded into numbers using the following mapping:

'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
To decode an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, "11106" can be mapped into:

"AAJF" with the grouping (1 1 10 6)
"KJF" with the grouping (11 10 6)
Note that the grouping (1 11 06) is invalid because "06" cannot be mapped into 'F' since "6" is different from "06".

Given a string s containing only digits, return the number of ways to decode it.

The test cases are generated so that the answer fits in a 32-bit integer.

Example 1:

```
Input: s = "12"
Output: 2
Explanation: "12" could be decoded as "AB" (1 2) or "L" (12).
```

Example 2:

```
Input: s = "226"
Output: 3
Explanation: "226" could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

Example 3:

```
Input: s = "06"
Output: 0
Explanation: "06" cannot be mapped to "F" because of the leading zero ("6" is different from "06").
```

Constraints:

```
1 <= s.length <= 100
s contains only digits and may contain leading zero(s).
```

**解答**
本题采用动态代理方式：
(1)case1: f(n) = f(n-1), when s[n] != 0
(2)case2: f(n) = f(n-2), when s[n-1] != 0 and 10*s[n-1]+s[n] <= 26
(3)当n=1时，f(n) = 1
* 

##### (1).动态规划，时间复杂度为O(n), 空间复杂度为O(n)

```golang
func numDecodings(s string) int {
 n := len(s)
 dp := make([]int, n+1)
 dp[0] = 1
 for i := 1; i <= n; i++ {
  if s[i-1] != '0' {
   dp[i] += dp[i-1]
  }
  if i > 1 && s[i-2] != '0' && ((s[i-2]-'0')*10+(s[i-1]-'0') <= 26) {
   dp[i] += dp[i-2]
  }
 }
 return dp[n]
}

```

##### (2).动态规划，时间复杂度为O(n), 优化空间，提取出f(n-2),f(n-1),f(n)

```golang
func numDecodings(s string) int {
    n := len(s)
 // a=f(n-2), b=f(n-1), c=f(n)
 a, b, c := 0, 1, 0
 for i := 1; i <= n; i++ {
        c = 0
  if s[i-1] != '0' {
   c += b
  }
  if i > 1 && s[i-2] != '0' && ((s[i-2]-'0')*10+(s[i-1]-'0') <= 26) {
   c += a
  }
  a, b = b, c
 }
 return c
}
```

## 2.Review
[Event Sourcing pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)
[Pattern: Event sourcing](https://microservices.io/patterns/data/event-sourcing.html)

## 3.Tip
confluence本地化部署初始化数据库一直提示报错“ERROR 1419 (HY000): You do not have the SUPER privilege and binary logging is enabled (you *might* want to use the less safe log_bin_trust_function_creators variable)”

解决版本是：my.cnf中设置“log_bin_trust_function_creators = 1”
[Why SUPER privileges are disabled when binary logging option is on?](https://stackoverflow.com/questions/56389698/why-super-privileges-are-disabled-when-binary-logging-option-is-on)
["You do not have the SUPER privilege and binary logging is enabled" #76](https://github.com/soundcloud/lhm/issues/76)

## 4.Share
[从四方面聊聊，如何从0到1搭建营销活动后台](http://www.woshipm.com/pd/628318.html)
[vivo营销自动化技术解密｜开篇](https://mp.weixin.qq.com/s/Ja9aWRQ9QFdBn2o8MhWFjA)
[设计模式如何提升 vivo 营销自动化业务扩展性 | 引擎篇01](https://mp.weixin.qq.com/s/F0BFvFvufPJ7AdkguHTcwQ)
[企业数字化营销的“底盘”：营销中台和数据管理平台](http://www.woshipm.com/marketing/3857526.html)
[解析营销中台产品模型](http://www.woshipm.com/pd/2663713.html)
[用户增长的第三极——场景流量](http://www.woshipm.com/operate/2020277.html)

有关营销中台方面的几篇文章，最佳自己也在学习这块，非常值得借鉴学习