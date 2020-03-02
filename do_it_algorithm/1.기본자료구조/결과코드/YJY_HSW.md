 static void yjy(){
         
         // 인터넷참고
         int[][] arr = new int[][]{{2,0},{6,0},{6,6}};
         
         int x = 0;
         int y = 0;
         
         if(arr[0][0] == arr[2][0]){
            x = arr[1][0];
         }else if(arr[1][0] == arr[2][0]){
            x = arr[0][0];
         }else{
            x = arr[2][0];
         }
         
         
         if(arr[0][1] == arr[2][1]){
            y = arr[1][1];
         }else if(arr[1][1] == arr[2][1]){
            y = arr[0][1];
         }else{
            y = arr[2][1];
         }
         
         System.out.println( x + "," + y );
 
            
      }
