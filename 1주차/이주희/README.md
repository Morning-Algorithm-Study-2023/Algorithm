## 코드

```java
import java.util.*;

class Solution {
    public List<Integer> solution(int[] progresses, int[] speeds) {
        List<Integer> ans = new ArrayList<>();
        int now=(int)Math.ceil((100-progresses[0]) / (double)speeds[0]), cnt=1;	    // 현재 날짜
        for(int i=1; i<progresses.length; i++) {
            int day = (int)Math.ceil((100-progresses[i]) / (double)speeds[i]);      // 걸리는 날짜
            if(now >= day) {		// 현재 날짜보다 먼저 끝났다면 갯수 증가
                cnt++;
            } else {			// 늦게 끝난다면 이전 작업 ans 에 넣고 현재 날짜와 갯수 변경
                ans.add(cnt);
                cnt = 1;
                now = day;
            }
        }
        ans.add(cnt);			// 마지막 배포 갯수 삽입
        return ans;
    }
}
```
