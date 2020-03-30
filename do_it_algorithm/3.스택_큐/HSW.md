### 탑
```java

	public static int[] solution(int[] heights) {
		Queue<Integer> queue = new LinkedList<Integer>();
		
		int size = heights.length ;    // int[] Size
		int[] answer = new int[size];  // answer 길이 설정

		// Queue Setting
		for(int i = size - 1; 0 <= i ; i--) {
			queue.offer(heights[i]);
		}

		//Queue가 Empty일까지 실행
		while(!queue.isEmpty()) {
			int first = queue.poll();
			
			for(int i = queue.size(); 0 <= i ; i--) {
				if(heights[i] > first) {
					answer[queue.size()] = i+1;
					break;
				}else {
					answer[queue.size()] = 0;
				}
			}	
		}
		
		return answer;
	}

```

### 트럭
```java

	public static int solution(int bridge_length, int weight, int[] truck_weights) {

		Queue<Integer> queue = new LinkedList<Integer>();   // 다리
		int len = truck_weights.length;                     // 정류장의 크기
		
		int sum_weight = 0; // 다리 위의 총 무게
		int idx = 0;        // 트럭 index
		int max = 0;        // 도착한 트럭 수
		int answer = 0;     // 소요 시간
		
		
		while(len != max) { // 시작 정류장 트럭 수 == 도착한 트럭 수
			int truck = truck_weights[idx];   
			int arrive_weight = 0;
			
			// 다리 끝에 도착한 트럭 내보내기
			if( bridge_length == queue.size() ) {
				arrive_weight = queue.poll();
				sum_weight -= arrive_weight;
			}

			// 트럭 입장 여부 판단
			if( bridge_length > queue.size() ) {
				sum_weight += truck;
				
				// 다리 무게 체크
				if(weight >= sum_weight) {
					queue.offer(truck);
					
					//★ 트럭 1대 예외처리 (트럭 1대일때 자꾸 에러나서 강제로 박음) 잘못 짠듯 구조를.....
					if(len-1 > idx) {
						idx++;
					}
				// 다리 무게 초과 시 , 0
				}else {
					queue.offer(0);
					sum_weight -= truck;
				}
			}
			
			// 도착한 트럭 수 ++ 
			if(arrive_weight != 0) {
				max++;
			}
			
			answer++;
		}
		
		System.out.println(answer);
		return answer;
	}

```



#기능개발
```java

	class Develop {
		int progresses;
		int speeds;
		int idx;

		public Develop(int progresses, int speeds, int idx) {
			this.progresses = progresses;
			this.speeds = speeds;
			this.idx = idx;
		}

		public void commit() {
			progresses += speeds;
		}

		public int getProgresses() {
			return progresses;
		}

		public int getSpeeds() {
			return speeds;
		}

		public int getIdx() {
			return idx;
		}

	}

	public static void main(String[] args) {

		Performance_Queue performance = new Performance_Queue();
		performance.solution(new int[] { 93 , 30 , 55 , 60 }, new int[] { 1, 30 , 5 , 40  });
	}

	public int[] solution(int[] progresses, int[] speeds) {
		Queue<Develop> queue = new LinkedList<>();
		Queue<Develop> queue2 = new LinkedList<>();
		Queue<Integer> queue3 = new LinkedList<>();

		int finallyCnt = 0;  // 최종 완료 개수 
		int forwardIdx = 0;  // 최전방 Inx

		int progress = 0;
		int index  = 0;

		// Queue Setting
		for (int i = 0; i < progresses.length; i++) {
			queue.offer(new Develop(progresses[i], speeds[i], i));
		}

		while (finallyCnt != progresses.length) {   // 최종 완료 개수 == 프로세스 수 
			Develop develop = queue.poll();
			
			// 개발 진행
			if(develop != null) {
				develop.commit();
				// 진행률 / 인덱스 가져옴
				progress = develop.getProgresses();
				index    = develop.getIdx();
			}

			// 개발 완료된 건은 따로 보관 첫번째 순서부터
			if (progress >= 100 & forwardIdx == index) {
				queue2.offer(develop);
				forwardIdx++;
			} else {
				queue.offer(develop);
				
				// 100% 개발 건 내보내기
				if(!queue2.isEmpty()) {
					queue3.offer(queue2.size());
					finallyCnt += queue2.size();
					queue2.clear();
				}
			}
		}

		
		//결과 담기
		int[] answer = new int[queue3.size()];
		for (int i = 0; i < answer.length; i++) {
			System.out.println(queue3.peek());
			answer[i] = queue3.poll();
		}

		return answer;
	}

```