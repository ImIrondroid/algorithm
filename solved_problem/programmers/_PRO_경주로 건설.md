# PRO_경주로 건설


BFS, Dijkstra


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Solution {
	
	static boolean[][] visit;
	static int[][] result;

	static int[] dx = {0,1,0,-1};
	static int[] dy = {1,0,-1,0};
	static int[] dir = {1,2,3,4};
	
	public int solution(int[][] board) {
        int length = board.length;
        
        visit = new boolean[length][length];
        result = new int[length][length];
        for(int i=0; i<result.length; i++) Arrays.fill(result[i], Integer.MAX_VALUE);
        
        bfs(board);
        
        return result[length-1][length-1];
    }
	
	void print() {
		int length = result.length;
        for(int i=0; i<length; i++) {
        	for(int j=0; j<length; j++) {
        		if(result[i][j] == Integer.MAX_VALUE) System.out.print("INF"+" ");
        		else System.out.print(result[i][j]+" ");
        	}
        	System.out.println();
        }
	}
	
	void bfs(int[][] board) {
		
		Queue<Car> queue = new LinkedList<Solution.Car>();
		int length = board.length;
		
		queue.add(new Car(0, 0, 1, 0));
		queue.add(new Car(0, 0, 2, 0));
		result[0][0] = 0;
		visit[0][0] = true;
		
		int nextX = 0;
		int nextY = 0;
		int nextDir = 0;
		int nextValue = 0;
		while(!queue.isEmpty()) {
			Car car = queue.poll();	
			for(int i=0; i<4; i++) {
				nextX = car.x + dx[i];
				nextY = car.y + dy[i];
				nextDir = dir[i];
				nextValue = car.value + 100;
				if(car.dir != nextDir) nextValue += 500;
				
				if(isNotRange(nextX, nextY, length)) continue;
				if(board[nextX][nextY] == 1) continue;
				if(!visit[nextX][nextY] || result[nextX][nextY] >= nextValue) {
					result[nextX][nextY] = nextValue;
					visit[nextX][nextY] = true;
					queue.add(new Car(nextX, nextY, nextDir, nextValue));
				}
			}
		}
	}
	
	boolean isNotRange(int x, int y, int length) {
		return x < 0 || y < 0 || x >= length || y >= length ? true : false;
	}
	
	class Car {
		int x;
		int y;
		int dir;
		int value; 
		Car(int x, int y, int dir, int value) {
			this.x = x;
			this.y = y;
			this.dir = dir;
			this.value = value;
		}
	}
}


```

