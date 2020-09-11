# PRO_키패드 누르기


```java


public class Solution {

	public String solution(int[] numbers, String hand) {
        StringBuilder sb = new StringBuilder();
    	int[][] keypad = {{1,2,3}, {4,5,6}, {7,8,9}, {10,11,12}};
        int left = 10;
        int right = 12;
        for(int i=0; i<numbers.length; i++) {
        	int num = numbers[i];
        	if(num == 1 || num == 4 || num == 7) {
        		sb.append("L");
        		left = num;
        	} else if(num == 3 || num == 6 || num == 9) {
        		sb.append("R");
        		right = num;
        	} else {
        		if(num == 0) num = 11;
        		int leftDis = Math.abs((num-1)/3 - (left-1)/3) + Math.abs((num-1)%3 - (left-1)%3);
        		int rightDis = Math.abs((num-1)/3 - (right-1)/3) + Math.abs((num-1)%3 - (right-1)%3);
        		if(leftDis == rightDis) {
        			if(hand.equals("right")) {
        				sb.append("R");
        				right = num;
            		} else {
                		sb.append("L");
                		left = num;
            		}
        		} else {
        			if(leftDis > rightDis) {
                		sb.append("R");
        				right = num;
        			} else {
                		sb.append("L");
                		left = num;
        			}
        		}
        	}
        }
        return sb.toString();
    }
}


```

