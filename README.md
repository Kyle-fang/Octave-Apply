# Octave-Apply
## 学习吴恩达机器学习用到的Octave的使用、
### Basic Operations
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

㖛>> ones(2,3)
ans =

   1   1   1
   1   1   1

>> v = 1:6
v =

   1   2   3   4   5   6

>> 2*ones(2,3)
ans =

   2   2   2
   2   2   2

>> e = [2 2 2; 2 2 2]
e =

   2   2   2
   2   2   2

>> f = zeros(1,3)
f =

   0   0   0

>> F = zeros(4,6)
F =

   0   0   0   0   0   0
   0   0   0   0   0   0
   0   0   0   0   0   0
   0   0   0   0   0   0

>> g = rand(2,3)
g =

   0.11700   0.32703   0.17218
   0.26123   0.84775   0.63163

%髙斯随机分布
>> G = randn(2,3)
G =

   1.355792   0.108585  -0.035532
   0.091131  -0.471969   0.634990

>> G = randn(1,3)
G =

  -0.28783   0.18452  -0.84966
>> h = -6 + sqrt(10)*randn(1,10000);
>> hist(h)
>> hist(h,50)
㐛>> eye(4)
ans =

Diagonal Matrix

   1   0   0   0
   0   1   0   0
   0   0   1   0
   0   0   0   1

>> eye(3, 4)
ans =

Diagonal Matrix

   1   0   0   0
   0   1   0   0
   0   0   1   0

%帮助命令
>> help eye
>> help randn
```
### Moving Data Around
```
%向量和矩阵的大小
>> length(A)
ans =  3
>> sz = size(A)
sz =

   3   2

>> size(sz)
ans =

   1   2

>> size(A,1)
ans =  3
>> size()A,2
parse error:

  syntax error

>>> size()A,2
          ^

>> size(A,2)
ans =  2

%
>> pwd
ans = C:\Users\famg
>> cd ''
>> cd 'E:\JNB'
>> pwd
ans = E:\JNB
>> ls
 Volume in drive E has no label.
 Volume Serial Number is 0005-03D1

 Directory of E:\JNB

[.]              [..]             test.ipynb.url
               1 File(s)             68 bytes
               2 Dir(s)  157,024,747,520 bytes free
>> load 'E:\Machine-Learning\Octave'
error: load: unable to find file E:\Machine-Learning\Octave
>> cd 'E:\Machine-Learning\Octave'
>> pwd
ans = E:\Machine-Learning\Octave
>> load train.dat
>> load('train2.dat')
>> who
Variables in the current scope:

A       F       G       ans     e       f       g       h       sz      train   train2  v
>> whos
Variables in the current scope:

   Attr Name        Size                     Bytes  Class
   ==== ====        ====                     =====  =====
        A           3x2                         48  double
        F           4x6                        192  double
        G           1x3                         24  double
        ans         1x26                        26  char
        e           2x3                         48  double
        f           1x3                         24  double
        g           2x3                         48  double
        h           1x10000                  80000  double
        sz          1x2                         16  double
        train       3x2                         48  double
        train2      6x2                         96  double
        v           1x6                         24  double

Total is 10100 elements using 80594 bytes

>> size(train2)
ans =

   6   2

>> clear train
>> whos
Variables in the current scope:

   Attr Name        Size                     Bytes  Class
   ==== ====        ====                     =====  =====
        A           3x2                         48  double
        F           4x6                        192  double
        G           1x3                         24  double
        ans         1x2                         16  double
        e           2x3                         48  double
        f           1x3                         24  double
        g           2x3                         48  double
        h           1x10000                  80000  double
        sz          1x2                         16  double
        train2      6x2                         96  double
        v           1x6                         24  double

Total is 10070 elements using 80536 bytes

>> V = train2(1:3)
V =

   2013   3278   1429
>> whos
Variables in the current scope:

   Attr Name        Size                     Bytes  Class
   ==== ====        ====                     =====  =====
        A           3x2                         48  double
        F           4x6                        192  double
        G           1x3                         24  double
        V           1x3                         24  double
        ans         1x2                         16  double
        e           2x3                         48  double
        f           1x3                         24  double
        g           2x3                         48  double
        h           1x10000                  80000  double
        sz          1x2                         16  double
        train2      6x2                         96  double
        v           1x6                         24  double

Total is 10073 elements using 80560 bytes

>> V
V =

   2013   3278   1429

>> save V.data V
>> save V.dat V
>> clear
>> whos
>> load V.dat

>> whos
Variables in the current scope:

   Attr Name        Size                     Bytes  Class
   ==== ====        ====                     =====  =====
        V           1x3                         24  double

Total is 3 elements using 24 bytes

%以ascll码的格式保存，默认是以二进制格式保存
>> save I.dat i -ascii
>> j = [1 2; 3 4; 5 6; 7 8]
j =

   1   2
   3   4
   5   6
   7   8

>> j(2,1)
ans =  3
>> j(3,:)
ans =

   5   6

>> j(:,2)
ans =

   2
   4
   6
   8

>> j([1 3],:)
ans =

   1   2
   5   6
>> j(1,:) = [2 1]
j =

   2   1
   3   4
   5   6
   7   8

>> j(:,2) = [8;6;4;1]
j =

   2   8
   3   6
   5   4
   7   1

>> j(4,2) = 2
j =

   2   8
   3   6
   5   4
   7   2

>> j(1,1) = 1
j =

   1   8
   3   6
   5   4
   7   2
>> j = [j,[9;10;11;12]]
j =

    1    8    9
    3    6   10
    5    4   11
    7    2   12

>> j = [[1 2 3];j]
j =

    1    2    3
    1    8    9
    3    6   10
    5    4   11
    7    2   12

>> j(:)
ans =

    1
    1
    3
    5
    7
    2
    8
    6
    4
    2
    3
    9
   10
   11
   12
```
