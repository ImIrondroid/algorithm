# PRO_주식가격


//스택


```java


import java.util.*;


class Solution {


    public int[] solution(int[] prices) {
		
        int cycle = prices.length;
        int[] answer = new int[cycle];
        Stack<Point> stack = new Stack<>();
    
        for(int i=0; i<cycle; i++) {
        	while(!stack.isEmpty() && stack.peek().price > prices[i]) {
        		Point point = stack.pop();
        		answer[point.time] = i - point.time;
        	}
        	stack.push(new Point(prices[i], i));
        }
        while(!stack.isEmpty()) {
        	Point point = stack.pop();
        	answer[point.time] = cycle - point.time - 1;
        }
        
        return answer;
    }
}


class Point{
    int time;
    int price;
    Point(int price, int time){
        this.price = price;
        this.time = time;
    }
}



```

