# LeetCode-Problems
##(Problem 1)144. Binary Tree Preorder Traversal
class Solution(object):
    def preorderTraversal(self, root):
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            if node.right:
                stack.append(node.right)
            if node.left:
                stack.append(node.left)
        return result
    
##(Problem 2)145 Binary Tree Postorder Traversal
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def postorderTraversal(self, root):
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            result.append(node.val)
            if node.left:
                stack.append(node.left)
            if node.right:
                stack.append(node.right)
        return result[::-1]  
    
##(Problem 3)9 Palindrome Number
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        if 0 <= x < 10:
            return True
        s = str(x)
        return s == s[::-1]
        
##(Problem 4)69 Sqrt(x)
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        if 0 <= x < 10:
            return True
        s = str(x)
        return s == s[::-1]
        
##(Problem 5)498 Diagonal Traverse
class Solution(object):
    def findDiagonalOrder(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: List[int]
        """
        if not mat or not mat[0]:
            return []
        diagonals = {}
        m, n = len(mat), len(mat[0])
        for i in range(m):
            for j in range(n):
                if i + j not in diagonals:
                    diagonals[i + j] = []
                diagonals[i + j].append(mat[i][j])
        result = []
        for k in range(m + n - 1):
            if k % 2 == 0:  
                result.extend(diagonals[k][::-1])
            else:
                result.extend(diagonals[k])
        return result

##(Problem 6)231 Power of Two
class Solution(object):
    def isPowerOfTwo(self, n):
        if n<= 0 :
            return False
        while n % 2 == 0:
            n = n//2 
        if n == 1 :
            return True
        else :
            return False 
        """
        :type n: int
        :rtype: bool
        """

##(Problem 7)258 Add Digits
class Solution(object):
    def addDigits(self, num):
        while num > 9 :
            t = 0
            while num > 0:
                t += num%10
                num = num//10
            num = t
        return(num)
        if num==0:
            return 0
        return 1+(num-1)%9
        """
        :type num: int
        :rtype: int
        """

##(Problem 8)78 Subsets
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        n = len(nums)
        res = []
        for value in range (1<<n):
            s=[]
            for j in range(n):
                if value&(1<<j):
                    s.append(nums[j])
            res.append(s)
        return res

##(Problem 9)2220 Minimum Bit Flips to Convert Number
class Solution(object):
    def minBitFlips(self, start, goal):
        """
        :type start: int
        :type goal: int
        :rtype: int
        """
        ans = start^goal
        res = bin(ans).count("1")
        return res 

##(Problem 10)229 Majority Element 2
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        if not nums:
            return[]
        c1 , c2 = 0,0
        val1 = val2 = None
        for num in nums:
            if num == val1:
                c1 += 1
            elif num == val2 :
                c2 += 1 
            elif c1 == 0:
                val1 = num
                c1 = 1
            elif c2 == 0:
                val2 = num
                c2 = 1
            else:
                c1 -= 1
                c2 -= 1
        arr = []
        n = len(nums)
        if nums.count(val1)>n//3:
            arr.append(val1)
        if nums.count(val2)>n//3:
            arr.append(val2)
        return arr

##(Problem 11)169 Majority Element
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums.sort()
        return nums[len(nums)//2]

##(Problem 12)26 Removes Duplicates from Sorted Array
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0 
        i = 0
        for j in range(1,len(nums)):
            if nums[j] != nums[i] :
                i += 1
                nums[i] = nums[j]
        return i+1

##(Problem 13)38 Count and Say
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        if n==1:
            return "1"
        prev = "1"
        for i in range(2,n+1):
            res = ""
            c = 1
            for i in range(1,len(prev)):
                if prev[i]==prev[i-1]:
                    c += 1
                else :
                    res +=  str(c)+prev[i-1]
                    c = 1
            res += str(c)+prev[-1]
            prev = res
        return prev

##(Problem 14)204 Count Primes
class Solution(object):
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <= 2 :
            return 0 
        primes = [True]*n
        primes[0]=primes[1]=False
        count = 0
        for i in range(2,n):
            if primes[i]:
                count += 1
                for j in range(1*i,n,i):
                    primes[j]=False
        return count

##(Problem 15)242 Valid Anagram
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) != len(t):
            return False
        c = [0]*26
        for char in s:
            c[ord(char)-ord('a')] += 1
        for char in t:
            if c[ord(char)-ord('a')] == 0:
                return False
            c[ord(char)-ord('a')] -= 1
        return True

##(Problem 16)867 Transpose Matrix
class Solution(object):
    def transpose(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[List[int]]
        """
        rows = len(matrix)
        cols = len(matrix[0])
        res = [[0]*rows for k in range (cols)]
        for i in range (rows):
            for j in range (cols):
                res[j][i]= matrix [i][j]
        return res

##(Problem 17)2235 Add Two Integers
class Solution:
    def sum(self, num1: int, num2: int) -> int:
        return num1+num2

##(Problem 18)520 Detect Capital
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        if word.isupper() or word.islower() or word[0].isupper() and word[1:].islower():
            return True
        else:
            return False

##(Problem 19)709 To Lower Case
class Solution:
    def toLowerCase(self, s: str) -> str:
        return s.lower() 

##(Problem 20)1108 Defanging an IP Address
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return address.replace('.','[.]')

##(Problem 21)344 Reverse String
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s.reverse()
        """
        Do not return anything, modify s in-place instead.
        """
        
##(Problem 22)20 Valid Parentheses
class Solution:
    def isValid(self,s: str)->bool:
        st=[]
        for ch in s:
            if ch in '([{':
                st.append(ch)
            else:
                if not st:
                    return False
                top=st.pop()
                if ch==')'and top!='(':
                    return False
                if ch ==']' and top != '[':
                    return False
                if ch =='}' and top != '{':
                    return False
        return not st

##(Problem 23)394 Decode String
class Solution:
    def decodeString(self, s: str) -> str:
        st=[]
        num = 0
        cs = ""
        for ch in s:
            if ch.isdigit():
                num = num *10+int(ch)
            elif ch =='[':
                st.append((num,cs))
                num = 0
                cs = ""
            elif ch == ']':
                k,prev=st.pop()
                cs = prev+k*cs
            else :
                cs = cs + ch
        return cs

##(Problem 24)496 Next Greater Element 1
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        st = []
        nge = {}
        for num in reversed(nums2):
            while st and st[-1]<=num:
                st.pop()
            if st:
                nge[num]=st[-1]
            else:
                nge[num]=-1
            st.append(num)
        res=[]
        for i in nums1:
            res.append(nge[i])
        return res


##(Problem 25)402 Remove K Digits
class Solution:
    def removeKdigits(self, num: str, k: int) -> str:
        st = []
        for digit in num:
            while st and st[-1] > digit and k > 0:
                st.pop()
                k -= 1
            st.append(digit)
        while k > 0:
            st.pop()
            k -= 1  
        res = "".join(st).lstrip('0')
        if res:
            return res
        else:
            return "0"

##(Problem 26)283 Move Zeroes
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        idx = 0 
        for i in range(len(nums)):
            if nums[i] != 0 :
                nums[idx]=nums[i]
                idx+=1
        for i in range(idx,len(nums)):
            nums[i]=0

##(Problem 27)189 Rotate Array
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k=k%n
        nums[:]=nums[-k:]+nums[:-k]

##(Problem 28)118 Pascal's Triangle
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        res =[]
        for i in range(numRows):
            rows = [1]*(i+1)
            for j in range(1,i):
                rows[j]=res[i-1][j-1]+res[i-1][j]
            res.append(rows)
        return res

##(Problem 29)503 Next Greater Element 2
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        n = len(nums)
        ans = [-1]*n
        st=[]
        for i in range(2*n):
            idx = i%n
            while st and nums[idx]>nums[st[-1]]:
                prev=st.pop()
                ans[prev]=nums[idx]
            if(i<n):
                st.append(idx)
        return ans

##(Problem 30)735 Asteroid Collision
class Solution:
    def asteroidCollision(self, asteroids: List[int]) -> List[int]:
        st=[]
        for ast in asteroids:
            while st and ast<0 and st[-1]>0:
                if st[-1]<-ast:
                    st.pop()
                    continue
                elif st[-1]== -ast:
                    st.pop()
                break
            else:
                st.append(ast)
        return st

##(Problem 31)42 Trapping Rain Water 
class Solution:
    def trap(self, height: List[int]) -> int:
        l=lmax=rmax=w=0
        r=len(height)-1
        while l<r:
            if height[l]<height[r]:
                w+=max(0,lmax-height[l])
                lmax=max(lmax,height[l])
                l+=1
            else:
                w+=max(0,rmax-height[r])
                rmax=max(rmax,height[r])
                r-=1
        return w

##(Problem 32)84 Largest Rectangle in Histogram
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        st=[]
        n=len(heights)
        ma=0
        i=0
        while i<n:
            h=heights[i]
            start=i
            while st and st[-1][1]>h:
                idx,height=st.pop()
                ma=max(ma,height*(i-idx))
                start=idx
            st.append((start,h))
            i+=1
        for idx,height in st:
            ma=max(ma,height*(n-idx))
        return ma

##(Problem 33)205 Isomorphic Stringsclass Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        char_s={}
        char_t={}
        for i in range(len(s)):
            if s[i] not in char_s:
                char_s[s[i]]=i
            if t[i] not in char_t:
                char_t[t[i]]=i
            if char_s[s[i]] != char_t[t[i]]:
                return False
        return True

##(Problem 34)2586 Count the Number of Vowel Strings in Range
class Solution:
    def vowelStrings(self, words: List[str], left: int, right: int) -> int:
        v={'a','e','i','o','u'}
        c=0
        for i in range(left,right+1):
            word = words[i]
            if word[0] in v and word [-1] in v:
                c+=1
        return c

##(Problem 35)146 LRU Cache
class LRUCache:
    def __init__(self, capacity: int):
        self.capacity=capacity
        self.cache=OrderedDict()
    def get(self, key: int) -> int:
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]
    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key]=value
        if len(self.cache)>self.capacity:
            lru = self.cache.popitem(last=False)
# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
        

##(Problem 36)460 LFU Cache
class LFUCache:
    def __init__(self, capacity: int):
        self.capacity=capacity
        self.key_to_val={}
        self.key_to_freq={}
        minfreq=0
        self.frq_to_key=defaultdict(OrderedDict)
    def update(self,key):
        freq=self.key_to_freq[key]
        del self.frq_to_key[freq][key]
        if not self.frq_to_key[freq]:
            del self.frq_to_key[freq]
            if self.minfreq==freq:
                self.minfreq+=1
        self.key_to_freq[key]=freq+1
        self.frq_to_key[freq+1][key]=None
    def get(self, key: int) -> int:
        if key not in self.key_to_val:
            return -1
        self.update(key)
        return self.key_to_val[key]
    def put(self, key: int, value: int) -> None:
        if self.capacity==0:
            return
        if key in self.key_to_val:
            self.key_to_val[key]=value
            self.update(key)
            return
        if len(self.key_to_val)>=self.capacity:
            lfu,_=self.frq_to_key[self.minfreq].popitem(last=False)
            del self.key_to_val[lfu]
            del self.key_to_freq[lfu]
        self.key_to_val[key]=value
        self.key_to_freq[key]=1
        self.minfreq=1
        self.frq_to_key[1][key]=None
        return
