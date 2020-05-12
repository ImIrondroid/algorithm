# PRO_점프와 순간 이동


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(5000));
	}

	public int solution(int n) {
		int ans = 0;
		
		while(n>1) {
			if(n%2==1) {
				n--;
				ans++;
			}
			n/=2;
		}
		
		return ans+1;
	}
	
	//시간초과
	public int solution1(int n) {
        int ans = 0;
        Queue<Point> queue = new LinkedList<Point>();
        queue.add(new Point(0, 0));
        
        while(!queue.isEmpty()) {
        	Point p = queue.poll();
        	if(p.now!=n) {
        		if(2*p.now > p.now) queue.add(new Point(2*p.now, p.battery));
        		queue.add(new Point(p.now+1, p.battery+1));
        	} else {
        		ans = p.battery;
        		System.out.println(234);
        		break;
        	}
        }
        
        return ans;
    }
}

class Point {
	int now;
	int battery;
	Point(int now, int battery) {
		this.now = now;
		this.battery = battery;
	}
	
	@Override
	public String toString() {
		return now+" "+battery;
	}
}


```

