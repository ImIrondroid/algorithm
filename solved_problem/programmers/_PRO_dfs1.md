# PRO_dfs1


```java


import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {	

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
		int[] arr = {1,1,1,1,1};
		System.out.println(solution(arr, 3));
	}
	
	static int count = 0;
	
	static int solution(int[] numbers, int target) {
		
        int answer = 0;
        
        solve(numbers, target, 0, 0);

        answer = count;
        
        return answer;
    }
	
	static void solve(int[] numbers, int target, int start, int sum) {
		
		if(start==numbers.length) {
			if(sum==target) count++;
			return;
		} 
		
		solve(numbers, target, start+1, sum+numbers[start]);
		solve(numbers, target, start+1, sum-numbers[start]);
	}
}


```

