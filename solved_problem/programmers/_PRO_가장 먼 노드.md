# 가장 먼 노드


//인접 리스트 통과 / 인접 행렬 실패(시간초과)


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr = {{3,6},{4,3},{3,2},{1,3},{1,2},{2,4},{5,2}};
		int[][] arr1 = {{1,5},{2,3},{4,5}};
		System.out.println(s.solution(6, arr));
	}

	public int solution(int n, int[][] edge) {
        int answer = 0;
      
        ArrayList<ArrayList<Integer>> list = new ArrayList<ArrayList<Integer>>();
        
        for(int i=0; i<n+1; i++) {
        	list.add(new ArrayList<Integer>());
        }
        
        int x,y;
        for(int i=0; i<edge.length; i++) {
        	x = edge[i][0];
        	y = edge[i][1];
        	list.get(x).add(y);
        	list.get(y).add(x);
        }
    	
        Queue<Node> q = new LinkedList<Node>();
        
        int[] edgeArr = new int[n+1];
        boolean[] vCheck = new boolean[n+1];
        
        vCheck[1] = true;
        for(int i=0; i<list.get(1).size(); i++) {
        	q.add(new Node(list.get(1).get(i), 1));
        	vCheck[list.get(1).get(i)] = true;
        	edgeArr[1]++;
        }
        
        while(!q.isEmpty()) {
        	Node node = q.poll();
        	int next = node.next;
        	for(int i=0; i<list.get(next).size(); i++) {
        		int nodeNum = list.get(next).get(i);
        		if(!vCheck[nodeNum]) {
        			q.add(new Node(nodeNum, node.val+1));
            		edgeArr[node.val+1]++;
                	vCheck[nodeNum] = true;
        		}
        	}
        }
        
        int idx = -1;
        for(int i=1; i<=n; i++) {
        	if(edgeArr[i]==0) {
        		idx = i;
        		break;
        	}
        }
        
        if(idx==-1) return edgeArr[n];
        else return edgeArr[idx-1];
    }
}

class Node {
	int next;
	int val;
	Node(int next, int val) {
		this.next = next;
		this.val = val;
	}
}


```

