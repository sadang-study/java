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

# 4. 다리를 지나는 트럭

```java
public int solution(int bridge_length, int weight, int[] truck_weights) {
    int answer = 1;
    Queue<Integer[]> wait = new LinkedList<Integer[]>();
    Queue<Integer[]> progress = new LinkedList<Integer[]>();

    for (int i = 0; i < truck_weights.length; i ++ ) {
        wait.offer(new Integer[] {1, truck_weights[i]});
    }

    Integer[] x = wait.poll();
    progress.offer(x);

    int bridgeWeight = x[1];
    while(!progress.isEmpty()) {
        answer++;

        progress.stream().forEach(i -> ++i[0]);

        while(!progress.isEmpty() && progress.peek()[0] > bridge_length) {
            bridgeWeight -= progress.poll()[1];
        }

        if (!wait.isEmpty() && bridgeWeight + wait.peek()[1] <= weight) {
            x = wait.poll();
            progress.offer(x);
            bridgeWeight += x[1];
        }
    }

    return answer;
}
```
