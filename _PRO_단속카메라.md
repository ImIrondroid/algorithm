# PRO_단속카메라


```java


import java.io.IOException;
import java.util.*;


class Solution {
	 
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] routes = {{-20,-15},{-14,-5},{-18,-13},{-5,-3}};
		System.out.println(s.solution(routes));
	}

	public int solution(int[][] routes) {
        int answer = 0;

        Arrays.sort(routes, new Comparator<int[]>() {
			@Override
			public int compare(int[] o1, int[] o2) {
				return o1[1]-o2[1];
			}
		});
        
        int point = Integer.MIN_VALUE;
        for(int i=0; i<routes.length; i++) {
        	if(point < routes[i][0]) {
        		point = routes[i][1];
        		answer++;
        	}
        }
        
        return answer;
    }
}


```

