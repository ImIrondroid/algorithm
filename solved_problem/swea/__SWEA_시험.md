# SWEA_시험


```java


import java.util.*;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
	
public class Main {
	
	public static void main(String args[]) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
		int Tc = Integer.valueOf(br.readLine());

		for(int test_case = 1; test_case <= Tc; test_case++) {
			st = new StringTokenizer(br.readLine());
			int N = Integer.valueOf(st.nextToken());
			int T = Integer.valueOf(st.nextToken());
			int P = Integer.valueOf(st.nextToken());
			
			int[][] arr = new int[N][T];
			for(int i=0; i<N; i++) {
				st = new StringTokenizer(br.readLine());
				for(int j=0; j<T; j++) {
					arr[i][j] = Integer.valueOf(st.nextToken());
				}
			}
			int[] scores = new int[T];
			for(int i=0; i<T; i++) {
				int count = 0;
				for(int j=0; j<N; j++) {
					if(arr[j][i]==0) count++;
				}
				scores[i] = count;
			}
			
			int[] allscores = new int[N];
			int[] allanswers = new int[N];
			for(int i=0; i<N; i++) {
				int sum = 0;
				int count = 0;
				for(int j=0; j<T; j++) {
					if(arr[i][j]==1) {
						count++;
						sum += scores[j];
					}
				}
				allanswers[i] = count;
				allscores[i] = sum;
			}
			
			List<Student> list = new ArrayList<Student>();
			for(int i=0; i<N; i++) {
				list.add(new Student(allscores[i], allanswers[i], i+1));
			}
			
			Collections.sort(list);
			
			for(int i=0; i<N; i++) {
				if(list.get(i).index==P) {
					System.out.println("#"+test_case+" "+list.get(i).allscore+" "+(list.size()-i));
					break;
				}
			}
		}
	}
}

class Student implements Comparable<Student> {
	
	int allscore;
	int allanswer;
	int index;
	
	Student(int allscore, int allanswer, int index) {
		this.allscore = allscore;
		this.allanswer = allanswer;
		this.index = index;
	}

	@Override
	public int compareTo(Student o) {
		if(this.allscore > o.allscore) return 1;
		else if(this.allscore == o.allscore) {
			if(this.allanswer > o.allanswer) return 1;
			else if(this.allanswer == o.allanswer) {
				if(this.index < o.index) return 1;
				else if(this.index == o.index) return 0;
				else return -1;
			} else return -1;
		} else return -1;
	}
}


```

