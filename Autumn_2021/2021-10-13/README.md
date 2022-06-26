# Week Long Kattis Practice #5 Solutions
[Kattis Link](https://open.kattis.com/contests/e6sahj/standings)

[Russell Zhu's Solutions](https://github.com/zhur123/Competitive-Programming/tree/main/Kattis%20Practice%2010-13-2021)

[Chenzhang Hu's Solutions](https://github.com/buckeye-cn/ACM_ICPC_Materials/tree/master/solutions/kattis):
---
A
- Do some modulo calculation. 
- Be careful that a month can have < 13 days.

B
- Count the number of problems that you have the same answer. Let it be x.
- Match x with k, and n - x with n - k.

C
- Map the letter at position i to pre-calculated numbers a[i], b[i], c[i] if the letter is A, B, C.
- Make a[i] and b[i] random. Make c[i] = a[i] ^ b[i].
- In each string, xor all the mapped numbers of letters. Let them be h1, h2, and h3.
- If the three strings match, h1 ^ h2 ^ h3 should be 0, because a[i], b[i], c[i] (for each i) cancel each other in the xor result.
- So, you can check each rotation in O(1).
- There are n^2 possible ways to rotate. Handle symmetric cases carefully.

Another solution:
- For each rotation of the first two strings, calculate the expected third string s*.
- Duplicate the third string and search s* in it.

D
- For each circle, find the begin and end angle of its intersections with circles above it.
- Consider each circle as a number axis from -PI to PI. Sort the angles.
- Sweep from -PI to PI, find the segments with no intersection.
- If the begin angle of a intersection is larger than the end angle, handle the overflow carefully.

E
- Yes, it is Eight Queens.

F
- It is binary search.
- Test IO carefully.

G
- Build a tree structure and do a buttom-up recursion.
- During recursion, calculate the best result from two cases: the current person has been chosen or not.
- The underlying idea is DP.

H
- If |ax - bx| is small, use the arc min(ay, by).
- Otherwise, go to the center point.
- Choose the shorter one from them.

I
- It toggles a "+" pattern of 5 cells.
- Scan from top to bottom and from left to right.
- Think each cell as the top cell of "+" and toggle it.

J
- It is similar to problem D.
- Move the radius of boar to each tree. It will not affect the result.
- For each tree, find the range of angle which the boar will hit the tree's circle.
- The range comes from either the tangent lines or the intersection points of the tree's circle with the circle of the boar's distance.
- Again, sort the angles, sweep from -PI to PI, and sum up the segments.

K
- Simply use a hash table.

L
- Sort the course requests by (course, name).
- Do a linear scan to count unique names.

M
- Calculate the distance between the book and each candle.

N
- For those books which stay on the same shelf, it is about finding the minimal insertions to sort them.
- Find the sequence of those books and find the longest increasing subsequence using DP.
- The non-increasing part requires one lift per each.
- For those books which should go to another shelf, it always requires one lift.
- If a shelf has no space but requires some action, it may use a space from some other shelf.
- Merge shelfs which a book move from and to into groups using union-find with path compression.
- If there is no space in this group, it takes one extra lift.
- Do not forget to handle a special case which there is no space at all.

O
- Do a memorized search on n by removing the last digit.
- If n < b, the first and only digit is n.
- Otherwise, try each posible digit from ceil(sqrt(b)) to b - 1.
- Check numeric overflow carefully.