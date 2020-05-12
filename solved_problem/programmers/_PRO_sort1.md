# PRO_sort1


```java


import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {	

	
	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int[] array = {1, 5, 2, 6, 3, 7, 4};
		int[][] commands = {{2, 5, 3}, {4, 4, 1}, {1, 7, 3}};
		
		System.out.println(Arrays.toString(solution(array,commands)));
	}
	
	static int[] solution(int[] array, int[][] commands) {
		
	    int[] answer = {};
	    int[] result = new int[commands.length];
	   
	    int i = 0;
	    int j = 0;
	    int k = 0;
	    
	    for(int index=0; index<commands.length; index++) {
	    	
	    	// i : 2, j : 5, k : 3
	    	i = commands[index][0];
	    	j = commands[index][1];
	    	k = commands[index][2];
	    	int tempPos = 0;
	    	int[] subanswer = new int [j-i+1];
	    	 
	    	for(int sub = i-1 ; sub < j ; sub++) {
	    		subanswer[tempPos] = array[sub];
	    		tempPos++;
	    	}
	    	
	    	Arrays.sort(subanswer);
	    	
	    	result[index] = subanswer[k-1];
	    }
	    
	    answer = result;
	    
	    return answer;
	}
}


```

