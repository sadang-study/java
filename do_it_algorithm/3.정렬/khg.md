# 결과 코드


## 1. K번째 수
```java
import java.util.Arrays;

class Solution {

    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for (int i = 0; i < commands.length; i ++) {
            int[] newArray = Arrays.copyOf(array, array.length); 
            this.quickSort(newArray, commands[i][0] - 1, commands[i][1] - 1);

            answer[i] = newArray[commands[i][0] + commands[i][2] - 2];
        }

        return answer;
    }

    private void quickSort(int[] array, int left, int right) {
        int low = left;
        int high = right;
        int mid = array[(low+high) /2];
        
        do {
            while(array[low] < mid) { low ++; }
            while(array[high] > mid) { high --; }
            
            if (low <= high ) {
                int temp = array[low];
                array[low++] = array[high];
                array[high--] = temp;
            }
        } while (low <= high);

        if (left < high) { quickSort(array, left, high); }
        if (low < right) { quickSort(array, low, right); }
    }
}
```

## 2. 가장 큰 수

```java
import java.util.*;

class Solution {

    public String solution(int[] numbers) {
        String answer = "";
        String[] array = new String[numbers.length];

        for (int i = 0; i < numbers.length; i ++) {
            array[i] = String.valueOf(numbers[i]);
        }

        Arrays.sort(array, new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return (o2 + o1).compareTo(o1 + o2);
            }
        });     

        answer = String.join("", array);  
        return answer.charAt(0) == '0' ? "0" : answer;
    }
}
```
