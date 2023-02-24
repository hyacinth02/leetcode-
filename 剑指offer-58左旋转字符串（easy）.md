# 题目
字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。  
请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。  

# 求解
```
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        s = list(s)
        res = s[n:]+s[:n]
        return ''.join(res)

# class Solution:
#     def reverseLeftWords(self, s: str, n: int) -> str:
#     return s[n:] + s[:n]
```

# 反思
字符串可以像列表一样，使用s[n:]切片，和s[n]索引  
