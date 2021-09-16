# Array_reduction
This is problem statement of Atlassian women in tech event .

ARRAY REDUCTION-
There is an array of n integers called num. The array can be reduced by 1 element by performing a move. Each move consists of the following three steps:
1.Pick two different elements num[i] and num[j], i # j
2.Remove the two selected elements from the array
3.Add the sum of the two selected elements to the end of the array.
Each move has a cost associated with it : the sum of the two elements removed from the array during the move. Calculate the minimum total cost of reducing the array to one element.

Example-
num = [4,6,8]
 Remove 4 and 6 in the first move at a cost of 4+6 = 10  , and the resultant array is num’ = [8,10]. Remove 8 and 10 in the second move at a cost of 8+10 = 18  , and the resultant array is num” =[18].
The total cost of reducing  this array to one element using the sequence of moves is 10 + 18= 28 . This is just one set of possible moves. For instance, one could have started with 4 and 8  . Then 4+8 = 12 ,num’=[6,12], 6+12=18 ,num”= 18  cost = 12+18=30.
FUNCTION DESCRIPTION-
Complete the function reductionCost in the editor below
reductionCost has the following parameter
int num[n] an array of integer.
Return
The minimum total cost of reducing the input array to one element.

CONSTRAINTS:
2<=num<=10^4
0<=num[i]<=10^5

Input format for custom testing:
Sample input1:
N= 3(size of array)
num = [1,2,3]
Sample output1:
9
Explanation 1:
Make the following moves to reduce the num = [1,2,3] 
•	Remove 1 and 2 to cost = 1+2 = 3 resulting array num = [3,3]
•	Remove 3 and 3 to cost = 3+3 = 6 resulting array num = [6]
•	Sum up the Cost of each reduction= 3+6 = 9

Sample input2:
N= 4(size of array)
num = [1,2,3,4]
Sample output1:
19
Explanation 2:
Make the following moves to reduce the num=[1,2,3,4] 
•	Remove 1 and 2 to cost = 1+2 = 3 resulting array num = [3,4,3]
•	Remove 3 and 3 to cost = 3+3 = 6 resulting array num = [6,4]
•	Remove 6 and 4  to cost = 6+4 = 10 resulting array num = [10]
•	Sum up the Cost of each reduction= 3+6+10= 19


CODE-

# The function accepts an integer array
# The function returns an integer

def reductionCost(num):
    
    # An empty list
    Cost = [ ]
    
    # while length of array num greater than 1
    while len(num) > 1:
        num.sort()            # Sorting an array num
        sm = num[0]+num[1]    # adding first two values(two minimum values) of sorted array to find minimum cost
        
        # remove two minimum elements and append minimum cost
        num = num[2:] 
        num.append(sm)
        
        #add cost of each reduction to list Cost
        Cost.append(sm)
        
    # return •	Sum up the Cost of each reduction.
    return sum(Cost)
        
if __name__ == '__main__':
    N = int(input())
    num = list(map(int,input().strip().split()))
    mincost = reductionCost(num)
    print(mincost)
    
Input:
4
1 2 3 4

Output:
19
