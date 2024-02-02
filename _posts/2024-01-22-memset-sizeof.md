---
layout : post
title : memset과 sizeof
---

# memset
`void* memset(void* ptr, int val, size_t size)`

- ptr 주소에서 size만큼을 val로 초기화시키는 함수

### 주의 : arr의 모든 원소를 1로 초기화 하고 싶을 때

`memset(arr, 1, sizeof(arr))`

- 위처럼 사용하면 원치않는 값이 나옴

- memset은 val이 **unsigned char**로써 **byte 단위**로 초기화 됨

- 특별한 목적이 없다면 0으로 초기화 할 때 사용

# sizeof
> **컴파일 타임** 연산자로 피연산자의 크기를 연산

## 배열의 크기
`sizeof(arr)` 를 사용하면 배열의 크기를 연산함

### 깨달음
- 기존에는 arr는 배열의 시작주소로 변환이 되는데, 주소값의 크기를 연산해야 된다고 생각했다 (4 or 8 bytes)

- 그러나, 만약 `int arr[5];` 라면 arr의 type은 `int [5]` 이다.

- sizeof 연산자는 피연산자의 타입에 따른 크기를 연산하므로 컴파일러가 `int [5]` 라는 타입의 크기를 연산해서 arr의 바이트 사이즈를 알 수 있게 된다

# fill
> 연속된 자료형의 시작~끝 범위까지를 원하는 값, 객체로 초기화 하는 함수

- \<algorithm> 헤더

`void fill(FowardIterator first, FowardIterator last, const T& val)`

- first iterator부터 last전까지 val로 채움

`fill(arr, arr+21, 0);` 은 arr의 시작부터 21개를 0으로 채움

- 이 함수는 memset과 달리 바이트 단위로 초기화 하지않음

- 아마 이 함수는 내부적으로 fowarditerator의 사이즈를 계산해서 val에서 해당 fowarditerator의 사이즈만큼을 복사하는 듯 함

```
char arr[5];
int a = 0xcafebabe;

fill(arr, arr+5, a);
```
위 코드를 실행해보니

arr[0,1,2,3,4] = 0xbe; 로 초기화 되어있었다

# type casting과 rax

## implicit, explicit type casting

- 둘 다 **cvt2si2sd**와 같은 명령어로 형 변환


- 여기서 xmm 레지스터를 사용함
    - xmm은 SIMD 명령어를 쓸 때 사용하는 레지스터
    
    - xmm은 16바이트 레지스터

- SIMD : Same Instruction Multiple Data
    - 하나의 연산으로 여러 데이터를 연산 가능하다???

### rax

- rax는 함수의 반환값을 저장하는 역할

- 함수 호출 전 vector 값을 몇개 전달하는지를 저장하는 용도로 사용

- vector registor도 위의 SIMD와 관련이 있는 듯 보임

- 해당 링크로 SIMD와 관련된 정보 공부

https://m.blog.naver.com/fs0608/221650925743

# range based for

# 올림/내림 알고리즘

- `3 / 2`를 하면 1.5가 아니라 1이 결과가 나옴

- 정수의 **/** 연산에서는 소숫점을 버리는 내림 연산을 함

- 따라서 올림 연산을 하고 싶으면 `(3 + 1) / 2`를 하면 됨