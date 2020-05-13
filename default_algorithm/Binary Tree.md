# 이진 트리 - Binary Tree

### 이진 트리 특징


1) 가장 많이 사용되는 비선형 자료구조 <-> 선형 자료구조 : 배열, 스택, 큐 등
2) 데이터의 탐색 속도 증진을 위해 사용하는 자료구조(높이 1에 따라 탐색 데이터 1/2로 줄음)
3) 효율적인 공간 사용을 위해 이진 트리는 포인터를 사용하여 구현함
4) 완전 이진 트리가 아닌 이진 트리는 배열로 표현하기 어려움


### 탐색 방법 3가지


##### 전위 순회

1) 먼저 자기자신을 처리합니다.
2) 왼쪽 자식을 방문합니다.
3) 오른쪽 자식을 방문합니다.

##### 중위 순회

1) 왼쪽 자식을 방문합니다.
2) 먼저 자기자신을 처리합니다.
3) 오른쪽 자식을 방문합니다.

##### 후위 순회

1) 왼쪽 자식을 방문합니다.
2) 오른쪽 자식을 방문합니다.
3) 먼저 자기자신을 처리합니다.


### 이진 트리 및 순회 구현


```java


import java.util.*;

public class BinaryTree {

	public static void main(String[] args) {
		Node[] nodes = new Node[16];
		for(int i=1; i<nodes.length; i++) nodes[i] = new Node(i);
		for(int i=2; i<nodes.length; i++) {
			if(i%2==0 ) {
				nodes[i/2].leftChild = nodes[i];
			} else {
				nodes[i/2].rightChild = nodes[i];
			}
		}

		preorder(nodes[1]);
		System.out.println();
		inorder(nodes[1]);
		System.out.println();
		postorder(nodes[1]);
	}
	//전위 순회 구현
	static void preorder(Node node) {
		if(node.data!=-1) {
			System.out.print(node.data+" ");
			if(node.leftChild!=null) preorder(node.leftChild);
			if(node.rightChild!=null) preorder(node.rightChild);
		}
	}
	
	//중위 순회 구현
	static void inorder(Node node) {
		if(node.data!=-1) {
			if(node.leftChild!=null) inorder(node.leftChild);
			System.out.print(node.data+" ");
			if(node.rightChild!=null) inorder(node.rightChild);
		}
	}
	
	//후위 순회 구현
	static void postorder(Node node) {
		if(node.data!=-1) {
			if(node.leftChild!=null) postorder(node.leftChild);
			if(node.rightChild!=null) postorder(node.rightChild);
			System.out.print(node.data+" ");
		}
	}
}

class Node implements Comparable<Node>{
	int data = -1;
	Node leftChild = null;
	Node rightChild = null;	
	Node(int data) {
		this.data = data;
	}
	@Override
	public String toString() {
		return String.valueOf(data);
	}
	@Override
	public int compareTo(Node arg0) {
		return this.data - arg0.data;
	}
}


```