# Your LFUCache object will be instantiated and called as such:
# obj = LFUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)


##(Problem 37)206 Reverse Linked List
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr=head
        prev=None
        while curr:
            nxt=curr.next
            curr.next=prev
            prev=curr
            curr=nxt
        return prev


##(Problem 38)876 Middle of the Linked List
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow= fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow

##(Problem 39)14 Longest Common Prefix
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        p=strs[0]
        x=len(p)
        for i in strs[1:]:
            while p != i[0:x]:
                x-=1
                if x==0:
                    return ""
                p=p[0:x]
        return p

##(Problem 40)19 Remove Nth Node From End of List
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy =ListNode(0,head)
        fast = slow =dummy
        for i in range(n):
            fast = fast.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next
        slow.next=slow.next.next
        return dummy.next

##(Problem 41)21 Merge Two Sorted Lists
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0)
        curr = dummy
        while list1 and list2:
            if list1.val<list2.val:
                curr.next=list1
                list1=list1.next
            else:
                curr.next=list2
                list2=list2.next
            curr=curr.next
        if list1:
            curr.next=list1
        if list2:
            curr.next=list2
        return dummy.next

##(Problem 42)141 Linked List Cycle
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False

##(Problem 43)234 Palindrome Linked List 
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        slow=fast=head
        while fast and fast.next:
            fast =  fast.next.next 
            slow=slow.next
        prev = None
        curr = slow
        while curr:
            nxt = curr.next
            curr.next=prev
            prev = curr
            curr = nxt
        l=head
        r=prev
        while r:
            if l.val != r.val:
                return False
            l=l.next
            r=r.next
        return True

