---
title: 380. O(1) 时间插入、删除和获取随机元素
date: 2023-06-29 14:42:45
tags:
  - 数组
  - 哈希表
  - 设计
  - medium
  - leetcode
categories:
  - 算法
top:
---

> [380. O(1) 时间插入、删除和获取随机元素](https://leetcode.cn/problems/insert-delete-getrandom-o1/description/)
>
> 
>
> 实现`RandomizedSet` 类：
>
> - `RandomizedSet()` 初始化 `RandomizedSet` 对象
> - `bool insert(int val)` 当元素 `val` 不存在时，向集合中插入该项，并返回 `true` ；否则，返回 `false` 。
> - `bool remove(int val)` 当元素 `val` 存在时，从集合中移除该项，并返回 `true` ；否则，返回 `false` 。
> - `int getRandom()` 随机返回现有集合中的一项（测试用例保证调用此方法时集合中至少存在一个元素）。每个元素应该有 **相同的概率** 被返回。
>
> 你必须实现类的所有函数，并满足每个函数的 **平均** 时间复杂度为 `O(1)` 。
>
>  
>
> **示例：**
>
> ```
> 输入
> ["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
> [[], [1], [2], [2], [], [1], [2], []]
> 输出
> [null, true, false, true, 2, true, false, 2]
> 
> 解释
> RandomizedSet randomizedSet = new RandomizedSet();
> randomizedSet.insert(1); // 向集合中插入 1 。返回 true 表示 1 被成功地插入。
> randomizedSet.remove(2); // 返回 false ，表示集合中不存在 2 。
> randomizedSet.insert(2); // 向集合中插入 2 。返回 true 。集合现在包含 [1,2] 。
> randomizedSet.getRandom(); // getRandom 应随机返回 1 或 2 。
> randomizedSet.remove(1); // 从集合中移除 1 ，返回 true 。集合现在包含 [2] 。
> randomizedSet.insert(2); // 2 已在集合中，所以返回 false 。
> randomizedSet.getRandom(); // 由于 2 是集合中唯一的数字，getRandom 总是返回 2 。
> ```
>
>  
>
> **提示：**
>
> - `-231 <= val <= 231 - 1`
> - 最多调用 `insert`、`remove` 和 `getRandom` 函数 `2 * ``105` 次
> - 在调用 `getRandom` 方法时，数据结构中 **至少存在一个** 元素。

既然题目中指定了时间复杂度为 O(1) 那么可供选择的数据结构也就只剩下了哈希表，但是题目又要求 **相同的概率随机返回** 表明这个存储数据必须要有序，那么可供选择的就只剩下 **可变数组 + 哈希表** ，可变数组用于提供随机访问的概率稳定性、哈希表用来存储对象及对象在数组中的位置。

```java
class RandomizedSet {

    List<Integer> list = new ArrayList<>();
    Map<Integer, Integer> hashMap = new HashMap<>();
    Random random = new Random();

    public RandomizedSet() {

    }

    public boolean insert(int val) {
        if (hashMap.containsKey(val)) {
            return false;
        }
        hashMap.put(val, list.size());
        list.add(val);
        return true;
    }

    public boolean remove(int val) {
        if (!hashMap.containsKey(val)) {
            return false;
        }
        Integer idx = hashMap.get(val);
        Integer last = list.get(list.size() - 1);
        list.set(idx, last);
        list.remove(list.size() - 1);
        hashMap.put(last, idx);
        hashMap.remove(val);
        return true;
    }

    public int getRandom() {
        return list.get(random.nextInt(list.size()));
    }
}
```

