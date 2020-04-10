# SWEA_코딩 토너먼트 1


```java


import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

class Main
{
	public static void main(String args[]) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
	
		int T = Integer.valueOf(br.readLine());

		for(int test_case = 1; test_case <= T; test_case++) {
			
			int K = Integer.valueOf(br.readLine());
			Queue<Integer> queue = new LinkedList<>();
			
			st = new StringTokenizer(br.readLine());
			for(int i=0; i<Math.pow(2, K); i++) {
				queue.add(Integer.valueOf(st.nextToken()));
			}
			
			int sum = 0;
			while(queue.size() != 1) {
				int left = queue.poll();
				int right = queue.poll();
				
				sum += Math.abs(left-right);
				if(left>=right) queue.add(left);
				else queue.add(right);
			}
			
			System.out.println("#"+test_case+" "+sum);
		}
	}
}


```

