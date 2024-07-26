Blog Day 3 Linked List

# 203. Remove Linked List Elements
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

## Terminology
- What is a linked list?
	It’s a linear structure connected by pointers. Each node has two parts: Data and pointer. 
- 特殊节点（头、尾节点），需要特别处理：
	- 直接处理
	- 引入dummy node
- 链表类型：
	- 单链表
	- 双链表
	- 循环链表：循环链表，顾名思义，就是链表首尾相连。循环链表可以用来解决约瑟夫环问题。
- Tips:
	- 数组在内存中是连续分布，而链表不是，其因有指针的关系，可以分布在内存中的不同位置。

## My thought:
There are two different situations. We need to judge if it’s in a special situation. 

## Solution:
Turns out it doesn’t have to be that special. Just need to add a dummy node and then solve everything.

# 707. Design Linked List
Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: val and next. Val is the value of the current node, and next is a pointer/reference to the next node.
If you want to use the doubly linked list, you will need one more attribute prev to indicate the previous node in the linked list.
Assume all nodes in the linked list are 0-indexed.

## Terminology:
- 0-indexed: 在 0-indexed（零索引）系统中，序列的第一个元素的索引是 0，而不是 1。

## Solution:
There are a few things need to be noticed:
1. Linked List is not like array, when we need to query an element, we need to go over all the list, so that’s why people said we need O(N) time in linked list but only O(1) time in array.
2. Some times we need to <= index and sometimes we need to < index. Depends on diff situations.
# Define a normal listnode
class ListNode:

    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

# Define my linked list obj, which has my own functions
class MyLinkedList:

    def __init__(self):
        self.dummy_head = ListNode()
        self.size = 0

    def get(self, index: int) -> int:
        # index's legal range is [0, size-1]
        if index<0 or index >= self.size:
            return -1
        
        current = self.dummy_head.next
        for i in range(index):
            current = current.next
        
        return current.val

    def addAtHead(self, val: int) -> None:
        self.dummy_head.next = ListNode(val, self.dummy_head.next)
        self.size += 1

    def addAtTail(self, val: int) -> None:
        # Here we have to pass the new tail from head to tail one by one. Which takes O(n)  time.
        current = self.dummy_head
        while current.next:
            current = current.next
        current.next = ListNode(val)
        self.size += 1

    def addAtIndex(self, index: int, val: int) -> None:
        # Why not make size <= index is bc index cloud be append at the tail
        if index < 0 or index > self.size:
            return
        
        current = self.dummy_head
        for i in range(index):
            current = current.next
        current.next = ListNode(val, current.next)
        self.size += 1

    def deleteAtIndex(self, index: int) -> None:
        # Why not make size < index is bc only index in the legal range will be deleted.
        if index < 0 or index >= self.size:
            return
        
        current = self.dummy_head
        for i in range(index):
            current = current.next
        current.next = current.next.next
        self.size -= 1

# 206. Reverse Linked List
Given the head of a singly linked list, reverse the list, and return the reversed list.

## My thought:
We have the head of the linked list. So to reverse it, we need to do it one by one from the head.

## Solution:
- Two pointer:
We can use two pointers here, which also means we don’t have to keep it in array. As long as the question related to it.
- Recursion:
Recursion is just the similar thought but used one more function to do it.
