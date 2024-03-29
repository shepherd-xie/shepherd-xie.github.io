---
title: 833. 字符串中的查找与替换
date: 2023-08-15 11:53:50
tags:
  - 数组
  - medium
  - leetcode
categories:
  - 算法
top:
---

https://leetcode.cn/problems/find-and-replace-in-string/description/

<!-- more -->

> 你会得到一个字符串 `s` (索引从 0 开始)，你必须对它执行 `k` 个替换操作。替换操作以三个长度均为 `k` 的并行数组给出：`indices`, `sources`, `targets`。
>
> 要完成第 `i` 个替换操作:
>
> 1. 检查 **子字符串** `sources[i]` 是否出现在 **原字符串** `s` 的索引 `indices[i]` 处。
> 2. 如果没有出现， **什么也不做** 。
> 3. 如果出现，则用 `targets[i]` **替换** 该子字符串。
>
> 例如，如果 `s = "abcd"` ， `indices[i] = 0` , `sources[i] = "ab"`， `targets[i] = "eee"` ，那么替换的结果将是 `"eeecd"` 。
>
> 所有替换操作必须 **同时** 发生，这意味着替换操作不应该影响彼此的索引。测试用例保证元素间**不会重叠** 。
>
> - 例如，一个 `s = "abc"` ， `indices = [0,1]` ， `sources = ["ab"，"bc"]` 的测试用例将不会生成，因为 `"ab"` 和 `"bc"` 替换重叠。
>
> *在对 `s` 执行所有替换操作后返回 **结果字符串** 。*
>
> **子字符串** 是字符串中连续的字符序列。
>
>  
>
> **示例 1：**
>
> ![img](https://images.orkva.com/images/2023/08/15/833-ex1.png)
>
> ```
> 输入：s = "abcd", indices = [0,2], sources = ["a","cd"], targets = ["eee","ffff"]
> 输出："eeebffff"
> 解释：
> "a" 从 s 中的索引 0 开始，所以它被替换为 "eee"。
> "cd" 从 s 中的索引 2 开始，所以它被替换为 "ffff"。
> ```
>
> **示例 2：**![img](https://images.orkva.com/images/2023/08/15/833-ex2-1.png)
>
> ```
> 输入：s = "abcd", indices = [0,2], sources = ["ab","ec"], targets = ["eee","ffff"]
> 输出："eeecd"
> 解释：
> "ab" 从 s 中的索引 0 开始，所以它被替换为 "eee"。
> "ec" 没有从原始的 S 中的索引 2 开始，所以它没有被替换。
> ```
>
>  
>
> **提示：**
>
> - `1 <= s.length <= 1000`
> - `k == indices.length == sources.length == targets.length`
> - `1 <= k <= 100`
> - `0 <= indices[i] < s.length`
> - `1 <= sources[i].length, targets[i].length <= 50`
> - `s` 仅由小写英文字母组成
> - `sources[i]` 和 `targets[i]` 仅由小写英文字母组成

如果要想做到前一个替换之后不影响之后的替换，那么就从后向前进行替换，这样后面已经替换的字符串长度就不会影响前面未替换的字符位置。

由于 indices 实际是未排序的，所以我们要先将他排序，同时需要记录 indices 中未排序前的索引。由于 `1 <= s.length <= 1000` ，所以我们可以将 indices 中的数 `x10000` ，此时我们可以将这一个数看做两部分，10000 以上的部分是 indices 中的值，10000 以下的部分是 indices 的索引。

```java
class Solution {
    public String findReplaceString(String s, int[] indices, String[] sources, String[] targets) {
        StringBuilder sb = new StringBuilder(s);
        for (int i = 0; i < indices.length; i++) {
            indices[i] = indices[i] * 10000 + i;
        }
        Arrays.sort(indices);
        for (int i = indices.length - 1; i >= 0; i --) {
            int point = indices[i] % 10000;
            String r = sources[point];
            int left = indices[i] / 10000;
            int right = indices[i] / 10000 + r.length();
            if (right <= sb.length()) {
                String sub = sb.substring(left, right);
                if (sub.equals(r)) {
                    sb.replace(left, right, targets[point]);
                }
            }
        }
        return sb.toString();
    }
}
```



