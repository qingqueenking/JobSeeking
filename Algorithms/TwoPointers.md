# Two Pointers
## Reverse
### [Rotate Array](https://leetcode.com/problems/rotate-array/description/)
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
### [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)
```
class Solution {
    public boolean isPalindrome(String s) {
        if (s == null || s.length() == 0) {
            return true;
        }
        int left = 0;
        int right = s.length() - 1;
        while (left < right) {
            if (!Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            } else if (!Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            } else if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            } else {
                left++;
                right--;
            }
        }
        return true;
    }
}
```
### [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/description/)
```
class Solution {
    public boolean validPalindrome(String s) {
        if (s == null || s.length() == 0) {
            return true;
        }
        int left = 0;
        int right = s.length() - 1;
        while (left < right && s.charAt(left) == s.charAt(right)) {
            left++;
            right--;
        }
        if (left == right) {
            return true;
        }
        return helper(s, left, right - 1) || helper(s, left + 1, right);
    }
    private boolean helper(String s, int left, int right) {
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```
## Two Sum
### [Two Sum](https://leetcode.com/problems/two-sum/description/)
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return new int[2];
        }
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(nums[i])) {
                return new int[] {map.get(nums[i]), i};
            }
            map.put(target - nums[i], i);
        }
        return new int[2];
    }
}
```
### [Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
```
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        if (numbers == null || numbers.length == 0) {
            return new int[2];
        }
        int left = 0;
        int right = numbers.length - 1;
        while (left < right) {
            if (numbers[left] == target - numbers[right]) {
                return new int[] {left + 1, right + 1};
            } else if (numbers[left] < target - numbers[right]) {
                left++;
            } else {
                right--;
            }
        }
        return new int[2];
    }
}
```
### [Two Sum III - Data structure design](https://leetcode.com/problems/two-sum-iii-data-structure-design/description/)
* #1: O(1) add, O(n) find
```
class TwoSum {
    private Map<Integer, Integer> map;
    public TwoSum() {
        map = new HashMap<Integer, Integer>();
    }
    public void add(int number) {
        map.put(number, map.getOrDefault(number, 0) + 1);
    }
    public boolean find(int value) {
        for (int key : map.keySet()) {
            int target = value - key;
            if (key == target && map.get(key) >= 2) {
                return true;
            } else if (key != target && map.containsKey(target)) {
                return true;
            }
        }
        return false;
    }
}
```
* #2: O(n) add, O(1) find
```
class TwoSum {
    private Set<Integer> nums;
    private Set<Integer> sums;
    public TwoSum() {
        nums = new HashSet<Integer>();
        sums = new HashSet<Integer>();
    }
    public void add(int number) {
        for (int num : nums) {
            sums.add(num + number);
        }
        nums.add(number);
    }
    public boolean find(int value) {
        return sums.contains(value);
    }
}
```
### [Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)
* #1: Time O(n), Space O(n), n is the number of nodes
```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        if (root == null) {
            return false;
        }
        List<Integer> list = new ArrayList<>();
        inorder(root, list);
        int left = 0;
        int right = list.size() - 1;
        while (left < right) {
            if (list.get(left) == k - list.get(right)) {
                return true;
            } else if (list.get(left) < k - list.get(right)) {
                left++;
            } else {
                right--;
            }
        }
        return false;
    }
    private void inorder(TreeNode node, List<Integer> list) {
        Stack<TreeNode> stack = new Stack<>();
        while (node != null || !stack.empty()) {
            while (node != null) {
                stack.push(node);
                node = node.left;
            }
            node = stack.pop();
            list.add(node.val);
            node = node.right;
        }
    }
}
```
## Partition
### [Move Zeroes](https://leetcode.com/problems/move-zeroes/description/)
```
class Solution {
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length == 0) {
            return;
        }
        int index = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                swap(nums, index++, i);
            }
        }
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
## Slow and Fast Pointers
### [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/description/)
```
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}
```
### [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description/)
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        ListNode slow = head;
        ListNode fast = head.next;
        while (slow != fast) {
            if (fast == null || fast.next == null) {
                return false;
            }
            slow = slow.next;
            fast = fast.next.next;
        }
        return true;
    }
}
```
### [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)
```
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) {
            return null;
        }
        ListNode slow = head;
        ListNode fast = head.next;
        while (slow != fast) {
            if (fast == null || fast.next == null) {
                return null;
            }
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode node = head;
        while (slow.next != node) {
            node = node.next;
            slow = slow.next;
        }
        return node;
    }
}
```
## Sliding Window
### Template
```
int j = 0;
for (int i = 0; i < n; i++) {
    while (j < n && condition) {
        j++;
        update j;
    }
    update i;
}
```
### [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)
```
class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
        int minLen = Integer.MAX_VALUE;
        int sum = 0;
        int j = 0;
        for (int i = 0; i < nums.length; i++) {
            while (j < nums.length && sum < s) {
                sum += nums[j++];
            }
            if (sum >= s) {
                minLen = Math.min(minLen, j - i);
            }
            sum -= nums[i];
        }
        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }
}
```
### [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
* #1: O(2n)
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if (s == null || s.length() == 0) {
            return 0;
        }
        int maxLen = 0;
        Set<Character> set = new HashSet<>();
        int j = 0;
        for (int i = 0; i < s.length(); i++) {
            while (j < s.length() && !set.contains(s.charAt(j))) {
                set.add(s.charAt(j++));
            }
            maxLen = Math.max(maxLen, j - i);
            set.remove(s.charAt(i));
        }
        return maxLen;
    }
}
```
* #2: O(n)
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if (s == null || s.length() == 0) {
            return 0;
        }
        int maxLen = 0;
        Map<Character, Integer> map = new HashMap<>();
        for (int i = 0, j = 0; j < s.length(); j++) {
            if (map.containsKey(s.charAt(j))) {
                i = Math.max(i, map.get(s.charAt(j)));
            }
            maxLen = Math.max(maxLen, j - i + 1);
            map.put(s.charAt(j), j + 1);
        }
        return maxLen;
    }
}
```
### [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)
```
class Solution {
    public String minWindow(String s, String t) {
        Map<Character, Integer> freq = new HashMap<>();
        for (int i = 0; i < t.length(); i++) {
            char c = t.charAt(i);
            freq.put(c, freq.getOrDefault(c, 0) + 1);
        }
        int count = 0;
        int j = 0;
        int minLen = Integer.MAX_VALUE;
        String ans = "";
        char c;
        for (int i = 0; i < s.length(); i++) {
            while (j < s.length() && count < t.length()) {
                c = s.charAt(j);
                if (freq.containsKey(c)) {
                    freq.put(c, freq.get(c) - 1);
                    if (freq.get(c) >= 0) {
                        count++;
                    }
                }
                j++;
            }
            if (count == t.length() && j - i < minLen) {
                minLen = j - i;
                ans = s.substring(i, j);
            }
            c = s.charAt(i);
            if (freq.containsKey(c)) {
                freq.put(c, freq.get(c) + 1);
                if (freq.get(c) > 0) {
                    count--;
                }
            }
        }
        return ans;
    }
}
```
### [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/description/)
```
class Solution {
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
        if (s == null || s.length() == 0 || k < 1) {
            return 0;
        }
        Map<Character, Integer> freq = new HashMap<>();
        int j = 0;
        int maxLen = 0;
        char c;
        for (int i = 0; i < s.length(); i++) {
            while (j < s.length() && freq.size() <= k) {
                c = s.charAt(j);
                if (freq.containsKey(c)) {
                    freq.put(c, freq.get(c) + 1);
                } else if (freq.size() == k) {
                    break;
                } else {
                    freq.put(c, 1);
                }
                j++;
            }
            maxLen = Math.max(maxLen, j - i);
            c = s.charAt(i);
            if (freq.get(c) == 1) {
                freq.remove(c);
            } else {
                freq.put(c, freq.get(c) - 1);
            }
        }
        return maxLen;
    }
}
```
### [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)
```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode left = dummy;
        ListNode right = dummy;
        for (int i = 0; i < n + 1; i++) {
            if (right == null) {
                return head;
            }
            right = right.next;
        }
        while (right != null) {
            left = left.next;
            right = right.next;
        }
        left.next = left.next.next;
        return dummy.next;
    }
}
```
