# Dynamic Programming

## **Sequence** ```dp[n + 1]```
### House Robber
```
dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i - 1]);
```
### Decode Ways
```
if (s.charAt(i - 1) != 0) {
    dp[i] = dp[i - 1];
}
int twoDigits = (s.charAt(i - 2) - '0') * 10 + (s.charAt(i - 1) - '0');
if (10 <= twoDigits && twoDigits <= 26) {
    dp[i] += dp[i - 2];
}
```

## **Chain** ```dp[n]```
### Longest Increasing Subsequence
```
for (int j = 0; j < i; j++) {
    if (nums[j] < nums[i]) {
        dp[i] = Math.max(dp[i], dp[j] + 1);
    }
    maxLen = Math.max(maxLen, dp[i]);
}
```

## **Coordinate** ```dp[n]```

## **2D Coordinate** ```dp[m][n]```
### Dungeon Game
```
dp[i][j] = Math.min(Math.max(1, dp[i + 1][j] - dungeon[i][j]),
                    Math.max(1, dp[i][j + 1] - dungeon[i][j]));
```

## **Range** ```dp[m][n]```
### Longest Palindromic Substring
```
dp[i][j] = dp[i + 1][j - 1] && s.charAt(i) == s.charAt(j);
```
* Greedy: expand around center

## **Matching** ```dp[m + 1][n + 1]```
### Regular Expression Matching
```
if (s.charAt(i - 1) == p.charAt(j - 1) || p.charAt(j - 1) == '.') {
    dp[i][j] = dp[i - 1][j - 1];
} else if (p.charAt(j - 1) == '*' && j >= 2) {
    dp[i][j] = dp[i][j - 2];
    if (s.charAt(i - 1) == p.charAt(j - 2) || p.charAt(j - 2) == '.') {
        dp[i][j] |= dp[i - 1][j];
    }
}
```
### Wildcard Matching
```
if (s.charAt(i - 1) == p.charAt(j - 1) || p.charAt(j - 1) == '?') {
    dp[i][j] = dp[i - 1][j - 1];
} else if (p.charAt(j - 1) == '*') {
    dp[i][j] = dp[i][j - 1] || dp[i - 1][j];
}
```

## **Greedy**
### Longest Valid Parentheses
* Stack
* left, right
### Maximum Subarray
* sum, minSum, maxSum
* sum, maxSum
### Best Time to Buy and Sell Stocks
* minPrice, maxPrice
