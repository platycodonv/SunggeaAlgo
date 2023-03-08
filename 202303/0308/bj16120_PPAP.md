## bj16120_PPAP.md

https://www.acmicpc.net/problem/16120

---
#### 알고리즘 : BFS
#### 시간제한 : 1초, 메모리 제한 : 512MB
#### 시간 : 384ms, 메모리 : 52942KB
---
### 풀이 과정 : 
1. 입력받은 문자열을 한 글자씩 StringBuilder 에 추가 
2. StringBuilder의 길이가 4이상일 경우 끝에 4개가 PPAP 일 경우 P만 남기고 제거
3. 마지막에 StringBuilder가 P또는 PPAP 일 경우 PPAP 출력
4. 아닐경우 NP 출력
### 배울점

https://www.acmicpc.net/problem/9935 <br>
문자열 폭발 문제랑 비슷한거같음. <br>
풀어봤던게 도움이 된거같다.

----
### Source
```java
import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.InputStreamReader;

public class Main{
    static String str;
    final static String ppap = "PPAP";

    public static void main(String[] args) throws Exception {
        init();
    }

    static void init() throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        str = br.readLine();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < str.length(); i++) {
            sb.append(str.charAt(i));
            if (sb.length() < 4) continue;
            String tmp = sb.substring(sb.length() - 4, sb.length());
            if (tmp.equals(ppap)) {
                sb.delete(sb.length() - 3, sb.length());
            }
        }
        String toString = sb.toString();
        if (toString.equals("P") || toString.equals(ppap)) System.out.print(ppap);
        else System.out.print("NP");
    }
}
```
