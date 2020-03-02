```java
public class alTest {
	   
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
	         
	         //rotationBingo(bingo);
	         findEngWord(bingo);
	         
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
	         
	      
	      static void rotationBingo(char[][] Ary){
	        char[][] Ary2 = copyArray();  
	         
	         //첫 세로줄 기준
	         //4,2 -> 1,2
	         //3,2 -> 1,3
	         //2,2 -> 1,4
	         //1,2 -> 1,5  위치에 맞게 세팅
	         int size = 4;  // 회전시킬 퍼즐의 사이즈
	         
	         for(int i = 0; i < size; i++){
	            for(int z = 0; z < size; z++){
	               if(i == 1 || i == 4){                          //세로준 기준 첫줄 마지막줄만 수행 
	                  Ary2[i][z+2] = Ary[size-z][i+2];
	               }else if(z == 0 || z == 3){                   //가로줄 기준 첫줄과 마지막줄만 수행   
	                  Ary2[i][z+2] = Ary[size-z][i+2];
	               }
	            }
	         }
	         printArray(Ary2);
	      }
	      
	      
	      static void findEngWord(char[][] Ary){
	        char[][] Ary3 = copyArray(); 
	         StringBuffer sb = new StringBuffer();
	         
	         //가로(정방향)
	         for(int i = 0; i< Ary3.length; i++){
	            sb.setLength( 0 );
	            for(int z = 0; z < Ary3[i].length; z++){
	                sb.append(Ary3[i][z]);
	            }
	            String str = sb.toString();
	            searhWord(str);
	         }
	         
	         //가로(역방향)
	         for(int i = Ary3.length-1; 0 <= i ; i--){
	            sb.setLength( 0 );
	            for(int z = Ary3[i].length-1; 0 <= z; z--){
	                sb.append(Ary3[i][z]);
	            }
	            String str = sb.toString();
	            searhWord(str);
	         }
	         
	       //세로(정방향)
	         for(int i = 0; i< Ary3.length-1; i++){
	            sb.setLength( 0 );
	            for(int z = 0; z < Ary3[i].length+1; z++){
	                sb.append(Ary3[z][i]);
	            }
	            String str = sb.toString();
	            searhWord(str);
	         }
	         
	         //세로(역방향)
	         for(int i = Ary3.length-2; 0 <= i ; i--){
	            sb.setLength( 0 );
	            for(int z = Ary3[i].length-1; 0 <= z; z--){
	                sb.append(Ary3[z][i]);
	            }
	            String str = sb.toString();
	            searhWord(str);
	         }
	         
	       //대각선(역방향)
		      
	      }
	      
	      
	//////////////////////////////////////공통 묘듈///////////////////////////////////////////////      
	      
	      //정렬된 String값으로 답안 찾기
	      static void searhWord(String str){
	         String[] wordList = new String[]{"car","web","milk","study","run"};
	         
	          for(int t = 0; t < wordList.length; t++){
	               int result = str.toLowerCase().indexOf( wordList[t] );
	               if(result != -1){
	                  System.out.println( "답은 : " + wordList[t] );
	               }
	          }
	      }
	      
	      //배열 복사 
	      static char[][] copyArray(){
	        char[][] Ary2 = new char[9][8];
	         
	        //배열 복사
	         for(int i = 0; i< bingo.length; i++){
	            for(int z = 0; z < bingo[i].length; z++){
	                Ary2[i][z] = bingo[i][z];
	            }
	         }
	         return Ary2;
	      }
	      
	      //배열 출력
	      static void printArray(char[][] arry){
	         
	         for(int i =0 ; i < arry.length; i++){
	            for(int z =0; z < arry[i].length; z++){
	               System.out.print( "[" + arry[i][z] +"]" );
	            }
	            System.out.println(  );
	         }
	      }
	      
	}
```
