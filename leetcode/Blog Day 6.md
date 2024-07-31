Blog Day 6 Hash Map 

# 242. Valid Anagram
Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## My thought:
In this kind of question, the simplest way to find it is to compare the length first, and then use a hash map to compare the letters to see if they are the same.

## Solution:
- Knowledge of hash map:
“当我们遇到了要快速判断一个元素是否出现集合里的时候，就要考虑哈希法。 这句话很重要，大家在做哈希表题目都要思考这句话。”
- Define an array called ‘record’, size = 26, because a-z’s ASCII are 26 continue numbers.
- Every letter appears in s, we increment the counts. For every letter appears in t, we decrement there counts. Obviously, it will be 0 eventually if they are anagram.

# 349. Intersection of Two Arrays
Given two integer arrays nums1 and nums2, return an array of their intersection.  Each element in the result must be unique and you may return the result in any order.

## My thoughts:
- It feels like the same as the last question. Because they have the same problem which is to find the same element in two of arrays.
- I’m trying to use the method we used before. But we are counting numbers instead of letters. So we can’t create an array with size of 26.
## Solution:
- 那有同学可能问了，遇到哈希问题我直接都用set不就得了，用什么数组啊。直接使用set 不仅占用空间比数组大，而且速度要比数组慢，set把数值映射到key上都要做hash计算的。不要小瞧这个耗时，在数据量大的情况，差距是很明显的。
- 所以，在数值范围明确的情况下使用array会比较好，而不明确的情况下才考虑用set。
- Python中，数组就是list列表。
- Set() 是集合，其无序的特性导致我们无法像数组一样通过索引访问元素。
- 字典：键值对的数据结构，对于哈希表很好用。

#202. Happy Number 
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1(where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.

Return true if n is a happy number, and false if not.

## My thoughts:
- First step is to get all the digits. To do that, we could…

## Solution:
- 还有一个难点就是求和的过程，如果对取数值各个位上的单数操作不熟悉的话，做这道题也会比较艰难。

def get_sum(self, n:int) -> int:
        new_num = 0
        # We use while n here, which means we don't need to worry about how many digits do we have in total, because the loop will end after adding last digit of the number. 
        while n:
            n, r = divmod(n, 10)
            new_num += r ** 2
        return new_num

- 这道题目看上去貌似一道数学问题，其实并不是！题目中说了会 无限循环，那么也就是说求和的过程中，sum会重复出现，这对解题很重要！所以这道题目使用哈希法，来判断这个sum是否重复出现，如果重复了就是return false， 否则一直找到sum为1为止。判断sum是否重复出现就可以使用unordered_set。

def isHappy(self, n: int) -> bool:
        record = set()
        while True:
            n = self.get_sum(n)
            if n == 1:
                return True
            
            if n in record:
                return False
            else:
                record.add(n)

# 1. Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## My thoughts:
- Since we are trying to find the numbers quickly, we should use hash map here.
- Also it also says there is only one solution.
- The key for this question is to save the diff between.

## Solution:
- Although it’s the first question on leetcode, but this is also a very good hash map question. We use array and set in hash map questions already. Now here we are going to use map to solve hash map question.
- enumerate(nums):
这个方法是用来遍历数组的
