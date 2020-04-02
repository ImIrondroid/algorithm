# PRO_문자열 내 p와 y의 개수


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution("PyyY"));
	}
	
	boolean solution(String s) {

        boolean answer = true;
        
		int[] store = new int[2];
		String lowerStr = s.toLowerCase();
		
		for(int i=0; i<lowerStr.length(); i++) {
			if(lowerStr.charAt(i)=='p') {
				store[0]++;
			} else if(lowerStr.charAt(i)=='y') {
				store[1]++;
			}
		}

        return (store[0]==store[1])? true : false;
    }
}


```

