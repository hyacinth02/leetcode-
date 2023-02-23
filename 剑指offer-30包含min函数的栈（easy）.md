# 题目
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，
调用 min、push 及 pop 的时间复杂度都是 O(1)。

# 求解
重点思路是寻找min的时间复杂度为O（1），说明最小值一直存储着，而非当时寻找；因此建立一个辅助站存储当前数量数据时栈中最小值；  
易错点：超限问题，思考为什么直接添加（没有float（'inf'））不行
```
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.A = []
        self.help = [float('inf')]


    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        self.A.append(x)
        self.help.append(min(x,self.help[-1]))



    def pop(self):
        """
        :rtype: None
        """
        self.A.pop()
        self.help.pop()


    def top(self):
        """
        :rtype: int
        """
        return self.A[-1]


    def min(self):
        """
        :rtype: int
        """
        return self.help[-1]
```

# 反思
1.定义最大值：float('inf')，最小值：float('-inf')  
2.碰到一个很奇怪的问题：
```
if not self.help:
    self.help.append(x)
else:
    if x<self.help[-1]:   # 新加入的数比当前最小数还小
        self.help.append(x)
    else:
        self.help.append(self.help[-1])
```
与下面情况不同（下面不通过）
```
if not self.help:   # 辅助站help为空
    self.help.append(x)
if self.help   # 辅助站help非空
    if x<self.help[-1]:   # 新加入的数比当前最小数还小
        self.help.append(x)
    else:
        self.help.append(self.help[-1])
```
3.通过“if list_i”判断列表list_i是否为空：非0、非null为true，0或者null为false  
