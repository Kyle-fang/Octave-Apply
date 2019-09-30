# Octave-Apply
## 学习吴恩达机器学习用到的Octave的使用
```
%数学基本运算
>> 3 + 2
ans =  5
>> 6 -1
ans =  5
>> 3*4
ans =  12
>> 2^3
ans =  8

%逻辑运算
>> 1 == 2
ans = 0
>> 2 ~= 5
ans = 1
>> 1 && 0
ans = 0
>> 1 || 0
ans = 1
>> a = 3
a =  3
>> b = 7;
>> b
b =  7
>> str = 'hello world';
>> disp(str)
hello world

%数据类型
>> c = pi
c =  3.1416
>> disp(sprintf('2 decimals: %0.2f', c))
2 decimals: 3.14
>> disp(sprintf('2 decimals: %0.7f', c))
2 decimals: 3.1415927
>> format long
>> c
c =  3.141592653589793
>> format short
>> c
c =  3.1416


%矩阵、向量
>> A = [1 2; 3 4; 5 6]
A =

   1   2
   3   4
   5   6
   ࠒƩ>> B = [1 2 3]
B =

   1   2   3

>> C = [1; 2; 3;4]
C =

   1
   2
   3
   4

>> D = 1:2:10
D =

   1   3   5   7   9
```
