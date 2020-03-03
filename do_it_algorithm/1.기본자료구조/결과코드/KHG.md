### 문제 풀이 

```java

public class Solution {

    /**
     * 숫자 역순
     *
     * @since 2020. 3. 3.
     * @author 김형기
     *
     * @return
     */
    public int[] solution(long n) {
        int[] answer = new int[(int) (Math.log10(n) + 1)];
        
        int i = 0;
        while (n > 0) {
            answer[i++] = (int) (n % 10);
            n /= 10;
        }
        
        return answer;
    }
    
    
     
    /**
     * 회전 문제
     *
     * @since 2020. 3. 3.
     * @author 김형기
     *
     * @return
     */
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
    
    /**
     * 직사각형 꼭지점 구하기
     *
     * @since 2020. 3. 3.
     * @author 김형기
     *
     * @return
     */
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


```java

public class arrayExample {
    
    static char[][] bingo;

/*
 *  문제) 8X8로 이루어진 빙고가 존재합니다.
 * 
 * 
 *  1-1) 빙고를 array_Image1과 같도록 우로 1회 회전시키시오.
 *  
 *  
 *  
 *  
 *  1-2) 원본의 빙고에서 아래 단어들을 찾아내시오.
 *    단어는 왼쪽-> 오른쪽, 오른쪽->왼쪽 , 위 -> 아래 , 아래 -> 위 , 대각선 방향으로 존재합니다. 
 *    [MILK , CAR , WEB , RUN , STUDY]
 *    
 *    출력할 답 : 찾은 단어 리스트는 : 1.CAR 2.MILK 3.RUN 4.STUDY 5.WEB 입니다. 
 *    
 * 
 * 
 */
    
    
   //실행
   public static void main( String[] args ) {
      
      bingo = makeBingo();
      
      RotationBingo(bingo);
      FindEngWord(bingo);
      
   }
   
   
   // 8X8 빙고 만들기
   static char[][] makeBingo(){
      
      System.out.println( "****************** 8 X 8 ******************" );
      
      char[][] tempArray = {
            {'C','A','R','F','G','W','Q','O',},
            {'H','D','E','N','D','E','Q','C'},
            {'C','V','Q','A','K','B','R','T'},
            {'S','Q','D','C','L','K','Q','S'},
            {'B','T','b','b','I','b','T','P'},
            {'E','B','Y','R','M','U','I','O'},
            {'P','K','Y','T','D','Q','C','V'},
            {'B','N','U','Y','B','E','W','X'},
            {'N','U','R','T','C','E','K','B'},};
      
      
      for(int i = 0 ; i < tempArray.length; i++){
         for(int z = 0 ; z<tempArray[i].length; z++){
            System.out.print( "[" + tempArray[i][z] +"]" );
         }
         System.out.println();
      }
      
      System.out.println( "******************************************" );
      
      return tempArray;
   }
      
   
   static void RotationBingo(char[][] Ary){
      
      /***
       *  정답란 
       */
       
       char[][] arr = new char[Ary.length][Ary[0].length];
       
       for(int i = 0; i < arr.length; i ++) {
           int k = 0;
           
           for(int j = 0; j < arr[i].length; j++) {
               
               if (i >=1 && i<=4 && (j >=2 && j<=5)) {
                   
                   if (i == 1 || i == 4) {
                       arr[i][j] = Ary[4-k][i+1];
                   } else if ((i == 2 || i == 3) && (j==2 || j == 5)) {
                       arr[i][j] = Ary[4-k][i+1];
                   } else {
                       arr[i][j] = Ary[i][j];
                   }
                   
                   k ++;
               } else {
                   arr[i][j] = Ary[i][j];
               }
           }
       }
       
       for(int i = 0 ; i < arr.length; i++){
           for(int z = 0 ; z<arr[i].length; z++){
              System.out.print( "[" + arr[i][z] +"]" );
           }
           System.out.println();
        }
   }
   
   
   static void FindEngWord(char[][] Ary){
      
      /***
       *  정답란 
       */
      
   }

}
```
