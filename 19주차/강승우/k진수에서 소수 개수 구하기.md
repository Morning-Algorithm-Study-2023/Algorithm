![20230922133839](https://github.com/Morning-Algorithm-Study-2023/Algorithm/assets/121210456/6dd6f41e-e2e2-4a0d-ad62-5397669c5384)

## 코드
```java
class Solution {
    
    // 소수이면 true
    public boolean pri(Long a){
        if(a==1) return false;
        
        for(int i=2; i<Math.sqrt(a)+1; i++){
            if(a==i) continue;
            if(a%i==0) return false;
        }
        return true;
    }
    
    // 10진수 n을 k 진수로 변환
    public String change(int n, int k){
        StringBuilder result=new StringBuilder();
        while(n>k){
            result.append(n%k);
            n/=k;
        }
        result.append(n);
        return result.reverse().toString();
    }
    
    public int solution(int n, int k) {
        int answer = 0;
        
        String s=change(n,k);

        String str[] = s.split("0");
        
        // P처럼 소수 양쪽에 아무것도 없는 경우
        if(str.length==1){
            if(pri(Long.parseLong(str[0]))) return 1;
            else return 0;
        }
        
        for(int i=0; i<str.length; i++){
            if(str[i].equals("")) continue;
            if(pri(Long.parseLong(str[i]))) answer++;
        }
        
        return answer;
    }
}

 
```
