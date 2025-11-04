# Counter

파이썬에서 Counter는 collections 모듈에 포함된 클래스입니다. Counter는 해시 가능한 객체의 개수를 세는 데 사용됩니다. 주로 리스트, 문자열, 튜플 등에서 요소의 빈도를 계산하는 데 유용합니다.

## 사용법

```python
from collections import Counter
# 리스트에서 요소의 빈도 계산
data = ['apple', 'banana', 'orange', 'apple', 'orange', 'banana', 'apple']
counter = Counter(data)
print(counter)
# 출력: Counter({'apple': 3, 'banana': 2, 'orange': 2})     

# 문자열에서 문자 빈도 계산
text = "hello world"
char_counter = Counter(text)
print(char_counter)
# 출력: Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, ' ': 1, 'w': 1, 'r': 1, 'd': 1})     
```

