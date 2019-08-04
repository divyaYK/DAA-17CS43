# Assignment-1: Problems and Solutions

1. Compute N2  <br />
• Given input as positive integer N, compute N2 using
addition, subtraction and comparison operation. The
operation of multiplication, division, remainder, shift left/
right etc are not permitted. The computation of N2
should be done in time complexity less than O(N), i.e.
preferably O(log N). The simple solution of adding N
times the number N itself would have time complexity of
O(N). 

2. Hanoi Towers with 2+K towers  <br />
• Implement Hanoi’s tower using more than 2+K towers to
transfer N discs from tower 1 to tower 2. The number K
(greater than 1) of additional towers should be input
parameter along with N. Compute the time complexity
(i.e. total number of disc moves). The program should
output each tower status after each move. <br />
• For example, for 4 discs, and 3 (K=1) towers, tower
status after each move should be like below <br /> <br />
['D1', 'D2', 'D3', 'D4']  <br />
[]  <br />
[]  <br />
Initial  <br /> <br />
['D2', 'D3', 'D4']  <br />
[]  <br />
['D1']  <br />
Move 1  <br /> <br />
['D3', 'D4']  <br />
['D2']  <br />
['D1']  <br />
Move 2  <br /> <br />
['D3', 'D4']  <br />
['D1', 'D2']  <br />
[]  <br />
Move 3<br />

3. Given input N, using N-bit representation, the lowest
value corresponds to all bits with value ‘0’ and highest
value corresponds to all bits with value ‘1’. Taking the
lowest value as 1, and highest value as 2N, Generate the
N sets each having 2N-1 numbers in it. The set S1
corresponds to all those values where 1st bit i.e. bit
number 0 (Least Significant bit) is set to 0, and set SN
corresponds to all those values where Nth bit (Most
Significant bit) is set to 0. For example, if N=3, three sets
would be <br />
• S1 (xx0) = 1,3,5,7  <br />
• S2 (x0x) = 1,5,2,6  <br />
• S3 (0xx) = 1,2,3,4  <br />

4. Given two inputs positive integer M and N, find all
consecutive prime numbers between M and N (inclusive
of both M and N). For example, if M=20, and N=61, then
program should output <br />
• 29,31 <br />
• 41,43 <br />
• 59,61 <br />

5. Given two input positive integers M and N, compute all
the perfect numbers between M and N (inclusive of both
M and N). A perfect number is defined as the number
which is equal to sum of all its factors other than itself.
Example for first three perfect numbers are <br />
• 6 = 1+2+3 <br />
• 28 = 1+2+4+7+14 <br />
• 496 = 1+2+4+8+16+31+62+124+248 <br />

6. Construct 2-dimentional grid(array) of size MxN
consisting of english letters (to be read from input file)
and a set of english words (to be read from another file),
identify all the english words that appear in the grid
either horizontally, vertically or diagonally,.

7. Given N number of date of births (to be read from input
file in the format YYYY-MM-DD), identify the two dates
which are closest to each other.

8. Grocery discount problem. <br />
There was an
advertisement in the paper from a grocery store
providing prices of various items. The store made an offer
that if a subscriber chooses grocery items totalling equal
to a specific value N (neither less than nor greater than),
then the subscriber will get 90% discount. A grocery item
can be picked as many times as desired. The pricelist
(item, price) is to be read from a file, the special offer
price N is another positive integer. Assume prices of all
grocery items are positive integers.

9. Given input positive integer N, list all sequences
(consisting of letters ‘H’ and ’T’) of length N, where two
’T’ does not appear together. For simplicity, consider H
corresponds to Head and T corresponds to Tail when
tossing a coin. For example, when N=3, the answer would
be <br />
• HHH, HHT, HTH, THH, THT <br />
Hint: Use recursion.

10. Dyck words: Given input positive integer N,
generate all possible dyck word i.e. a balanced
string of left and right parentheses. For example for
N=3, all possible dyck words of parentheses are <br />
((())) <br />
(()()) <br />
(())() <br />
()(()) <br />
()()() <br />
– Hint : Use Recursion

11. Given two input positive integer M and N, identify
all such positive integers between M and N
(inclusive of both), such that the number is perfectly
divisible by all of its digits. For example for number
1236, it is divisible by 1, 2, 3, and 6 and this
number qualifies. The number 1234 does not
qualify because it is perfectly divisible by 1, 2, and 3
but not by 4.

12. Given input positive integer N, construct a box
with lines depicting outline, diagonals, horizonal
and vertifical divisions. The diagram will look
slightly different from odd and even as below <br />
![boxes](image)
