# 题目
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。
(若队列中没有元素，deleteHead 操作返回 -1 )

# 求解  
'''  
class CQueue():
    def __init__(self):
        self.A, self.B = [],[]
    
    def appendTail(self,num):
        self.A.append(num)
    
    def deleteHead(self):
        if self.B:
            return self.B.pop()
        if not self.A:
            return -1
        while self.A:
            self.B.append(self.A.pop())
        return self.B.pop()
'''

# 反思
1.list.pop()可弹出末尾数字，并从list中删除  
2.if list可以判断空值，还可作为循环体使用while循环  
