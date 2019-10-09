# Kadane-s_algo

In computer science, the maximum subarray problem is the task of finding a contiguous subarray with the largest sum, within a given one-dimensional array A[1...n] of numbers. Formally, the task is to find indices {\displaystyle i}i and {\displaystyle j}j with {\displaystyle 1\leq i\leq j\leq n}{\displaystyle 1\leq i\leq j\leq n}, such that the sum

{\displaystyle \sum _{x=i}^{j}A[x]}{\displaystyle \sum _{x=i}^{j}A[x]}
is as large as possible. (Some formulations of the problem also allow the empty subarray to be considered; by convention, the sum of all values of the empty subarray is zero.) Each number in the input array A could be positive, negative, or zero.

For example, for the array of values [−2, 1, −3, 4, −1, 2, 1, −5, 4], the contiguous subarray with the largest sum is [4, −1, 2, 1], with sum 6.

Some properties of this problem are:

If the array contains all non-negative numbers, then the problem is trivial; the maximum subarray is the entire array.
If the array contains all non-positive numbers, then the solution is the number in the array with the smallest absolute value (or the empty subarray, if it is permitted).
Several different sub-arrays may have the same maximum sum.
This problem can be solved using several different algorithmic techniques, including brute force, divide and conquer, dynamic programming, and reduction to shortest paths.

Kadane's algorithm scans the given array {\displaystyle A[1...n]}{\displaystyle A[1...n]} from left to right. In the {\displaystyle j}jth step, it computes the subarray with the largest sum ending at {\displaystyle j}j; this sum is maintained in variable current_sum.[9] Moreover, it computes the subarray with the largest sum anywhere in {\displaystyle A[1...j]}{\displaystyle A[1...j]}, maintained in variable best_sum,[10] and easily obtained as the maximum of all values of current_sum seen so far, cf. line 6 of the algorithm.

As a loop invariant, in the {\displaystyle j}jth step, the old value of current_sum holds the maximum over all {\displaystyle i\in \{1,...,j\}}{\displaystyle i\in \{1,...,j\}} of the sum {\displaystyle A[i]+...+A[j-1]}{\displaystyle A[i]+...+A[j-1]}.[11] Therefore, current_sum{\displaystyle +A[j]}{\displaystyle +A[j]}[12] is the maximum over all {\displaystyle i\in \{1,...,j\}}{\displaystyle i\in \{1,...,j\}} of the sum {\displaystyle A[i]+...+A[j]}{\displaystyle A[i]+...+A[j]}. To extend the latter maximum to cover also the case {\displaystyle i=j+1}{\displaystyle i=j+1}, it is sufficient to consider also the empty subarray {\displaystyle A[j+1\;...\;j]}{\displaystyle A[j+1\;...\;j]}. This is done in line 5 by assigning {\displaystyle \max(0,}{\displaystyle \max(0,}current_sum{\displaystyle +A[j])}{\displaystyle +A[j])} as the new value of current_sum, which after that holds the maximum over all {\displaystyle i\in \{1,...,j+1\}}{\displaystyle i\in \{1,...,j+1\}} of the sum {\displaystyle A[i]+...+A[j]}{\displaystyle A[i]+...+A[j]}.
