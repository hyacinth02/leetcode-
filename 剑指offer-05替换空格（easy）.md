# 题目
请实现一个函数，把字符串 s 中的每个空格替换成"%20"。  

# 求解
```
# class Solution:
#     def replaceSpace(self, s: str) -> str:
#         return s.replace(" ","%20")

class Solution:
    def replaceSpace(self, s: str) -> str:
        s = list(s)
        for i,string in enumerate(s):
            if string == " ":
                s[i] = "%20"
        return ''.join(s)
```
# 反思
1.''.join(list)将list中的连接成字符串  
2.字符串修改，python中可用replace，或者转成list，或者for c in str但需分类复制成list  
