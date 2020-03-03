```java

  
/**
 * 자연수 뒤집어 배열로 만들기.
 * 자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요.
 * 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.
 *
 * 입출력 예)
 *
 * n : 12345 -> return [5,4,3,2,1]
 * n : 3000 -> return [0,0,0,3]
 */
public class ArrReverse {
    public static void main(String[] args) {
        System.out.println("입력");
        Scanner scanner = new Scanner(System.in);
        long n = scanner.nextLong();
        int[] results = ArrReverse.solution(n);

        System.out.println(Arrays.toString(results));
    }

    public static int[] solution(long n) {
        String[] numStr = String.valueOf(n).split("");
        int[] answer = new int[numStr.length];

        for(int i = numStr.length-1; i>=0; i--) {
            answer[(numStr.length-1)-i] = Integer.parseInt(numStr[i]);
        }

        return answer;
    }
}

```
