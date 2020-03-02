```java

  static void ReverseArry(){
      /*
       * 입출력 예)

      * n : 12345 -> return [5,4,3,2,1]
      * n : 3000 -> return [0,0,0,3]
       * 
       */
      int [] arry = new int[]{1,2,3,4,5};
      int[] answer = new int[5];
      int len = arry.length-1;
      
      for(int i = len; i>=0; i--){
         answer[len-i] = arry[i];
      }
      
      
      for(int i =0; i<answer.length; i++){
         System.out.print( answer[i] );
      }
      
      
   }

```
