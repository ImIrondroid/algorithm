# SWEA_백만 장자 프로젝트


```java


import java.util.*;


class Solution
{
	public static void main(String args[]) throws Exception {
		
		Scanner sc = new Scanner(System.in);
		
		int T;
		
		T=sc.nextInt();
		
		for(int test_case = 1; test_case <= T; test_case++) {
		
			int size = sc.nextInt();
			long sum = 0;
			int[] arr = new int[size];
			int[] max = new int[size];
			
			for(int i=0; i<size; i++) {
				arr[i] = sc.nextInt();
			}
			
			max[size-1] = Integer.MAX_VALUE;
			
			for(int i=size-1; i>=0; i--) {
				
				if(i==size-1) {
					if(arr[i-1]<arr[i]) max[i-1] = arr[i];
					else if(arr[i-1]>=arr[i]) max[i-1] = arr[i-1];
					continue;
				} else if(i==0) {
					break;
				}
				
				if(arr[i-1]<max[i]) {
					max[i-1] = max[i];
				} else {
					max[i-1] = arr[i-1];
				}
			}
			
			for(int i=0; i<size-1; i++) {
				if(max[i]!=0) {
					sum += (max[i] - arr[i]);
				}
			}
			
			System.out.println("#"+test_case+" "+sum);
		}
	}
}


```

