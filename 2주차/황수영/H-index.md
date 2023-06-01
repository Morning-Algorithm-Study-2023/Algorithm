### 코드

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        // 오름 차순 정렬
        Arrays.sort(citations);
        
        // h-index의 최대! 
        for (int i = 0; i < citations.length; i++) {
            int h = citations.length - i;
            
            // 인용 횟수 > 논문 갯수
            if (citations[i] >= h) {
                answer = h;
                break;
            }
        }
        
        return answer;
    }
}
```