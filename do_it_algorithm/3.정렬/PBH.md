### [프로그래머스(정렬) K번째수](https://programmers.co.kr/learn/courses/30/lessons/42748) 

```java
import java.util.Arrays;

public class k번째수 {

    /**
     * 버블정렬
     * @param arr
     * @return
     */
    static int[] bubbleSort(int[] arr){
        int k = 0;
        while(k < arr.length-1) {
            int last = arr.length-1;
            for(int i = arr.length-1; i> k; i--){
                if(arr[i-1] > arr[i]) {
                    int temp = arr[i-1];
                    arr[i-1] = arr[i];
                    arr[i] = temp;
                    last = i;
                }
            }
            k = last;
        }
        return arr;
    }

    static int commandsTask(int[] arr, int start, int end, int k) {
        int[] result = new int[(end-start)+1];
        int index = 0;
        for(int i = start-1; i<end; i++) {
            result[index] = arr[i];
            index++;
        }
        System.out.println(Arrays.toString(arr) + "를 " + start + "번째부터 " + end + "번째까지 자른 후 정렬합니다." + Arrays.toString(result) + "의 " + k +"번째 숫자는 " + result[k-1] + "입니다."  );
        bubbleSort(result); // sort
        return result[k-1];
    }

    public static int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        for(int i = 0; i<commands.length; i++){
            answer[i] = commandsTask(array, commands[i][0], commands[i][1], commands[i][2]);
        }
        return answer;
    }

    public static void main(String[] args) {
        int[] arr = {1, 5, 2, 6, 3, 7, 4};
        int[][] commands = {{2, 5, 3}, {4, 4, 1}, {1, 7, 3}};
        System.out.println("시작");
        solution(arr, commands);
    }
}
 
```   

```java
import java.util.Arrays;

public class k번째수_quick {

    static void swap (int[] arr, int idx1, int idx2) {
        int temp = arr[idx1];
        arr[idx1] = arr[idx2];
        arr[idx2] = temp;
    }

    static void quickSort(int[] arr, int left, int right) {
        int pl = left;
        int pr = right;
        int x = arr[(pl+pr)/2];

        do {
            while (arr[pl] < x) pl++;
            while (arr[pr] > x) pr--;
            if(pl <= pr) {
                swap(arr, pl++, pr--);
            }
        }while (pl <= pr);
        if(left < pr) quickSort(arr, left, pr);
        if(pl < right) quickSort(arr, pl, right);

    }

    static int commandsTask(int[] arr, int start, int end, int k) {
        int[] result = new int[(end-start)+1];
        int index = 0;
        for(int i = start-1; i<end; i++) {
            result[index] = arr[i];
            index++;
        }

        quickSort(result, 0, result.length-1); // sort
        return result[k-1];
    }

    static int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        for(int i = 0; i<commands.length; i++){
            answer[i] = commandsTask(array, commands[i][0], commands[i][1], commands[i][2]);
        }
        return answer;
    }

    public static void main(String[] args) {
        int[] array = new int[] {1,5,2,6,3,7,4};
        int[][] commands = new int[][] {{2, 5, 3}, {4, 4, 1}, {1, 7, 3}};
        int[] values = solution(array, commands);
        System.out.println(Arrays.toString(values));
    }
}
```


### [프로그래머스(정렬)  가장 큰 수](https://programmers.co.kr/learn/courses/30/lessons/42746) 

```java
    public class 가장큰수 {
    
        /**
         * 버블정렬 내림차순으로.
         * @param arr
         * @return
         */
        static int[] bubbleSort(int[] arr){
            int k = 0;
            while(k < arr.length-1) {
                int last = arr.length-1;
                for(int i = arr.length-1; i> k; i--){
                    if(arr[i-1] < arr[i]) {
                        int temp = arr[i-1];
                        arr[i-1] = arr[i];
                        arr[i] = temp;
                        last = i;
                    }
                }
                k = last;
            }
            return arr;
        }
    
        static String arrToString(int[] arr){
            String str = "";
            for(int i = 0; i<arr.length; i++){
                str += arr[i];
            }
            return str;
        }
    
        public static String solution(int[] numbers) {
            String answer = "";
            answer = arrToString(numbers);
            int[] arr = new int[answer.toCharArray().length];
            for(int i = 0; i<answer.toCharArray().length; i++){
                arr[i] = Integer.parseInt(String.valueOf(answer.toCharArray()[i]));
            }
            answer = arrToString(bubbleSort(arr));
            System.out.println(answer);
            return answer;
        }
    
        public static void main(String[] args) {
            //int[] arr = {6, 10, 2};
            int[] arr = {3, 30, 34, 5, 9};
            solution(arr);
            if(9543330 > 9534330){
                System.out.println(true);
            }else{
                System.out.println(false);
            }
        }
    }
``` 

### [프로그래머스(정렬)  H-INDEX](https://programmers.co.kr/learn/courses/30/lessons/42747) 
```java
public class hIndex_quick {
    static void swap (int[] a, int idx1, int idx2) {
        int t = a[idx1];
        a[idx1] = a[idx2];
        a[idx2] = t;
    }

    static void quickSort(int[] a, int left, int right) {
        int pl = left;
        int pr = right;
        int x = a[(pl + pr) / 2];

        do {
            while (a[pl] < x) pl++;
            while (a[pr] > x) pr--;
            if(pl <= pr) {
                swap(a, pl++, pr--);
            }
        }while (pl <= pr);
        if(left < pr) quickSort(a, left, pr);
        if(pl < right) quickSort(a, pl, right);

    }

    public static int solution(int[] citations) {
        int answer = 0;
        int k = 0;

        quickSort(citations, 0, citations.length-1);

        for (int i = 0; i < citations.length; i++) {
            k =  citations.length - i;
            if (k <= citations[i]) {
                answer = k;
                break;
            }
        }
        return answer;
    }

    public static void main(String[] args) {
        int[] arr = new int[]{3, 0, 6, 1, 5};
        System.out.println(solution(arr));
    }
}
```
