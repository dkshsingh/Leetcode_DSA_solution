# Leetcode_DSA_solution_python

### In computer science, a data structure is a way to store and organize data.
## Array
### 1. Contains Duplicate
      I. input: nums=[1,2,3,1]                   II. input: nums=[1,2,3,4]
         output: true                                output: false
####  Code:
     def containsDuplicate(self, nums: List[int]) -> bool:
        numsSet =  set(nums)
        if len(nums) == len(numsSet):
            return False
        return True 
        
### 2. Two Sum
       I. Input: nums = [2,7,11,15], target = 9                                      II. Input: nums = [3,2,4], target = 6
          Output: [0,1]                                                                   Output: [1,2]
          Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].



#### Code:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                sum = nums[i] + nums[j]
                if sum == target:
                    return[i,j]
        
### 3. Merge sorted array
      I.  Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3                                   II. Input: nums1 = [0], m = 0, nums2 = [1], n = 1
          Output: [1,2,2,3,5,6]                                                                          Output: [1]
          Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
          The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
     
     
#### Code:
      def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
          nums1[:] = sorted(nums1[:m] + nums2[:n])
          
### 4. Intersection of two Arrays II
       Example:
       I. input:  nums1 = [1,2,2,1], nums2 = [2,2]
          Output: [2,2]

#### Code:
     def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        output = []
        for x in nums1:
            if x in nums2:
                output.append(x)
                nums2.remove(x)
        return output
        
### 5. Best time to buy and sell stock
     Example:
     Input: prices = [7,1,5,3,6,4]
     Output: 5
     Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6),   profit = 6-1 = 5.
     Note that buying on day 2 and selling on day 1 is not allowed because  you must buy before you sell.
     
#### Code:
     def maxProfit(self, prices: List[int]) -> int:
        n=len(prices)
        if n<=1:
            return 0
        maxprofit=0
        low=prices[0]
        for i in range(1,n):
            low=min(low,prices[i])
            maxprofit=max(maxprofit, prices[i]-low)
        return maxprofit

### 6. Pascal's Triangle
<img width="229" alt="l" src="https://user-images.githubusercontent.com/78050476/179895122-2bab9be6-ba2a-4e17-8de5-a318cdbac9ba.png">
      Input: numRows = 5
      Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

#### Code:
      def generate(self, numRows: int) -> List[List[int]]:
         res = [[1]]
        for i in range(numRows - 1):
            temp = [0]+res[-1] + [0]
            row = []
            for j in range(len(res[-1]) + 1):
                row.append(temp[j]+temp[j+1])
            res.append(row)
        return res 
        
### 7. First Unique Character in a string
      I. Input: s = "leetcode"                      II. input: s="loveleeycode"
      Output: 0                                         output:2

#### Code:
          class Solution:
          def firstUniqChar(self, s: str) -> int:
              s_dict = {}
              for i in range(len(s)):
                  try:
                     s_dict[s[i]] += 1
                  except KeyError:
                      s_dict[s[i]] = 1

               for i in range(len(s)):
                   if s_dict[s[i]] == 1:
                      return i

                return -1
                
### 8. Ransom Note
      Input: ransomNote = "a", magazine = "b"      Input: ransomNote = "aa", magazine = "aab"
      Output: false                                Output: true



#### Code:
          class Solution:
          def canConstruct(self, ransomNote: str, magazine: str) -> bool:
              m=list(magazine)
              for i in ransomNote:
                  if i in m:
                      m.remove(i)
                  else:
                      return False
              return True
### 9. Valid Anagram
       I. input: s="anagram" , t="nagram"                 II. input: s = "rat", t = "car"
          output: true                                        output: false

#### code:
          class Solution:
          def isAnagram(self, s: str, t: str) -> bool:
             if sorted(s) == sorted(t):
                 return True
             else:
                 return False
### 10. Linked list cycle
       Input: head = [3,2,0,-4], pos = 1
       Output: true
       Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

<img width="295" alt="li" src="https://user-images.githubusercontent.com/78050476/180607070-ece56c72-e90c-4b6e-8ab6-0743a9226060.png">

### code:
         # Definition for singly-linked list.
         # class ListNode:
         #     def __init__(self, x):
         #         self.val = x
         #         self.next = None

         class Solution:
         def hasCycle(self, head: Optional[ListNode]) -> bool:
             if head is None:
                 return False
             start=head
             end=head.next
             while start is not None and end is not None and end.next is not None:
                 if start==end:
                     return True
                 start=start.next
                 end=end.next.next
            return False
            
### 11. Remove linkedlist element
       Input: head = [1,2,6,3,4,5,6], val = 6
       Output: [1,2,3,4,5]
<img width="309" alt="lii" src="https://user-images.githubusercontent.com/78050476/180609532-7ee06a91-fb1b-47e0-8b9c-4dfe923f73fa.png">

#### code:
         # Definition for singly-linked list.
         # class ListNode:
         # def __init__(self, val=0, next=None):
         # self.val = val
         # self.next = next
          class Solution:
          def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
          arr = []
          newList = head
          newListHead = head
          while head != None:
               if head.val != val:            
                   arr.append(head.val)
               head = head.next  
           for i in range(len(arr)):
           newList.val = arr[i]
           if(i == len(arr) - 1):
               newList.next = None
            else:
                newList = newList.next
            if len(arr) == 0:
                newListHead = None
            return newListHead
            


### 12. Reverse Linked list
         Input: head = [1,2,3,4,5]
         Output: [5,4,3,2,1]
#### code:
          # Definition for singly-linked list.
          # class ListNode:
          # def __init__(self, val=0, next=None):
          # self.val = val
          # self.next = next
           class Solution:
           def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
               if head == None:
                   return None

               p = head
               while p.next:
               n = p.next
               p.next = n.next
               n.next = head
               head = n
            
           return head
 ### 13. Invert binary tree
 <img width="285" alt="f" src="https://user-images.githubusercontent.com/78050476/184419344-b2578410-f0c7-4e3b-a4c8-573d31223145.png">
 
 ### code:
          # Definition for a binary tree node.
          # class TreeNode:
          #     def __init__(self, val=0, left=None, right=None):
          #         self.val = val
          #         self.left = left
          #         self.right = right
          class Solution:
             def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
                 if root: root.left,root.right = self.invertTree(root.right),self.invertTree(root.left)
                 return root

