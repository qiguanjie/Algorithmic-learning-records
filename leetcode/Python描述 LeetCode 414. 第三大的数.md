#  Python描述 LeetCode 414. 第三大的数
>>&emsp; 大家好，我叫亓官劼（qí guān jié ），在GitHub & CSDN中记录学习的点滴历程，时光荏苒，未来可期，加油~博主目前仅在GitHub & CSDN中写博客，唯一博客更新的地址为：[亓官劼的博客](https://blog.csdn.net/qq_43422111)  ，近期将逐渐同步刷题相关记录到GitHub：[Algorithmic-learning-records](https://github.com/qiguanjie/Algorithmic-learning-records)，大多是本人的刷题记录，如果转载请附上原文地址，谢谢。
>
>----
>
>由于学习工作的需要，算法刷题将会逐渐由C++向Python3过度，正在过度中，如实现的不太优美，请见谅。
>
>> 本文原创为亓官劼，请大家支持原创，部分平台一直在恶意盗取博主的文章！！！ 
>> 若需联系博主，可以联系本人微信：qiguanjie2015
>> 

---


给你一个非空数组，返回此数组中 **第三大的数** 。如果不存在，则返回数组中最大的数。

 

**示例 1：**

```
输入：[3, 2, 1]
输出：1
解释：第三大的数是 1 。
```

**示例 2：**

```
输入：[1, 2]
输出：2
解释：第三大的数不存在, 所以返回最大的数 2 。
```

**示例 3：**

```
输入：[2, 2, 3, 1]
输出：1
解释：注意，要求返回第三大的数，是指在所有不同数字中排第三大的数。
此例中存在两个值为 2 的数，它们都排第二。在所有不同数字中排第三大的数为 1 。
```

 

**提示：**

- `1 <= nums.length <= 104`
- `-231 <= nums[i] <= 231 - 1`

 

**进阶：**你能设计一个时间复杂度 `O(n)` 的解决方案吗？

## 算法实现

```python
class Solution:
    def thirdMax(self, nums: List[int]) -> int:
        nums = sorted(list(set(nums)))
        if len(nums) < 3:
            return nums[-1]
        else:
            return nums[-3]
```

 