## 나무자르기
```java
package app;

import java.util.Arrays;
import java.util.Scanner;

/**
 * PBW
 */
public class PBW {
    public static void main(String[] args) {
        cutTree();
    }

    private static void cutTree() {
        // 1. 입력
        Scanner scan = new Scanner(System.in);
        int treeCount = scan.nextInt();
        int wantLength = scan.nextInt();

        int[] hArr = new int[treeCount];
        for (int i = 0; i < treeCount; i++) {
            hArr[i] = scan.nextInt();
        }

        // 2. 정렬 (asc)
        Arrays.sort(hArr);

        // 3. 정렬 (desc)
        for (int i = 0; i < hArr.length / 2; i++) {
            int tmp = hArr[i];
            hArr[i] = hArr[hArr.length - 1 - i];
            hArr[hArr.length - 1 - i] = tmp;
        }

        // 4. 앞에서 부터 가지치기
        // 나무 높이별로 구간을 나눈다.
        // 20 ~ 17 => 20 -h
        // 16 ~ 15 => 20 + 17 - 2h
        // 14 ~ 10 => 20 + 17 + 10 - 3h
        int max = hArr[0];
        int min = hArr[hArr.length - 1];
        // 나무 절단기
        for (int h = max - 1; h >= min; h--) {
            // 배열 인덱스
            int x = 0;
            int treeSum = 0;
            for (int t = 0; t < hArr.length; t++) {
                if (h >= hArr[t]) {
                    break;
                } else {
                    x++;
                }
                treeSum += hArr[t];
            }
            if (wantLength <= (treeSum - x * h)) {
                System.out.println("절단기 높이 최댓값 : " + h);
                break;
            }
        }
    }
}
```
<br>

## Search Exam
```java
package app;

import java.util.Scanner;

/**
 * HSW
 */
public class HSW {

    public static void main(String[] args) {
        arrExist();
    }

    private static void arrExist() {
        // int[] trgtArr, int trgtArrLength,int[] srcArr, int srcArrLength

        try (Scanner scan = new Scanner(System.in);) {
            int trgtArrLength = scan.nextInt();
            int[] trgtArr = new int[trgtArrLength];
            for (int i = 0; i < trgtArrLength; i++) {
                trgtArr[i] = scan.nextInt();
            }
            int srcArrLength = scan.nextInt();
            int[] srcArr = new int[srcArrLength];
            for (int i = 0; i < srcArrLength; i++) {
                srcArr[i] = scan.nextInt();
            }
            // 소스배열 정렬
            for (int i = 0; i < srcArrLength; i++) {
                boolean flag = false;
                for (int j = 0; j < trgtArrLength; j++) {
                    if (srcArr[i] == trgtArr[j]) {
                        flag = true;
                        break;
                    } 
                }
                if (flag) {
                    System.out.println(1);
                }
                else {
                    System.out.println(0);
                }
            }
        }
    }
}
```
<br>

## 예산 나누기
```java
package app;

public class YJY {
    public static void main(String[] args) {

        int[] arr = {120, 110, 140, 150};
        int budget = 485;
        int result = solution(arr, budget);
        System.out.println(result);
    }
    private static int solution(int[] arr, int budget) {

        // 0. 합계 & 평균 구하기
        int budgetSum = 0;
        for (int i = 0; i < arr.length; i++) {
            budgetSum += arr[i];
        }
        int budgetAvg = budgetSum / arr.length;

        // 1. 모든 요청이 배정될 수 있는 경우에는 요청한 금액 그대로 배정
        if (budgetSum <= budget) {
            return budget;
        }

        // 3. 나머지 금액에 대해서 찾아보자. 이때 평균.
        int mid = budgetAvg;
        int tmpSum = 0;
        int counter = 0;
        int result = 0;
        while (counter <= arr.length) {
            counter++;
            // 여기서는 이진탐색과 다르게 키값을 찾으려는게 아니라
            // 예산최댓값을 찾는 것이다. 따라서
            int sum = 0;
            for (int i = 0; i < arr.length; i++) {
                if (arr[i] >= mid) {
                    arr[i] = mid;
                }
                sum += arr[i];
            }
            // 같은 경우는 최적의 값. 리턴
            if (sum == budget) {
                result = mid;
                break;
            } 
            // budget의 더 큰 경우에는 mid를 올려준다.
            else if (sum < budget) {
                // 그러나 바로전 합계에서 tmpSum이 budget보다 컸다면
                // 더 내려 가면 안된다. 리턴
                if(tmpSum > budget){
                    result = mid;
                    break;
                }
                mid ++;
            } else {
                mid --;
            }
            tmpSum = sum;
        }
        System.out.println("loop count : "+ counter);
        return result;
    }
}
```