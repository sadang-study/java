### Search_exam_HSW.md 작성코드

```java
package main;

import java.util.Arrays;
import java.util.Scanner;


public class MainClass {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);

        System.out.println("정수 N 입력 : ");
        int n = scan.nextInt();
        int[] nArr = new int[n];
        for(int i = 0; i<n; i++) {
            System.out.println("a 배열 " + i + "번째 입력 : ");
            nArr[i] = scan.nextInt();
        }

        System.out.println("정수 M 입력 : ");
        int m = scan.nextInt();
        int[] mArr = new int[m];
        for(int i = 0; i<m; i++) {
            System.out.println("m 배열 " + i + "번째 입력 : ");
            mArr[i] = scan.nextInt();
        }

        // System.out.println(n);
        System.out.println(Arrays.toString(nArr));

        // System.out.println(m);
        System.out.println(Arrays.toString(mArr));


        numSearch(nArr, mArr);

    }

    public static void numSearch(int[] nArr, int[] mArr) {
        for(int i = 0; i<mArr.length; i++){
            int output = 0;
            for(int k = 0; k<nArr.length; k++){
                if(nArr[k] == mArr[i]){
                    output = 1;
                    break;
                }
            }
            System.out.println(output);

        }
    }
}

```

### PBH_나무자르기.md 작성코드
```java
public class 나무자르기{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("나무의 수 입력 : ");
        int n = scan.nextInt();
        int[] treeArr = new int[n];

        for(int i = 0; i<treeArr.length; i++){
            System.out.println("나무의 길이 입력"); //랜덤이라고 가정함.
            treeArr[i] = scan.nextInt();
        }

        System.out.println("필요한 나무의 길이 입력 : ");
        int m = scan.nextInt();
        
        int max = 0; //최대길이 
        for(int i = 0; i<treeArr.length; i++){
            if(max < treeArr[i]){
                max = treeArr[i];
            }
        }
        
        treeSolution(max, treeArr, m);
    }

    /**
     * 이진탐색 활용.
     * @param max treeArr 배열의 최댓값,
     * @param treeArr 나무 배열
     * @param m 필요한 나무의 길이
     */
    public static void treeSolution(int max, int[] treeArr, int m){
        int pl = 0; 
        int pr = max;
        int pc = (pl+pr)/2;

        while(pc >= pl && pc <= pr){ // 종료조건1 
            int sum = 0;
            for(int i = 0; i<treeArr.length; i++){
                if(pc < treeArr[i]){
                    sum += treeArr[i] - pc;
                }
            }

            if(sum < m ){
                pc -= 1;
            }else if(sum > m ) {
                pc += 1;
            }else if(sum == m){ //종료조건2 자른 나무의 길이의 합과 필요로 하는 나무의 길이가 같음.
                System.out.println(pc);
                break; 
            }
        }
    }
}

```

### yjy.md  예산심사 작성코드
```java
import java.util.Arrays;

public class 예산심사 {
    public static void main(String[] args) {
        solution(new int[]{120, 110, 140, 150}, 485);
    }

    public static int solution(int[] arr, int M) {
        int answer = 0;
        Arrays.sort(arr);
        int min = arr[0];
        int max = arr[arr.length-1];
        int mid = (min+max)/2;
        int sum = 0;
        
        for(int i = 0; i<arr.length; i++) {
            sum+=arr[i];
        }

        while(sum > M) {
            sum = 0;
            for(int i = 0; i<arr.length; i++) {
                if(arr[i] > mid) {
                    arr[i] = mid;
                }
                sum += arr[i];
            }
            if(sum > M) {
                mid = mid-1;
            }
            System.out.println(Arrays.toString(arr));
        }
        System.out.println(mid);
        return mid;
    }
}

```

### khg.md 작성코드
```java
```


