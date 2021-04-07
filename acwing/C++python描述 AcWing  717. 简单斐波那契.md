# C++/python描述 AcWing  717. 简单斐波那契

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
以下数列 `0 1 1 2 3 5 8 13 21 ...` 被称为斐波纳契数列。

这个数列从第 33 项开始，每一项都等于前两项之和。

输入一个整数 NN，请你输出这个序列的前 NN 项。

#### 输入格式

一个整数 NN。

#### 输出格式

在一行中输出斐波那契数列的前 NN 项，数字之间用空格隔开。

#### 数据范围

0<N<460<N<46

#### 输入样例：

```
5
```

#### 输出样例：

```
0 1 1 2 3
```

## 算法实现一 C++

```cpp
#include<iostream>
using namespace std;
int main(){
    int n;
    cin >> n;
    int a = 0, b = 1;
    if(n == 1){
        cout<<"0";
        return 0;
    }
    if (n == 2){
        cout <<"0 1";
        return 0;
    }
    cout << "0 1";
    for(int i = 2; i < n; i++){
        int c = a + b;
        cout <<" "<<c;
        a = b;
        b = c;
    }
    return 0;
}
```

## 算法实现二 Python

```python
n = int(input())
tmp = [0,1]
for i in range(min(2,n)):
    print(tmp[i],end=' ')
if n >2:
    i = 2
    while i < n:
        tmp[0],tmp[1],i = tmp[1],tmp[0]+tmp[1],i+1
        print(tmp[1],end=' ')
```

