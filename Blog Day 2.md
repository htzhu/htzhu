Blog Day 2

# 977. Square of a sorted array

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Terminology:
- Non-decreasing meaning: The second element is always larger or equal than the previous element.

Analysis:
We have an array: nums. We need to return an array which contain all the squared number in nums.

- My thought: To do so, we need to create a new array to store new elements. Also we need to calculate the square of the numbers. This method could take O(n) time complexity.

class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        square = [0]*len(nums)
        i = 0
        while i < len(nums):
            square[i] = nums[i] * nums[i]
            i+=1
        square.sort()

        return square

- 代码随想录解法：Two pointer, for this question, the key is to solve the sorting problem, because there might be some negative number. So it could be sort after that is right, but it will take O(n+logn) time complexity. With two pointer, we can easily sort the new array while calculating square. Which will take O(n).

class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        square = [float('inf')] * len(nums)
        k = len(nums)-1
        i = 0
        j = len(nums)-1
        while i <= j:
            if nums[i] * nums[i] < nums[j] * nums[j]:
                square[k] = nums[j] * nums[j]
                j-=1
            else:
                square[k] = nums[i] * nums[i]
                i+=1
            k-=1

        return square

Summary:
For two pointer, can either be slow&fast or left&right.

# 209 Minimum size subarray sum

Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Terminology:
- Subarray meaning: The subarray here will need to follow the original order.

Analysis:
- My thought: For this question, Firstly, we need to calculate the sum of all the possible subarray, and find the minimal length one. Secondly, we need to compare the sum with the target, if sum = target, we compare the length with the current minimal length. 
To do so, there are a few ideas:
- We might use a variable to store the minimal length.
- We could use an array to store the length of all the matched subarrays. And then sort the array, and return the first element.
The key point is how to find all the subarrays.
