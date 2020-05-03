# PRO_입국심사


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[] times = {7,10};
		int[] times1 = {100000000,100000000,100000000};
		System.out.println(s.solution(3, times1));
	}

	public long solution(int n, int[] times) {
        long answer = Long.MAX_VALUE;
        long left = 0;
        long right = 0;
        for(int i=0; i<times.length; i++) {
        	if(right<times[i]) {
        		right = times[i];
        	}
        }
        
        right*=n;
        
        while(left<=right) {
        	long mid = (left+right)/2;
        	long nCheck = check(times, mid);

        	if(nCheck>=n) {
        		answer = Math.min(answer, mid);
        		System.out.println(answer);
        		right = mid-1;
            } else {
              	left = mid+1;
            }
        }
        
        return answer;
    }
	
	public static long check(int[] times, long mid) {
		long sum = 0;
		for(int i=0; i<times.length; i++) {
			sum += mid/times[i];
		}
		return sum;
	}
}


```

