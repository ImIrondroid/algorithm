# PRO_저울


```java



import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Arrays;

public class Main {	

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
		int[] arr = {4,4,4,5,2,2};
		
		System.out.println(Arrays.toString(solution(arr)));
	}
	
	static int[] solution(int[] answers) {
        int[] answer = {};
        
        int[] a = new int[] {1,2,3,4,5};
        int[] b = new int[] {2,1,2,3,2,4,2,5};
        int[] c = new int[] {3,3,1,1,2,2,4,4,5,5};
        
        //Map을 대신하는 
        int[] studentKey = {1,2,3};
        int[] studentCount = {0,0,0};
        
        int temp = 0; //swap
        
        for(int i=0; i<answers.length; i++) {
        	if(answers[i]-a[i%5]==0) {
        		studentCount[0]++;
        	}
        	if(answers[i]-b[i%8]==0) {
        		studentCount[1]++;
        	}
        	if(answers[i]-c[i%10]==0) {
        		studentCount[2]++;
        	}
        }
        
        //버블정렬을 이용해 내림차순 으로 만들기
        for(int i=0; i<studentKey.length; i++) {
        	for(int j=0+i; j<studentKey.length-1; j++) {
        		if(studentCount[j]<studentCount[j+1]) {
        			temp = studentCount[j];
        			studentCount[j] = studentCount[j+1];
        			studentCount[j+1] = temp;
        			
        			temp = studentKey[j];
        			studentKey[j] = studentKey[j+1];
        			studentKey[j+1] = temp;
        		}
        	}
        }
        
        //size 동적으로 이용하기 위한 방법
        ArrayList list = new ArrayList();
        
        //첫 인덱스 값을 이용하여 최고점수 값만 표현 or 동점 표시하기 위함
        int init = studentCount[0];
        
        for(int i=0; i<studentKey.length; i++) {
          	if(init == studentCount[i]) {
          		list.add(studentKey[i]);
          	} else {
          		break;
          	}
        } 
      
        answer = new int[list.size()];
        
        for(int i=0; i<answer.length; i++) {
        	answer[i] = (int) list.get(i);
        }
        		
        return answer;
    }

	static int[] solution1(int[] answers) {
	    int[] player1 = {1, 2, 3, 4, 5};//5
	    int[] player2 = {2, 1, 2, 3, 2, 4, 2, 5};// 8
	    int[] player3 = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};// 10
	    int[] answer = new int[]{0,0,0};
	    int maxNum = 0;
	    ArrayList<Integer> countNum = new ArrayList();

	    for (int i = 0; i < answers.length; i++) {
	        if (answers[i] == player1[i % 5]) {
	            answer[0]++;
	        }

	        if (answers[i] == player2[i % 8]) {
	            answer[1]++;
	        }

	        if (answers[i] == player3[i % 10]) {
	            answer[2]++;
	        }
	    }

	    for (int i : answer) {
	        if (i > maxNum) {
	            maxNum = i;
	        }
	    }

	    for (int i = 0; i < 3; i++) {
	        if (answer[i] == maxNum) {
	            countNum.add(i+1);
	        }
	    }
	    return countNum.stream().mapToInt(i->i).toArray();
	}

}


```

