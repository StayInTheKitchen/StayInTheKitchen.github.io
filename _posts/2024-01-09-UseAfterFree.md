---
layout : post
title : Use After Free
---

# Use After Free

## Dangling Pointer
> 할당되지 않은 공간을 가리키는 포인터

- 그 자체로는 문제가 없지만 예기치 못한 행동을 할 수 있음

## Use After Free
> 해제된 메모리에 접근할 때 발생하는 취약점

- 이전의 객체가 사용하던 데이터를 그대로 읽어 올 수 있음

- 원하는 값을 넣어 프로그램의 실행 흐름을 바꿀 수 있음

---

# Exploit : uaf_overwrite

