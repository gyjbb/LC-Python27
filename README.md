# LC-Python27
Greedy Algorithm 2

## 122.Best Time to Buy and Sell Stock II, 55. Jump Game, 45.Jump Game II

June 27, 2023  4h

Congratulations!\
This is the 27th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about the two jump games. All used the concept of largest coverage. But the last question is hard because it needs to record the current distance, which needs to be updated by the largest next distance! Hard to come up with so many variables and keep track of them.


## 122.Best Time to Buy and Sell Stock II
Here we only collect positive profits everyday.\
Attention: in the for loop, the i start from 1 because we need at least 1 day to buy first.
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        result = 0
        for i in range(1, len(prices)):
            result += max(prices[i] - prices[i-1], 0)
        return result
```


## 55. Jump Game
We can solve this question by check if all numbers can be covered by the previous step sizes, check the coverage range.\
And remember to record and update the largest cover range. When the coverage range reaches the last number, return true.
```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        cover = 0
        if len(nums) == 1: return True
        for i in range(len(nums)):
            if i <= cover:
                cover = max(i+nums[i], cover)
                if cover >= len(nums)-1:
                    return True     #the last item now can be coverd
        return False
```


##  45.Jump Game II
For example, the array [2, 3, 1, 1, 4] \
<img src="https://github.com/gyjbb/LC-Python27/blob/main/Screen%20Shot%202023-06-28%20at%201.01.42%20AM.png" width="300" height="100">
```python
class Solution:
    def jump(self, nums):
        if len(nums) == 1:
            return 0
        
        cur_distance = 0  # 当前覆盖最远距离下标
        ans = 0  # 记录走的最大步数
        next_distance = 0  # 下一步覆盖最远距离下标
        
        for i in range(len(nums)):
            next_distance = max(nums[i] + i, next_distance)  # 更新下一步覆盖最远距离下标
            if i == cur_distance:  # 遇到当前覆盖最远距离下标
                ans += 1  # 需要走下一步
                cur_distance = next_distance  # 更新当前覆盖最远距离下标（相当于加油了）
                if next_distance >= len(nums) - 1:  # 当前覆盖最远距离达到数组末尾，不用再做ans++操作，直接结束
                    break
        
        return ans
```

