$O(n)$ Time Complexity
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        ListNode newHead;

        ListNode cur = head;
        ListNode prev = null;
        int count = 1;
        ListNode mid;
        while(count<left){
            prev = cur;
            cur = cur.next;
            count++;
        }
        ListNode first = head;
        if(prev!=null)
            prev.next = null;

        mid = cur;
        while(count<=right){
            prev = cur;
            cur=cur.next;
            count++;
        }
        ListNode second = cur;
        prev.next = null;
        ListNode rev = reverseList(mid);

        //updates
        newHead = head;
        if(left>1){
            cur = first;
            while(cur.next!=null)
                cur = cur.next;
            cur.next = rev;
        }
        else if(left==1){
            newHead = rev;
        }

        cur = rev;
        while(cur.next!=null)
            cur = cur.next;
        cur.next = second;
        return newHead;
    }

    public ListNode reverseList(ListNode head){
        ListNode cur = head;
        ListNode prev = null;
        ListNode next;
        while(cur!=null){
            next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        return prev;
    }
}
```