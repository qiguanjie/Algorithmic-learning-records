# C++/Python描述 AcWing 92. 递归实现指数型枚举

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


从 1∼n 这 nn 个整数中随机选取任意多个，输出所有可能的选择方案。

#### 输入格式

输入一个整数 nn。

#### 输出格式

每行输出一种方案。

同一行内的数必须升序排列，相邻两个数用恰好 11 个空格隔开。

对于没有选任何数的方案，输出空行。

本题有自定义校验器（SPJ），各行（不同方案）之间的顺序任意。

#### 数据范围

1≤n≤15

#### 输入样例：

```
3
```

#### 输出样例：

```
3
2
2 3
1
1 3
1 2
1 2 3
```

## 解题思路

采用dfs递归搜索+回溯即可搜索出所有的方案，如果我们对每一个数字，先选择不选，后选择选，则可以达到升序。

## 算法实现一 C++

```cpp
#include<iostream>
using namespace std;
const int N = 15;
int s[N],n;
void dfs(int u){
    if(u == n){
        for(int i = 0; i < n ; i++)
            if(s[i] == 1)
                cout << i+1 <<" ";
        cout << endl;
        return ;
    }
    s[u] = 2;
    dfs(u+1);
    s[u] = 1;
    dfs(u+1);
    s[u] = 0;
}
int main(){
    cin >> n;
    dfs(0);
    return 0;
}
```



## 算法实现二 python

```python
def dfs(u):
    global n
    global s
    if u == n:
        for i in range(n):
            if s[i] == 1:
                print(i+1,end=' ')
        print('')
        return 
    
    s[u] = 2
    dfs(u+1)
    s[u] = 1
    dfs(u+1)
    s[u] = 0
n = int(input())
s = [0 for i in range(n)]
dfs(0)
```

