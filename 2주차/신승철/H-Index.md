```java
import java.util.*;
import java.util.stream.IntStream;

class Solution {
    public int solution(int[] citations) {
        Arrays.sort(citations);
        return IntStream.range(0, citations.length)
                .filter(i -> citations[i] >= citations.length - i)
                .map(i -> citations.length - i)
                .findFirst()
                .orElse(0);
    }
}
```
