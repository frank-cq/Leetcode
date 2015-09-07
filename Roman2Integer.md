##13 Roman to Integer

>Given a roman numeral, convert it to an integer.Input is guaranteed to be within the range from 1 to 3999.


```
public class Solution {
    public int romanToInt(String s) {
        s = s.toUpperCase();
        int len = s.length(), pre = 0, sum = 0 , countOfContinSameNum = 0;
        boolean isMinus = false;
	// ��������ɨ�裬�����ڴ�ļ����ܺ��У�������С�Ĵ��ܺ��м���
        for(int i=len-1; i>=0; i--){
            int cur = romanChar2Int(s.charAt(i));
            if(cur > pre){
                sum += cur;
                isMinus = false;
                countOfContinSameNum = 0;
            }
	    // �����������ǰֵ�������ڵ�ֵ
	    // ����һ������Ϊ������ǰӦ��Ҳ�Ǽ�������һ��Ϊ�ӣ���ǰҲӦ��Ϊ�ӡ�
	    // ��ĳ��������������3�κ���һ��ͬ������Ӧ�ü����ܺ���
            else if(cur == pre){
                countOfContinSameNum++;    // �ظ�����
                // ��һ���Ǳ���
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
    // �������������ַ�ת��Ϊ��Ӧ������
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