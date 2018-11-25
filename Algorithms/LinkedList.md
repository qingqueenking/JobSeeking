# Linked List

* Dummy Node
* Next Node

## Add Two Numbers
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        int carry = 0;
        while (l1 != null || l2 != null) {
            int sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
            carry = sum / 10;
        }
        if (carry != 0) {
            cur.next = new ListNode(carry);
        }
        return dummy.next;
    }
}
```
## Merge Two Sorted Lists
```
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                cur.next = l1;
                l1 = l1.next;
            } else {
                cur.next = l2;
                l2 = l2.next;
            }
            cur = cur.next;
        }
        if (l1 != null) {
            cur.next = l1;
        }
        if (l2 != null) {
            cur.next = l2;
        }
        return dummy.next;
    }
}
```
## Merge K Sorted Lists
```
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) {
            return null;
        }
        ListNode dummy = new ListNode(0);
        ListNode cur = dummy;
        PriorityQueue<ListNode> pq = new PriorityQueue<>(lists.length, (a, b) -> a.val - b.val);
        for (ListNode list : lists) {
            if (list != null) {
                pq.offer(list);
            }
        }
        while (!pq.isEmpty()) {
            ListNode node = pq.poll();
            cur.next = node;
            cur = cur.next;
            if (node.next != null) {
                pq.offer(node.next);
            }
        }
        return dummy.next;
    }
}
```
## Reverse Linked List
```
public class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        while (cur != null) {
            ListNode temp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = temp;
        }
        return pre;
    }
}
```
## Linked List Cycle
```
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode intersect = getIntersect(head);
        if (intersect == null) {
            return null;
        }
        while (head != intersect) {
            head = head.next;
            intersect = intersect.next;
        }
        return head;
    }
    private ListNode getIntersect(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        int length = 0; // cycle size
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            length++;
            if (slow == fast) {
                return slow;
            }
        }
        return null;
    }
}
```
## Intersection of Two Linked Lists
```
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        ListNode a = headA;
        ListNode b = headB;
        while (a != b) {
            a = (a != null) ? a.next : headB;
            b = (b != null) ? b.next : headA;
        }
        return a;
    }
}
```
## Delete Node in a Linked List
```
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```
## Swap Nodes in Pairs
```
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        while (pre != null && pre.next != null && pre.next.next != null) {
            ListNode n1 = pre.next;
            ListNode n2 = pre.next.next;
            pre.next = n2;
            n1.next = n2.next;
            n2.next = n1;
            pre = n1;
        }
        return dummy.next;
    }
}
```
## Reverse Nodes in k-Group
```
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        while (pre != null) {
            pre = reverse(pre, k);
        }
        return dummy.next;
    }
    private ListNode reverse(ListNode node, int k) {
        ListNode p = node;
        for (int i = 0; i < k; i++) {
            p = p.next;
            if (p == null) {
                return null;
            }
        }
        ListNode pre = node;
        ListNode cur = node.next;
        ListNode n1 = node.next;
        ListNode nk = p;
        ListNode nkplus = p.next;
        while (cur != nkplus) {
            ListNode temp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = temp;
        }
        node.next = nk;
        n1.next = nkplus;
        return n1;
    }
}
```
## Copy List with Random Pointer
* \#1: HashMap
```
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        if (head == null) {
            return null;
        }
        RandomListNode cur = head;
        Map<Integer, RandomListNode> map = new HashMap<>();
        while (cur != null) {
            if (!map.containsKey(cur.label)) {
                map.put(cur.label, new RandomListNode(cur.label));
            }
            if (cur.next != null) {
                if (!map.containsKey(cur.next.label)) {
                    map.put(cur.next.label, new RandomListNode(cur.next.label));
                }
                map.get(cur.label).next = map.get(cur.next.label);
            }
            if (cur.random != null) {
                if (!map.containsKey(cur.random.label)) {
                    map.put(cur.random.label, new RandomListNode(cur.random.label));
                }
                map.get(cur.label).random = map.get(cur.random.label);
            }
            cur = cur.next;
        }
        return map.get(head.label);
    }
}
```
* \#2
```
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        if (head == null) {
            return null;
        }
        RandomListNode node = head;
        while (node != null) {
            RandomListNode temp = node.next;
            node.next = new RandomListNode(node.label);
            node.next.next = temp;
            node = temp;
        }
        node = head;
        while (node != null && node.next != null) {
            if (node.random != null) {
                node.next.random = node.random.next;
            }
            node = node.next.next;
        }
        RandomListNode dummy = new RandomListNode(0);
        RandomListNode copy = dummy;
        node = head;
        while (node != null && node.next != null) {
            copy.next = node.next;
            copy = copy.next;
            node.next = node.next.next;
            node = node.next;
        }
        return dummy.next;
    }
}
```
## Rotate List
```
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null) {
            return null;
        }
        k %= getLength(head);
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode slow = dummy;
        ListNode fast = dummy;
        for (int i = 0; i < k; i++) {
            fast = fast.next;
        }
        while (fast.next != null) {
            slow = slow.next;
            fast = fast.next;
        }
        fast.next = dummy.next;
        dummy.next = slow.next;
        slow.next = null;
        return dummy.next;
    }
    private int getLength(ListNode head) {
        int length = 0;
        while (head != null) {
            length++;
            head = head.next;
        }
        return length;
    }
}
```
* Rotate Array
```
class Solution {
    public void rotate(int[] nums, int k) {
        if (nums == null || nums.length == 0) {
            return;
        }
        k %= nums.length;
        reverse(nums, 0, nums.length - k - 1);
        reverse(nums, nums.length - k, nums.length - 1);
        reverse(nums, 0, nums.length - 1);
    }
    private void reverse(int[] nums, int left, int right) {
        while (left < right) {
            int temp = nums[left];
            nums[left] = nums[right];
            nums[right] = temp;
            left++;
            right--;
        }
    }
}
```
