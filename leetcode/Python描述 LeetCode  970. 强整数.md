# Python描述 LeetCode  970. 强整数
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
给定两个正整数 `x` 和 `y`，如果某一整数等于 `x^i + y^j`，其中整数 `i >= 0` 且 `j >= 0`，那么我们认为该整数是一个*强整数*。

返回值小于或等于 `bound` 的所有*强整数*组成的列表。

你可以按任何顺序返回答案。在你的回答中，每个值最多出现一次。

 

**示例 1：**

```
输入：x = 2, y = 3, bound = 10
输出：[2,3,4,5,7,9,10]
解释： 
2 = 2^0 + 3^0
3 = 2^1 + 3^0
4 = 2^0 + 3^1
5 = 2^1 + 3^1
7 = 2^2 + 3^1
9 = 2^3 + 3^0
10 = 2^0 + 3^2
```

**示例 2：**

```
输入：x = 3, y = 5, bound = 15
输出：[2,4,6,8,10,14]
```

 

**提示：**

- `1 <= x <= 100`
- `1 <= y <= 100`
- `0 <= bound <= 10^6`

## 算法实现

```python
class Solution:
    def powerfulIntegers(self, x: int, y: int, bound: int) -> List[int]:
        res = []
        for i in range(20):
            for j in range(20):
                tmp = x**i + y**j
                if tmp <= bound:
                    res.append(tmp)
        res = list(set(res))
        return res
```

