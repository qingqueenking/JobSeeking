# Dynamic Programming

## **Coordinate** ```dp[n]```
### Climbing Stairs
```
dp[i] = dp[i - 1] + dp[i - 2];
```

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

## **2D Coordinate** ```dp[m][n]```
### Unique Path
```
dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
```
### Minimum Path Sum
```
dp[i][j] = Math.min(dp[i - 1][j], dp[i][j - 1]) + grid[i][j];
```
### Maximal Square
```
if (matrix[i][j] == '1') {
    dp[i][j] = Math.min(dp[i - 1][j - 1], Math.min(dp[i - 1][j], dp[i][j - 1])) + 1;
    maxLen = Math.max(maxLen, dp[i][j]);
}
```
### Dungeon Game
```
dp[i][j] = Math.min(Math.max(1, dp[i + 1][j] - dungeon[i][j]),
                    Math.max(1, dp[i][j + 1] - dungeon[i][j]));
```

## **Range** ```dp[m][n]```
### Longest Palindromic Substring
* Greedy: expand around center
```
dp[i][j] = dp[i + 1][j - 1] && s.charAt(i) == s.charAt(j);
```
### Burst Balloons
```
for (int k = i; k <= j; k++) {
    int coin = (i - 1 >= 0 ? nums[i - 1] : 1) *  nums[k] * (j + 1 < n ? nums[j + 1] : 1);
    dp[i][j] = Math.max(dp[i][j], (k - 1 >= 0 ? dp[i][k - 1] : 0) + (k + 1 < n ? dp[k + 1][j] : 0) + coin);
}
```
### Scramble String
```
```

## **Range and Game** ```dp[m][n]```
### Guess Number Higher or Lower II
```
dp[i][j] = Integer.MAX_VALUE;
for (int k = i + 1; k < j; k++) {
    dp[i][j] = Math.min(dp[i][j], Math.max(dp[i][k - 1], dp[k + 1][j]) + k);
}
```
### Predict the Winner / Stone Game
```
dp[i][j] = Math.max(sum - dp[i + 1][j], sum - dp[i][j - 1]);
```

## **Game** ```dp[m][n]```
### Coins in a line

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
### Edit Distance
```
dp[i][j] = Math.min(dp[i][j - 1] + 1, dp[i - 1][j] + 1);
if (word1.charAt(i - 1) == word2.charAt(j - 1)) {
    dp[i][j] = Math.min(dp[i][j], dp[i - 1][j - 1]);
} else {
    dp[i][j] = Math.min(dp[i][j], dp[i - 1][j - 1] + 1);
}
```
### Longest Common Subsequence
### Interleaving String

## **Backpack** ```dp[m + 1][n + 1]```
### Backpack
```
dp[i][j] = dp[i - 1][j];
dp[i][j] |= (j >= A[i - 1]) && dp[i - 1][j - A[i - 1]];
```
### Backpack II
```
dp[i][j] = dp[i - 1][j];
if (j >= A[i - 1]) {
    dp[i][j] = Math.max(dp[i][j], dp[i][j - A[i - 1]] + V[i - 1]);
}
```
### Backpack III
```
dp[i][j] = dp[i - 1][j];
if (j >= A[i - 1]) {
    int times = j / A[i - 1];
    for (int k = 1; k <= times && !dp[i][j]; k++) {
        dp[i][j] |= dp[i - 1][j - k * A[i - 1]];
    }
}
```

## **Greedy**
### Longest Valid Parentheses
* Stack
* left, right
### Maximal Rectangle
* Stack
### Maximum Subarray
* sum, minSum, maxSum
* sum, maxSum
### Best Time to Buy and Sell Stocks
* minPrice, maxPrice
