### 1. 나무자르기

```java
    //나무자르기
    public static void Namu() {
      int cnt = 4; //나무의 수
      int necessary = 7; //필요한 나무
      int [] treeH = new int[] {20,15,10,17}; //나무의 높이

      int H = 1; //절단기 높이
      int maxH= 0; //최대 절단기 높이
      int sumTree = 999;

      while(sumTree != 0) {
        sumTree = 0;

        //절단기 TEST
        for(int z = 0; z < cnt; z++) {
          int result = treeH[z]-H;

          if(result > 0) {
            sumTree += result;
          }
        }

        System.out.println("자른 나무의 양 : " + sumTree);
        //자른나무의 값이 필요한 값과 일치하는지의 여부
        if(sumTree == necessary) {
          maxH = H;
        }

        H++;
      }

      System.out.println();
      System.out.println("절단기의 최대치 : " + maxH);
    }
```


### 2. 국가 총예산 나누기

```java
	   public static void yjy (){
		      
		      int [] budget = new int[]{120,110,140,150}; //지방 예산
		      int M = 485; //총 국가 예산
		      
		      int limit = 0; // 상한액
		      int totalBg = 0;  // 지방 총 요청예산
		      
		      while(limit < 999){
		         for(int i = 0; i < budget.length; i++){
		            if(budget[i] > limit){ // 상한액보다 클때
		               totalBg += limit;
		            }else{                // 상한액보다 같거나 작을때
		               totalBg += budget[i];
		            }
		         }
		         
		         if(totalBg > M){
		            limit--;
		            break;
		         }
		         
		         totalBg = 0;
		         limit++;
		      }
		      
		      System.out.println( limit );
		   }
```


### 3. 배열과 배열의 비교

```java
     public static void hsw(){
          int N = 5;
          int M = 5;

          int Narry[] = makeArry(N);
          int Marry[] = makeArry(M);
          int resultArry[] = new int[5];

          for(int i = 0; i < Marry.length; i++){
             // boolean flag = IntStream.of(Narry).anyMatch(x -> x == Marry[i]); Java8 이상 가능
             for(int z = 0; z < Narry.length; z++){
                if(Narry[z] == Marry[i]){
                   resultArry[i] = 1;
                }
             }
             System.out.println( resultArry[i] );
          }
       }

       public static int[] makeArry(int cnt){
          int [] tmpArry = new int[cnt];
          for(int i = 0; i < tmpArry.length; i++ ){
             tmpArry[i] = new Random().nextInt(10);
             System.out.print( tmpArry[i] + " " );
          }
          System.out.println(  );
          return tmpArry;
       }
```
