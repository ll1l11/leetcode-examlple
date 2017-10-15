自己的解决方案::

  class Solution(object):
      def twoSum(self, nums, target):
          """
          :type nums: List[int]
          :type target: int
          :rtype: List[int]
          """
          nums2 = [(x, i) for i, x in enumerate(nums)]
          nums2.sort(key=lambda x: x[0])
          l = len(nums2)

          result = 0
          end = False

          for i in range(l):
              if (end):
                  break
              for j in range(l-1, 0, -1):
                  two_sum = nums2[i][0] + nums2[j][0]
                  if i >= j:
                      break
                  if two_sum == target:
                      result = [nums2[i][1], nums2[j][1]]
                      end = True
                      break
                  elif two_sum < target:
                      break
          return result
      
      
一个O(n)的解决方案::

  class Solution(object):
      def twoSum(self, nums, target):
          if len(nums) <= 1:
              return False
          buff_dict = {}
          for i in range(len(nums)):
              if nums[i] in buff_dict:
                  return [buff_dict[nums[i]], i]
              else:
                  buff_dict[target - nums[i]] = i
