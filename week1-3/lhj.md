# Linear Algebra Review
기계학습 적용 0-indexed 를 주로 사용
수학은 1-indexed  , // 강의는 1-indexed 로 진행

행렬 표시는 대문자로 표시함


## Matrices and Vectors
```
% The ; denotes we are going back to a new row.
A = [1, 2, 3; 4, 5, 6; 7, 8, 9; 10, 11, 12]
A = 4x3 matrix

% Initialize a vector
v = [1;2;3]

% Get the dimension of the matrix A where m = rows and n = columns
[m,n] = size(A)

% You could also store it this way
dim_A = size(A)

% Get the dimension of the vector v
dim_v = size(v)

% Now let's index into the 2nd row 3rd column of matrix A
A_23 = A(2,3)
```

## Addition and Scalar Multiplication
```
% Initialize matrix A and B
A = [1, 2, 4; 5, 3, 2]
B = [1, 3, 4; 1, 1, 1]

% Initialize constant s
s = 2

% See how element-wise addition works
add_AB = A + B

% See how element-wise subtraction works
sub_AB = A - B

% See how scalar multiplication works
mult_As = A * s

% Divide A by s
div_As = A / s

% What happens if we have a Matrix + scalar?
add_As = A + s
```

3 x 4 * 4 x 1 = 3 x 1 matrix

## Matrix-Vector Multiplication
```
% Initialize matrix A
A = [1, 2, 3; 4, 5, 6;7, 8, 9]

% Initialize vector v
v = [1; 1; 1]

% Multiply A * v
Av = A * v
```

## Matrix-Matrix Multiplication
```
% Initialize a 3 by 2 matrix
A = [1, 2; 3, 4;5, 6]

% Initialize a 2 by 1 matrix
B = [1; 2]

% We expect a resulting matrix of (3 by 2)*(2 by 1) = (3 by 1)
mult_AB = A*B

% Make sure you understand why we got that result
```


## Matrix Multiplication Properties

실수는 교환법칙이 성립
행렬은 교환법칙 성립x, 임의로 행렬곱셈순서 바꾸면안됨

실수는 곱셈간 결합법칙이 성립 (associative)
행렬또한 결합법칙 성립한다.
용어를 기억할 필요는 없음


```
% Initialize random matrices A and B
A = [1,2;4,5]
B = [1,1;0,2]

% Initialize a 2 by 2 identity matrix
I = eye(2)

% The above notation is the same as I = [1,0;0,1]

% What happens when we multiply I*A ?
IA = I*A

% How about A*I ?
AI = A*I

% Compute A*B
AB = A*B

% Is it equal to B*A?
BA = B*A

% Note that IA = AI but AB != BA
```

## Inverse and Transpose

### 역행렬
역행렬을 계산해주는 오픈소스라이브러리를 사용하기떄문에 직접할필요 없음
(Optive)


### 전치행렬 Matrix Transpose
- A<sup>T</sup>

```
% Initialize matrix A
A = [1,2,0;0,5,6;7,0,9]

% Transpose A
A_trans = A'

% Take the inverse of A
A_inv = inv(A)

% What is A^(-1)*A?
A_invA = inv(A)*A
```

-3 4 3
-9 4 15
