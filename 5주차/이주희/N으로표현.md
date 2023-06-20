## 소요시간, 메모리
![image](https://github.com/Morning-Algorithm-Study-2023/Algorithm/assets/83942393/78313119-a36e-4687-884f-63c4e8e88f85)

## 코드
```Java
import java.util.*;

class Solution {
    
    final int MAX=8;
    Set<Integer>[] cache;       //index개의 base로 만들 수 있는 수의 집합
    int base;                   //사용할 숫자
    
    public int solution(int N, int number) {
        int answer = -1;

        base = N;
        //cache init
        cache = new HashSet[MAX+1];      
        for(int i=1; i<=MAX; i++) {
            cache[i] = new HashSet<Integer>();
        }
        
        for(int i=1; i<=MAX; i++) {
            solve(i);       //i개의 base로 만들 수 있는 숫자 집합
            if(cache[i].contains(number)) {
                answer = i;
                break;
            }
        }
        return answer;
    }
    
    //n개의 base로 만들 수 있는 집합 
    Set<Integer> solve(int n) {
        if(!cache[n].isEmpty()) return cache[n];
        Set<Integer> res = new HashSet<>();
        
        int number=0;
        for(int i=0; i<n; i++) {
            number = number*10+base;
            res.add(number);
        }
        
        for(int i=1; i<n; i++){
            int j=n-i;
            
            Set<Integer> res1 = solve(i);
            Set<Integer> res2 = solve(j);
            
            for(Integer n1 : res1) {
                for(Integer n2 : res2) {
                    res.add(n1+n2);
                    res.add(n1-n2);
                    res.add(n1*n2);
                    if(n2!=0)
                        res.add(n1/n2);
                }
            }
        }
        
        return cache[n] = res;
    }
}
```
