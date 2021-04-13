generate Parenthesis

### 题目描述

请写个算法,输入是一个正整数n,输出是n对括号的所有合法组合

### 题目解析

可将题目改写为:现在有2*n个位置,每个位置可以放 '(' 或者 ')' 组成的所有括号组合中,有多少是合法的,将这些合法的给列出来.

合法的括号组合,最后一定是左括号=右括号,在增加括号到n对的过程中,左括号的数量>右括号

### 思路解析

首先,想办法得到这全部的2的2n次方种组合,然后根据合法组合的性质删选合法的组合.

得到所有的组合: 暴力穷举回溯框架

得到合法的括号: 左括号可以随便加,只要不超过n, 加右括号必须保证左括号的数量比右括号的多

### 规范代码

1.  暴力穷举回溯

   ```
   class Solution{
      public List<String> generateParthesie(int n) {
         generate(0,2*n,"");
         return null;
      }
      
      
      public void generate(int level ,int max ,String s) {
         //termintor
         if(level == max){
             System.out.println(s);
             return;
         }
         
         //process current logic 
         String s1 = s+"(";
         String s2 = s+ ")";
         
         //drill down
         generate(level+1,max,s1);
         generate(lever+1,max,s2);   
      }
   }
   ```



2.根据条件合理剪枝

```
 class Solution {
        private List<String> result;

        public List<String> generateParenthesis(int n) {
            result = new ArrayList<>();
            generate(0, 0, n, "");
            return result;

        }

        private void generate(int left, int right, int max, String s) {
            if (left == max && right == max) {
                result.add(s);
                return;
            }
            if (left < max)
                generate(left + 1, right, max, s + "(");
            if (right < left && right < max)
                generate(left, right + 1, max, s + ")");
        }
    }

```

