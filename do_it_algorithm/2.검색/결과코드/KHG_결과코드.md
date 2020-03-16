### 결과 코드


```java
/**
 * 클래스명: <code>Search_PBH</code><br/><br/>
 *
 * 나무 자르기
 *
 * @author 김형기
 *
 */
public class Search_PBH {

    public static void main(String[] args) {
        
        int arr[] = {20, 15, 10, 17};
        Arrays.sort(arr);
        
        System.out.println(binarySearch(arr, 7));
    }
    
    
    public static int binarySearch(int[] arr, int key) {
        int low = 0;
        int high = arr[arr.length - 1];
        int min = 0;
        
        while (low <= high) {
            int mid = (low + high) / 2;
            int sum  = arrSum(arr, mid);
            
            if (sum > key) {
                low = mid + 1;
                
                if ((key - min) > (key - sum)) {
                    min = mid;
                }
            } else if (sum < key) {
                high = mid - 1;
            } else {
                return mid;
            }
        }
        
        return min;
    }
    
    private static int arrSum(int[] arr, int m) {
        int sum = 0;
        for (int i = 0; i < arr.length; i ++ ) {
            if (arr[i] > m) {
                sum += (arr[i]-m);
            }
        }
        
        return sum;
    }
}

```

```java

/**
 * 클래스명: <code>Search_YJY</code><br/><br/>
 *
 * 예산 구하기
 *
 * @author 김형기
 *
 */
public class Search_YJY {

    public static void main(String[] args) {
        //120, 110, 140, 150
        int[] arr = {120, 110, 140, 150};
        int key = 484;
        
        System.out.println(binarySearch(arr, key));
        
    }
    
    public static int binarySearch(int[] arr, int key) {
        Arrays.sort(arr);
        
        int low = 0;
        int high = arr[arr.length - 1];
        int min = 0;
        
        while(low <= high) {
            int mid = (low + high) / 2;
            int sum = 0;
            for (int x : arr) {
                sum += x > mid ? mid : x;
            }
            
            if (sum < key) {
                low = mid + 1;
                if ((key - min) > (key - sum)) {
                    min = mid;
                }
            } else if (sum > key) {
                high = mid - 1;
                
            } else {
                return mid;
            }
        }
        
        return min;
    }
}

```

```java

/**
 * 클래스명: <code>Search_HSW</code><br/><br/>
 *
 * 존재 하는 수 구하기
 *
 * @author 김형기
 *
 */
public class Search_HSW {

    public static void main(String[] args) {
        int arr[] = {4 , 1, 5, 2, 3};
        int m[] = {1, 3, 7, 9, 5};
        
        Arrays.sort(arr);
        for (int x : m) {
            System.out.println(binarySearch(arr, x));
        }
    }
    
    
    public static int binarySearch(int[] arr, int key) {
        int low = arr[0];
        int high = arr[arr.length - 1];
        
        while(low <= high) {
            int mid = (low + high) / 2;
            
            if (mid > key) {
                high = mid - 1;
            } else if (mid < key) {
                low = mid + 1;
            } else {
                return 1;
            }
        }
        
        return 0;
    }
}

```
