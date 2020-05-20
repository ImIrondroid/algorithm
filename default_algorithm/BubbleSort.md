# 버블정렬 알고리즘 - Bubble Sort


### 아이디어


'옆에 있는 값과 비교해서 더 작은 값을 앞으로 보내면 어떨까?


### 특징


1) 구현이 매우 간단하다. 삽입정렬, 선택정렬과 비교해보면 코드가 더 짧다.
2) 모든 원소들을 비교하고 교환시킨다.
3) 최종 위치에 정렬된 원소라고해도 교환이 되는 일이 발생한다.
4) 선택정렬과 마찬가지로 Best일때 n^2, Worst일때도 n^2의 시간복잡도를 가진다.
5) 계속해서 비교하고 값을 바꾸기 때문에 일반적으로 알고있는 정렬 알고리즘 중에 제일 많은 Run-time시간이 걸린다. 


### 그림


아래 그림은 버블정렬의 과정을 나타낸다. 직관적으로 이해하기 매우 쉬운 알고리즘이다.

![](http://postfiles11.naver.net/20140128_282/justant_1390842794487v9kxH_PNG/%B9%F6%BA%ED%C1%A4%B7%C4.png?type=w2)

그림참고 : http://blog.naver.com/PostView.nhn?blogId=justant&logNo=20204028286&parentCategoryNo=&categoryNo=16&viewDate=&isShowPopularPosts=true&from=search


```java


public class MyBubbleSort {

    public MyBubbleSort() {
        bubble_sort();
    }
    
    public void bubble_sort() {
        
        int[] arr = {1,3,2,6,3,4,-1,4,2,2,-99};
        int temp = 0;
        int lth = arr.length;
        
        for(int i=0; i<lth; i++) {
            for(int j=0; j<lth-i-1; j++) {
                if(arr[j]>arr[j+1]) {
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
        
        for(int item : arr) {
            System.out.print(item + " ");
        }
    }
}


```
