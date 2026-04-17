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
        
