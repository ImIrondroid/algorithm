# PRO_이중우선순위큐


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"I 16","D 1"};
		String[] arr1 = {"I 7","I 5","I -5","D -1"};
		String[] arr2 = {"I -45", "I 653", "D 1", "I -642", "I 45", "I 97", "D 1", "D -1", "I 333"};
		String[] arr3 = {"I 16", "I -5643", "D -1", "D 1", "D 1", "I 123", "D -1"};
		System.out.println(s.solution(arr3));
	}

	public int[] solution(String[] operations) {
		
        int[] answer = new int[2];
        int qSize = 0;
        
        Queue<Integer> queue = new PriorityQueue<Integer>(Collections.reverseOrder());
        
        for(int i=0; i<operations.length; i++) {
        	String[] arr = operations[i].split(" ");
        	if(arr[0].equals("I")) {
        		queue.add(Integer.valueOf(arr[1]));
        		qSize++;
        	} else if(arr[0].equals("D")) {
        		if(qSize==0) continue;
        		if(arr[1].equals("1")) {
        			//최댓값 삭제
        			queue.poll();
        		} else {
        			//최솟값 삭제
        		}
        		qSize--;
        	}
        }
        if(qSize==0) {
        	answer[0] = 0;
        	answer[1] = 0;

            //System.out.println(answer[0]+" "+answer[1]);
        } else {
        	answer[0] = queue.peek();
            
            int count = 0;
            while(true) {
            	count++;
            	int min = queue.poll();
            	if(count==qSize) {
            		answer[1] = min;
            		break;
            	}
            }

            //System.out.println(answer[0]+" "+answer[1]);
        }
        
        return answer;
    }
}


```

