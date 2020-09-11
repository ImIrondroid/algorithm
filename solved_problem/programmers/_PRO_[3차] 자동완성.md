# [3차] 자동완성


트라이 자료구조 사용


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Solution {
	
	public int solution(String[] words) {
		Trie trie = new Trie();
		for(String word : words) {
			trie.insert(word);
		}
		for(String word : words) {
			trie.search(word);
		}
        		return answer;
	}
	
	static int answer = 0;
	
	class Trie {
		private TrieNode rootNode;
		Trie() {
			rootNode = new TrieNode();
		}
		
		void insert(String word) {
			TrieNode trieNode = this.rootNode;
			for(int i=0; i<word.length(); i++) {
				char ch = word.charAt(i);
				trieNode = trieNode.childNodes.computeIfAbsent(ch, node -> new TrieNode());
				trieNode.increaseValue();
			}
		}
		
		void search(String word) {
			TrieNode trieNode = this.rootNode;
			for(int i=0; i<word.length(); i++) {
				char ch = word.charAt(i);
				TrieNode childNode = trieNode.childNodes.get(ch);

				answer++;
				if(childNode.getValue() == 1) return;
				else trieNode = childNode;
			}
		}
	}
	
	class TrieNode {
		private Map<Character, TrieNode> childNodes = new HashMap<Character, Solution.TrieNode>();
		private int value = 0;
		
		Map<Character, Solution.TrieNode> getChildNodes() {
			return childNodes;
		}
		
		void increaseValue() {
			this.value++;
		}
		
		int getValue() {
			return this.value;
		}
	}
}


```

