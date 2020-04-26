### [프로그래머스(정렬) K번째수]

```java
public class Solution_K {

	public static void main(String[] args) {
		int array[] = new int[] {1,1,2,6,8,4,1,3,4,5,2};
		int[][] commands = new int[][] {{2,5,3},{4,4,1},{1,7,3}};
		
		int[] aa = new Solution_K().solution(array,commands);
		
		for(int i = 0; i < aa.length; i++) {
			System.out.println(aa[i]);
		}
	}
	
	public int[] solution(int[] array , int[][] commands) {
		
		int[] array_result = new int[commands.length];
		
		for(int i = 0; i < commands.length; i++) {
			int s = commands[i][0];
			int e = commands[i][1];
			int k = commands[i][2];
			
			int[] array_temp = new int[e-s+1];  
			int cnt = 0;	
			
			//배열 자르기
			for(int j = s-1; j < e; j++ ) {
				array_temp[cnt] = array[j];
				cnt++;
			}
			
			//버블 정렬
			int result = bubbleSort(array_temp,k);
			
			array_result[i] = result;
		}
		
		return array_result;
	}
	
	public int bubbleSort(int[]a, int k) {
		for(int n = 0; n < a.length-1; n++) {
			int idx = 0;
			for(int p = n; p < a.length-1; p++) {
				if(a[p] > a[p+1]) {
					int temp = a[p];
					a[p] = a[p+1];
					a[p+1] = temp;
					idx++;
				}
			}
			
			if(idx == 0) {
				break;
			}
		}
		
		return a[k-1];
	}
}
 
```   

### [프로그래머스(정렬)  가장 큰 수]

```java
public class Solution_Maximum {
	
	class Value {
        int rest;
        int value;

        public Value(int rest, int value) {
            this.rest = rest;
            this.value = value;
        }

		public int getRest() {
			return rest;
		}

		public int getValue() {
			return value;
		}
        
        
    }
	
	public static void main(String[] args) {
		String result = new Solution_Maximum().solution(new int[] {0,0,0,1000});
		
		System.out.println(result);
	}
	
	 public String solution(int[] numbers) {
		 
		 	Value[] value_array = new Value[numbers.length];
	     	
		 	// 값/10 = 나머지 
		 	for(int i = 0; i < numbers.length; i ++) {
		 		Value value = new Value(numbers[i]%10, numbers[i]);
		 		value_array[i] = value;
		 	}
		 	
		 	//quickSort(value_array,0,numbers.length-1 );
		 	bubbleSort(value_array,numbers.length);
		 	
		 	StringBuffer sb = new StringBuffer();
		 	
		 	for(int j = value_array.length - 1 ; j >= 0; j--) {
		 		sb.append(value_array[j].getValue());
		 	}
		 	
		 	return sb.toString();
	 }
	 
	 
	////////////////// 버블정렬     //////////////////////////////////
	static void bubbleSort(Value [] a, int n) {
		for(int i = 0; i < n - 1; i++) {
			int exchg = 0;
			for(int j = i; j < n-1; j++) {
				if(a[j+1].getRest() < a[j].getRest()) {
					swap(a,j,j+1);
					exchg++;
				}
				if(exchg == 0)break;
			}
		}
	}
	 
	 
	 
	 
	////////////////// Quick 정렬////////////////////////////////// 
	 
	static void quickSort(Value [] a, int left , int right) {
		int pl = left; //0
		int pr = right; //4
		Value x = a[(pl + pr) / 2]; //중간 값
		
		
		do {
			while(a[pl].getRest() < x.getRest()) pl++;
			while(a[pr].getRest() > x.getRest()) pr--;
			if(pl <= pr) {
				swap(a, pl++, pr--);
			}
		}while(pl <= pr);
		
		if(left < pr) quickSort(a,left,pr);
		if(pl < right) quickSort(a, pl, right);
	}
	
	
	static void swap(Value[] a , int idx1, int idx2) {
		Value t = a[idx1];
		a[idx1] = a[idx2];
		a[idx2] = t;
	}
	 
}
```
