Blog Day 4

# 24 Swap Nodes in Pairs
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list’s nodes(i.e., only nodes themselves may be changed.)

## Terminology:
-  Every two adjacent nodes: Does it means every two pairs? Do we need to swap 1&2, 2&3 or 1&2, 3&4? What do we do if there is only one element or we have the odd num of elements? **The question itself gave the definition:** 1. When there is no element, we just return. 2. When there is only one element, we just return this element bc we don’t need to swap anymore. 3. Else we can do swap.

## Solution:
Honestly, the thought is very simple, but the only thing is to follow the linked list’s rule, so it would be very careful every move is legal.

# 19. Remove Nth Node From End of List
Given the head of a linked list, remove the nth node from the end of the list and return its head.

##My thoughts:
- Use dummy node is almost in every linked list problems. It can help solving most of the linked list problems.

## Solution:
- Use two pointers and dummy node. It’s a good way but I don’t understand why fast move n+1 steps will work. But after tried on a few examples, it actually work! So I might just believe it for now.

# 142. Linked List Cycle II
Given the head of a linked list, return the node when the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some nodes in the list that can be reached again by continuously following the next point. Internally, pos is used to denote the index of the node that tail’s next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.

## Terminology:
- Cycle: Some nodes can be reached again by continuously following the next point.
- This is about Floyd’s Algorithm. （也称龟兔赛跑算法，出现在Joma的视频中）
- 关键点：
1. 在最坏的情况下（有环，且环几乎和链表一样长），第一个循环可能会遍历整个链表。
2. 第二个循环最多也只会遍历链表的长度。
因此，总的操作次数最多是链表长度的常数倍，不会超过2N或3N。在大O表示法中，我们忽略常数因子，所以这个算法的时间复杂度就是O(N)。
空间复杂度是O(1)，因为只使用了两个指针，不管链表多长，额外空间使用是常量的。
Floyd's循环检测算法（也称为"龟兔赛跑"算法）是解决链表中环检测问题的经典方法。在面试中，如果遇到类似的问题，你确实可以直接使用这种方法来快速解决。这种方法不仅高效，而且在面试中展示了你对经典算法的理解。
以下是一些可能在面试中遇到的相关问题例子：
	1	检测链表中是否有环 问题：给定一个链表，判断链表中是否有环。 解决：使用Floyd's算法，如果快慢指针相遇，则有环；否则无环。
	2	找到环的起始节点 问题：如果链表中存在环，找到环的起始节点。 解决：这正是我们之前讨论的完整Floyd's算法。
	3	找到环的长度 问题：如果链表中存在环，计算环的长度。 解决：在快慢指针第一次相遇后，让其中一个指针固定，另一个继续移动直到再次相遇，记录移动的步数即为环的长度。
	4	找到两个链表的相交点 问题：给定两个可能相交的链表，找到它们相交的节点。 解决：这个问题可以转化为环检测问题。将其中一个链表的尾部连接到另一个链表的头部，然后使用Floyd's算法找到环的起点，即为相交点。
	5	判断链表是否为回文 问题：判断一个链表是否为回文结构。 解决：虽然这不直接使用Floyd's算法，但可以用快慢指针找到链表中点，然后比较前后两半。
在面试中使用这种方法时，记得解释你的思路：
	1	先说明你准备使用Floyd's循环检测算法。
	2	解释算法的基本原理（快慢指针）。
	3	描述如何实现，包括两个阶段（检测环和找到环起点）。
	4	分析时间复杂度（O(N)）和空间复杂度（O(1)）。
	5	如果面试官要求，可以现场编写代码。
记住，虽然这是一个强大的方法，但也要根据具体问题灵活应用。有时候，面试官可能会故意给出一些变体问题来测试你的思维灵活性。所以，理解算法的核心原理比单纯记忆更重要。
