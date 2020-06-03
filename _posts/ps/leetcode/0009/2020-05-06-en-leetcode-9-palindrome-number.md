---
layout: post
title: "9. Palindrome Number"
ref: leetcode-9
date: 2020-05-06 01:15:00 +0900
categories: LeetCode
lang: en
---

## Problem
- **Difficulty**: Easy
- **Related Topic**: Implement

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Follow up:
Coud you solve it without converting the integer to a string?

[LeetCode](https://leetcode.com/problems/palindrome-number/)

<div class="divider"></div>

## Code

- Runtime: 48 ms, faster than 89.84%
- Memory Usage: 9.3 MB, less than 100.00%

```rb
def is_palindrome(x)
  x = x.to_s
  x.reverse == x
end
```

- Without converting to a string
- Runtime: 40ms, faster than 98.35%
- Memory: 9.2 MB, less than 100.00%

```rb
def is_palindrome(x)
    return false if x < 0 or (x%10==0 and x!=0)
    rev = 0
    temp = x
    while temp > 0
        rev = rev*10 + temp%10
        temp /= 10
    end
    rev == x
end
```
<div class="divider"></div>

## Complextiy
### With a string
`String#reverse` takes linear time (n/2 to be specific) so the time complexity is O(n).
The space complexity is constant.

### Without a string
`while` loop depends on the length of `x`, so the time complexity is O(S), where `S = length of x`.
The space complexity is also constant.