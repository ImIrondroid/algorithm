# PRO_카펫


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		System.out.println(solution.solution(10, 2));
	}
	
	public int[] solution(int brown, int red) {
        int[] answer = new int[2];
        int num = brown+red;
        
        ArrayList<Integer> list = divide(num);
        
        for(int i=0; i<list.size(); i++) {
        	int width = list.get(i);
        	int height = num/width;

        	if(width<height) continue;

    		System.out.println(width+" "+height);
    		
        	if(check(width,height,brown,red)) {
        		answer[0] = width;
        		answer[1] = height;
        		break;
        	}
        }
        
        return answer;
    }
	
	public boolean check(int width, int height,int brown, int red) {
		int sum = brown + red;
		int temp = brown + red;
		
		for(int i=0; i<height; i++) {
			for(int j=0; j<width; j++) {
				if(i==0 || j==0 || i==height-1 || j==width-1) temp--;
			}
		}
		if(sum-temp == brown && temp == red) return true;
		else return false;
	}
	
	public ArrayList<Integer> divide(int num) {
		ArrayList<Integer> list = new ArrayList<>();
		int copy = num;
		int divide = 1;
		while(copy!=0) {
			if(divide==num/2) break;
			if(copy%divide==0) list.add(copy/divide);
			divide++;
		}
		return list;
	}
} 


```

