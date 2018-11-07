# Sliding Window Template
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
## [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)
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
## [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
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
## [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)
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
## [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/description/)
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
