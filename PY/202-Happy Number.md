# Problem:
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.

 

Example 1:

Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
Example 2:

Input: n = 2
Output: false
 

Constraints:

1 <= n <= 231 - 1



# ----------------------------------------------------------
# ✅ Approach 1: Brute Force
# ----------------------------------------------------------
# Idea:

if N == 1: return True [Happy Number]
if N repeats itself (that means there's a cycle not ending in 1): return False [Not Happy Number]
keep a record of N (in a seen set)
update N to sum of square of digits


# Soln 1
# Time Complexity : O(log n)
# Space Complexity: O(1)

class Solution:

    def getSumSquare(self, no):
        sum = 0
        while(no > 0):
            digit = no%10
            sum+= digit*digit
            no = no//10
        return sum


    def isHappy(self, n: int) -> bool:
        if n == 1:
            return True
        sum_set = set()

        while(True):
            sum = self.getSumSquare(n)
            if sum == 1:
                return True
            elif sum in sum_set:
                return False
            else:
                sum_set.add(sum)
                n = sum
                


# Soln 2
# Time Complexity : O(log n)
# Space Complexity: O(1)

class Solution:
    def getSumSquare(self, n):
        total = 0
        while n > 0:
            digit = n % 10
            total += digit * digit
            n = n // 10
        return total

    def isHappy(self, n: int) -> bool:
        slow = n
        fast = self.getSumSquare(n)
        while fast != 1 and slow != fast:
            slow = self.getSumSquare(slow)
            fast = self.getSumSquare(self.getSumSquare(fast))
        return fast == 1

        

        

        