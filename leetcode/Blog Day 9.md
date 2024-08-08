Blog Day 9 String

# 151. Reverse Words in a String
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separared by at least one space.

Return a string of the words in reverse order concatenated by a single space.

## My thoughts:
- Steps:
	1. Detect spaces, I think use ‘ ’ should be ok.
	2. For all of the words, use two pointers.
	3. Save words as a dictionary.
	3. Delete extra spaces.

## Solution:
1. Base on thought:
 class Solution:
    def reverseWords(self, s: str) -> str:
        # .strip() 在 Python 中用于去除字符串开头和结尾的空白字符（或其他指定字符）。这是一个非常有用的字符串处理方法。
        s = s.strip()
        # 翻转了整个字符串
        # 也就是说，这个是给s整个倒序了
        s = s[::-1]
        # 这一句非常地简练，包含了一下三种语法值得学习：
        # 1. ' '.join()
        # 2. word[::-1] 把之前倒序的单词全都反转回来
        # 3. .split() 可以将单词提取出来，成为一个列表形式
        s = ' '.join(word[::-1] for word in s.split())
        return s
2. Two pointers: 基本和之前一样
class Solution:
    def reverseWords(self, s: str) -> str:
        word = s.split()
        left = 0
        right = len(word)-1

        while left < right:
            word[left], word[right] = word[right], word[left]
            left += 1
            right -= 1
        
        return (' '.join(word))

# 28. Find the Index of the First Occurrence in a String
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

## My Thoughts:
- If we can use haystack.split().
- But here we have a problem, which is  here we don’t have words, we have a continue string.
- Therefore, we should maybe use KMP algo.

## Solution:
- KMP: This algo contains prefix table, next array... (learned in 379)
- 
