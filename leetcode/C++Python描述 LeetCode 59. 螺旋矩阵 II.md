# C++/Python描述 LeetCode 59. 螺旋矩阵 II

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




给你一个正整数 `n` ，生成一个包含 `1` 到 `n2` 所有元素，且元素按顺时针顺序螺旋排列的 `n x n` 正方形矩阵 `matrix` 。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/spiraln.jpg)

```
输入：n = 3
输出：[[1,2,3],[8,9,4],[7,6,5]]
```

**示例 2：**

```
输入：n = 1
输出：[[1]]
```

 

**提示：**

- `1 <= n <= 20`

## 解题思路

模拟法，设置方向变量，每次走到头或者已访问过的时候，换下一个方向。将1到n*n放入到所有的格子中即可。

## 算法实现一 C++

```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n,vector<int>(n));
        int dx[] = {1,0,-1,0};
        int dy[] = {0,1,0,-1};
        int x = 0, y = 0, d = 0, end = n*n;
        for(int i = 1; i <= end; i++){
            res[y][x] = i;
            int a = x + dx[d], b = y + dy[d];
            if(a >= n || a < 0 || b >= n || b < 0 || res[b][a]){
                d = (d+1)%4;
                a = x + dx[d], b = y + dy[d];
            }
            x = a, y = b;
        }
        return res;
    }
};
```

## 算法实现二 Python

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        # 右下左上
        dx = [1,0,-1,0]
        dy = [0,1,0,-1]
        res = [[0 for i in range(n)] for j in range(n)]
        y = 0
        x = 0
        d = 0
        for i in range(1,n*n+1):
            res[y][x] = i
            nx = x + dx[d]
            ny = y + dy[d]
            if nx < 0 or nx >= n or ny < 0 or ny >= n or res[ny][nx]:
                d = (d+1)%4
                nx = x + dx[d]
                ny = y + dy[d]
            x = nx
            y = ny
        return res
```

  