# 题目
在一个 n * m 的二维数组中，每一行都按照从左到右 非递减 的顺序排序，每一列都按照从上到下 非递减 的顺序排序。  
请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。  

# 求解
1.我的从右上角开始，需要规避[]的情况
```
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        if matrix == []:return False
        n = len(matrix)
        m = len(matrix[0])
        i,j = 0,m-1
        while i<n and j>=0:   # 该值存在
            if target<matrix[i][j]:   # 小向左
                j -= 1
            elif target>matrix[i][j]:    # 大向下
                i += 1
            elif target==matrix[i][j]:
                return True
        return False
```

2.佬的从左下角开始，自动规避空的情况；但也不能规避一维数组的情况，测试案例中并未出现
```
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        i, j = len(matrix) - 1, 0
        while i >= 0 and j < len(matrix[0]):
            if matrix[i][j] > target: i -= 1
            elif matrix[i][j] < target: j += 1
            else: return True
        return False
```

# 反思
上述求解不难想到；开始想用递归先判断对角线上元素，再分别在右上矩阵和左下矩阵里递归判断，但由于list不能切片，访问列只能用循环，遂作罢；  

list的性质：  
1.len(list)得到行数，len([])=0  
2.len(list[n])得到第n+1列的列数/数目，如果该list是一维，则会报错
3.获得list某行很容易，某列比如第i列则需要：x[i] for x in list
4.list[i][j]  VS  array[i,j],array好用得多，但力扣不能import库
