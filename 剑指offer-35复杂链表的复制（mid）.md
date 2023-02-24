# 题目
请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。  

# 求解
```
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""
class Solution:
    def copyRandomList(self, head: 'Node') -> 'Node':
        if not head:
            return
        dic = {}     # 使用字典存储指针（key）和Node（value）的映射关系
        cur = head
        while cur:
            dic[cur] = Node(cur.val)        # 字典的value可以是任意格式
            cur = cur.next
        
        cur = head
        while cur:
            dic[cur].next = dic.get(cur.next)   # value部分是Node
            dic[cur].random = dic.get(cur.random)
            cur = cur.next
        return dic[head]
```

# 反思
1.使用字典存储指针（key）和Node（value）的映射关系  
2.字典的value可以是任意格式  
3.value部分是Node  
