# PRO_무지의 먹방 라이브


구현


```java


public class Solution {
	
        public int solution(int[] food_times, long k) {
        int answer = 0;
        long total = 0;
        
        PriorityQueue<Food> queue_time = new PriorityQueue<>(new Comparator<Food>() {
        	@Override
        	public int compare(Food o1, Food o2) {
        		return o1.time - o2.time;
        	}
		});
        
        PriorityQueue<Food> queue_index = new PriorityQueue<>(new Comparator<Food>() {
        	@Override
        	public int compare(Food o1, Food o2) {
        		return o1.index - o2.index;
        	}
		});
        
        for(int i=0; i<food_times.length; i++) {
        	total += food_times[i];
        	queue_time.add(new Food(i+1, food_times[i]));
        }
        
        if(total<=k) return -1;
        
        long size = queue_time.size();
        int eachtime = 0;
        long remain = 0;
        long alltime = 0;
        Food food;
        outer : while(true) {
        	food = queue_time.peek();
        	remain = k - alltime;
        	food.time -= eachtime;
        	
        	if(food.time * size <= remain) {
        		queue_time.poll();
        		if(food.time * size < remain) {
        			alltime += food.time * size;
        			eachtime += food.time;
        			size--;
        		} else {
        			queue_index.addAll(queue_time);
        			answer = queue_index.peek().index;
             		break outer;        			
        		}
        	} else {
    			queue_index.addAll(queue_time);
    			remain %= size;
    			while(true) {
    				food = queue_index.poll();
    				if(remain == 0) {
    					answer = food.index;
                 		break outer;        			
    				}
    				remain--;
    			}
        	}
        }	
        
        return answer;
	}
	
	class Food {
		int time;
		int index;
		Food(int index, int time) {
			this.index = index;
			this.time = time;
		}
	}
}


```

