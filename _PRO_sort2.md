# PRO_sort2


```java


import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;

public class Main {	

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
		//sample
		int[] arr = {20,0,0};
		
		System.out.println(solution(arr));
	}
	
	 static String solution(int[] numbers) {
	       	
			String answer = "";
			String[] arr = new String[numbers.length];
			
			//int배열 -> String배열 옮기기 작업
			for(int i=0; i<arr.length; i++) {
				arr[i] = String.valueOf(numbers[i]);
			}
			
			//comparator 사용하기 위하여
			Arrays.sort(arr, new Comparator<String>() {
				@Override
				public int compare(String o1, String o2) {
					
					return (o2+o1).compareTo(o1+o2);
				}
			});
			
			//내림차순 했는데도 불구하고 맨 앞의 숫자가 0이면 
			if(arr[0].equals("0")) {
				answer+="0";
			} else {
				for(int i=0; i<numbers.length; i++) {
					answer+=arr[i];
				}
			}
			
			return (answer.equals("0")) ? "0" : answer;
	    }
}


```

