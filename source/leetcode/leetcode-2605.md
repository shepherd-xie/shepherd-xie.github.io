---
title: 2605. 从两个数字数组里生成最小数字
date: 2023-09-05 16:55:46
tags:
  - 数组
  - medium
  - leetcode
categories:
  - 算法
top:
---

https://leetcode.cn/problems/form-smallest-number-from-two-digit-arrays/description/

<!-- more -->

> 给你两个只包含 1 到 9 之间数字的数组 `nums1` 和 `nums2` ，每个数组中的元素 **互不相同** ，请你返回 **最小** 的数字，两个数组都 **至少** 包含这个数字的某个数位。
>
>  
>
> **示例 1：**
>
>  ```
>输入：nums1 = [4,1,3], nums2 = [5,7]
> 输出：15
>解释：数字 15 的数位 1 在 nums1 中出现，数位 5 在 nums2 中出现。15 是我们能得到的最小数字。
> ```
> 
> **示例 2：**
> 
>```
> 输入：nums1 = [3,5,2,6], nums2 = [3,1,7]
>输出：3
> 解释：数字 3 的数位 3 在两个数组中都出现了。
> ```
> 
>  
>
>  **提示：**
>
> - `1 <= nums1.length, nums2.length <= 9`
>- `1 <= nums1[i], nums2[i] <= 9`
> - 每个数组中，元素 **互不相同** 。

由题目可以知道，最小的自然是两个数组都包含的数字，其次是两个数组中最小的数组成的两位数。由于数组中的数字范围是 `[1,9]` 所以我们可以使用哈希表来判断这个数组是否出现过。

```java
class Solution {
    public int minNumber(int[] nums1, int[] nums2) {
        int[] hash = new int[10];
        int min1 = 10;
        for (int num : nums1) {
            hash[num] += 1;
            min1 = Math.min(min1, num);
        }
        int min2 = 10;
        for (int num : nums2) {
            hash[num] += 1;
            min2 = Math.min(min2, num);
        }
        // 不包含 0 所以从 1 开始遍历
        for (int i = 1; i < hash.length; i ++) {
            if (hash[i] == 2) {
                return i;
            }
        }
        return min1 > min2 ? min2 * 10 + min1 : min1 * 10 + min2;
    }
}
```

