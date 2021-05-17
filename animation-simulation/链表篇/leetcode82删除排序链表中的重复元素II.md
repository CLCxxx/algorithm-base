> 如果阅读时，发现错误，或者动画不可以显示的问题可以添加我微信好友  **[tan45du_one](https://raw.githubusercontent.com/tan45du/tan45du.github.io/master/个人微信.15egrcgqd94w.jpg)** ，备注  github  + 题目 + 问题  向我反馈
>
> 感谢支持，该仓库会一直维护，希望对各位有一丢丢帮助。
>
> 另外希望手机阅读的同学可以来我的 <u>[**公众号：袁厨的算法小屋**](https://raw.githubusercontent.com/tan45du/test/master/微信图片_20210320152235.2pthdebvh1c0.png)</u> 两个平台同步，想要和题友一起刷题，互相监督的同学，可以在我的小屋点击<u>[**刷题小队**](https://raw.githubusercontent.com/tan45du/test/master/微信图片_20210320152235.2pthdebvh1c0.png)</u>进入。 

#### [82. 删除排序链表中的重复元素 II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)

题目描述

给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中没有重复出现的数字。

示例 1:

```java
输入: 1->2->3->3->4->4->5
输出: 1->2->5
```


示例 2:

```java
输入: 1->1->1->2->3
输出: 2->3
```

> 注意这里会将重复的值全部删除，1，1，2，3最后只会保留2，3。

这道题目还是很简单的，更多的是考察大家的代码完整性，删除节点也是题库中的一类题目，我们可以可以通过这个题目举一反三。去完成其他删除阶段的题目。

链表的题目建议大家能有指针实现还是尽量用指针实现，很多链表题目都可以利用辅助空间实现，我们也可以用，学会了那种方法的同时应该再想一下可不可以利用指针来完成。下面我们来思考一下这个题目如何用指针实现吧！

做题思路：

这个题目也是利用我们的双指针思想，一个走在前面，一个在后面紧跟，前面的指针就好比是侦察兵，当发现重复节点时，后面指针停止移动，侦察兵继续移动，直到移动完重复节点，然后将该节点赋值给后节点。思路是不是很简单啊，那么我们来看一下动图模拟吧。

注：这里为了表达更直观，所以仅显示了该链表中存在的节点

![删除重复节点2](https://cdn.jsdelivr.net/gh/tan45du/photobed@master/photo/删除重复节点2.3btmii5cgxa0.gif)

**题目代码**

Java Code:

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null||head.next==null){
            return head;
        }
        ListNode pre = head;
        ListNode low = new ListNode(0);
        low.next = pre;
        ListNode ret = new ListNode(-1);
        ret = low;
        while(pre != null && pre.next != null) {
            if (pre.val == pre.next.val) {
                while (pre != null && pre.next != null && pre.val == pre.next.val) {
                    pre = pre.next;
                }
                pre = pre.next;
                low.next = pre;                     
             }
             else{
                 pre = pre.next;
                 low = low.next;
             }
        }
     return ret.next;
    }
}
```

C++ Code:

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(head == nullptr || head->next == nullptr){
            return head;
        }
        ListNode * pre = head;
        ListNode * low = new ListNode(0);
        low->next = pre;
        ListNode * ret = new ListNode(-1);
        ret = low;
        while(pre != nullptr && pre->next != nullptr) {
            if (pre->val == pre->next->val) {
                while (pre != nullptr && pre->next != nullptr && pre->val == pre->next->val) {
                    pre = pre->next;
                }
                pre = pre->next;
                low->next = pre;                     
             }
             else{
                 pre = pre->next;
                 low = low->next;
             }
        }
     return ret->next;
    }
};
```

