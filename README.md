# Leetcode_DSA_solution

### In computer science, a data structure is a way to store and organize data.
## Array
### 1. Contains Duplicate
####  Code:
     def containsDuplicate(self, nums: List[int]) -> bool:
        numsSet =  set(nums)
        if len(nums) == len(numsSet):
            return False
        return True 
        
### 2. Two Sum
#### Code:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                sum = nums[i] + nums[j]
                if sum == target:
                    return[i,j]
        
### 3. Merge sorted array
#### Code:
      def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
          nums1[:] = sorted(nums1[:m] + nums2[:n])
