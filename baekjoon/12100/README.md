### 문제
- https://www.acmicpc.net/problem/12100

### 접근
- dfs, 브루트포스를 이용해 구현한다.

### 실수했던 부분
- `12100_fail.java` 파일을 보면 dfs시 직전에 수행했던 방향에 대해서는 탐색을 수행하지 않도록 하였다.
  - 한번 움직인 방향으로는 그 직후순서에는 움직일 필요가 없다고 단순히 생각한 것이 원인이었다.
- 그런데 예를 들어 `[2 2 2 2]` 꼴의 행이 있을때 왼쪽방향으로 1번 움직이면 `[4 4 0 0]`이 되는데, 한번 더 왼쪽 방향으로 움직일 경우 `[8 0 0 0]`이 되어 이전 결과와 달라진다.

```java
for (int direction = 0; direction < 4; direction++) {
    // 불필요한 부분
    if (direction == prevDirection) {
        continue;
    }
}
```

 
- 따라서 dfs시 항상 모든 방향에 대해 탐색하도록 하도록 수정했다.
