# PRO_예산


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr = {120, 110, 140, 150};
		System.out.println(solution.solution(arr, ));
	}
	
	static int max = Integer.MIN_VALUE;
	
	public int solution(int[] budgets, int M) {
		
     
        Arrays.sort(budgets);

        search(budgets, budgets[0], budgets[budgets.length-1], M);

        int answer = max;
        
        if(max == Integer.MIN_VALUE) {
        	return M/budgets.length;
        } else {
            return answer;
        }
    }
	
	public void search(int[] budgets, int left, int right, int limit) {
		if(left>right ) {
			return;
		}
		
		int mid = (left+right)/2;
		int budget = cal(budgets, mid);
		if(limit>=budget) {
			max = Math.max(mid, max);
			search(budgets, mid+1, right, limit);
		} else {
			search(budgets, left, mid-1, limit);
		}
		
	}
	
	public int cal(int[] budgets, int mid) {
		int sum = 0;
		for(int i=0; i<budgets.length; i++) {
			if(budgets[i]<mid) sum+=budgets[i];
			else sum+=mid;
		}
		return sum;
	}
} 


```

