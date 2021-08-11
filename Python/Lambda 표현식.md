# Unit 32. Lambda 표현식

## 32.1 lambda 표현식으로 함수 만들기

지금까지 배운 0기본적인 함수 사용법은 다음과 같다.

```python
def plus_ten(x):
	return x + 10

plus_ten(1)


11
```

---

- **lambda 매개변수들: 식**

  ```python
  lambda x: x + 10
  
  <function <lambda> at 0x02C27270>
  ```

  lambda는 이름이 없는 함수(anonymous function)을 만든다.

  따라서 lambda로 만든 익명함수를 호출하려면 변수에 할당해주어야 한다.

  ```python
  plus_ten = lambda x: x + 10
  
  plus_ten(1)
  
  11
  ```

  ```bash
  (lambda x: x + 10)(1)	# 이런 방식으로 람다 표현식 자체를 호출할 수 있다
  ```

  

  ![032001](./md-images/032001.png)

- ```python
(lambda x: y = 10; x + y)(1)	# 람다 표현식 안에서는 변수 생성 불가
  SyntaxError: invalid syntax
  ```
  


