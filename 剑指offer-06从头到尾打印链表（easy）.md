# 题目
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。  

# 求解
1.辅助栈法  
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reversePrint(self,head:ListNode):
        res = []
        while head:
            res.append(head.val)
            head = head.next
        return res[::-1]
```

2.递归法  
```
class Solution:
    def reversePrint(self, head: ListNode) -> List[int]:
        # 递归的终止条件
        if not head :
            return []
        else:
            return self.reversePrint(head.next) + [head.val]
```

# 反思
1.python没有定义链表结构，需要按照题目中给定定义进行操作：链表也可以用while循环
2.list[::-1]表示切片法倒叙，具体三个参数见https://blog.csdn.net/Cimiy_/article/details/123481624  
3.力扣中定义的类和方法名不能更改，系统判定固定  
4.python3的数据可以用冒号说明类型，如：def reversePrint(self, head: ListNode) -> List[int]（->是什么？？）  
