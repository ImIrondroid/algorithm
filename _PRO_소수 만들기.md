# PRO_소수 만들기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[] arr = {1,2,3,4};
		System.out.println(s.solution(arr));
	}
	
	boolean[] visit;
	boolean[] check;
	int[] ret;
	int count = 0;
	
	public int solution(int[] nums) {

		ret = new int[3];
		visit = new boolean[nums.length];
		check = new boolean[3001];
	 
		for(int i=2; i*i<=check.length; i++) {
			for(int j=i*i; j<=check.length; j+=i) {
				check[j] = true;
			}
		}
		
		dfs(nums, -1, 0);
	 
		return count;
	}
	
	public void dfs(int[] nums, int compare, int start) {
		if(start==3) {
			int sum = getSum(ret);
			if(!check[sum]) count++;
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
	
	public int getSum(int[] ret) {
		int sum = 0;
		for(int i=0; i<ret.length; i++) sum += ret[i];
		return sum;
	}
}


```