##(Problem 44)2 Add two Numbers
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        carry = 0
        dummy = ListNode(0)
        curr = dummy
        while l1 and l2:
            val = l1.val + l2.val + carry
            carry = val // 10
            val = val % 10
            curr.next = ListNode(val)
            curr = curr.next
            l1 = l1.next
            l2 = l2.next
        while l1:
            if carry == 1:
                val = l1.val + carry
                carry = val // 10
                val = val % 10
                curr.next = ListNode(val)
            else:
                curr.next = ListNode(l1.val)
            curr = curr.next
            l1 = l1.next
        while l2:
            if carry==1:
                val=l2.val+carry
                carry=val//10
                val=val%10
                curr.next=ListNode(val)
            else:
                curr.next=ListNode(l2.val)
            curr=curr.next
            l2=l2.next
        if carry==1:
            curr.next=ListNode(carry)
        return dummy.next

##(Problem 45)226 Invert Binary Tree        
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        root.left,root.right=root.right,root.left
        lt=self.invertTree(root.left)
        rt=self.invertTree(root.right)
        return root

##(Problem 46)100 Same Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if not p or not q:
            return False
        if p.val!=q.val:
            return False
        lt=self.isSameTree(p.left,q.left)
        rt=self.isSameTree(p.right,q.right)
        if lt and rt:
            return True
        else:
            return False

##(Problem 47)101 Symmetric Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def samet(p,q):
            if not p and not q:
                return True
            if not p or not q:
                return False
            if p.val!=q.val:
                return False
            lt=samet(p.left,q.right)
            rt=samet(p.right,q.left)
            if lt and rt:
                return True
            else:
                return False
        return samet(root.left,root.right)

##(Problem 48)104 Maximum Depth of Binary Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        q=[root]
        c=0
        while q:
            for i in range(len(q)):
                node=q.pop(0)
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            c+=1
        return c

##(Problem 49)110 Balanced Binary Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def help(node):
            if not node:
                return 0
            lh = help(node.left)
            rh = help(node.right)
            if lh==-1 or rh==-1:
                return -1
            if abs(lh-rh)>1:
                return -1
            return 1+max(lh,rh)
        return help(root)!=-1

##(Problem 50)543 Diameter of Binary Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.diameter=0
        def help(node):
            if not node:
                return 0
            lh=help(node.left)
            rh=help(node.right)
            self.diameter=max(self.diameter,lh+rh)
            return 1+max(lh,rh)
        help(root)
        return self.diameter
        
##(Problem 51)230 Kth Smallest Element in a BST
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        res=0
        c=0
        def inorder(root):
            nonlocal c
            nonlocal res
            if root :
                inorder(root.left)
                c+=1
                if c==k:
                    res=root.val
                inorder(root.right)
        inorder(root)
        return res

##(Problem 52)124 Binary Tree Maximum Path Sum
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        self.maxpath=float('-inf')
        def help(node):
            if not node:
                return 0
            lt=max(help(node.left),0)
            rt=max(help(node.right),0)
            curr=node.val+lt+rt
            self.maxpath=max(self.maxpath,curr)
            return node.val + max(lt, rt)
        help(root)
        return self.maxpath

##(Problem 53)48 Rotate Image
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n=len(matrix)
        for i in range(n):
            for j in range(i+1,n):
                matrix[i][j],matrix[j][i]=matrix[j][i],matrix[i][j]
        for row in matrix:
            row.reverse()

##(Problem 54)547 Number of Provinces
class Solution:
    def findCircleNum(self, isConnected: List[List[int]]) -> int:
        n=len(isConnected)
        visited=set()
        def dfs(city):
            for neighbour in range(n):
                if isConnected[city][neighbour]==1 and neighbour not in visited:
                    visited.add(neighbour)
                    dfs(neighbour)
        p=0
        for city in range(n):
            if city not in visited:
                visited.add(city)
                dfs(city)
                p+=1
        return p

##(Problem 55)58 Length of Last Word
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        s = s.strip()
        words =s.split()
        return len(words[-1])

##(Problem 56)3 Longest Substring Without Repeating Characters
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left = 0
        ml = 0
        chset = set()
        for r in range(len(s)):
            if s[r] not in chset:
                chset.add(s[r])
                ml = max(ml, r - left + 1)
            else:
                while s[r] in chset:
                    chset.remove(s[left])
                    left+=1
                chset.add(s[r])
        return ml

