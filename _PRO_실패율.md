# PRO_실패율


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr = {2,1,2,6,2,4,3,3};
		System.out.println(solution.solution(5, arr));
	}
	
	public int[] solution(int N, int[] stages) {
		
		int[] answer = new int[N];
		for(int i=0; i<N; i++) {
			answer[i] = i+1;
		}
		
		double[] ret = new double[N];
		int[] failed = new int[N];
		
		for(int i=0; i<stages.length; i++) {
			int stage = stages[i];
			if(stage>=1 && stage<=N) {
				failed[stage-1]++;
			}
		}
		
		int divide = stages.length;
		
		for(int i=0; i<failed.length; i++) {
			ret[i] = (double) failed[i]/divide;
			divide-=failed[i];
		}
		
		int temp1= 0;
		double temp2 = 0.0d;
		for(int i=0; i<ret.length-1; i++) {
			for(int j=0; j<ret.length-i-1; j++) {
				if(ret[j]<ret[j+1]) {
					temp2 = ret[j+1];
					ret[j+1] = ret[j];
					ret[j] = temp2;
					temp1 = answer[j+1];
					answer[j+1] = answer[j];
					answer[j] = temp1;
				}
			}
		}
		
        return answer;
    }
} 


```

