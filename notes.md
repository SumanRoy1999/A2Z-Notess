Step 3 : Solve Problems on Arrays [Hard]
Q:1:-Program to generate Pascal's Triangle

Problem Statement: This problem has 3 variations. They are stated below:

Variation 1: Given row number r and column number c. Print the element at position (r, c) in Pascal’s triangle.

Variation 2: Given the row number n. Print the n-th row of Pascal’s triangle.

Variation 3: Given the number of rows n. Print the first n rows of Pascal’s triangle.

In Pascal’s triangle, each number is the sum of the two numbers directly above it as shown in the figure below:

![Alt text](Images/image.png)

Variation 1

In this case, we are given the row number r and the column number c, and we need to find out the element at position (r,c). 

Naive Approach
In this case, we are given the row number r and the column number c, and we need to find out the element at position (r,c). 

One of the Naive approaches is to generate the entire Pascal triangle and then find the element at position (r,c). We will discuss in variation 3 how to generate Pascal’s triangle.

We have an easier formula to find out the element i.e. r-1Cc-1. Let’s try to analyze the formula to find the value of the combination assuming r-1 as n and c-1 as r:

nCr = n! / (r! * (n-r)!)
Calculating the value of nCr:

Naive Approach: 

We can separately calculate n!, r!, (n-r)! and using their values we can calculate nCr. This is an extremely naive way to calculate. The time complexity will be O(n)+O(r)+O(n-r).

Optimal Approach
Algorithm / Intuition
We can optimize this calculation by the following observation. 
Assume, given r = 7, c = 4. 
Now, n = r-1 = 7-1 = 6 and r = c-1 = 4-1 = 3
Let’s calculate 6C3 = 6! / (3! *(6-3)!) = (6*5*4*3*2*1) / ((3*2*1)*(3*2*1))
This will boil down to (6*5*4) / (3*2*1)
So, nCr = (n*(n-1)*(n-2)*.....*(n-r+1)) / (r*(r-1)*(r-2)*....1)
                                
Now, we will use this optimized formula to calculate the value of nCr. But while implementing this into code we will take the denominator in the forward direction like: 

(n / 1)*((n-1) / 2)*.....*((n-r+1) / r).
The code will be like the following:


Approach:
The steps are as follows:

First, we will consider r-1 as n and c-1 as r.
After that, we will simply calculate the value of the combination using a loop. 
The loop will run from 0 to r. And in each iteration, we will multiply (n-i) with the result and divide the result by (i+1).
Finally, the calculated value of the combination will be our answer.
