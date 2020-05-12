# PRO_멀쩡한 사각형


```java


import java.util.*;


class Solution {

	public static void main(String[] args) {
		
		//https://programmers.co.kr/learn/courses/30/lessons/62048
		Solution solution = new Solution();
		System.out.println(solution.solution(8,12));
	}

	public long solution(int w,int h) {
		long answer = 0;
		
		for(int i=0; i<w; i++) {
			
			answer += (long)h*i / (long)w;
		}
		return answer*2;
	}
}


```

