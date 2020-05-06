# PRO_길 찾기 게임


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr = {{5,3},{11,5},{13,3},{3,5},{6,1},{1,3},{8,6},{7,2},{2,2}};
		System.out.println(s.solution(arr));
	}

	public int[][] solution(int[][] nodeinfo) {
        
        List<Node> list = new ArrayList<Node>();
        for(int i=0; i<nodeinfo.length; i++) {
        	list.add(new Node(nodeinfo[i][0], nodeinfo[i][1], i+1));
        }
        
        //https://gmlwjd9405.github.io/2018/09/06/java-comparable-and-comparator.html
        Collections.sort(list);

        //이진트리 구성하기
        Node root = list.get(0);
        List<Node> order = new ArrayList<Node>();
        for(int i=1; i<list.size(); i++) {
        	binarySearch(root, list.get(i));
        }
        
        //결과 저장
        int[][] answer = new int[2][list.size()];

        List<Node> retList = new ArrayList<Node>();
        preorder(root, retList);
        setResult(answer[0], retList);
        
        //list 초기화
        retList.clear();
        
        postorder(root, retList);
        setResult(answer[1], retList);
        return answer;
	}
	
	static void setResult(int[] answer, List<Node> list) {
		for(int i=0; i<answer.length; i++) {
			answer[i] = list.get(i).num;
			//System.out.print(answer[i]+" ");
		}
		//System.out.println();
	}
	
	static void binarySearch(Node root, Node node) {
		
		if(root.x > node.x) {
			if(root.left==null) root.left = node;
			else binarySearch(root.left, node);
		} else {
			if(root.right==null) root.right = node;
			else binarySearch(root.right, node);
		}
	}
	
	static void preorder(Node node, List<Node> list) {
		list.add(node);
		if(node.left!=null) {
			preorder(node.left, list);
		}
		
		if(node.right!=null) {
			preorder(node.right, list);
		}
	}
	
	static void postorder(Node node, List<Node> list) {
		if(node.left==null && node.right==null) {
			list.add(node);
			return;
		}
		
		if(node.left!=null) {
			postorder(node.left, list);
		} 
		if(node.right!=null){
			postorder(node.right, list);
		}
		list.add(node);
	}
}

class Node implements Comparable<Node> {
	int x;
	int y;
	int num;
	Node left = null;
	Node right = null;
	Node(int x, int y, int num) {
		this.x = x;
		this.y = y;
		this.num = num;
	}
	
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return "("+x+","+y+")";
	}
	
	@Override
	public int compareTo(Node o) {
		//return 1일때 자리바꿈
		if(this.y < o.y) return 1;
		else if(this.y > o.y) return -1;
		else {
			if(this.x > o.x) return 1;
			else return -1;
		}
	}
}


```

