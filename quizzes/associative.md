# Associative Containers
## 1. Outline
`TreeMap` vs. `HashMap`

Language | TreeMap    | HashMap
---------|------------|---------
Java     | `TreeMap`  | `HashMap` 
C++      | `std::map` | `std::unordered_map`
C#       | `SortedDicationary` | `Dictionary`




## 2. 기초 문제
### 2.1. 개념
`TreeMap` vs. `HashMap`, 이 둘의 공통점과 차이점에 대하여 논하라

### 2.2. 사용법
`TreeMap` 과 `HashMap` 은 어떻게 사용하는가? 

### 2.3. 용도
이들은 주로 어떤 때에 사용하면 좋은가?




## 3. 심화 문제
`TreeMap` 과 `HashMap` 은 어떻게 구현하는가?

### 3.1. 개별 탐색
`TreeMap` 은 개별 탐색 복잡도가 *O (log<sub>2</sub>N)* 이며, `HashMap` 은 개별 탐색 복잡도가 최소 *O (1)* 에서 최대 *O (N)* 까지에 이른다. 이들의 개별 탐색 복잡도가 이러한 이유는 무엇인가? 아는대로 최대한 자세히 설명할 것, 그리고 그것의 구현 방법이나 원리에 대해 설명할 수 있으면 더 좋다.

### 3.2. 전체 순회
`TreeMap` 과 `HashMap` 이 내부 원소에 대한 개별 탐색 뿐 아니라, 마치 배열이나 리스트마냥, `for` 문을 통한 양방향 전체 순회까지 가능하다. 이 것이 가능한 이유는 무엇인가?

```cpp
#include <iostream>
#include <string>
#include <map>

int main()
{
    std::map<std::string, int> m;
    m.emplace("First", 1);
    m.emplace("Second", 2);
    m.emplace("Third", 3);

    for (auto it : m)
        std::cout << it->first << ", " << it->second << std::endl;

    for (auto it = m.rbegin(); it != m.rend(); ++it)
        std::cout << it->first << ", " << it->second << std::endl;

    return 0;
}
```
> ```bash
> First 1
> Second 2
> Third 3
> Third 3
> Second 2
> First 1
> ```

### 3.3 퍼포먼스
어떨 때 `Array` (또는 `Vector`) 를 쓰면 좋은지, 그리고 어떨 때에 `TreeMap` 이나 `HashMap` 을 쓰면 좋은지, 최적화의 관점에서 이야기해보자. 또한, `TreeMap` 이나 `HashMap` 을 사용함에 있어, 최종 입력하게 될 원소의 수를 미리 알 수 있으며, 이후 컨테이너에 원소 입출력 빈도가 낮은 경우 (아예 없는 건 아님), 어떤 식으로 최적화를 하면 좋겠는가?