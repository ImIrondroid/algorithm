# PRO_기지국 설치


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int arr[] = {4,11};
		System.out.println(s.solution(11,arr,1));
	}

	public int solution(int n, int[] stations, int w) {
        int answer = 0;

        int start = 1;
        for(int i=0; i<stations.length; i++) {
        	if(start < stations[i]-w ) {
        		int space = stations[i]-w-start;
        		answer += space/(2*w+1);
        		if(space%(2*w+1)!=0) answer+=1;
        	}
        	start = stations[i]+w+1;
        }

        if(start<=n) {
            int rest = n-stations[stations.length-1]-w;
            answer += rest/(2*w+1);
    		if(rest%(2*w+1)!=0) answer+=1;
        }
        
        return answer;
    }
}


```

