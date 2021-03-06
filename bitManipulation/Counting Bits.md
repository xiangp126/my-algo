## Counting Bits
### Illustrate
<https://leetcode.com/problems/counting-bits/>

### Concept
**`num & (num - 1)`**

remove the last *1*

```
10 & (10 - 1) =
        0000 1010
(+)     0000 1001
    -------------
        0000 1000
             ^
```

### Code
C++

```c++
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> ret(num + 1, 0);
        for (int i = 0; i <= num; ++i) {
            ret[i] = countBit(i);
        }
        return ret;
    }

    int countBit(int val) {
        int cnt = 0;
        while (val) {
            val &= (val - 1);
            ++cnt;
        }
        return cnt;
    }
};
```

Java

```java
class Solution {
    public int[] countBits(int num) {
        int[] ret = new int[num + 1];
        for (int i = 0; i <= num; ++i) {
            ret[i] = countBit(i);
        }
        return ret;
    }

    public int countBit(int val) {
        int cnt = 0;
        while (val != 0) {
            val &= val - 1;
            ++cnt;
        }
        return cnt;
    }
}
```