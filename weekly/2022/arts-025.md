## 1.Algorithm

[57]&nbsp;&nbsp;[Insert Interval](https://leetcode.com/problems/insert-interval/description/)

**Medium** &nbsp;&nbsp; **array** &nbsp;&nbsp;

You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return intervals after the insertion.

Example1:

```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```

Example2:

```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

Constraints:

```
0 <= intervals.length <= 104
intervals[i].length == 2
0 <= starti <= endi <= 105
intervals is sorted by starti in ascending order.
newInterval.length == 2
0 <= start <= end <= 105
```

**解答**
本题的关键点在于区间的ovlap处理，不断更新start和end值

##### (1).常规解法, 1 层循环，时间复杂度 O(n)

```java
public int[][] insert(int[][] intervals, int[] newInterval) {
    List<int[]> retVals = new ArrayList();
    int i = 0;
    while (i < intervals.length && intervals[i][1] < newInterval[0]) {
        retVals.add(intervals[i]);
        i++;
    }
    while (i < intervals.length && intervals[i][0] <= newInterval[1]) {
        newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
        newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
        i++;
    }
    retVals.add(newInterval);
    while (i < intervals.length) {
        retVals.add(intervals[i]);
        i++;
    }
    return retVals.toArray(new int[0][]);
}
```

```golang
func insert(intervals [][]int, newInterval []int) [][]int {
	retVal, i := [][]int{}, 0
	start, end := newInterval[0], newInterval[1]
	for ; i < len(intervals) && intervals[i][1] < start; i++ {
		retVal = append(retVal, intervals[i])
	}

	for ; i < len(intervals) && intervals[i][0] <= end; i++ {
		start = Min(intervals[i][0], start)
		end = Max(intervals[i][1], end)
	}
	retVal = append(retVal, []int{start, end})

	for ; i < len(intervals); i++ {
		retVal = append(retVal, intervals[i])
	}
	return retVal
}

func Max(x, y int) int {
	if x < y {
		return y
	}
	return x
}

func Min(x, y int) int {
	if x < y {
		return x
	}
	return y
}
```

## 2.Review
* [Case Styles: Camel, Pascal, Snake, and Kebab Case](https://betterprogramming.pub/string-case-styles-camel-pascal-snake-and-kebab-case-981407998841)
* [The Forty-Year Programmer](https://codefol.io/posts/the-forty-year-programmer/)
* [Becoming a Full-Time Creator as a Software Engineer: Controversial Advice](https://blog.pragmaticengineer.com/how-to-become-a-full-time-creator/)

## 3.Tip
最近在负责一个报表项目的研发实施，前端涉及多端的展示，而之前有2个端是是两拨人独立开发的，没有考虑组件的公用等；而本期里大部分组件要做到多端融合，因此研发人员在评估这部分需求功能时，对工作量的考虑严重低估，导致整个项目人力非常吃紧。而历史包袱，技术债这个问题，是我们经常需要面对的问题，而如何去平衡新功能需求和历史包袱问题，是一个非常难的问题，想去对历史问题进行重写，时间可能不够，如果去重构，在短时间内完成了功能开发，回归线上功能又是一个大难题。缺乏顶层设计，欠考虑的设计，脱离代码层面的设计是一个非常不可取的方案，迫于研发交付压力，只是临时完成了功能开发，而后续要付出更多的人力去解决遗留问题。

## 4.Share
* [阿里低代码引擎和生态建设实战及思考](https://mp.weixin.qq.com/s/MI6MrUKKydtnSdO4xq6jwA)
* [前端智能化—思维转变之路](https://juejin.cn/post/6844904104448393223)