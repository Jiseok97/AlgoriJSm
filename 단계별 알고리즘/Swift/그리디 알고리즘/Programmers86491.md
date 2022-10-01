# 86491 → 최소직사각형
### 문제 정리📝
1. 명함 지갑이 있는데, 다양한 크기의 명합이 배열 `sizes`로 주어진다.
2. 해당 명합 모두를 지갑에 수납하려고 할 때, 지갑의 `최소 크기`를 반환해준다.
> 단, 명합을 가로로 눕혀 수납하는 경우도 있다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
* 지문에서 가로로 눕혀 수납하는 경우를 따져보았을 때, `가로 길이`와 `세로 길이` 각각의 `최대값`을 추출해 곱해주면 된다고 생각이 들었고, 두 가지의 구현을 생각해볼 수 있을 것 같다.
    * `for문`을 돌리면서 `.sorted`한 배열 하나를 더 만들어 `[0]`, `[1]`의 값을 이용해 구현해주는 경우
    * `for문`을 돌리면서 `.max()`, `.min()`을 이용해 구현해주는 경우

* 두 경우를 다 구현해서 시간이 더 짧게 나오는 구현은 어떤건지 비교해봐야겠다고 생각했다.

</br>

### 첫 번째 코드👨🏻‍💻
```swift
import Foundation

func solution(_ sizes:[[Int]]) -> Int {
    var max_Width = 0
    var max_Height = 0

    for size in sizes {
        let sort_Size = size.sorted(by: <)
        max_Width = max(max_Width, sort_Size[0])
        max_Height = max(max_Height, sort_Size[1])
    }
    
    return max_Width * max_Height
}
```

* 테스트 케이스 
    * 최소 시간: `0.09ms`
    * 최소 메모리: `16.1MB`

    * 최대 시간: `11.64ms`
    * 최대 메모리: `19.3MB`

</br></br>

### 두 번째 코드👨🏻‍💻
```swift
import Foundation

func solution(_ sizes:[[Int]]) -> Int {
    var max_Value = 0
    var min_Value = 0
    
    for size in sizes {
        guard let max_Size = size.max() else { return 0 }
        guard let min_Size = size.min() else { return 0 }
        max_Value = max(max_Value, max_Size)
        min_Value = max(min_Value, min_Size)
    }
    return max_Value * min_Value
}
```

* 테스트 케이스 
    * 최소 시간: `0.03ms`
    * 최소 메모리: `16.1MB`

    * 최대 시간: `12.12ms`
    * 최대 메모리: `18.8MB`

</br></br>

### Additional 📂
* 두 케이스를 비교했을 때 `두 번째 코드`는 짧은 경우는 엄청 짧게 나오지만 길 경우는 더 길게 나오는 것을 볼 수 있었는데, 메모리를 더 적게쓰는 대신 시간이 더 걸린 것 같다. 해당 이유로는 다음과 같을 것 같다.

    * `첫 번째 코드` 정렬시킨 배열 변수를 만들기 떄문에 메모리는 더 드는 부분이 있고, `두 번째 코드`는 단순한 정수형 변수지만 `.max()`와 `.min()`을 매 번 체크해야되는 부분에서 메모리보단 시간이 더 걸린것으로 보인다.

* 알고리즘 캠프를 하면서 `시간 복잡도`와 `공간 복잡도`는 반비례(trade-off 관계)한다고 했는데 이번 문제를 통해 직접 경험 할 수 있었다.