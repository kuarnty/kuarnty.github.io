---
layout: article
title: Vector
description:
category: Computer Science - Data Structure - Vector
---

# Vector(벡터)

## 개념

**벡터(Vector)**는 **동적(dynamic) 배열** 자료구조입니다.

먼저 [배열(array)](/pages/computer-science/data-structure/array.html)에 대한 이해가 필요합니다.

벡터는 **내부 배열에 요소들을 저장**하며, 이 **배열의 크기**는 내부 변수 **capacity** 값에 해당합니다. 실제 쓰이는 공간, 즉 **요소의 개수**는 내부 변수 **size** 값에 해당합니다. 요소의 추가 및 삭제 시 필요에 따라 **동적**으로 **적절한 크기의 배열을 새로 할당**하고 기존 값을 복사하여 저장합니다.

요소에 접근할 때에는 배열과 마찬가지로 **인덱스(Index)를 사용**하여 빠르게 접근할 수 있습니다.

**벡터의 용량, 크기**, 그리고 **요소**라 함은 일반적으로 벡터 **내부 배열의 용량**과 **내부 size 값**, **내부 배열의 요소**를 의미합니다.

## 동적 크기 조절

벡터 사용자에게 **추가(push_back)** 및 **삭제(pop_back, erase)** 기능을 제공합니다. 추가 및 삭제 시 **size 값을 변경**하며, 이때 size가 **capacity를 초과**하거나 **너무 작아지면** 배열의 크기를 동적으로 **resize** 합니다.

- **추가(push_back)**: 요소를 배열의 **마지막 요소 다음**(index: size)에 추가합니다. 이때 만약 **size와 capacity 값이 같으면**, **더 큰 capacity 값(보통 2배)으로 resize**하고 나서 요소를 추가하고 size를 1 증가시킵니다.

- **삭제(pop_back/erase)**: **size를 1 감소**시켜 **마지막 요소가 삭제된 것으로 간주**합니다. 필요에 따라 capacity에 비해 size가 너무 작아지면(보통 1/4) 더 작은 capacity 값(보통 1/2)으로 resize할 수 있습니다.

- **resize**: **새 capacity 값을 매개변수로** 받아 해당 크기의 **새 배열을 동적으로 할당**받습니다. **기존 배열**의 요소들(size 개)을 새 배열로 **복사**한 후, **내부 배열 변수를 새 배열로** 변경하고, **기존 배열은 해제**(delete/free)합니다. 내부 capacity 변수 값을 새 capacity 값으로 변경합니다.
    - 단, resize만 수행했을 떈 size 값은 변경되지 않습니다.
    - 크기를 줄일 때 size가 새 capacity보다 클 수 있으며(즉, 일부 요소가 잘림), 상황에 따라 잘리는 요소들에 상관 없이 resize할 수도 있고, 잘리는 요소들이 없도록 capacity를 조절할 수도 있습니다.

## 주요 연산

일반적으로 벡터 자료구조가 제공하는 주요 연산들은 다음과 같습니다:

- `push_back(value)`: 벡터의 마지막에 `value`를 추가합니다.
- `pop_back()`: 벡터의 마지막 요소를 제거합니다.
- `resize(new_capacity)`: 벡터의 capacity를 `new_capacity`로 변경합니다. 일반적으로 내부적으로만 접근 가능한 private 메서드입니다.

<details markdown=1>
<summary>추가로 특정 위치에 접근하거나 조작, 상태 확인 등의 연산들을 구현하여 사용할 수 있습니다</summary>

> - `size()`: 내부 배열에 저장된 요소의 개수를 반환합니다.
> - `capacity()`: 내부 배열의 할당된 길이를 반환합니다.
> - `is_empty()`: 벡터가 비어있는지 여부를 반환합니다.

> - `at(index)`: `index` 위치의 요소를 반환합니다.
> - `front()`: 벡터의 첫 번째 요소를 반환합니다.
> - `back()`: 벡터의 마지막 요소를 반환합니다.

> - `insert(index, value)`: `index` 위치에 `value`를 삽입합니다. resize가 필요할 수 있습니다.
> - `erase(index)`: `index` 위치의 요소를 제거합니다. resize가 이뤄질 수 있습니다.
> - `clear()`: 벡터의 모든 요소를 제거하고 size를 0으로 설정합니다.

> - `reserve(new_capacity)`: 내부 배열의 크기를 `new_capacity` 이상으로 할당합니다. 미리 일정 수준으로 capacity를 확보하고자 할 때 사용할 수 있으며, 이미 충분한 capacity가 있으면 아무 동작도 하지 않습니다.
> - `shrink_to_fit()`: 현재 size에 맞게 capacity를 줄입니다.

</details>

## 예시

다음은 C++의 `std::vector`를 사용한 예시입니다:

```cpp
#include <vector>

std::vector<int> vec;

vec.push_back(10);                  // 값 10 추가
vec.push_back(20);                  // 값 20 추가
vec.push_back(30);                  // 값 30 추가

int first = vec[0];                 // 첫 번째 요소: 10

vec[1] = 25;                        // 두 번째 요소 값 변경 (20 -> 25)
int second = vec[1];                // (변경된)두 번째 요소: 25

int last = vec[vec.size() - 1];     // vec.size() == 3, 마지막 요소: 30

vec.pop_back();                     // 마지막 요소 삭제 (30 삭제)
```

**배열(arrary)와 비슷**하게 선언 및 접근할 수 있습니다. 그러나 배열과 달리 **선언 시 크기를 지정하지 않아도** 요소를 추가할 때 자동으로 크기가 조절됩니다.

`push_back`, `pop_back` 등의 메서드로 요소를 추가 및 삭제할 수 있습니다. 벡터의 사용자는 이 과정에서 **내부 배열의 용량을 신경 쓸 필요가 없습니다**. 추가 및 삭제 과정에서 내부에서 자동으로 동적 크기 조절이 이뤄집니다.

## 참고

[GitHub - 벡터 구현 예시(cpp) - cpp의 std::vector를 사용하지 않고 벡터 자료구조를 직접 구현한 예시](https://github.com/kuarnty/implement-CS/blob/main/data-structure/Vector.cpp) 

벡터는 배열의 장점(빠른 인덱스 접근)을 유지하면서, **동적 크기 조절**을 통해 **유연한 요소 관리**가 가능해 다양한 상황에서 널리 사용됩니다. 대부분의 현대 프로그래밍 언어에서 벡터 또는 유사한 동적 배열 자료구조를 제공합니다.

단, 벡터의 동적 크기 조절이나 여러 요소 관리 기능들이 필요 없는 경우, 단순 배열을 사용하는 것이 성능 면에서 더 유리할 수 있습니다.