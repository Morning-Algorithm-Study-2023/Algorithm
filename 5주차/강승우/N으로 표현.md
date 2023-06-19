![20230619154646](https://github.com/Morning-Algorithm-Study-2023/Algorithm/assets/121210456/a5e337e3-6392-4368-ba6b-2beed045f2c5)

## 코드

```java
import java.util.*;

class Solution {
    public int solution(int N, int number) {
        if(N==number){
            return 1;
        }
        
        // dp[index] -> 숫자 N을 index번 사용했을 때 나올 수 있는 모든 값
        ArrayList<Set<Integer>> dp = new ArrayList<>();
        Set<Integer> sub = new HashSet<>();
        
        // dp[0]을 null로 채우기 위해
        sub.add(0);
        dp.add(sub);
        
        // dp[1]={5}, dp[2]={55}, dp[3]={555} 초기화
        for (int i=1; i<=8; i++){
            Set<Integer> sublist = new HashSet<>();
            String value = "";

            for (int j = 1; j <= i; j++) {
                value += String.valueOf(N);
            }

            sublist.add(Integer.valueOf(value));
            dp.add(sublist);
        }
        
        // i가 4인 경우
        // dp[1],dp[3] 배열에 있는 값끼리 사칙연산
        // dp[2],dp[2] 배열에 있는 값끼리 사칙연산
        for (int i=2; i<=8; i++){
            for (int j=1; j<=i-1; j++){
                for(Integer k :dp.get(j)){
                    for (Integer l :dp.get(i-j)){
                        dp.get(i).add(k+l);
                        dp.get(i).add(k-l);
                        dp.get(i).add(k*l);
                        if (l!=0){
                            dp.get(i).add(k/l);
                        }
                    }
                }
            }
            // 최종값 number가 포함되어 있으면 index 리턴
            if (dp.get(i).contains(number)){
                return i;
            }
        }
        
        return -1;
    }
}
```
