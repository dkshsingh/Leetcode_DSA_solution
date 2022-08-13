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
          # def __init__(self, val=0, left=None, right=None):
          # self.val = val
          # self.left = left
          # self.right = right
          class Solution:
             def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
                 if root: root.left,root.right = self.invertTree(root.right),self.invertTree(root.left)
                 return root
### 14. Search in a binary search tree
<img width="305" alt="j" src="https://user-images.githubusercontent.com/78050476/184419954-e4d7dadd-24be-4b8e-a1f4-4a1d9f88b057.png">

### code:
          # Definition for a binary tree node.
          # class TreeNode:
          # def __init__(self, val=0, left=None, right=None):
          # self.val = val
          # self.left = left
          # self.right = right
         class Solution:
             def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
                def searchUtil(node: Optional[TreeNode]) -> Optional[TreeNode]:
                  if not node:
                      return None
                  if node.val == val:
                      return node
                  elif val < node.val:
                      return searchUtil(node.left)
                  elif val > node.val:
                      return searchUtil(node.right)
                  return searchUtil(root)
                  
### 15. Maximum depth of binary search tree(C++ solution)
<img width="302" alt="g" src="https://user-images.githubusercontent.com/78050476/184422714-ae0db892-d152-4b0d-ba48-e07e686ffa5a.png">

    II.  Input: root = [1,null,2]
         Output: 2

### Code: (C++)
          /**
          * Definition for a binary tree node.
          * struct TreeNode {
          *     int val;
          *     TreeNode *left;
          *     TreeNode *right;
          *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
          *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
          *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
          * };
          */
          class Solution {
          public:
              int maxDepth(TreeNode* root) {
                  if(root == NULL)
                      return 0;
        
             return 1 + max(maxDepth(root->left), maxDepth(root->right));
        
          }
        };

### 16.Symmetric tree
<img width="294" alt="s" src="https://user-images.githubusercontent.com/78050476/184423617-0a175abe-c1ab-4dd9-99a0-6a2dc9bcf1b5.png">

### Code:
         # Definition for a binary tree node.
         # class TreeNode:
         # def __init__(self, val=0, left=None, right=None):
         # self.val = val
         # self.left = left
         # self.right = right
         class Solution:
         def isSymmetric(self, root: Optional[TreeNode]) -> bool:
             return self.is_mirror(root, root)

        def is_mirror(self, root_one, root_two):
            if not root_one and not root_two:
                return True

            if not root_one or not root_two:
                return False

        out_nodes = self.is_mirror(root_one.right, root_two.left)
        in_nodes = self.is_mirror(root_one.left, root_two.right)
        equal_values = root_one.val == root_two.val

        return out_nodes and in_nodes and equal_values
### 17. Validate binary tree 
<img width="302" alt="d" src="https://user-images.githubusercontent.com/78050476/184502648-62b8051f-0338-4756-aad1-800954948718.png">

      II. Input: root = [5,1,4,null,null,3,6]
          Output: false
          Explanation: The root node's value is 5 but its right child's value is 4.
    
### Code:
         # Definition for a binary tree node.
         # class TreeNode:
         # def __init__(self, val=0, left=None, right=None):
         # self.val = val
         # self.left = left
         # self.right = right
         class Solution:
             def isValidBST(self, root: Optional[TreeNode]) -> bool:
                 output = []
                 self.inOrder(root, output)
        
            for i in range(1, len(output)):
                if output[i-1] >= output[i]:
                    return False

            return True

            def inOrder(self, root, output):
                if root is None:
                    return
        
            self.inOrder(root.left, output)
            output.append(root.val)
            self.inOrder(root.right, output)

### 18. Insert in to a binary search tree
<img width="249" alt="f" src="https://user-images.githubusercontent.com/78050476/184502819-a31fed47-2b53-43ea-8ec9-ad5b19528fa0.png">
      
      II. Input: root = [40,20,60,10,30,50,70], val = 25
          Output: [40,20,60,10,30,50,70,null,null,25]
### Code:
        # Definition for a binary tree node.
        # class TreeNode:
        # def __init__(self, val=0, left=None, right=None):
        # self.val = val
        # self.left = left
        # self.right = right
        class Solution:
            def insertIntoBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
                if(root == None):
                    return TreeNode(val);
                if(root.val < val): root.right = self.insertIntoBST(root.right, val);
                else:
                    root.left = self.insertIntoBST(root.left, val);
                return(root)









