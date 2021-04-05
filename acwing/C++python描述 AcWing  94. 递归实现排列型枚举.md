# C++/python描述 AcWing  94. 递归实现排列型枚举

把 1∼n 这 n 个整数排成一行后随机打乱顺序，输出所有可能的次序。

#### 输入格式

一个整数 n。

#### 输出格式

按照从小到大的顺序输出所有方案，每行 1 个。

首先，同一行相邻两个数用一个空格隔开。

其次，对于两个不同的行，对应下标的数一一比较，字典序较小的排在前面。

#### 数据范围

1≤n≤9

#### 输入样例：

```
3
```

#### 输出样例：

```
1 2 3
1 3 2
2 1 3
2 3 1
3 1 2
3 2 1
```

## 算法实现一 	C++

```cpp
#include<iostream>
#include<algorithm>
using namespace std;
int main(){
    int n,res[10] = {0};
    cin >> n ;
    for(int i = 0 ; i < n; i++) res[i] = i+1;
    do{
        for(int i = 0 ; i < n ;i++)
            cout<<res[i] <<" ";
        cout<<endl;
    }while(next_permutation(res,res+n));
    return 0;
}
```

## 算法实现二 C++

```cpp
#include<iostream>
#include<algorithm>
using namespace std;
int main(){
    int n,res[10] = {0},m=1;
    cin >> n ;
    for(int i = 0; i < n; i++) res[i] = i+1;
    for(int i = 1; i <= n; i++) m *= i;
    for(int i = 0 ; i < n ;i++)
            cout<<res[i] <<" ";
        cout<<endl;
    m--;
    while(m--){
        int i = n-1;
        while(i && res[i] < res[i-1]) i--;
        int j = i;
        while(j + 1 < n && res[j+1] > res[i-1]) j++;
        swap(res[i-1],res[j]);
        reverse(res+i,res+n);
        for(int i = 0 ; i < n ;i++)
            cout<<res[i] <<" ";
        cout<<endl;
    }
    return 0;
}
```

## 算法实现三 Python

```python
from itertools import permutations
n = int(input())
res = [i+1 for i in range(n)]
for item in permutations(res):
    for d in item:
        print(d,end=' ')
    print('')
```

## 算法实现四 Python

```python
from itertools import permutations
n = int(input())
res = [i+1 for i in range(n)]
m = 1
for i in range(n):
    m *= (i+1)
for item in res:
    print(item,end=' ')
print(' ')
m -= 1
while m:
    i = n - 1
    while n > 0 and res[i] < res[i-1]:
        i -= 1
    j = i
    while j+1 < n and res[i-1] < res[j+1]:
        j += 1
    res[i-1],res[j] = res[j],res[i-1]
    res[i:] = reversed(res[i:])
    for item in res:
        print(item,end=' ')
    print('')
    m -= 1
```

