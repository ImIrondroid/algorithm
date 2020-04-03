# PRO_징검다리 건너기


```java


class Solution {
	
	static int min = Integer.MAX_VALUE;
	static int max = Integer.MIN_VALUE;
	
	public int solution(int[] stones, int k) {
	
        int start = stones[0];
		int end = stones[0];
		
        for(int i=0; i<stones.length; i++) {
        	start = Math.min(start, stones[i]);
        	end = Math.max(end, stones[i]);
        }
        
        search(stones, start, end, k,0);
        
        return min;
    }
	
	public void search(int[] stones, int left, int right, int k, int toss) {
		if(left>right) {
			System.out.println(toss);
			return;
		}
		int mid = (left+right)/2;
		boolean flag = check(stones,mid,k);
		System.out.println(mid+"  "+flag);
		if(flag) {
			max = Math.max(max, mid);
			search(stones, mid+1, right, k, max);
		} else {
			min = Math.min(min, mid);
			search(stones, left, mid-1, k, min);
		}
	}
	
	//내 생각에분명히 여기가 문제임 너무 좆밥같이 체크하는중
	public boolean check(int[] stones, int mid, int k) {
		int count = 0;
		for(int i=0; i<stones.length; i++) {
			
			if(count==k) {
				return false;
			}
			
			stones[i] -= mid;
			if(stones[i]<=0) count++;
			else count = 0;
			stones[i] += mid;
		}
		return true;
	}
}


```

