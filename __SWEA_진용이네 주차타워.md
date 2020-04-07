# SWEA_진용이네 주차타워


```java


import java.util.*;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
	
public class Main {
	
	static int TC;
	
	static long[][] dp = new long[31][31];
	
	public static void main(String[] args) throws IOException {
	
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
		
		TC = Integer.valueOf(br.readLine());
	
		for(int k=0; k<TC; k++) {
			st = new StringTokenizer(br.readLine());
			int n = Integer.valueOf(st.nextToken());
			int m = Integer.valueOf(st.nextToken());
			
			boolean[] visit = new boolean[n];
			int[] enter = new int[n];
			int[] fee = new int[n];
			int[] cars = new int[m];
			
			Queue<Integer> queue = new LinkedList<Integer>();
			Queue<Integer> extra = new LinkedList<Integer>();
			
			for(int i=0; i<n; i++) {
				fee[i] = Integer.valueOf(br.readLine());
			}
			for(int i=0; i<m; i++) {
				cars[i] = Integer.valueOf(br.readLine());
			}
			for(int i=0; i<2*m; i++) {
				queue.add(Integer.valueOf(br.readLine()));
			}

			boolean useExtra = false;
			int allfee = 0;	
			while(!queue.isEmpty()) {	
				int index = check(visit);
				int car = 0;
				if(useExtra) {
					car = extra.poll();
					useExtra = false;
				} else {
					car = queue.poll();
				}	
				if(index!=-1) {
					if(car>0) {
						visit[index] = true;
						enter[index] = car;
						allfee += cars[car-1]*fee[index];
					} else {
						int carIdx = -1;
						for(int j=0; j<visit.length; j++) {
							if(enter[j]==Math.abs(car)) {
								carIdx = j;
								break;
							}
						}
						if(carIdx==-1) {
							queue.add(car);
						} else {
							visit[carIdx] = false;
						}
					}
				} else {
					if(car>0) { 
						extra.add(car);
					} else {
						int carIdx = -1;
						for(int j=0; j<visit.length; j++) {
							if(enter[j]==Math.abs(car)) {
								carIdx = j;
								break;
							}
						}
						if(carIdx==-1) {
							queue.add(car);
						} else {
							visit[carIdx] = false;
						}
						
						if(!extra.isEmpty()) useExtra = true;
					}
				}
			}
			
			System.out.println("#"+(k+1)+" "+allfee);
		}
	}
	
	public static int check(boolean[] visit) {
		int count = 0;
		int index = 0;
		for(int i=0; i<visit.length; i++) {
			if(!visit[i]) {
				index = i;
				break;
			} else {
				count++;
			}
		}
		
		if(count==visit.length) {
			return -1;
		} else {
			return index;
		}
	}
}


```

