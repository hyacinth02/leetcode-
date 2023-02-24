# 题目
找出数组中重复的数字。  
在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，  
也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

# 求解
```
# 时间超出
# class Solution:
#     def findRepeatNumber(self, nums: List[int]) -> int:
#         for i,num1 in enumerate(nums):
#             for num2 in nums[i+1:]:
#                 if num1 == num2:
#                     return num1

class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        new = sorted(nums)
        for i in range(len(new)):
            if new[i] == new[i+1]:
                return new[i]
```

# 反思
1.python 可以使用sorted(),或者list.sort()排序