##(Problem 57)1423 Maximum Points You Can Obtain from Cards
class Solution:
    def maxScore(self, cardPoints: List[int], k: int) -> int:
        n = len(cardPoints)
        if(k==n):
            return sum(cardPoints)
        ts = sum(cardPoints)
        windowsize=n-k
        win_sum=sum(cardPoints[:windowsize])
        min_w_sum=win_sum
        for i in range(windowsize,n):
            win_sum+=cardPoints[i]-cardPoints[i-windowsize]
            min_w_sum=min(min_w_sum,win_sum)
        return ts-min_w_sum

##(Problem 58)2062 Count Vowel Substrings of a String
class Solution:
    def countVowelSubstrings(self, word: str) -> int:
        c = 0
        vowels = {'a','e','i','o','u'}
        n = len(word)
        for i in range(n):
            if word[i] in vowels:
                seen = set()
                for j in range(i, n):
                    if word[j] in vowels:
                        seen.add(word[j])
                        if len(seen) == 5:
                            c += 1
                    else:
                        break
        return c

##(Problem 59)424 Longest Repeating Character Replacement
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        ans=0
        n=len(s)
        mf=0
        i=0
        freq={}
        for j in range(n):
            ch=s[j]
            if ch in freq:
                freq[ch]+=1
            else:
                freq[ch]=1
            mf=max(mf,freq[ch])
            while (j-i+1)-mf>k:
                freq[s[i]]-=1
                i+=1
            ans = max(ans,j-i+1)
        return ans


##(Problem 60)904 Fruit Into Baskets
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        freq={}
        left=0
        ans=0
        for r in range(len(fruits)):
            if fruits[r] in freq:
                freq[fruits[r]]+=1
            else:
                freq[fruits[r]]=1
            while len(freq)>2:
                freq[fruits[left]]-=1
                if freq[fruits[left]]==0:
                    del freq[fruits[left]]
                left+=1
            ans =max(ans,r-left+1)
        return ans


##(Problem 61)560 Subarray Sum Equals K
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        ans=0
        ps=0
        freq={0:1}
        for num in nums:
            ps+=num
            if ps-k in freq:
                ans+=freq[ps-k]
            if ps in freq:
                freq[ps]+=1
            else:
                freq[ps]=1
        return ans

##(Problem 62)128 Longest Consecutive Sequence
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        longest=0
        nset=set(nums)
        for num in nset:
            if num-1 not in nset:
                curr=num
                le=1
                while curr+1 in nset:
                    curr+=1
                    le+=1
                longest=max(longest,le)
        return longest

##(Problem 63)79 Word Search
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        rows = len(board)
        cols = len(board[0])

        def bt(r, c, idx):
            if idx == len(word):
                return True
            
            if r < 0 or c < 0 or r >= rows or c >= cols or board[r][c] != word[idx]:
                return False
            
            temp = board[r][c]
            board[r][c] = "#"
            
            found = (
                bt(r+1, c, idx+1) or
                bt(r-1, c, idx+1) or
                bt(r, c+1, idx+1) or
                bt(r, c-1, idx+1)
            )
            
            board[r][c] = temp
            return found

        for r in range(rows):
            for c in range(cols):
                if bt(r, c, 0):
                    return True
        
        return False

##(Problem 64)51 N-Queens
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        board=[["."]*n for i in range(n)]
        res=[]
        def issafe(board,r,c):
            for i in range(r-1,-1,-1):
                if board[i][c]=='Q':
                    return False
            row,col=r-1,c-1
            while row>-1 and col>-1:
                if board[row][col]=='Q':
                    return False
                row-=1
                col-=1
            row,col=r-1,c+1
            while row>-1 and col<n:
                if board[row][col]=='Q':
                    return False
                row-=1
                col+=1
            return True
        def bt(row,n,board,res):
            if row==n:
                res.append(["".join(row) for row in board])
                return
            for col in range(n):
                if issafe(board,row,col):
                    board[row][col]="Q"
                    bt(row+1,n,board,res)
                    board[row][col]="."
        bt(0,n,board,res)
        return res

##(Problem 65)131 Palindrome Partitioning
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res=[]
        path=[]
        def ispal(l,r):
            while (l<r):
                if s[l]!=s[r]:
                    return False
                l+=1
                r-=1
            return True
        def bt(start):
            if start==len(s):
                res.append(path[:])
                return
            for end in range(start,len(s)):
                if ispal(start,end):
                    path.append(s[start:end+1])
                    bt(end+1)
                    path.pop()
        bt(0)
        return res

