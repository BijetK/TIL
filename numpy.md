# numpy

## - numpy.argsort

: Array를 정렬하는 함수

```python
a = np.array([1.5, 0.2, 4.2, 2.5])

# 오름차순
a[a.argsort()]

=> [0.2, 1.5, 2.5, 4.2]

# 내림차숭
a[a.argsort()[::-1]] or a[a.argsort()][::-1]

=> [4.2, 2.5, 1.5, 0.2]
```





## - numpy.arange([start], stop, [step])

: 반열린구간 [start, stop) 에서 step 의 크기만큼 일정하게 떨어져 있는 숫자들을 array 형태로 반환해 주는 함수

```python
np.arange(3)	# stop=-3만 주어져서 기본단위인 1단위로 0, 1, 2
=> array([0, 1, 2])

np.arange(3.0)	# stop = 3.0 형식으로 주어져서 어레이도 0., 1., 2. 으로 나옴
=> array([ 0.,  1.,  2.])

np.arange(3,7)	# step이 주어지지않아서 [3, 7) 에서 1 단위씩.
=> array([3, 4, 5, 6])

np.arange(3,7,2) # [3, 7)에서, 3부터 2단위씩 증가하는 어레이 반환
=> array([3, 5])
```

