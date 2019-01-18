## [59. 螺旋矩阵 II](https://leetcode-cn.com/problems/spiral-matrix-ii/)
给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。

##### 示例:
```
输入: 3
输出:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```

#### 解题思路
```
用递归的方式解题（也可以用迭代）


class Solution(object):
    def generateMatrix(self, n):
    	## 创建 n*n 大小的二维数组
        matrix = [[0 for _ in range(n)] for _ in range(n)]
        self.__genMatrix(matrix, n, 1, (0,0), -1)
        return matrix
    ## -----------------------------------------    
    ## params:
    ## matrix: 二维数组
    ## t: 数组的长宽
    ## n: 填充到数组的数
    ## loc: 当前坐标
    ## dirc: 方向
    def __genMatrix(self, matrix, t, n, loc, dirc):
        if n > t**2:
            return
    
        i, j = loc[1] , loc[0]
        matrix[j][i] = n
        
        d_v, d_h = self.__direction(dirc)
        
        ## key：在当前方向走，如果走到四个角或者当前坐标在当前方向的下一个位置的值不为0，就要改变方向
        if (i == 0 and j == 0)or(i == 0 and j == t-1)or(i == t-1 and j == 0)or(i == t-1 and j == t-1)or(matrix[j+d_v][i+d_h] != 0):
            dirc += 1
            d_v, d_h = self.__direction(dirc)
        ## 更新下一个要填充的位置
        loc = (j+d_v , i+d_h)
        
        self.__genMatrix(matrix,t,n+1,loc,dirc)
    ## ------------------------------------------------    
    ## 方向固定是顺时针， 右->下->左->上
    ## left:(0,-1) right:(0,1) up(-1,0) down:(1,0)
    def __direction(self,n):
        if n < 0:
            return (0,1)
        dirs = [(0,1),(1,0),(0,-1),(-1,0)]
        return dirs[n % 4]

```