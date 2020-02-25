# 정수의 2차원 배열 (3X3) 을 90, 180, 270으로 회전시키기
## 설명.

||||
|---|---|---|
|1|2|3|              
|4|5|6|   
|7|8|9|  

 90도 회전
 
||||  
|---|---|---|        
|7|4|1|              
|8|5|2|   
|9|6|3|   

---
||||                    
|---|---|---|        
|1|2|3|              
|4|5|6|   
|7|8|9| 

180도 회전

||||                
|---|---|---|        
|9|8|7|              
|6|5|4|   
|3|2|1|
---

||||                   
|---|---|---|        
|1|2|3|              
|4|5|6|   
|7|8|9|   

 270도 회전
 
||||                  
|---|---|---|        
|3|6|9|              
|2|5|8|   
|1|4|7|

```java

public class 배열_회전 {

    public static void main(String[] args) {
        int[][] arr = new int[][]{{1,2,3},{4,5,6},{7,8,9}};

        배열_회전.turn90(arr);
        배열_회전.turn180(arr);
        배열_회전.turn270(arr);
    }

    /**
     * 90도 회전
     * 회전 전의 열번호와 회전후의 행번호가 일치.
     * 회전 후의 열은 N-1에서 회전 전의 행(현재행)을 뺀 값과 같다.
     * @param arr
     */
    public static void turn90(int[][] arr){
        배열_회전.arrToString(arr);
        int len = arr.length;
        int[][] cloneArr = new int[3][3];
        for(int i = 0; i<arr.length; i++){
            for(int k = 0; k<arr.length; k++){
                cloneArr[k][(len-1)-i] = arr[i][k];
            }
        }

        배열_회전.arrToString(cloneArr);
    }

    /**
     * 회전 후의 행번호는 N-1의 값에서 전의 행번호(현재 행)를 뺀 것과 같다.
     * 회전 후의 열 번호는 N-1의 값에서 전의 열번호(현재 열)를 뺀것과 같다.
     * @param arr
     */
    public static void turn180(int[][] arr){
        배열_회전.arrToString(arr);

        int len = arr.length;
        int[][] cloneArr = new int[3][3];
        for(int i = 0; i<arr.length; i++) {
            for(int k = 0; k<arr.length; k++) {
                cloneArr[(len-1)-i][(len-1)-k] = arr[i][k];
            }
        }

        배열_회전.arrToString(cloneArr);
    }

    /**
     * 회전 후의 열과 회전 전의 행(현재 행)이 일치함.
     * 회전 후의 번호는 N-1의 값에서 회전 전의 열 번호(현재 열)를 뺀 값과 같다.
     * @param arr
     */
    public static void turn270(int[][] arr){
        배열_회전.arrToString(arr);

        int len = arr.length;
        int[][] cloneArr = new int[3][3];
        for(int i = 0; i<arr.length; i++) {
            for(int k =0; k<arr.length; k++) {
                cloneArr[(len-1)-k][i] = arr[i][k];
            }
        }

        배열_회전.arrToString(cloneArr);
    }

    /**
     * 프린트
     * @param arr
     */
    public static void arrToString(int [][]arr){
        System.out.println("--------------------");
        for(int i = 0; i<arr.length; i++){
            for(int k = 0; k<arr[i].length; k++){
                System.out.print(arr[i][k] + " ");
            }
            System.out.println();
        }
        System.out.println("-----------------------");
    }
}

```