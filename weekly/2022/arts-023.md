## 1.Algorithm

[412]&nbsp;&nbsp;[Fizz Buzz](https://leetcode.com/problems/fizz-buzz/description/)

**Easy** &nbsp;&nbsp; **Math** &nbsp;&nbsp; **String**

Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.

Example 1:

```
Input: n = 3
Output: ["1","2","Fizz"]
```

Example 2:

```
Input: n = 5
Output: ["1","2","Fizz","4","Buzz"]
```

Example 3:

```
Input: n = 15
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
```

Constraints:

```
1 <= n <= 104
```

**解答**
本题是简单题，考察对数组的运算操作

##### (1).常规解法, 先初始化数组，再对数组位上的值进行比较，时间复杂度 O(n)

```golang
func fizzBuzz(n int) []string {
 retVal := make([]string, n)
 for index := 0; index < n; index++ {
  retVal[index] = fmt.Sprintf("%d", index+1)
 }

 step := 15
 for step <= n {
  retVal[step-1] = "FizzBuzz"
  step += 15
 }

 step = 3
 for step <= n {
  if retVal[step-1] != "FizzBuzz" {
   retVal[step-1] = "Fizz"
  }
  step += 3
 }

 step = 5
 for step <= n {
  if retVal[step-1] != "FizzBuzz" {
   retVal[step-1] = "Buzz"
  }
  step += 5
 }
 return retVal
}
```

##### (2).对方法（1）的代码优化，直接比较值进行数组的初始化

```golang
func fizzBuzz(n int) []string {
 var retVal []string
 for index := 1; index <= n; index++ {
  if index%3 == 0 && index%5 == 0 {
   retVal = append(retVal, "FizzBuzz")
  } else if index%3 == 0 {
   retVal = append(retVal, "Fizz")
  } else if index%5 == 0 {
   retVal = append(retVal, "Buzz")
  } else {
   retVal = append(retVal, fmt.Sprintf("%d", index))
  }
 }
 return retVal
}
```

## 2.Review

* [Microservices - Not A Free Lunch!](http://highscalability.com/blog/2014/4/8/microservices-not-a-free-lunch.html)
* [The Hidden Costs of Microservices](https://www.stackbuilders.com/blog/the-hidden-costs-of-microservices/)

## 3.Tip

本周暂无

## 4.Share

* [2022 高效学习法：如何成为知识的主人？](https://time.geekbang.org/dailylesson/detail/100056967)
  * 学习的“三个一”
   * 一种思维方式——生产者思维（以输出为导向去获取输入，学习即获取输入的过程，初步实践：做笔记）
   * 一个学习方法——费曼学习法（确定学习目标，已教促学，发掘与再学习，提炼与简化）
   * 一个学习技巧——生活化联想（将技术中的原理和知识映射到生活中来）