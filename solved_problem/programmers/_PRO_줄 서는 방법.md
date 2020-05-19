# PRO_줄 서는 방법


```java


import java.util.*;
import java.io.IOException;


public class Solution {
	
	public static void main(String[] args) throws IOException {
		Solution s = new Solution();
		System.out.println(s.solution(3, 5));
	}

	public int[] solution(int n, long k) {
        long factorial = 1L;
        long div = n;
        int[] answer = new int[n];
        List<Integer> list = new ArrayList<Integer>();
        for(int i=1; i<=n; i++) {
        	list.add(i);
        	factorial*=Long.valueOf(i);
        }
        
        int idx = 0;
        long rest = k-1;
        while(true) {
        	if(list.size()==0) break;
        	factorial/=div;
        	int target = (int) (rest/factorial);
        	answer[idx++] = list.get(target);
        	list.remove(target);
        	rest%=factorial;
        	div--;
        }
        return answer;
    }
}


```

