# [Online Stock Span](https://leetcode.com/problems/online-stock-span/)
```
class StockSpanner {
    Stack<int[]> stack;
    int index = 0;

    public StockSpanner() {
        stack = new Stack<int[]>();
    }

    public int next(int price) {
        while (!stack.empty() && stack.peek()[1] <= price) {
            stack.pop();
        }
        int ans = stack.empty() ? index + 1 : index - stack.peek()[0];
        stack.push(new int[] {index, price});
        index++;
        return ans;
    }
}
```