##(Problem 66)1248 Count Number of Nice Subarrays
class Solution:
    def numberOfSubarrays(self, nums: List[int], k: int) -> int:
        prefix_sum=0
        count={0:1}
        ans=0
        for num in nums:
            if num%2==1:
                prefix_sum+=1
            if prefix_sum-k in count:
                ans+=count[prefix_sum-k]
            if prefix_sum in count:
                count[prefix_sum]+=1
            else:
                count[prefix_sum]=1
        return ans

##(Problem 67)930 Binary Subarrays with Sum
class Solution:
    def numSubarraysWithSum(self, nums: List[int], goal: int) -> int:
        ps=0
        freq={0:1}
        ans=0
        for num in nums:
            ps+=num
            if ps-goal in freq:
                ans+=freq[ps-goal]
            if ps in freq:
                freq[ps]+=1
            else:
                freq[ps]=1
        return ans

##(Problem 68)1358 Number of Substrings Containing All Three Characters
class Solution:
    def numberOfSubstrings(self, s: str) -> int:
        freq={'a':0,'b':0,'c':0}
        c=0
        left=0
        for r in range(len(s)):
            freq[s[r]]+=1
            while freq['a']>0 and freq['b']>0 and freq['c']>0:
                c+=len(s)-r
                freq[s[left]]-=1
                left+=1
        return c

##(Problem 69)76 Minimum Window Substring
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if not t or not s:
            return ""
        n=len(s)
        freq={}
        for c in (t):
            if c in freq:
                freq[c]+=1
            else:
                freq[c]=1
        left=0
        c=0
        start=0
        ml=float('inf')
        for r in range(n):
            if s[r] in freq:
                if freq[s[r]]>0:
                    c+=1
                freq[s[r]]-=1
            else:
                freq[s[r]]=-1
            while c==len(t):
                if r-left+1<ml:
                    ml=r-left+1
                    start = left
                freq[s[left]]+=1
                if freq[s[left]]>0:
                    c-=1
                left+=1
        if ml==float('inf'):
            return ""
        else:
            return s[start:start+ml]

