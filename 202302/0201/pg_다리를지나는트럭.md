## pg_다리를지나는트럭.md

https://school.programmers.co.kr/learn/courses/30/lessons/42583

---
#### 알고리즘 : 큐
---
### 풀이 과정 : 
1. 대기중인 트럭이 다리 위에 올라갈 수 있는지 조건 확인(무게, 다리길이) 가능하다면 다리를 나타내는 bridge queue에 삽입.
2. 다리 위에 오른 트럭들이 오른 시간 + 1
3. 다리에 오른 순서대로 다리 길이만큼 시간이 경과하였을 경우 다리에서 내려온다.(queue에서 제거)
4. 처음에 대기중이 었던 트럭의 수만큼 트럭이 내려오면 종료
### 배울점
큐

----
### Source
```java
public class 다리를지나는트럭 {

    static class Pair {
        int weight;
        int time;

        public Pair(int weight, int time) {
            this.weight = weight;
            this.time = time;
        }
    }

    public static void main(String[] args) throws Exception {
        System.out.print(solution(2, 10, new int[]{7, 4, 5, 6}));
    }

    static int solution(int bridge_length, int weight, int[] truck_weights) {
        int answer = 0;
        ArrayDeque<Integer> queue = new ArrayDeque<>();
        ArrayDeque<Pair> bridge = new ArrayDeque<>();
        int curr_weight = 0;
        int clear = 0;
        for (int truck : truck_weights) queue.offer(truck);

        while (true) {
            if (!queue.isEmpty()) {
                if (bridge.size() + 1 <= bridge_length && curr_weight + queue.peek() <= weight) {
                    curr_weight += queue.peek();
                    bridge.offer(new Pair(queue.pop(), 0));
                }
            }
            for (Pair pair : bridge) pair.time += 1;
            if (bridge.peek().time == bridge_length) {
                curr_weight -= bridge.pop().weight;
                clear++;
            }

            answer++;
            if (clear == truck_weights.length) break;
        }
        return answer + 1;
    }
}


```
