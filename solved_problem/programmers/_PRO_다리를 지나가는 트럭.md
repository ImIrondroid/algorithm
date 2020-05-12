# PRO_다리를 지나가는 트럭


//큐


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(2, 10, new int[] {7,4,5,6}));
	}
	
	
	public int solution(int bridge_length, int weight, int[] truck_weights) {
		int answer = 0;
		int index = 0;
		int sum = 0;
		Queue<Truck> done = new LinkedList<Truck>();
		Queue<Truck> doing = new LinkedList<Truck>();
		
		while(done.size() != truck_weights.length) {
			
			for(Truck truck : doing) {
				truck.time++;
			}
			
			if(!doing.isEmpty() && doing.peek().time >= bridge_length) {
				Truck truck = doing.poll();
				sum -= truck.weight;
				done.add(truck);
			}
			
			while(index<=truck_weights.length-1 && 
					doing.size() <= bridge_length && 
					sum+truck_weights[index]<=weight) {
				sum += truck_weights[index];
				doing.add(new Truck(truck_weights[index++], 0));
			}
		
			answer++;
		}
		
		return answer;
	}
}

class Truck {
	int weight;
	int time;
	Truck(int weight, int time) {
		this.weight = weight;
		this.time = time;
	}
}


```

