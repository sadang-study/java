```java
public class arrayTurn {
   
   static int[][] array  = new int[][]{  {1,2,3} ,{4,5,6}, {7,8,9}  };
   static int len = array.length;
   static int[][] array2 = null;
   
   public static void main( String[] args ) {
      bbw1();
      bbw2();
      yjy();
   }
   
   //90도 회전
   static void bbw1(){
      array2 = new int[3][3];
      
      for(int a = 0; a <len; a++){
         for(int z = 0; z < len; z++){
            array2[a][(len-1)-z] = array[z][a];
         }
      }
      printArray(1,array2);                           
   }
   
   //180도 회전
   static void bbw2(){
      array2 = new int[3][3];
      
      for(int a = 0; a <len; a++){
         for(int z = 0; z < len; z++){
            array2[(len-1)-z][(len-1)-a] = array[z][a];
         }
      }
      printArray(2,array2);         
   }
   
   //출력
   static void printArray(int cnt,int[][] arr){
      System.out.println( "*****************"+cnt+"번문제********************" );
      for(int a = 0; a < arr.length; a++){
         for(int z = 0; z < arr.length; z++){
            System.out.print(arr[a][z]);
         }
         System.out.println(  );
      }
      System.out.println( "********************************************" );
      System.out.println(  );
   }
   
   }

```
