# 题目
统计一个数字在排序数组中出现的次数。

# 求解
```
# class Solution:
#     def search(self, nums: List[int], target: int) -> int:
#         times = 0
#         for i in range(len(nums)):
#             if nums[i] == target:
#                 for num in nums[i:]:
#                     if num == target: 
#                         times+=1
#                 return times
#         return times

# 大佬的奇妙二分法
class Solution:
    def search(self, nums: [int], target: int) -> int:
        def helper(tar):
            i, j = 0, len(nums) - 1
            while i <= j:
                m = (i + j) // 2
                if nums[m] <= tar: i = m + 1
                else: j = m - 1
            return i
        return helper(target) - helper(target - 1)
```

# 反思
二分法还没完全搞明白
