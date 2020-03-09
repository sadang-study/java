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

### khg.md 작성코드
```java
```

### PBH_나무자르기.md 작성코드
```java
```
