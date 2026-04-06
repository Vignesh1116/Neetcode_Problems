<!-- Given an integer array nums and an integer k, return the k most frequent elements within the array.

The test cases are generated such that the answer is always unique.

You may return the output in any order.

Example 1:

Input: nums = [1,2,2,3,3,3], k = 2

Output: [2,3] -->

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count={}
        for num in nums:
           count[num]=1+count.get(num,0)

        arr=[]
        for num,cnt in count.items():
           arr.append([cnt,num])
        arr.sort()

        res=[]
        while len(res)<k:
          res.append(arr.pop()[1])
        return res  
