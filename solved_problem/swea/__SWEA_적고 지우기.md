# SWEA_적고 지우기


```java


import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;

class Main
{
	public static void main(String args[]) throws Exception
	{
		Scanner sc = new Scanner(System.in);
		int T;
		T=sc.nextInt();

		for(int test_case = 1; test_case <= T; test_case++)
		{
			String numStr = sc.next();
			HashMap<Integer, Integer> hashMap = new HashMap<>();
			for(int i=0; i<numStr.length(); i++) {
				int num = numStr.charAt(i)-48;
				if(!hashMap.containsKey(num)) hashMap.put(num, 1);
				else hashMap.remove(num);
			}
			
			int count = 0;
			Iterator<Integer> iterator = hashMap.keySet().iterator();
			while(iterator.hasNext()) {
				int key = iterator.next();
				count++;
			}
			
			System.out.println("#"+test_case+" "+count);
		}
	}
}


```

