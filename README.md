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
   
>> k = [1 2;3 4]
k =

   1   2
   3   4

>> l = [5 6;7 8]
l =

   5   6
   7   8

>> m = [k l]
m =

   1   2   5   6
   3   4   7   8

>> n = [k;l]
n =

   1   2
   3   4
   5   6
   7   8
```

### Computing on Data
```
>> A = [1 2; 3 4; 5 6]
A =

   1   2
   3   4
   5   6

>> B = [11 12; 13 14; 15 16]
B =

   11   12
   13   14
   15   16

>> C = [1 1; 2 2]
C =

   1   1
   2   2

>> A*C
ans =

    5    5
   11   11
   17   17

%矩阵A的转置
>> A'
ans =

   1   3   5
   2   4   6
   
%将两个矩阵中的元素对应相乘
>> A.*B
ans =

   11   24
   39   56
   75   96

%将矩阵中的每个元素平方
>> A.^2
ans =

    1    4
    9   16
   25   36

%用1除以矩阵中的每一个元素
>> v = [1;2;3]
v =

   1
   2
   3

>> 1./v
ans =

   1.00000
   0.50000
   0.33333
>> 1./A
ans =

   1.00000   0.50000
   0.33333   0.25000
   0.20000   0.16667

%对矩阵中的每一个元素取对数、指数、绝对值、负数
>> log(v)
ans =

   0.00000
   0.69315
   1.09861

>> exp(v)
ans =

    2.7183
    7.3891
   20.0855

>> abs(v)
ans =

   1
   2
   3

>> -v
ans =

  -1
  -2
  -3
>> v + 1

%求矩阵元素的最大值
瑮ㄛ>> val = max(A)
val =

   5   6

>> A
A =

   1   2
   3   4
   5   6

>> [val, ind] = max(A)
val =

   5   6

ind =

   3   3

>> val1 = max(v)
val1 =  3
>> [val1,ind1] = max(v)
val1 =  3
ind1 =  3

%将矩阵中的每一个元素与某个值比较，返回1和0表示真假
>> a = [1 3 8 2 6 7 4 8 5]
a =

   1   3   8   2   6   7   4   8   5

>> a<5
ans =

  1  1  0  1  0  0  1  0  0

>> a>8
ans =

  0  0  0  0  0  0  0  0  0

>> a>=8
ans =

  0  0  1  0  0  0  0  1  0
  
%margic矩阵是每一行、每一列、对角线元素相加都相等的矩阵  
>> M = magic(3)
M =

   8   1   6
   3   5   7
   4   9   2

>> M1 = magic(5)
M1 =

   17   24    1    8   15
   23    5    7   14   16
    4    6   13   20   22
   10   12   19   21    3
   11   18   25    2    9

%寻找矩阵中符合条件的元素
>> find(M>=7)
ans =

   1
   6
   8
%r、c分别表示符合条件元素的横纵坐标
>> [r,c] = find(M<=4)
r =

   2
   3
   1
   3

c =

   1
   1
   2
   3
%验证   
>> M(2,1)
ans =  3
>> M(1,2)
ans =  1

%将矩阵中的元素相加
>> sum(a)
ans =  18.500
%将矩阵中的元素相乘
>> prod(a)
ans =  15
%向下取整
>> floor(a)
ans =

    1   15    2    0
%向上取整
>> ceil(a)
ans =

    1   15    2    1

%将两个矩阵对应的元素相比较，得到较大的那个元素留下
>> max(rand(3),rand(3))
ans =

   0.38542   0.73975   0.93984
   0.73813   0.51988   0.52885
   0.99654   0.46006   0.92770

%得矩阵每一列的最大值，‘1’的含义是第一维的元素
>> max(M, [], 1)
ans =

   8   9   7

>> max(M, [], 2)
ans =

   8
   7
   9

%
>> M2 = magic(9)
M2 =

   47   58   69   80    1   12   23   34   45
   57   68   79    9   11   22   33   44   46
   67   78    8   10   21   32   43   54   56
   77    7   18   20   31   42   53   55   66
    6   17   19   30   41   52   63   65   76
   16   27   29   40   51   62   64   75    5
   26   28   39   50   61   72   74    4   15
   36   38   49   60   71   73    3   14   25
   37   48   59   70   81    2   13   24   35

%对矩阵的每一列求和
>> sum(M2, 1)
ans =

   369   369   369   369   369   369   369   369   369
%对矩阵的每一行求和
>> sum(M2,2)
ans =

   369
   369
   369
   369
   369
   369
   369
   369
   369

%求对角线元素的和
>> M2.*eye(9)
ans =

   47    0    0    0    0    0    0    0    0
    0   68    0    0    0    0    0    0    0
    0    0    8    0    0    0    0    0    0
    0    0    0   20    0    0    0    0    0
    0    0    0    0   41    0    0    0    0
    0    0    0    0    0   62    0    0    0
    0    0    0    0    0    0   74    0    0
    0    0    0    0    0    0    0   14    0
    0    0    0    0    0    0    0    0   35

%
>> sum(sum(ans))
ans =  369


>> t = [1 2; 3 4]
t =
   1   2
   3   4
%对矩阵t求逆
>> pinv(t)
ans =

  -2.00000   1.00000
   1.50000  -0.50000
```
### plotting data
```
>>t = 0:0.01:1;
>> y = sin(2*pi*4*t);
>> plot(t,y)
>> y2 = cos(2*pi*4*t);
>> plot(t,y2)
>> hold on;
>> plot(t,y)
>> plot(t,y2)
%添加标签和标题
>> xlabel('time')
>> ylabel('values')
>> title('my plot')
%保存图片
>> cd 'E:\Machine-Learning\Octave'; print -dpng 'myplot.png'
%关闭显示图像窗口
>> close
%将图像显示在不同的窗口上
>> figure(1);plot(t, y);
>> figure(2);plot(t, y2);
%分区显示图像
>> subplot(121);
>> plot(t, y)
>> subplot(122);
>> plot(t, y2)
```
