计算x的n次幂函数

### 直觉解法

Solution 1:

```
 class Solution{
    public double myPow(double x ,int n){
       doublle result = 1;
       for(int i =0 ; i < n; i++){
          reuslt *= x;
       }
       return result;
    }
 }
 
 时间复杂度o(n) 
 上面的没有考虑x,n为负数的情况,完善一下
 public class Solution{
   public double pow(dobule x ,int n) {
     if(n == 0) {
       return 1;
     }
     
     if(n < 0){
        n = -n;
        x = 1/x;
        
       doublle result = 1;
       for(int i =0 ; i < n; i++){
          reuslt *= x;
       }
       return result;
     }
   }
 }
 
 
 
 //此处需要再次复习  result *= x的用法  java的运算系统再次复习
```



Solution 2 

```
 class Solution{
    public double myPow(double x, int n ){
        return Math.pow(x,n);
    }
 }
```





### 解法分析

```
Pow(x,n):

  Subproblem:   subresult = pow(x,n/2)

Merge:

  if  n%2 == 1{

​      result = subresult *subresult *x;

}  else{

​     result = subresult * subresult;

}
```





Solution 3

分治的模板

1.terminator

2.process (split your big problem )

3.drill down(solve subproblem)

4.merge(subresult)

5.rever states



```
 class Solution{
   public double pow(double x ,int n) {
     if(n ==0){
       return 1;
     }
     if(n <0){
       n = -n;
       x = 1/x;
     }
     
     return (n%2 == 0) ? pow(x*x,n/2): x* pow(x*x,n/2);
   }
}



 class Solution{
  public double myPow(double x, int n ){
    
    //termintor
    if(n == 0){
       return 1;
     }
     if(n<0){
       n = -n;
       x= 1/x;
     }
     
     
     //split your problem and drill down
     double half= myPow(x,n/2);
     
     //merge
     return (n%2 ==0)? half*half : x*half*half;
  }
}
```

