### 문제 풀이 

```java

public class Solution {

    // 숫자 역순 회전
    public int[] solution(long n) {
        int[] answer = new int[(int) (Math.log10(n) + 1)];
        
        int i = 0;
        while (n > 0) {
            answer[i++] = (int) (n % 10);
            n /= 10;
        }
        return answer;
    }
    
    
    // 회전 문제 
    public int[][] turnArr(int[][] arr, int n) {
        int[][] answer = new int[arr.length][arr[0].length];
        
        if (n == 90) {
            
            for(int i = 0; i < arr.length; i ++) {
                for(int j = 0; j < arr[i].length; j++) {
                    answer[i][j] = arr[2-j][i];
                }
            }
        } else if (n == 180) {
            
            for(int i = 0; i < arr.length; i ++) {
                for(int j = 0; j < arr[i].length; j++) {
                    answer[i][j] = arr[2-i][2-j];
                }
            }
        } else if (n == 270) {
            
            for(int i = 0; i < arr.length; i ++) {
                for(int j = 0; j < arr[i].length; j++) {
                    answer[i][j] = arr[j][2-i];
                }
            }
        }
        
        return answer;
    }
    
    // 직사각형 꼭지점 구하기
    public int[] rectangle (int[][] v) {
        int[] answer = new int[2];
        
        for(int i=0; i<v.length; i++) {
            answer[0] ^= v[i][0];
            answer[1] ^= v[i][1];
        }
        return answer;
    }
    
}
    
```
