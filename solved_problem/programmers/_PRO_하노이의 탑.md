# PRO_하노이의 탑


```java


import java.util.*;
import java.io.IOException;


public class Solution {
	
	public static void main(String[] args) throws IOException {
		Solution s = new Solution();
		System.out.println(s.solution(3));
	}

	public int[][] solution(int n) {
		List<int[]> ret = new ArrayList<int[]>();
        hanoi(n, 1, 2, 3, ret);

		int[][] answer = new int[ret.size()][2];
        for(int i=0; i<ret.size(); i++) {
        	int[] result = ret.get(i);
        	answer[i][0] = result[0];
        	answer[i][1] = result[1];
        	//System.out.println(result[0]+" "+result[1]);
        }
		return answer;
    }
	
	//start, end만 생각하기
	static void hanoi(int count, int start, int mid, int end, List<int[]> ret) {
		if(count==1) {
			//원반이 한개 남으면 3번으로 옮기기
			ret.add(new int[] {start, end});
			return;
		}
		
		//1번에서 2번으로 n-1개 옮기기
		hanoi(count-1, start, end, mid, ret);
		
		//1번에 남아있는 가장 큰 원반을 3번으로 옮기기
		ret.add(new int[] {start, end});
		
		//2번에서 3번으로 n-1개 옮기기
		hanoi(count-1, mid, start, end, ret);
	}
}


```

