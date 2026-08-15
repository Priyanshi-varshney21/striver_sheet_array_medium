# striver_sheet_array_medium

#TWO SUM
def twoSum(self, nums, target):
        mp={}
        for i in range(len(nums)):
            complement=target-nums[i]
            if complement in mp:
                return [mp[complement],i]
            mp[nums[i]]=i

#SORT AN ARRAY OF 0'S,1'S AND 2'S
def sortZeroOneTwo(self, nums):
        count_zero=0
        count_one=0
        count_two=0
        for n in nums:
            if n==0:
                count_zero+=1
            elif n==1:
                count_one+=1
            else:
                count_two+=1
        for i in range(count_zero):
            nums[i]=0
        for i in range(count_zero,count_zero+count_one):
            nums[i]=1
        for i in range(count_zero+count_one,len(nums)):
            nums[i]=2
        return nums


#MAJORITY ELEMENT
def majorityElement(self, nums):
        freq={}
        for num in nums:
            if num in freq:
                freq[num]+=1
            else:
                freq[num]=1
        for num in freq:
            if freq[num]>len(nums)//2:
                return num


#KADANE'S ALGORITHIM (Maximum subarray sum)
def maxSubArray(self, nums):
        max_ending=nums[0]
        max_so_far=nums[0]
        for i in range(1,len(nums)):
            max_ending=max(nums[i],max_ending+nums[i])
            max_so_far=max(max_ending,max_so_far)
        return max_so_far                

#STOCK BUY AND SELL
 def stockBuySell(self, nums, n):
        mini=nums[0]
        profit=0
        for i in range(1,n):
            mini=min(mini,nums[i])
            profit=max(profit,nums[i]-mini)
        return profit

#REARRANGE ELEMENTS BY SIGN
def rearrangeArray(self, nums):
        ans=[0]*len(nums)
        pos=0
        neg=1
        for num in nums:
            if num>0:
                ans[pos]=num
                pos+=2
            else:
                ans[neg]=num
                neg+=2
        return ans

#LEADERS IN AN ARRAY
def leaders(self, nums):
        max_right=nums[-1]
        leaders=[]
        leaders.append(max_right)
        for i in range(len(nums)-2,-1,-1):
            if nums[i]>max_right:
                leaders.append(nums[i])
                max_right=nums[i]
        leaders.reverse()
        return leaders

#LONGEST CONSECUTIVE SEQUENCE IN AN ARRAY
def longestConsecutive(self, nums):
        s=set(nums)
        longest=0
        for num in s:
            if num-1 not in s:
                count=1
                current=num
                while current+1 in s:
                    count+=1
                    current+=1
                longest=max(longest,count)
        return longest
        

#SET MATRIX ZEROES
def setZeroes(self, matrix):
        # Your code goes here
        row=len(matrix)
        col=len(matrix[0])
        row_track=[0 for _ in range(row)]
        col_track=[0 for _ in range(col)]
        for i in range(0,row):
            for j in range(0,col):
                if matrix[i][j]==0:
                    row_track[i]=-1
                    col_track[j]=-1
        for i in range(0,row):
            for j in range(0,col):
                if row_track[i]==-1 or col_track[j]==-1:
                    matrix[i][j]=0

#ROTATE MATRIX BY 90 DEGREES
def rotateMatrix(self, matrix):
        n=len(matrix)
        for i in range(n):
            for j in range(i,n):
                matrix[i][j],matrix[j][i]=matrix[j][i],matrix[i][j]
        for i in range(n):
            matrix[i].reverse()

# SPIRAL MATRIX
res=[]
top=0
bottom=len(matrix)-1
left=0
right=len(matrix[0])-1
while left<right and top<bottom:
    #left->right
    for col in range(left,right+1):
        res.append(matrix[top][col])
    top+=1
    #top->bottom
    for row in range(top,bottom+1):
        res.append(matrix[row][right])
    right-=1
    #right->left
    if top<=bottom:
        for col in range(right,left-1,-1):
            res.append(matrix[bottom][col])
        bottom-=1
    if left<=right:
        for row in range(bottom,top-1,-1):
            res.append(matrix[row][left])
        left+=1
return res


#SUBARRAY SUM
def subarraySum(self, nums, k):
        count=0
        total=0
        freq={0:1}
        for num in nums:
            total+=num
            if total-k in freq:
                count+=freq[total-k]
            freq[total]=freq.get(total,0)+1
        return count

              
