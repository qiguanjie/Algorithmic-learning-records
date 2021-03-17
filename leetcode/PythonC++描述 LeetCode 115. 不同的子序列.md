# Python/C++描述 LeetCode 115. 不同的子序列

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

给定一个字符串 `s` 和一个字符串 `t` ，计算在 `s` 的子序列中 `t` 出现的个数。

字符串的一个 **子序列** 是指，通过删除一些（也可以不删除）字符且不干扰剩余字符相对位置所组成的新字符串。（例如，`"ACE"` 是 `"ABCDE"` 的一个子序列，而 `"AEC"` 不是）

题目数据保证答案符合 32 位带符号整数范围。

 

**示例 1：**

```
输入：s = "rabbbit", t = "rabbit"
输出：3
解释：
如下图所示, 有 3 种可以从 s 中得到 "rabbit" 的方案。
(上箭头符号 ^ 表示选取的字母)
rabbbit
^^^^ ^^
rabbbit
^^ ^^^^
rabbbit
^^^ ^^^
```

**示例 2：**

```
输入：s = "babgbag", t = "bag"
输出：5
解释：
如下图所示, 有 5 种可以从 s 中得到 "bag" 的方案。 
(上箭头符号 ^ 表示选取的字母)
babgbag
^^ ^
babgbag
^^    ^
babgbag
^    ^^
babgbag
  ^  ^^
babgbag
    ^^^
```

 

**提示：**

- `0 <= s.length, t.length <= 1000`
- `s` 和 `t` 由英文字母组成

## 解题思路

DP思想。

状态表示：`dp[i][j]`表示`s[i:]中t[j:]`的子串数量。

初始化：当`i == s.length()`时，`s[i:]`为空，则子串数量一定为0 ；当`j == t.length()`时，`t[j:]`是空，则一定有一个是`s[i:]`的子串，子串数量为1。这里需要主要的是当`s[i:]和t[j:]`同时为空时，空是空的子串，数量为1.

状态转移：当`s[i] == s[j]`是，`dp[i][j] = dp[i+1][j+1] + dp[i+1][j]`；当`s[i] != s[j]`时，`dp[i][j] = dp[i+1][j]`

## 算法实现一 C++

```cpp
class Solution {
public:
    int numDistinct(string s, string t) {
        int len1 = s.length(),len2 = t.length();
        if( len1 < len2 )
            return 0;
        vector<vector<long long int>> dp(len1+1,vector<long long int>(len2+1));
        for(int i = 0; i <= len1 ; i++){
            dp[i][len2] = 1;
        }
        for(int i = len1-1 ; i >= 0 ; i--){
            for(int j = len2-1 ; j >= 0; j--){
                if (s[i] == t[j]){
                    dp[i][j] = dp[i+1][j+1] + dp[i+1][j];
                }else{
                    dp[i][j] = dp[i+1][j];
                }
            }
        }
        return dp[0][0];
    }
};
```



## 算法实现二 Python

```python
class Solution:
    def numDistinct(self, s: str, t: str) -> int:
        len1 = len(s)
        len2 = len(t)
        if len1 < len2 :
            return 0
        dp = [[0 for i in range(len2)] + [1,] for _ in range(len1+1)]
        for i in range(len1-1,-1,-1):
            for j in range(len2-1,-1,-1):
                if s[i] == t[j]:
                    dp[i][j] = dp[i+1][j+1] + dp[i+1][j]
                else:
                    dp[i][j] = dp[i+1][j]
        return dp[0][0]
```

