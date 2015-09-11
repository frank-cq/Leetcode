## 263. Ugly Number

> Write a program to check whether a given number is an ugly number.
Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.
Note that 1 is typically treated as an ugly number.


```java
public class Solution {
    public boolean isUgly(int num) {
        if(num <= 0){
            return false;
        }
        if(num == 1){
            return true;
        }
        while(num != 1){
            boolean isChanged = false;
            if(num%2 == 0){
                num /= 2;
                isChanged = true;
            }
            if(num%3 == 0){
                num /=3;
                isChanged = true;
            }
            if(num%5 == 0){
                num /=5;
                isChanged = true;
            }
            if(!isChanged && num != 1){
                return false;
            }
        }
        return true;
    }
}
```