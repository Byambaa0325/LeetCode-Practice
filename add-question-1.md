You wake up at the `Nth` floor of the mysterious building. You find the elevator in an attempt to get out of the building. However, the elevator has a warning saying it was programmed incorrectly, and it can only be used in following way:

- This elevator only works on floors with an even number.
- This elevator only goes to floors with the half or the double of its floor's number.
- In case you are unable to use the elevator, use the stairs.

Your goal is to get to floor number 1. Note the mysterious building has floors numbered from 1 to 10^39.

Given `N`, the number of the floor you wake up, return the minimum number of moves required to get down to floor 1. A move is defined by:

- Using the elevator once. For example, going from floor 8 to 2 using elevator is counted as 2 moves as the elevator is used in a way `8 -> 4 -> 2`.
- Taking the stairs to go up or down one floor. For example, going from floor 8 to 2 using stairs is counted as 6 moves as `8 -> 7 -> 6 -> 5 -> 4 -> 3 -> 2`.

**Example 1:**

```
Input: Given N = 23
Output: The minimum number of moves required to go down to floor 1 is 6
Path:
23 -> 24, using the stairs go up one floor
24 -> 12, using the elevator
12 -> 6, using the elevator
6 -> 3, using the elevator
3 -> 2, using the stairs go down one floor
2 -> 1, using the stairs go down one floor
```

**Example 2:**

```
Input: Given N = 17
Output: The minimum number of moves required to go down to floor 1 is 5
Path:
17 -> 16, using the stairs go up down floor
16 -> 8, using the elevator
8 -> 4, using the elevator
4 -> 2, using the elevator
2 -> 1, using the stairs go down one floor
```

[solution](add-question-1-solution)
