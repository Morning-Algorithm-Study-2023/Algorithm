## 코드

```python
from bisect import bisect_left 

def solution(citations):
    answer = 0
    citations.sort()
    
    for h in range(max(citations)+1):
        # 정렬된 배열에 i을 넣을 경우 몇번째 index에 들어가게 되는지 return 
        temp=bisect_left(citations, h)
        # h번 이상 인용된 논문이 h편 이상이면
        if len(citations)-temp>=h:
            answer=max(answer, h)
    
    return answer
```
