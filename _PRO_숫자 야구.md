# PRO_숫자 야구


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[][] arr = {{123,1,1},{356,1,0},{327,2,0},{489,0,1}};
		System.out.println(solution.solution(arr));
	}
	
	public int solution(int[][] baseball) {
		
        int answer = 0;
        
        for(int i=100; i<988; i++) {
        	
        	String num = String.valueOf(i);
        	int first = num.charAt(0)-48;
        	int second = num.charAt(1)-48;
        	int third = num.charAt(2)-48;
        	
        	if(first==second) continue;
        	if(second==third) continue;
        	if(first==third) continue;
        	if(first==0 || second==0 || third==0) continue;

    		System.out.println(i);
        	int count = 0;
        	
        	for(int j=0; j<baseball.length; j++) {
        		
        		int strike = baseball[j][1];
        		int ball = baseball[j][2];
       		
        		int[] result = check(i, baseball[j][0]);
        
        		if(strike==result[0] && ball==result[1]) { 
        			count++;
        		} else {
        			break;
        		}
        	}
        	
        	if(count==baseball.length) {
        		answer++;
        	}
        }
        return answer;
    }
	
	static int[] check(int a, int b) {
		String num1 = String.valueOf(a);
		String num2 = String.valueOf(b);
		int strike = 0;
		int ball = 0;
		for(int i=0; i<num1.length(); i++) {
			for(int j=0; j<num2.length(); j++) {
				if(i==j && num1.charAt(i)==num2.charAt(j)) {
					strike++;
				} else if(i!=j && num1.charAt(i)==num2.charAt(j)){
					ball++;
				}
			}
		}
		return new int[] {strike, ball};
	}
} 


```

