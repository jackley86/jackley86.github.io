题目描述：
给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

示例：
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

难点分析：
1. 按位相加时的进位逻辑，需要梳理清楚。
2. 链表这种数据结构的特性，要比较清楚。

我个人在解这个题目时，感觉是按位相加的逻辑比较容易梳理，无非就是需要考虑进位，以及两个被加数长度不同时的情况处理。
而链表的数据结构特性，相对来说更复杂，有几个方面值得注意：首先，链表是由节点组成，节点即代码注释中所给的ListNode，链表的节点不等同于链表，节点只是链表的组成部分。其次，链表可以由首个节点来表示，因为每个节点都会记录其下一节点的信息，只要有首个节点的信息，就能遍历出整个列表的元素。其三，ListNode的next属性，初始化时设为None，让我以为next和val一样都是int型数据，事实上根本不是，next应该指向下一个ListNode，即next应为ListNode类型。

相关技术细节：
该问题中还有几个相关的技术细节，也比较影响到解题，具体说明如下。
1. 两个被加数长度不同时，高位上整数与空值None相加的实现。用l.val or 0表示即可，即当节点对应的位为None时，将其变换为0值，即能够实现高位的相加。
2. 每一位加完之后，怎么进行移位操作。用p=p.next就可以了，因为每个节点都是一个ListNode，p和p.next事实上都是ListNode类型。
3. 全部计算完之后，如何表示整个链表。用p=dummy=ListNode(-1)，即用dummy记录下首个节点即可。对于链表而言，只要记录下第一个节点，就相当于记录了整个链表。

具体实现代码如下：
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        p=dummy=ListNode(-1) #链表记录好首个节点
        carry=0 #进位
        while l1 or l2:
            # 考虑进位和高位为空的情况
            val=(l1 and l1.val or 0)+(l2 and l2.val or 0)+carry
            p.next=ListNode(val%10)
            carry=val/10
            l1=l1 and l1.next
            l2=l2 and l2.next
            # p.next指向的应该是下一个Listnode
            p=p.next
        return dummy.next
```