##(Problem 70)37 Sudoku Solver
class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        rows=[set() for i in range(9)]
        cols=[set() for i in range(9)]
        boxes=[set() for i in range(9)]
        for r in range(9):
            for c in range(9):
                if board[r][c] !=".":
                    num=board[r][c]
                    rows[r].add(num)
                    cols[c].add(num)
                    boxes[(r//3)*3+(c//3)].add(num)
        def bt(r,c):
            if r==9:
                return True
            if c==9:
                return bt(r+1,0)
            if board[r][c]!=".":
                return bt(r,c+1)
            boxid=(r//3)*3+(c//3)
            for num in "123456789":
                if num not in rows[r] and num not in cols[c] and num not in boxes[boxid]:
                    board[r][c]=num
                    rows[r].add(num)
                    cols[c].add(num)
                    boxes[boxid].add(num)
                    if bt(r,c+1):
                        return True
                    board[r][c]="."
                    rows[r].remove(num)
                    cols[c].remove(num)
                    boxes[boxid].remove(num)
            return False
        bt(0,0)

##(Problem 71)455 Assign Cookies
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        g.sort()
        s.sort()
        i=0
        j=0
        c=0
        while i<len(g) and j<len(s):
            if s[j]>=g[i]:
                c+=1
                i+=1
                j+=1
            else:
                j+=1
        return c

##(Problem 72)860 Leamonade Change
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        f = 0  
        t = 0  
        
        for bill in bills:
            if bill == 5:
                f += 1
            elif bill == 10:
                if f == 0:
                    return False
                f -= 1
                t += 1
            else:  
                if t > 0 and f > 0:
                    t -= 1
                    f -= 1
                elif f >= 3:
                    f -= 3
                else:
                    return False  
        return True

##(Problem 73)55 Jump Game
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        maxi=0
        for i in range(len(nums)):
            if i>maxi:
                return False
            maxi=max(maxi,i+nums[i])
        return True

##(Problem 74)45 Jump Game 2
class Solution:
    def jump(self, nums: List[int]) -> int:
        ce=0
        f=0
        j=0
        n=len(nums)
        for i in range(n-1):
            f=max(f,i+nums[i])
            if i==ce:
                j+=1
                ce=f
        return j

##(Problem 75)435 Non-overlapping Intervals
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        ends=[]
        for s,e in intervals:
            ends.append((e,s))
        ends.sort()
        c=0
        le= ends[0][0]
        for e,s in ends[1:]:
            if s<le:
                c+=1
            else:
                le=e
        return c


##(Problem 76)57 Insert Interval
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        i = 0
        res = []
        n = len(intervals)
        while i < n and intervals[i][1] < newInterval[0]:
            res.append(intervals[i])
            i += 1
        while i < n and intervals[i][0] <= newInterval[1]:
            newInterval[0] = min(newInterval[0], intervals[i][0])
            newInterval[1] = max(newInterval[1], intervals[i][1])
            i += 1
        res.append(newInterval)
        while i < n:
            res.append(intervals[i])
            i += 1
        return res

##(Problem 77)678 Valid Parenthesis String
class Solution:
    def checkValidString(self, s: str) -> bool:
        minopen, maxopen = 0, 0
        for ch in s:
            if ch == "(":
                minopen += 1
                maxopen += 1
            elif ch == ")":
                minopen -= 1
                maxopen -= 1
            else:
                minopen -= 1
                maxopen += 1

            if maxopen < 0:
                return False
            if minopen < 0:
                minopen = 0

        return minopen == 0

##(Problem 78)135 Candy
class Solution:
    def candy(self, ratings: List[int]) -> int:
        n = len(ratings)
        candies = [1] * n
        for i in range(1, n):
            if ratings[i] > ratings[i-1]:
                candies[i] = candies[i-1] + 1
        for i in range(n-2, -1, -1):
            if ratings[i] > ratings[i+1]:
                candies[i] = max(candies[i], candies[i+1] + 1)
        return sum(candies)

##(Problem 79)852 Peak Index in a Mountain Array
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:
        left=0
        right=len(arr)-1
        while left<right:
            mid=(left+right)//2
            if arr[mid]<arr[mid+1]:
                left=mid+1
            else:
                right=mid
        return left

##(Problem 80)18 4Sum
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        res = []
        for i in range(n - 3):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            for j in range(i + 1, n - 2):
                if j > i + 1 and nums[j] == nums[j - 1]:
                    continue
                l, r = j + 1, n - 1
                while l < r:
                    total = nums[i] + nums[j] + nums[l] + nums[r]
                    if total == target:
                        res.append([nums[i], nums[j], nums[l], nums[r]])
                        l += 1
                        r -= 1
                        while l < r and nums[l] == nums[l - 1]:
                            l += 1
                        while l<r and nums[r] == nums[r + 1]:
                            r-=1
                    elif total<target:
                        l+=1
                    else:
                        r-=1
        return res

##(Problem 81)15 3Sum
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        n = len(nums)
        ans = []
        for i in range(n - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            left = i + 1
            right = n - 1
            while left < right:
                total = nums[i] + nums[left] + nums[right]
                if total == 0:
                    ans.append([nums[i], nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while left < right and nums[left] == nums[left - 1]:
                        left += 1
                    while left < right and nums[right] == nums[right + 1]:
                        right -= 1
                elif total < 0:
                    left += 1
                else:
                    right -= 1
        return ans

##(Problem 82)1 Two Sum
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range (len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i]+nums[j]==target:
                    return i,j

##(Problem 83)875 Koko Eating Bananas
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        left=1
        right=max(piles)
        ans = right
        while left<=right:
            mid=(left+right)//2
            hour=0
            for p in piles:
                hour+=math.ceil(p/mid)
            if hour<=h:
                ans=mid
                right=mid-1
            else:
                left=mid+1
        return ans

##(Problem 84)238 Product of Array Except Self
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n=len(nums)
        res=[1]*n
        left=1
        for i in range(n):
            res[i]=left
            left*=nums[i]
        right=1
        for i in range(n-1,-1,-1):
            res[i]*=right
            right*=nums[i]
        return res


##(Problem 85)127 Word Ladder
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        wordset = set(wordList)
        if endWord not in wordset:
            return 0
        q = deque([(beginWord, 1)])
        while q:
            word, steps = q.popleft()
            if word == endWord:
                return steps
            for i in range(len(word)):
                for ch in 'qwertyuiopasdfghjklzxcvbnm':
                    new = word[:i] + ch + word[i+1:]
                    if new in wordset:
                        q.append((new, steps + 1))
                        wordset.remove(new)
        return 0

##(Problem 86)210 Course Schedule 2
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        graph=defaultdict(list)
        indegree=[0]*numCourses
        for course,dest in prerequisites:
            graph[dest].append(course)
            indegree[course]+=1
        q=[]
        for i in range(numCourses):
            if indegree[i]==0:
                q.append(i)
        finish=[]
        while q:
            node=q.pop(0)
            finish.append(node)
            for nei in graph[node]:
                indegree[nei]-=1
                if indegree[nei]==0:
                    q.append(nei)
        
        if len(finish)==numCourses:
            return finish
        else:
            return []

##(Problem 87)802 Find Eventual Safe States
class Solution:
    def eventualSafeNodes(self, graph: List[List[int]]) -> List[int]:
        n=len(graph)
        states=[0]*n
        def dfs(node):
            if states[node]!=0:
                return states[node]==2
            states[node]=1
            for nei in graph[node]:
                if states[nei]==1 or not dfs(nei):
                    return False
            states[node]=2
            return True
        res=[]
        for i in range(n):
            if dfs(i):
                res.append(i)
        return res

##(Problem 88)207 Course Schedule
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        graph=defaultdict(list)
        indegree=[0]*numCourses
        for course,dest in prerequisites:
            graph[dest].append(course)
            indegree[course]+=1
        q=[]
        for i in range(numCourses):
            if indegree[i]==0:
                q.append(i)
        finish=0
        while q:
            node=q.pop(0)
            finish+=1
            for nei in graph[node]:
                indegree[nei]-=1
                if indegree[nei]==0:
                    q.append(nei)
        return finish==numCourses

##(Problem 89)700 Search in a Binary Search Tree
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        if not root:
            return None
        if root.val==val:
            return root
        elif val < root.val:
            return self.searchBST(root.left,val)
        else:
            return self.searchBST(root.right,val)

##(Problem 90)297 Serialize and Deserialize Binary Tree
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.
        
        :type root: TreeNode
        :rtype: str
        """
        if not root:
            return ""
        q=deque([root])
        res=[]
        while q:
            node=q.popleft()
            if node:
                res.append(str(node.val))
                q.append(node.left)
                q.append(node.right)
            else:
                res.append("null")
        return ",".join(res)
        

    def deserialize(self, data):
        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        if not data:
            return None
        nodes=data.split(",")
        root=TreeNode(int(nodes[0]))
        q=deque([root])
        i=1
        while q:
            node=q.popleft()
            if nodes[i]!="null":
                node.left = TreeNode(int(nodes[i]))
                q.append(node.left)
            i+=1
            if nodes[i]!="null":
                node.right = TreeNode(int(nodes[i]))
                q.append(node.right)
            i+=1
        return root

# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))

##(Problem 91)106 Construct Binary Tree from Inorder and Postorder Traversal
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
        inorder_map={}
        for i in range(len(inorder)):
            inorder_map[inorder[i]]=i
        self.post_index = len(postorder)-1
        def helper(left,right):
            if left > right:
                return None
            root_val = postorder[self.post_index]
            self.post_index -= 1
            root=TreeNode(root_val)
            mid=inorder_map[root_val]
            root.right=helper(mid+1,right)
            root.left=helper(left,mid-1)
            return root
        return helper(0,len(inorder)-1)

##(Problem 92)105 Construct Binary Tree from Preorder and Inorder Traversal
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        inorder_map={}
        for i in range(len(inorder)):
            inorder_map[inorder[i]]=i
        self.pre_index=0
        def helper(left,right):
            if left>right:
                return None
            root_val=preorder[self.pre_index]
            self.pre_index+=1
            root=TreeNode(root_val)
            mid=inorder_map[root_val]
            root.left=helper(left,mid-1)
            root.right=helper(mid+1,right)
            return root
        return helper(0,len(inorder)-1)

##(Problem 93)126 Word Ladder 2
class Solution:
    def findLadders(self, beginWord: str, endWord: str, wordList: List[str]) -> List[List[str]]:
        wordset=set(wordList)
        if endWord not in wordset:
            return []
        par={}
        found=False
        lev=set([beginWord])
        while lev and not found:
            nl=set()
            for word in lev:
                if word in wordset:
                    wordset.remove(word)
            for word in lev:
                for i in range(len(word)):
                    for ch in'qwertyuiopasdfghjklzxcvbnm':
                        nw=word[:i]+ch+word[i+1:]
                        if nw in wordset:
                            if nw not in par:
                                par[nw]=[]
                            par[nw].append(word)
                            nl.add(nw)
                            if nw==endWord:
                                    found=True
            lev=nl
        res=[]
        def dfs(word,path):
            if word==beginWord:
                res.append(path[::-1])
                return
            if word not in par:
                return
            for p in par[word]:
                dfs(p,path+[p])
        if found:
            dfs(endWord,[endWord])
        return res
        
