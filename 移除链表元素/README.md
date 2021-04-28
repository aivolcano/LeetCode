### 链表操作的两种方式：
「直接使用原来的链表来进行删除操作。」

「设置一个虚拟头结点在进行删除操作。」


### 第203题：移除链表元素
https://leetcode-cn.com/problems/remove-linked-list-elements/

题意：删除链表中等于给定值 val 的所有节点。

思路
这里以链表 1->4->2->4  来举例，移除元素4。
 
![image](https://user-images.githubusercontent.com/68730894/116357857-91530b00-a82f-11eb-84b9-62220eb972b6.png)

![image](https://user-images.githubusercontent.com/68730894/116357866-94e69200-a82f-11eb-8ac4-71f53b742cb5.png)

![image](https://user-images.githubusercontent.com/68730894/116357873-97e18280-a82f-11eb-9c22-744cf71c3350.png)

思路：头结点之前新增虚拟头结点，指向头结点
	初始化2个指针 curr（当前节点） & prev（下一个节点）
	如果当前节点存在
		比较当前节点的值和要删除的值是否相等
			相等：下一个节点.next 指向 curr.next
			不相等：下一个节点prev 指向 当前节点curr
		遍历下一个节点 curr = curr.next
 	return 头结点的时候，别忘了 return dummyNode.next，这才是新的头结点
	sentiel.next

移除头结点和移除其他节点的操作是不一样的，因为链表的其他节点都是通过前一个节点来移除当前节点，而头结点没有前一个节点。

移除头结点时，将头结点向后移动一位就可以，这样就从链表中移除了一个头结点。

![image](https://user-images.githubusercontent.com/68730894/116358084-d37c4c80-a82f-11eb-9f1a-e0cd1fe4090c.png)

return 头结点的时候，别忘了 return dummyNode->next;， 这才是新的头结点

```python
class Solution:
  def removeElements(self, head: ListNode, val: int) -> ListNode:
    # 头结点新增一个虚拟头结点，因为头结点没有前一个节点
    dummy = ListNode(0)
    
    # 
    dummy.next = head
    
    # 头结点先后移动一位可以移除当前节点  
    # 初始化2个指针curr和prev指向当前节点和下一个节点
    
    prev, curr = dummy, head
    
    while curr: 
      if curr.val == val:
        prev.next = curr.next: # 若当前节点就是要删除的节点
      else:
        prev == curr
      curr = curr.next
     
      return dummy.next   
    
```
