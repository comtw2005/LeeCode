29. Divide Two Integers


Java
![圖片](https://github.com/user-attachments/assets/ef7bb7ea-217a-402d-a3bb-28058e6a6804)


```
class Solution {
   public int divide(int dividend, int divisor) {

      Long dividendL = Long.valueOf(dividend);
      Long divisorL = Long.valueOf(divisor);

      boolean neg_flag = true;
      int count = 0;

      if (divisorL == 0)  return Integer.MAX_VALUE;
      if (dividendL == 0) return 0;
      if (divisorL == 1)  return dividend;

      if (dividendL < 0) {
         dividendL = -dividendL;
         neg_flag = !neg_flag;
      }

      if (divisorL < 0) {
         divisorL = -divisorL;
         neg_flag = !neg_flag;
      }

      while (divisorL <= dividendL) {
         dividendL = dividendL - divisorL;
         count++;

         if (dividendL > (divisorL * count)) {

            dividendL = dividendL - (divisorL * count);
            count += count;
//            System.out.println(dividendL + "=" + dividendL + "-" + divisorL + ", count = " + count);
         }

         
         if (!neg_flag) {
            int countTmp = -count ;

            if (Integer.MIN_VALUE >= countTmp) {
               return Integer.MIN_VALUE;
            }

            if (countTmp >= Integer.MAX_VALUE) {
               return Integer.MAX_VALUE;
            }
         } else {

            if (Integer.MIN_VALUE >= count) {
               return Integer.MIN_VALUE;
            }

            if (count >= Integer.MAX_VALUE) {
               return Integer.MAX_VALUE;
            }
         }
      }

      if (!neg_flag)
         count = -count;

      if (Integer.MIN_VALUE >= count) {
         return Integer.MIN_VALUE;
      }

      if (count >= Integer.MAX_VALUE) {
         return Integer.MAX_VALUE;
      }

      return count;
   }
}
```

Test Case
```
10
3
7
-3
-2147483648
-1
2147483647
2147483647
1981445587
1172010393
1100540749
-1090366779
-2147483648
2
-2147483648
1
-2147483648
-1
2147483647
1
-2147483648
1
2147483647
-1
0
0
-2147483648
-1
-2147483648
-1
2147483647
-1
```
