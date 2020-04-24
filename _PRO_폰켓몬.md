# PRO_폰켓몬


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[] arr = {3,1,2,3};
		int[] arr1 = {3,3,3,2,2,4};
		int[] arr2 = {3,3,3,2,2,2};
		System.out.println(s.solution(arr2));
	}

	boolean[] visit;
	int[] ret;
	int max = Integer.MIN_VALUE;
	
	public int solution(int[] nums) {
        ret = new int[nums.length/2];
        
        Set<Integer> set = new HashSet<>();
        for(int i=0; i<nums.length; i++) set.add(nums[i]);
        
        int ans = (set.size() > nums.length/2)? nums.length/2 : set.size();
        
        //dfs(nums, -1, 0);
        
        return ans;
	}
	
	//시간초과
	public void dfs(int[] nums, int compare, int start) {
		if(start==ret.length) {
			Set<Integer> set = new HashSet<>();
			for (Integer item : ret) {
				set.add(item);
			}
			max = Math.max(max, set.size());
			return;
		}
		
		
		for(int i=0; i<nums.length; i++) {
			if(!visit[i] && compare<i) {
				visit[i] = true;
				ret[start] = nums[i];
				dfs(nums, i, start+1);
				visit[i] = false;
			}
		}
	}
}


```

