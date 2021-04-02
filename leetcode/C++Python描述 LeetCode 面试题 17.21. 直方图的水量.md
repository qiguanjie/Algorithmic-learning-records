# C++/Python描述 LeetCode 面试题 17.21. 直方图的水量

>>&emsp; 大家好，我叫亓官劼（qí guān jié ），在GitHub & CSDN中记录学习的点滴历程，时光荏苒，未来可期，加油~博主目前仅在GitHub & CSDN中写博客，唯一博客更新的地址为：[亓官劼的博客](https://blog.csdn.net/qq_43422111)  ，近期将逐渐同步刷题相关记录到GitHub：[Algorithmic-learning-records](https://github.com/qiguanjie/Algorithmic-learning-records)，大多是本人的刷题记录，如果转载请附上原文地址，谢谢。
>
>----
>
>由于学习工作的需要，算法刷题将会逐渐由C++向Python3过度，正在过度中，如实现的不太优美，请见谅。
>
>> 本文原创为亓官劼，请大家支持原创，部分平台一直在恶意盗取博主的文章！！！ 
>> 若需联系博主，可以联系本人微信：qiguanjie2015
>

---

给定一个直方图(也称柱状图)，假设有人从上面源源不断地倒水，最后直方图能存多少水量?直方图的宽度为 1。

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rainwatertrap.png)

上面是由数组 [0,1,0,2,1,0,1,3,2,1,2,1] 表示的直方图，在这种情况下，可以接 6 个单位的水（蓝色部分表示水）。 **感谢 Marcos** 贡献此图。

**示例:**

```
输入: [0,1,0,2,1,0,1,3,2,1,2,1]
输出: 6
```

## 解题思路

这题和接雨水是一样的，有兴趣的话可以参考去年的文章：[LeetCode 每日一题 42. 接雨水 详细多种题解 C++描述](https://blog.csdn.net/qiguanjiezl/article/details/105315208)

这里我们求出左面的最大高度，右面的最大高度，那么当前位置可以存放的水就是min(左面最大高度，右面最大高度)-height[i]。

## 算法实现一 Python

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        ans = 0
        lmax = [0 for i in range(len(height))]
        rmax = [0 for j in range(len(height))]
        # 求右面最高点
        for i in range(1,len(height)):
            lmax[i] = max(lmax[i-1],height[i-1])
        # 求左面最高点
        for i in range(len(height)-2,-1,-1):
            rmax[i] = max(rmax[i+1],height[i+1])
        for i in range(0,len(height)):
            tmp = min(rmax[i],lmax[i])-height[i]
            ans += tmp if tmp > 0 else 0
        return ans
```

## 算法实现二 C++

```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int len = height.size();
        int ans = 0;
        vector<int> lmax(len),rmax(len);
        for(int i = 1 ; i < len ; i++) lmax[i] = max(lmax[i-1],height[i-1]);
        for(int i = len - 2 ; i >= 0; i--) rmax[i] = max(rmax[i+1],height[i+1]);
        for(int i = 0; i < len ; i++){
            int tmp = min(lmax[i],rmax[i])-height[i];
            ans += tmp > 0 ? tmp : 0;
        }
        return ans;
    }
};
```

