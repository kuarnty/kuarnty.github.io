---
layout: article
title: Data Structures
description:
category: Computer Sciences - Data Structures
---

# Data Structures / 자료구조

## 개념

**자료구조**(**Data Structure**)는 **데이터**를 효율적으로 저장하고 관리하기 위한 **방법**과 **형식**을 의미합니다.

컴퓨터는 모든 정보를 **이진수** 형태로 다룹니다. 모든 이진수 정보는 실제 물리적으로 메모리(RAM)와 저장장치(HDD, SSD 등)에 0 또는 1의 값으로 저장됩니다.

모든 자료구조는 가장 낮은(작은) 수준에서 이러한 **이진수 값들의 집합**으로 구성됩니다. 이에 더해 어느 위치의 값이 어떤 **의미**를 가지는지 **약속**하는 것을 통해 데이터에 **구조를 부여**한 것이 자료구조라고 할 수 있습니다.

널리 알려진 **기본적인 자료구조들**이 있으며, 이들은 가장 단순한 형태이면서 일반적으로 효율적입니다. 기본적인 자료구조들을 수정하거나 조합하여 특정 상황이나 조건에 최적화된 자료구조를 새로 만들 수 있습니다.

따라서 기본적인 프로그래밍 방법과 더 복잡하고 발전된 방법을 이해하기 위해서는 **기본적인 자료구조들을 이해**하는 것이 중요합니다.

자료구조에서 데이터를 저장하고 다루는 방법은 일종의 알고리즘으로 볼 수 있으며, 따라서 그 **효율성**을 [**시간 복잡도(Time Complexity)와 공간 복잡도(Space Complexity)**]<!--(/pages/computer-sciences/algorithm-basics/algorithmic-complexity-&-big-o-notation)-->를 기준으로 평가할 수 있습니다.

---

아래의 글들에서 이러한 기본적인 자료구조들에 대해 다룹니다.

### [**Array**](/pages/computer-sciences/data-structures/array.html)

**가장 기본적인 자료구조**로, **동일한 타입**의 데이터들을 **연속**적으로 저장하는 구조입니다.

### [**Vector**](/pages/computer-sciences/data-structures/vector.html)

Array와 유사하지만, 필요에 따라 **크기가 동적으로 변할 수 있도록** 한 자료구조입니다.

### [**Linked List**](/pages/computer-sciences/data-structures/linked-list.html)

**각 데이터 요소**를 연속적으로 저장하지 않고 **개별적으로 저장**하는 대신, 각 요소가 **다음 요소의 위치를 가리키도록** 연결한 자료구조입니다.

Array와 비슷하게 선형적으로 데이터가 저장되지만, 새 데이터의 삽입과 삭제가 더 효율적이며, 순서를 통한 접근이 느릴 수 있습니다.

### [**Stack**](/pages/computer-sciences/data-structures/stack.html)

Array나 Vector, Linked List에 기반하여, **후입선출**(**LIFO**, Last In First Out**) 방식으로만 요소를 추가/삭제할 수 있도록 합니다.

### [**Queue**](/pages/computer-sciences/data-structures/queue.html)

Stack과 유사하지만 **선입선출**(**FIFO**, First In First Out**) 방식으로만 요소를 추가/삭제할 수 있도록 합니다.

### [**Hash Table**](/pages/computer-sciences/data-structures/hash-table.html)

기본적으로 Array에 기반하지만, Array가 단순히 인덱스(위치)를 통해 요소에 접근하는 것과 달리, **키(key)**를 **해시 함수에 통과**시켜 생성된 **해시값을 인덱스로 값(value)에 접근**합니다.
