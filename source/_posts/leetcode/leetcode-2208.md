---
title: 2208. 将数组和减半的最少操作次数
date: 2023-07-25 10:49:35
tags:
  - 贪心
  - 优先队列
  - medium
  - leetcode
categories:
  - 算法
top:
---

https://leetcode.cn/problems/minimum-operations-to-halve-array-sum/description/

<!-- more -->

> 给你一个正整数数组 `nums` 。每一次操作中，你可以从 `nums` 中选择 **任意** 一个数并将它减小到 **恰好** 一半。（注意，在后续操作中你可以对减半过的数继续执行操作）
>
> 请你返回将 `nums` 数组和 **至少** 减少一半的 **最少** 操作数。
>
>  
>
> **示例 1：**
>
> ```
> 输入：nums = [5,19,8,1]
> 输出：3
> 解释：初始 nums 的和为 5 + 19 + 8 + 1 = 33 。
> 以下是将数组和减少至少一半的一种方法：
> 选择数字 19 并减小为 9.5 。
> 选择数字 9.5 并减小为 4.75 。
> 选择数字 8 并减小为 4 。
> 最终数组为 [5, 4.75, 4, 1] ，和为 5 + 4.75 + 4 + 1 = 14.75 。
> nums 的和减小了 33 - 14.75 = 18.25 ，减小的部分超过了初始数组和的一半，18.25 >= 33/2 = 16.5 。
> 我们需要 3 个操作实现题目要求，所以返回 3 。
> 可以证明，无法通过少于 3 个操作使数组和减少至少一半。
> ```
>
> **示例 2：**
>
> ```
> 输入：nums = [3,8,20]
> 输出：3
> 解释：初始 nums 的和为 3 + 8 + 20 = 31 。
> 以下是将数组和减少至少一半的一种方法：
> 选择数字 20 并减小为 10 。
> 选择数字 10 并减小为 5 。
> 选择数字 3 并减小为 1.5 。
> 最终数组为 [1.5, 8, 5] ，和为 1.5 + 8 + 5 = 14.5 。
> nums 的和减小了 31 - 14.5 = 16.5 ，减小的部分超过了初始数组和的一半， 16.5 >= 31/2 = 16.5 。
> 我们需要 3 个操作实现题目要求，所以返回 3 。
> 可以证明，无法通过少于 3 个操作使数组和减少至少一半。
> ```
>
>  
>
> **提示：**
>
> - `1 <= nums.length <= 105`
> - `1 <= nums[i] <= 107`

显然操作次数最小化的做法为：每次操作都选择当前数组的最大值进行减半操作。

那么问题就在于如何操作这个优先队列。

1. 去除最大元素 x
2. 令 xNum += x
3. 将 x / 2 放回优先队列
4. 直到 xNum > num

```java
class Solution {
    public int halveArray(int[] nums) {
        double sum = 0;
        // 默认按照字典序，即由小到大排列，这里传递反转排序
        PriorityQueue<Double> queue = new PriorityQueue<>(Comparator.reverseOrder());
        for (int num : nums) {
            queue.offer((double) num);
            sum += num;
        }
        double xSum = 0;
        int res = 0;
        while (xSum < sum) {
            Double num = queue.poll();
            xSum += num;
            queue.offer(num / 2);
            res ++;
        }
        return res;
    }
}
```

