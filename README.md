# leetcode3-string

Sliding-window

        class Solution:
            def lengthOfLongestSubstring(self, s: str) -> int:
                dict = {}
                left = 0
                maxL = 0

                for right in range(len(s)):
                    if s[right] not in dict:
                        maxL = max(right-left+1, maxL)
                    else:
                        if s[right] in dict and dict[s[right]] < left:
                            maxL = max(right-left+1, maxL)
                        else:
                            left = dict[s[right]] +1
                    dict[s[right]] = right
                return maxL

          这是我的想法，右边跑，左边不动，除非长得一样了。
          有一些亮点：
            1）右边在跑，所以取right in range。 
            2）差值为长度，注意+1
            3）【 要考虑存在的dict-item是否存在在dict里 】 ：
                如果在left左边，不用管；但是存在于left右边的话，left要右移
            4）【 最后对应上index 】



        # dict = {}
        # left = 0
        # cur_len = 0
        # maxL = 0

        自动对应每个item到index。 这个叫枚举 enumerate(s)

        # for i, char in enumerate(s):
        #     if char not in dict:
        #         dict[char] = i
        #         cur_len = i - left+1 

        #     elif char in dict and dict[char] >= left:
        #         left = dict[char]+1
        #         cur_len = i - dict[char]
        #         dict[char] = i    
                
        #     print(cur_len)
        #     maxL = max(maxL, cur_len)
        # return maxL
        

       

            
