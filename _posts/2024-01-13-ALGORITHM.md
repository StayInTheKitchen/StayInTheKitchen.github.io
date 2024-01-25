---
layout : post
title : 오늘의 Algorithm
---

# 홀수 판별

## 나머지 연산 (기본적인 방식)

```
if (x % 2 == 1)
```

## 비트 연산 (새로 배운 방식)
```
if (x & 1)
```

# 정렬 라이브러리 함수

## std::sort

- \<algorithm> header include

`sort(arr, arr + <number_of_arr>, (compare))`

- 구체적인 동작원리 등은 C++ 공부하면서 하자

## sum의 초기화

## std::reverse

- \<algorithm> header include

`std::reverse(시작주소, 끝주소 + 1)`

- 아직 iterator의 개념을 공부하지 않았으나 주로 아래와 같이 사용

`std::reverse(vec.begin(), vec.end())`

- 여기서 배열의 인덱스로 접근하려면 (마지막 + 1)의 주소를 넣어야 됨

`std::reverse(&arr[0], &arr[last+1])`