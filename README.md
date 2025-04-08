# april8_2025
The problem that i solved today in leetcode

1.You are given an integer array nums. You need to ensure that the elements in the array are distinct. To achieve this, you can perform the following operation any number of times:

Remove 3 elements from the beginning of the array. If the array has fewer than 3 elements, remove all remaining elements.
Note that an empty array is considered to have distinct elements. Return the minimum number of operations needed to make the elements in the array distinct.

Code:
class Solution {
    public boolean check(Map<Integer,Integer> m)
    {
        for(Map.Entry<Integer,Integer> x:m.entrySet())
        {
            if(x.getValue()>1)
                return true;
        }
        return false;
    }
    public int minimumOperations(int[] nums) {
        int n=nums.length;
        Map<Integer,Integer> m=new HashMap<>();
        for(int x:nums)
            m.put(x,m.getOrDefault(x,0)+1);
        int i=0;
        int cnt=0;
        while(check(m))
        {
            for(int j=i;j<i+3 && j<n;j++)
            {
                if(m.get(nums[j])==1)
                    m.remove(nums[j]);
                else
                    m.put(nums[j],m.get(nums[j])-1);
            }
            i+=3;
            cnt++;
        }
        return cnt;
    }
}
