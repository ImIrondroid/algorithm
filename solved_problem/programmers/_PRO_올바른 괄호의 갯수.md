# PRO_올바른 괄호의 갯수


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Practice {
	
	public static void main(String[] args) throws NumberFormatException, IOException {
		Practice main = new Practice();
		System.out.println(main.solution(14));
	}
	
	//(2 * n) ! / (n! * n! * n)
	
	public int solution(int n) {
        long answer = 1;
        for(int i=2*n; i>n; i--) {
        	answer *= i;
        }
        for(int i=2; i<=n+1; i++) {
        	answer /= i;
        }
        return (int) answer;
    }
}


```

