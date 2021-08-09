# Data Analysis

## Numpy 활용하기

### 1. Numpy란?

- **Num**erical **Py**thon
- Python의 고성능 과학 계산용 패키지

#### Numpy의 특징

- List보다 빠르고, 메모리 효율적 사용

### 2. ndarry (Numpy Diemsional Array)

- import

- ```python
  import numpy as np
  ```

- Array 생성

- ```python
  test_array = ([1, 4, 5, 8], float)
  print(test_array)
  ```

### 3. Array shape

1. Vector (1차원)

   ```python
   vector = [1, 4, 5, 8]
   np.array(vector, int).shape
   ```

   ```py
   (4, )
   ```

   : 1차원에 4개의 element 가 존재.

2. Matrix (2차원)

   ```py
   Matrix = [[1,2,5,8], [2,3,4,9]]
   np.array(matrix, int).shape
   ```

   ```py
   (2, 4)
   ```

   : 행이 2개, 열이 4개인 2차원 매트릭스

3. Tensor (3차원)

   ```Py
   tensor = [[[1,2,3,4], [2,3,4,6],[4,5,6,7]],
   		[[1,2,3,4], [2,3,4,6],[4,5,6,7]]
           [[1,2,3,4], [2,3,4,6],[4,5,6,7]]
   		[[1,2,3,4], [2,3,4,6],[4,5,6,7]]]
   np.array(tensor, int).shape
   ```

   ```py
   (4, 3, 4)
   ```

   : 평면이  4개, 행이 3개, 열이 4개인 3차원 텐서

4. Reshape

   - Array의 shape를 변경

     ```python
     np.array(test_array).reshape(x, y)
     ```

     (a, b) 모양의 array를 (x, y) 모양으로 변경.

     ```py
     np.array(test_array).reshape(x, y, -1)
     ```

     하나의 차원을 -1로 비워놓으면 전체 element의 크기에 따라서 파이썬이 자동으로 shape를 결정.

5.  Flatten

   ```python
   np.array(test_matrix).flatten()
   ```

   - 다차원 array를 1차원 array로 전환



### 4. Indexing & Slicing

1. indexing

   ```py
   a = np.array([[1,2,3],[4,5,6]], int)
   
   a[0][0] = a[0,0]
   ```

   - matrix의 경우 앞은 행(row), 뒤는 열(column)

2. Slicing

   ```python
   a = np.array([[1,2,3,4,5],[6,7,8,9,0]], int)
   
   a[:, 2:3] # 전체 row의 2열 이상
   a[1, 1:3] # 1행의 1~2열
   ```

   - List와 달리 행과 열 부분을 나눠서 slicing 가능.
   - 부분집합을 추출할 떄 유용.

