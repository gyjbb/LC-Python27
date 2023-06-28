# LC-Python27
Greedy Algorithm 2

## 122.Best Time to Buy and Sell Stock II, 55. Jump Game, 45.Jump Game II

June 27, 2023  4h

Congratulations!\
This is the 27th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are about ~~using local optimums to get the global optimum.~~


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
For example, the array [2, 3, 1, 1, 4] 
<img src="https://github.com/gyjbb/Leetcode-Python4/blob/main/Screen%20Shot%202023-05-17%20at%202.58.58%20PM.png" width="400" height="180">



