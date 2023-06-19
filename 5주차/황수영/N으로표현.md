### 코드

- N(5)으로 만들 수 있는 모든 수 구하기
  - ex. 5+5, 5/5, 5*5 등등
- 숫자 갯수를 기준으로! => 답은 1~8까지 이므로 8개까지만 구하기

```java
import java.util.*;

class Solution {
    
    public int solution(int N, int number) {        
        // 숫자 i개로 만들 수 있는 값들
        List<Set<Integer>> data = new ArrayList<>();
        for (int i = 0; i <= 8; i++ ) {
            data.add(new HashSet<Integer>());
        }
        data.get(1).add(N);
        
        // 1번 통 셋팅
        if (number == N) {
            return 1;
        }
        
        // 2~8번 통 셋팅
        for (int i = 2; i <= 8; i++) {
            Set<Integer> tmp = data.get(i);
            
            for (int j = 1; j < i ; j++) {
                Set<Integer> first = data.get(j);
                Set<Integer> second = data.get(i-j);
                
                // 두 통의 모든 경우의 수 구하기
                for (int firstTmp : first) {
                    for (int secondTmp : second) {
                        tmp.add(firstTmp+secondTmp);
                        tmp.add(firstTmp-secondTmp);
                        tmp.add(firstTmp*secondTmp);
                        if (firstTmp != 0 && secondTmp != 0) {
                            tmp.add(firstTmp/secondTmp);
                        }
                    }
                }
                
            }
            
            int sameNum = N;
            for (int k = 1; k < i; k++) {
                sameNum += Math.pow(10, k) * N;
            }
            tmp.add(sameNum);
    
            if(tmp.contains(number)) {
                return i;
            }
        }
        
        return -1;
    }
}
```