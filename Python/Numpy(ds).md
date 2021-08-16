# Numpy

## 1. 넘파이 배열

```python
import numpy as np
```

- **array** : 리스트를 넣으면 *ndarray 클래스 객체*(배열)로 전환해줌.

  ​		 	리스트와 비슷해보이지만 type을 쓰면 ndarry임을 알 수 있음.

- **벡터화 연산** : 각 원소에 대한 반복연산을 하나의 명령어로 처리 가능

  ```python
  data = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  ```

  ```python
  # for 반복문을 쓸 때
  answer = []
  for di in data:
      answer.append(2 * di)
  answer
  
  >>> [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
  
  # 벡터화 연산
  x = np.array(data)
  2 * x
  
  >>> array([0, 2, 4, 6, 8, 10, 12, 14, 16, 18])
  ```

- **2차원 배열 만들기**

  ```python
  c = np.array([[0, 1, 2], [3, 4, 5]])  # 2 x 3 array
  c
  
  
  >>> array([[0, 1, 2],
         [3, 4, 5]])
  ```

- 3차원 배열