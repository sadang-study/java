### 결과 코드


# 1. 기능 개발
```java
public int[] solution(int[] progresses, int[] speeds) {
    int[] answer = {};
    Stack<Integer> stack = new Stack<Integer>();

    int max = (int) Math.ceil((double)(100 - progresses[0])/speeds[0]);
    stack.push(max);

    int i = 1;
    while(!stack.isEmpty()) {
        int days = i < progresses.length ? (int) Math.ceil((double)(100 - progresses[i])/speeds[i]) : 101;
        i++;

        if (max >= days) {
            stack.push(days);
        } else {
            max = days;

            answer = Arrays.copyOf(answer, answer.length + 1);
            while(!stack.isEmpty()) {
                answer[answer.length - 1] = ++answer[answer.length - 1];
                stack.pop();
            }

            stack.push(days);

            if (i > progresses.length) { break;}
        }
    }
}
```

# 2. 프린터

```java
public int solution(int[] priorities, int location) {
    int answer = 0;

    Queue<Integer[]> queue = new LinkedList<Integer[]>();
    for (int i = 0; i < priorities.length; i ++ ) {
        queue.add(new Integer[] {i, priorities[i]});
    }

    while(!queue.isEmpty()) {
        Integer[] curr = queue.poll();
        if (queue.isEmpty()) { return ++answer; }

        int max = queue.peek()[1];
        for (Integer[] x : queue) {
            max = x[1] > max ? x[1] : max;
        }

        if (max > curr[1]) {
            queue.offer(curr);
        } else {
            answer++;
            if (curr[0] == location) {
                return answer;
            }
        }
    }

    return answer;
}
```
# 3. 탑

```java
public int[] solution(int[] heights) {
    int[] answer = new int[heights.length];
    for (int i = 1; i < heights.length; i ++) {

        for (int j = i - 1; j >= 0; j --) {
            if (heights[i] < heights[j]) {
                answer[i] = j + 1;
                break;
            }
        }
    }

    return answer;
}
```
