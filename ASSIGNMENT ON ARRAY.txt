FIND ALL DUPLICATES IN AN ARRAY

class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        List<Integer> list = new ArrayList<
        for(int i=0; i<nums.length; i++)
        {
            int r = Math.abs(nums[i]);
            if(nums[r-1] > 0)
            {
                nums[r-1] = -nums[r-1];
            }
            else
            {
                list.add(Math.abs(nums[i]));
            }
        }
        return list;
    }
}


NUMBER OF GOOD PAIRS

class Solution {
    public int numIdenticalPairs(int[] nums) {
        int count = 0;
        for(int i=0; i<nums.length; i++)
        {
            for(int j=i+1; j<nums.length; j++)
            {
                if(nums[i] == nums[j])
                {
                    count++;
                }
            }
        }
        return count;
    }
}

FIND GREATEST COMMON DIVISION OF ARRAY

class Solution {
    public int findGCD(int[] nums) {
        Arrays.sort(nums);
        int max = nums[nums.length-1];
        int min = nums[0];
        return op(min,max);
    }
    public int op(int r, int s)
    {
        if(s == 0)
        {
            return r;
        }
        if(r < s)
        {
            return op(s,r);
        }
        return op(s, r%s);
    }
}


UNIQUE NUMBER OF OCCURENCES

class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int i : arr)
        {
            map.put(i, map.getOrDefault(i, 0) + 1);
        }
        Set<Integer> set = new HashSet<>(map.values());
        return set.size() == map.size();
    }
}

FIND THE DUPLICATE NUMBER

class Solution {
    public int findDuplicate(int[] nums) {
        int r = 0;
        int s = 0;
        do{
            s = nums[s];
            r = nums[nums[r]];
        }
        while(s != r);
        s = 0;
        do{
            s = nums[s];
            r = nums[r]; 
        }
        while(s != r);
        return s;
    }
}


MAXIMUM POINTS YOU CAN OBATIN FROM CARDS

class Solution {
    public int maxScore(int[] cardPoints, int k) {
        int r = cardPoints.length;
        int lSide = 0;
        int rSide = 0;
        for(int i = 0; i < k; i++)
        {
             lSide += cardPoints[i];
        }
        int op = lSide;
        for(int i = 0; i < k; i++){
            lSide -= cardPoints[k - i - 1];
            rSide += cardPoints[r - i - 1];
            op = Math.max(lSide + rSide, op);
        }  
        return op;
    }
}