## 박불휘꺼 (배열 회전)
``` java
    static int[][] rotateWithAngle(int[][] source, int arrLength, int angle) throws Exception {

        int loopCount = 0;
        switch(angle){
            case 90: loopCount = 1; break;
            case 180: loopCount = 2; break;
            case 270: loopCount = 3; break;
            default: throw new Exception("Invalid angle");
        }
        int[][] result = new int[arrLength][arrLength];

        for (int k=0; k < loopCount; k++){
            int[][] target = new int[arrLength][arrLength];
            for (int i = 0; i < source.length; i++) {
                for (int j = 0; j < source[i].length; j++) {
                    target[i][j] = source[2-j][i];
                }
            }
            source = target;
            if (k == loopCount -1){
                result = target;
            }
        }
        return result;
    }
```

## 허석원꺼 (1번)
```java
   static void RotationBingo(char[][] arr) {

      char[][] trgtArr = new char[9][8];
      // 회전시키고 싶은 사각형의 가장 왼쪽 상단 좌표
      // (i, j)
      int[] origin = { 1, 2 };
      int oX = origin[0];
      int oY = origin[1];
      int d = oY - oX;
      // 회전하고자 하는 사각형 크기
      // (m, n)
      int[] size = { 4, 4 };
      int sX = size[0];
      int sY = size[1];
      for (int i = 0; i < arr.length; i++) {
         char[] trgtArrRow = arr[i].clone();
         for (int j = 0; j < arr[i].length; j++) {
            // 범위 설정
            if ((i == oX || i == oX + sX - 1) && (j >= oY && j <= oY + sY - 1)
                  || (i >= oY && i <= oX + sX - 1) && (j == oY || j == oY + sY - 1)) {
               trgtArrRow[j] = arr[6 - j][i + d];
            }
         }
         // 넣어준다.
         trgtArr[i] = trgtArrRow;
      }

      for (int i = 0; i < trgtArr.length; i++) {
         for (int z = 0; z < trgtArr[i].length; z++) {
            System.out.print("[" + trgtArr[i][z] + "]");
         }
         System.out.println();
      }

   }
```

