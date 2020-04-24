# PRO_예상 대진표


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(8, 4, 7));
	}
	
	public int solution(int n, int a, int b) {
        int answer = 1;

        while(n>0) {
        	int A = (1+a)/2;
        	int B = (1+b)/2;
        	if(A==B) break;
        	else {
        		a = A;
        		b = B;
        	}
        	n/=2;
        	answer++;
        }

        return answer;
    }


```

