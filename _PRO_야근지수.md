# PRO_야근지수


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[] works = {4,3,3};
		int[] works1 = {2,1,2};
		int[] works2 = {1,1};
		System.out.println(s.solution(4, works));
	}

	public long solution(int n, int[] works) {
        long answer = 0;
        Arrays.sort(works);

        int i = works.length-1;
    	int start = works[i];
        while(true) {
        	if(n==0) break;
        	if(start==works[i]) {
        		works[i]--;
        		i--;
        		n--;
        		if(i<0) {
        			i = works.length-1;
            		start = works[i];
        		}
        	} else {
        		i = works.length-1;
        		start = works[i];
        	}
        	//print(works);
        }
        
        int check = 0;
        for(int idx=0; idx<works.length; idx++) if(works[idx]<=0) check++;
        if(check == works.length) {
        	return 0;
        } else {
        	for (int work : works) {
				answer += Math.pow(work, 2);
			}
            return answer;
        }
    }
	
	public void print(int[] works) {
		for(int i=0; i<works.length; i++) System.out.print(works[i]+" ");
		System.out.println();
	}
}


```

