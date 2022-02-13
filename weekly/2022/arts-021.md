## 1.Algorithm

[1446]&nbsp;&nbsp;[Consecutive Characters](https://leetcode.com/problems/consecutive-characters/description/)

**Easy** &nbsp;&nbsp; **string** &nbsp;&nbsp;

The power of the string is the maximum length of a non-empty substring that contains only one unique character.

Given a string s, return the power of s.

Example 1:

```
Input: s = "leetcode"
Output: 2
Explanation: The substring "ee" is of length 2 with the character 'e' only.
```

Example 2:

```
Input: s = "abbcccddddeeeeedcba"
Output: 5
Explanation: The substring "eeeee" is of length 5 with the character 'e' only.
```

Constraints:

```
1 <= s.length <= 500
s consists of only lowercase English letters.
```

**解答**
本题直接采用常规的字符串变量方式，进行计数大小比较

##### (1).常规解法, 1层循环，时间复杂度 O(n)

```golang
func maxPower(s string) int {
    max, cMax, cFirst := 0, 0, rune(s[0])
    for _, v := range s {
        if cFirst == v {
            cMax += 1
        } else {
            if cMax > max {
                max = cMax
            }
            cFirst = v
            cMax = 1
        }
    }
    if cMax > max {
        return cMax
    }
    return max
}
```

## 2.Review

* [Microservices vs. SOA](https://dzone.com/articles/microservices-vs-soa-2)
* [Microservices vs. SOA – Is There Any Difference at All?](https://dzone.com/articles/microservices-vs-soa-is-there-any-difference-at-al)
* [Microservices, SOA, and APIs: Friends or enemies?](https://developer.ibm.com/tutorials/1601_clark-trs/)

## 3.Tip

no tips in this week

## 4.Share

* [COLA 4.0：应用架构的最佳实践](https://blog.csdn.net/significantfrank/article/details/110934799)
* [Clean Code之封装：把野兽关进笼子](https://blog.csdn.net/significantfrank/article/details/122738602)