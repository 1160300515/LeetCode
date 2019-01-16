---
title: 【LeetCode】328.Odd Even Linked List
tags: LeetCode | 小书匠
grammar_attrs: true
grammar_classy: false
grammar_decorate: false
---
<br>
<br>

#### 题目要求
Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.
You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

Note:
- The relative order inside both the even and odd groups should remain as it was in the input.
- The first node is considered odd, the second node even and so on ...
#### 示例
- Example 1:
```{#pre}
Input: 1->2->3->4->5->NULL
Output: 1->3->5->2->4->NULL
```
- Example 2:
```{#pre}
Input: 2->1->3->5->6->4->7->NULL
Output: 2->3->6->7->1->5->4->NULL
```

#### 思路
简单的链表操作，一个奇数节点的ListNode，一个偶数节点的ListNode，最后将偶数的链接到奇数后面。
#### 代码

```java
public ListNode oddEvenList(ListNode head) {
    ListNode odd = head;
    if (head == null || head.next == null)
      return head;
    ListNode node_even = head.next, even = head.next;
    while (even.next != null) {
      odd.next = even.next;
      odd = odd.next;
      if (odd.next != null) {
        even.next = odd.next;
        even = even.next;
      } else {
        even.next = null;
        break;
      }
    }
    odd.next = node_even;
    return head;
  }
```
