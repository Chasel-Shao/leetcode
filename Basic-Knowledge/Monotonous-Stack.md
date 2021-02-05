## Monotonous stack

----

[https://muyids.github.io/simple-algorithm/chapter/%E5%8D%95%E8%B0%83%E6%A0%88.html](https://muyids.github.io/simple-algorithm/chapter/单调栈.html)

# 单调栈（单调队列）

△ 单调递减栈：`A[i] >= A[stack.top()]`

▽ 单调递增栈：`A[i] <= A[stack.top()]`

单调栈是一种维护栈内元素递增(或递减)的栈。

单调栈分为单调递增栈和单调递减栈，单调递增栈即栈内元素保持单调递增的栈，同理单调递减栈即栈内元素保持单调递减的栈。

单调栈里可以保存元素的值或下标

某些场景下，我们需要维护栈底，这时候栈的数据结构是不满足要求的，可能需要借助**队列**或**双端队列**实现（比如求滑动窗口最大值），即单调队列

## 应用场景

- 可以在O(N)的时间复杂度，找出每个数**左右两边第一个大于或小于它的解**
- 单调递增栈用于查找两边第一个小于当前元素的值，单调递减栈用于查找两边第一个大于当前元素的值
- 一般数组中的单调性问题，题目中隐含第一个或离此元素最近的大于或小于元素的值，这类问题都可以考虑下，用单调栈是否可以求解

## 动画演示

数列`7 4 9 5 3 2`构建单调递减栈

![单调栈动画演示](https://muyids.oss-cn-beijing.aliyuncs.com/monotone-stack.gif)

## 代码模板

```cpp
stack<int> stk;
for (int i = 0; i < A.size(); i++) {
    while (stk.size() && A[i] <= A[stk.top()]) { // 单调递增栈（
        // 单调递减栈A[i] >= A[stk.top()]
        stk.pop();
    }
    stk.push(i);
}
​```

## 板子题

给定一个长度为N的正整数数组，输出每个数左右两边第一个比它小的数，如果不存在则输出-1。

```cpp
输入: [3, 4, 2, 7, 5]

输出：
左边：[-1, 3, -1, 2, 2]
右边：[2, 2, -1, 5, -1]
​```

### 解题思路

查找左右两边第一个更小的元素，使用单调递增栈

- 入栈时，**当前元素左边的第一个更小的元素**是**当前栈顶元素**
- 出栈时，**栈顶右边第一个更小的元素**是**即将入栈的当前元素**

### 代码实现

```cpp
void sumSubarrayMins(vector<int> &A) {
    int n = A.size();
    vector<int> lmin(n, -1);
    vector<int> rmin(n, -1);
    stack<int> stk; // 单调递增栈
    for (int i = 0; i < A.size(); i++) {
        while (stk.size() && A[i] <= A[stk.top()]) {
            rmin[stk.top()] = A[i];
            stk.pop();
            if (stk.size()) lmin[i] = A[stk.top()];
        }
        stk.push(i);
    }
}
​```

时间复杂度O(N)，空间复杂度O(N)

## 题目

- [LeetCode 239. Sliding Window Maximum (hard)](https://github.com/muyids/leetcode/blob/master/algorithms/201-300/239.sliding-window-maximum.md)

- [LeetCode 42. Trapping Rain Water (hard)](https://github.com/muyids/leetcode/blob/master/algorithms/1-100/42.trapping-rain-water.md)

- [LeetCode 84. Largest Rectangle in Histogram (hard)](https://github.com/muyids/leetcode/blob/master/algorithms/1-100/84.largest-rectangle-in-histogram.md)

- [LeetCode 85. Maximal Rectangle (hard)](https://github.com/muyids/leetcode/blob/master/algorithms/1-100/85.maximal-rectangle.md)

- [LeetCode 402. Remove K Digits (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/401-500/402.remove-k-digits.md)

- [LeetCode 503. Next Greater Element II (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/501-600/503.next-greater-element-ii.md)

- [LeetCode 768. Max Chunks To Make Sorted II (hard)](https://github.com/muyids/leetcode/blob/master/algorithms/701-800/768.max-chunks-to-make-sorted-ii.md)

- [LeetCode 739. Daily Temperatures (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/701-800/739.daily-temperatures.md)

- [LeetCode 901. Online Stock Span (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/901-1000/901.online-stock-span.md)

- [LeetCode 1019. Next Greater Node In Linked List (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/1001-1100/1019.next-greater-node-in-linked-list.md)

- [LeetCode 907. Sum of Subarray Minimums (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/901-1000/907.sum-of-subarray-minimums.md)

## 全局单调栈

上面我们遇到的单调栈问题，都是维护的**连续性的局部子序列**的单调性，还有一类问题，需要求解全局性的单调性序列，

- [LeetCode 962. Maximum Width Ramp (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/901-1000/962.maximum-width-ramp.md)

- [LeetCode 1124. Longest Well-Performing Interval (medium)](https://github.com/muyids/leetcode/blob/master/algorithms/1101-1200/1124.longest-well-performing-interval.md)


