# 排序

## 快速排序
```
# # time O(nlgn) space O(1)
# 迭代解法
def quicksort_iter(nums, left, right):
	 # 递归的终止条件 
    if left >= right: return
	
    low, high = left, right
    key = nums[left]
    while low < high:
    	 # 右指针左移，直到比key小
        while low < high and nums[high] >= key:
            high -= 1
        # 比key小后，右值赋值给左值
        nums[low] = nums[high]
		 # 左指针右移，直到比key大
        while low < high and nums[low] <= key:
            low += 1
        # 左值赋值给右值
        nums[high] = nums[low]
	 # 此时左右指针重合，key赋值给左值
    nums[low] = key
    # 此时分成左右两部分，分别进行递归
    quicksort_iter(nums, left, low)
    quicksort_iter(nums, high + 1, right)
```
```
# 递归解法
def quicksort_recursion(nums,reverse=False):
    
    return _quicksort(nums) if reverse == False else list(reversed(_quicksort(nums)))

def _quicksort(nums):
    if len(nums) <= 1:
        return nums

    key = nums[0]
    nums_left = _quicksort([x for x in nums[1:] if x < key])
    nums_right = _quicksort([x for x in nums[1:] if x >= key])

    return nums_left + [key] + nums_right
```

## 归并排序
```
# time O(nlgn) space O(n)
def merge_sort(nums,reverse=False):
    nums = __merge_sort(nums)
    return nums if reverse == False else list(reversed(nums))

def __merge_sort(nums):
    if len(nums) <= 1:
        return nums
    # 找到中点，
    mid = len(nums)//2
    # 对左右部分进行递归
    partA = __merge_sort(nums[:mid])
    partB = __merge_sort(nums[mid:])
    # 合并
    return __merge(partA,partB)

def  __merge(partA:list,partB:list):
	 # 储存合并的结果
    c = []
    while len(partA) > 0 and len(partB) > 0:
    	 # 从index=0开始，把小的一方加入c数组，然后把该元素从小的一方的数组中删除
        if partA[0] > partB[0]:
            c.append(partB[0])
            partB.remove(partB[0])
        else: # 
            c.append(partA[0])
            partA.remove(partA[0])
    # 兜底处理：循环在两部分其中一部分为空时跳出，把不为空的部分全部加到c数组
    c += partA if len(partB) == 0 else partB
    return c
```

## 插入排序
```
# time O(n^2) space O(1)
# 当前位置的数字和前面的逐个对比，比当前位置大就交换位置
def insert_sort(nums,reverse=False):
    for i in range(1,len(nums)):
        # i 为当前数的位置
        unsort_idx = i
        # 和前面的数逐个对比
        while unsort_idx > 0 and nums[unsort_idx-1] > nums[unsort_idx]:
            nums[unsort_idx-1],nums[unsort_idx] = nums[unsort_idx],nums[unsort_idx-1]
            # 当前位置往前移1
            unsort_idx -= 1
            
    if reverse == True: nums.reverse()
    return nums
```

## 选择排序
```
# time O(n^2) space O(1)
def select_sort(nums):
    for i in range(len(nums)):
        # 开始时假定一个最小值的位置 pos_min
        pos_min = i
        # 从i的下一位开始遍历对比
        for j in range(i+1,len(nums)):
            # 如果找到比位置i的数更小的就把j赋值给pos_min
            if nums[j] < nums[pos_min]:
                pos_min = j
        # i 和 pos_min 的数交换，此时最小值就在i，且i前面的数字都是排序好的
        nums[pos_min],nums[i] = nums[i],nums[pos_min]
    return nums
```

