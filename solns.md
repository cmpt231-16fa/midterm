---
layout: page
title: "HW1 Solns: CMPT231"
subtitle: "Lecture 1, ch1-3"
ext-js: "https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=AM_CHTML"
---

### HW1 Solutions (20pts)

+ (1) *(4pts)* Demonstrate **insertion sort**:

  | in  | 35 | 50 | 44 | 61 | 17 | 75 | 23 |  9 |
  |-----|----|----|----|----|----|----|----|----|
  | j=2 | 35 | 50 | 44 | 61 | 17 | 75 | 23 |  9 |
  | j=3 | 35 | 44 | 50 | 61 | 17 | 75 | 23 |  9 |
  | j=4 | 35 | 44 | 50 | 61 | 17 | 75 | 23 |  9 |
  | j=5 | 17 | 35 | 44 | 50 | 61 | 75 | 23 |  9 |
  | j=6 | 17 | 35 | 44 | 50 | 61 | 75 | 23 |  9 |
  | j=7 | 17 | 23 | 35 | 44 | 50 | 61 | 75 |  9 |
  | j=8 |  9 | 17 | 23 | 35 | 44 | 50 | 61 | 75 |

+ (2) *(4pts)* **Prove**: \` n^3 (2 + sin(n pi / 8)) + n^2 in Theta( n^3 ) \`

  The key observation is that `|sin|` &le; 1. <br/>
  So the first term is bounded by \` n^3 \` and \` 3n^3 \`. <br/>
  As for the second term, beyond \` n_0 \` = 1, we always have \` n^2 <= n^3 \`. <br/>
  So, for example, we can choose \` c_1 = 1, c_2 = 4, n_0 = 1 \`. <br/>
  The **lower bound** is shown by:

  \` c_1 n^3 = n^3 <= n^3 + n^2 <= n^3 (2 + sin(n pi/8)) + n^2 \`

  The **upper bound** is shown by:

  \` n^3 (2 + sin(n pi/8)) + n^2 <= 3n^3 + n^2 <= 4n^3 = c_2 n^3 \`

+ (3) a. *(3pts)* **running time** T(n):

  The function calculates the n-th Fibonacci number, but its running time
  (and number of recursive function calls) is also the n-th Fibonacci number.
  Fib(n) is roughly equal to \`phi^n\`, thus \`T(n) = Theta(phi^n)\`.

  + b. *(1pt)* Is this function **polynomial** time, **exponential** time, or other?

    **Exponential** time.

  + c. *(1pts)* **Re-write** this function to run in O(1) time.
    You can use pseudocode, Python, whatever you like.

            def fib(n):
              phi = 1.61803...
              return phi ** n		# or pow(phi, n), etc.

+ (4) a. *(2pts)* how many **hand shakes**?

  \` (n(n+1))/2 \`

  + b. *(1pt)* Express (a) in &Theta; **asymptotic** notation.
    Is this linear, quadratic, exponential, or other?

    \` Theta(n^2) \`, quadratic

  + c. *(3pt)* Discuss how you might **design** such a function,
    and what its asymptotic **running time** would be.
    Is it linear, quadratic, exponential, or other?

    Simple solution is a doubly-nested loop:
    T(n) = &Theta;( n \* (avg num of friends) ).
    With the info given, T(n) = &Theta;(190n) = &Theta;(n), linear time.

            def oldest_friend(n):
              for u in input_users:
                oldest_friend[u] = null
                oldest_duration = 0
                for f in friends(u):
                  duration = friendship_duration(u, f)
                  if duration > oldest_duration:
                    oldest_duration = duration
                    oldest_friend[u] = f
              return oldest_friend

  + d. *(1pt)* What's **different**?

    The big difference is the **sparsity** of the friend graph:
    in the hand-shaking situation, you need to loop over **all** n-1
    other people in the group.

    In the Facebook situation, you only need to loop over your friends.
    We assume the number of friends does not scale with n, so it's
    treated as a constant, not affecting the asymptotic complexity.

