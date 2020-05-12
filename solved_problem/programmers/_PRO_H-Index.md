# PRO_H-Index

```java


class Solution {

    public int solution(int[] citations) {

        int answer = 0;
        int temp = 0;
        int h = 0;

        // 정렬
        for(int i=0; i<citations.length; i++) {
            for(int j=0; j<citations.length-i-1; j++) {
                if(citations[j] > citations[j+1]) {
                    temp = citations[j];
                    citations[j] = citations[j+1];
                    citations[j+1] = temp;
                }
            }
        }

        // x x o x x, x x x o x x 에서 o의 배열 값을 리턴하는 알고리즘
        for(int i=0; i<citations.length; i++) {

            if(citations[i] >= citations.length-i) {
                answer = citations.length-i;
                break;
            }
        }

        return answer;
    }
}


```

