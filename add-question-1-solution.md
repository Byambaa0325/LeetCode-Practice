The problem can be minimized to reducing N to 1 in minimum number of moves. 

The first insight needed to solve this problem is picking out necessary moves. We have four options:
- Go up or down using elevator at even numbered floors.
- Go up or down using stairs from any floors.

However, the key moves are:
- Go up one floor using stairs
- Go down one floor using stairs
- Go half the floor using elevator
We don't need to use elevator to go up but it is essential to go up using stairs on odd numbered floors. Another intuition is to go down always either with stairs or elevator. But example of N = 23, shows going up one floor to take elevator results in better solution.

With this we can formulate brute force recursive solution.

```
If even:
  use elevator
else if odd:
  minimum of try down and up
```

https://leetcode.com/playground/VXSGS6gL

Time Complexity : approximately O(NlogN)

This solution works and can even be optimized with memoization.

https://leetcode.com/playground/e76AzZu6

Time Complexity : approximately O(NlogN)

Memory Complexity: O(N) memory up to N

The second insight is to realize elevator is our best friend, and we need to be greedy about it. The elevator ensures optimality. By this logic we can build the solution from the first floor and up.
The solution building logic is as follows:

```
if i is known aka optimal:
  any i*(2^k) numbers for any k is optimal with value (i's optimal value + k)
  calculate until it passes horizon N+1
if i is not known:
  i's optimal value = min( i-1's optimal value, i+1's optimal value) + 1
```

Therefore the job is to build solutions from 1 to N for all numbers. It is guaranteed to find optimal solutions for all the numbers as following proof:

```
if N is even: 
  N can be divided by two k times until it hits some odd base i
  if i == 1:
    i's optimal value  = 0
  else:
    find i's optimal value recursively
  N's optimal value = i's optimal value + k
if N is odd:
  it has two even neighbors that it can reach in 1 move, and they are known as 
  neighbor's odd bases<N. We are bound to have hit the bases before reaching N
  N's optimal value = minimum neighbor's value + 1 move to reach it
```

https://leetcode.com/playground/evFHayhy

Time Complexity: O(N) as we assume to hit every number once up to N

Memory Complexity: O(N) memory up to N

Lastly, the trick of the question is its constraint size. We are unable to use any brute-force or dynamic programming solution since 10^39 is too big for RAM to fit. In this nature the problem can almost be divided to two test set cases where full constraint case is hard.

However, we have two insights that we really need to solve this question optimally. The further insight is we only need to pay attention to which number is divided by the two the most. When N is odd, until now, we branched to N+1 and N-1; now, from N+1 and N-1, we branch to whichever can be divided by the two the most. This can be further seen as we convert N to binary number. We are interested in whichever neighbor has the most trailing zeros. 

This is further reinforced by the insight we had during tabular solution. We assume whichever even neighbor that has lower odd base i has lower optimal value. In a nutshell, we are being greedy about whichever neighbor has lower odd base.

https://leetcode.com/playground/6sV4ABR5

By this solution: 
Time complexity: O(logN)


