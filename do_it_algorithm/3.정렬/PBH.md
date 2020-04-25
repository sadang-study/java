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