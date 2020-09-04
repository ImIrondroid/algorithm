# PRO_도둑질


동적 계획법


```java


class Solution {
    
	public int solution(int[] money) {
        int answer = 0;
        int lth = money.length;
        int[] dp1 = new int[lth-1]; //첫 번째 돈 훔친 경우, 마지막 집 돈 못 훔침
        int[] dp2 = new int[lth];   //첫 번째 돈 훔치지 않은 경우, 마지막 집 돈 훔칠 수 있음

        dp1[0] = dp1[1] = money[0];
        dp2[0] = 0;
        dp2[1] = money[1];
        
        for(int i=2; i<lth-1; i++) {
        	dp1[i] = Math.max(dp1[i-1], dp1[i-2] + money[i]);
        }
        
        for(int i=2; i<lth; i++) {
        	dp2[i] = Math.max(dp2[i-1], dp2[i-2] + money[i]);
        }
        
        return Math.max(dp1[lth-2], dp2[lth-1]);
    }
}


```

