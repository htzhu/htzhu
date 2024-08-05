Blog Day 7 Hash Map

# 454. 4Sum II
Given four integer arrays nums1, nums2, nums3, and nums4 all of length n, return the number of tuples (i, j, k l) such that:
- 0 <= i, j, k, l < n 
- nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0
## My thoughts:
- 4 arrays are in the same length.
- Sum of all of them are 0.
- To hash this question, we can create a tuple first.(“table= {}”)

## Solution:
- To solve this, we have to divide it into 2 part. Bc if we do 4 of them, the time will be O(n^4). So O(n^2) is already good.
- So we could do a+b as one part, c+d as one part.
# divide them into two part
# get all possible sum of n1+n2, so we can simplify the question as a two sum question

# 383. Ransom Note
Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.

## My thoughts:
- Another question using hash map, so here we need to see if magazine has all letters in ransomNote. To look at it, I think it’s quite simple. We can just simply use a hash map to save the count of every letter in magazine. And compare the count of ransomNote.
- For letters, we can use the size of 26 array method.

# 15. 3Sum
Given an integer array nums, return all the triplets.

# 18. 4Sum
Given an array nums of n integers, return an array  of all the unique quadruplets.
