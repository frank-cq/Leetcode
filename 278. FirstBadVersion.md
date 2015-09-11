## 278. First Bad Version

> You are a product manager and currently leading a team to develop a new product. Unfortunately, 
the latest version of your product fails the quality check. Since each version is developed based 
on the previous version, all the versions after a bad version are also bad.

> Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, 
which causes all the following ones to be bad.

> You are given an API bool isBadVersion(version) which will return whether version is bad.
Implement a function to find the first bad version. You should minimize the number of calls to the API.


```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        if(isBadVersion(1)){
            return 1;
        }       
        int from = 1, to = n, mid;
        while(from != to){
            mid = from+(to-from)/2;    // 比 mid=(from+to)/2 降低了运算等级，否则会出现Time Limit exceeded
            if(isBadVersion(mid)){
                to = mid;
            }
            else {
                from = mid+1;
            }
        }
        return to;
    }
}
```
