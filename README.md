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

                

              
