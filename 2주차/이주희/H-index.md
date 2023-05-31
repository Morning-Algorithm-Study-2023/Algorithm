## 코드
```Java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = citations.length;
        // 내림차순 정렬
        citations = Arrays.stream(citations).boxed().sorted(Collections.reverseOrder()).mapToInt(Integer::intValue).toArray();
        
        for(int i=0; i<citations.length; i++) {
            if(citations[i] < i+1) {
                answer = i;
                break;
            }
        }
        
        return answer;
    }
}
```
