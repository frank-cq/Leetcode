##13 Roman to Integer

>Given a roman numeral, convert it to an integer.Input is guaranteed to be within the range from 1 to 3999.


```
public class Solution {
    public int romanToInt(String s) {
        s = s.toUpperCase();
        int len = s.length(), pre = 0, sum = 0 , countOfContinSameNum = 0;
        boolean isMinus = false;
	// 从右往左扫描，比右邻大的加入总和中，比右邻小的从总和中减掉
        for(int i=len-1; i>=0; i--){
            int cur = romanChar2Int(s.charAt(i));
            if(cur > pre){
                sum += cur;
                isMinus = false;
                countOfContinSameNum = 0;
            }
	    // 特殊情况，当前值等于右邻的值
	    // 若上一次运算为减，则当前应该也是减；若上一次为加，则当前也应该为加。
	    // 当某个数字连续出现3次后，下一相同的数字应该加入总和中
            else if(cur == pre){
                countOfContinSameNum++;    // 重复三次
                // 上一次是被减
                if(isMinus && countOfContinSameNum < 3){
                    sum -= cur;
                }
                else {
                    sum += cur;
                    isMinus = false;
                }
                if(countOfContinSameNum == 3){
                    countOfContinSameNum = 0;
                }
            }
            else {
                sum -= cur;
                isMinus = true;
                countOfContinSameNum = 0;
            }
            pre = cur;
        }
        return sum;
    }
    // 将单个的罗马字符转换为对应的数字
    public int romanChar2Int(char romanChar){
        int res;
        switch(romanChar){
            case 'I' :
                res = 1;
                break;
            case 'V' :
                res = 5;
                break;
            case 'X' :
                res = 10;
                break;
            case 'L' :
                res = 50;
                break;
            case 'C' :
                res = 100;
                break;
            case 'D' :
                res = 500;
                break;
            case 'M' :
                res = 1000;
                break;
            default :
                res = 0;
        }
        return res;
    }
}
```