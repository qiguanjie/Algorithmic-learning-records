# C++/Python描述 LeetCode 92. 反转链表 II

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

给你单链表的头节点 `head` 和两个整数 `left` 和 `right` ，其中 `left <= right` 。请你反转从位置 `left` 到位置 `right` 的链表节点，返回 **反转后的链表** 。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2021/02/19/rev2ex2.jpg)

```
输入：head = [1,2,3,4,5], left = 2, right = 4
输出：[1,4,3,2,5]
```

**示例 2：**

```
输入：head = [5], left = 1, right = 1
输出：[5]
```

 

**提示：**

- 链表中节点数目为 `n`
- `1 <= n <= 500`
- `-500 <= Node.val <= 500`
- `1 <= left <= right <= n`

 

**进阶：** 你可以使用一趟扫描完成反转吗？

## 解题思路

使用一个指针`pre`指向left的前一个位置，然后使用cur指针依次指向要反转的结点的前一个位置，然后将cur->next插入到pre的下一个结点。这里要注意插入时候的顺序，如果不理解的话，建议手画一下前几轮的插入过程，便于理解。

## 算法实现一 C++

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        // 创建虚拟头结点，使得当left=1时，操作统一
        ListNode *headnode =new ListNode(-1);
        headnode->next = head;
        ListNode *pre = headnode;
        // pre 指向left位置的前一个结点
        for(int i = 0 ; i < left-1; i++)
            pre = pre->next;
        ListNode *cur = pre->next;
        for(int i = 0; i < right - left; i++){
            ListNode *nextnode = cur->next;
            // 将nextnode结点插入到pre后一个结点
            // 这里的连接顺序很关键，如果看不懂的话建议用笔画一下前两次的插入的情况，进行理解
            cur->next = nextnode->next;
            nextnode->next = pre->next;
            pre->next = nextnode;
        }
        return headnode->next;
    }
};
```



## 算法实现二 Python

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: ListNode, left: int, right: int) -> ListNode:
        # 设虚拟头结点
        headnode = ListNode(-1)
        headnode.next = head
        # pre 走到 left的前一个结点
        pre = headnode
        for i in range(left - 1):
            pre = pre.next
        # 使用cur进行右移,进行在left处进行头插
        cur = pre.next
        for i in range(right - left):
            # 将nextnode结点插入到pre后一个结点
            # 这里的连接顺序很关键，如果看不懂的话建议用笔画一下前两次的插入的情况，进行理解
            nextnode = cur.next
            cur.next = nextnode.next
            nextnode.next = pre.next
            pre.next = nextnode
        return headnode.next
```

