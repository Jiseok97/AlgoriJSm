# 68644 → 두 개 뽑아서 더하기
### 문제 정리📝
1. 정수 배열 `numbers`가 주어진다.
2. `numbers`에서 `서로 다른 인덱스`에 있는 `두 개`의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 `오름차순`으로 담아 반환준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 지문 중 `서로 다른 인덱스`라는 포인트에선 `중복된 값`이 존재할 수 있다는 가능성을 생각해 `Set`에 담아 반환해는게 좋다고 생각했다. 기존 일반 배열을 사용할 경우 `.contains`를 사용해서 코드의 길이를 더 늘릴 수 있다고 생각했고, `두 개`의 수이므로, `이중 for문`을 통해서 `현재 인덱스 값` + `다음 인덱스 값`으로 구현하면 될 것으로 보였다.

</br>


### 내 코드👨🏻‍💻
```swift
import Foundation

func solution(_ numbers:[Int]) -> [Int] {
    let numbers_count = numbers.count
    var result = Set<Int>()

    for i in 0..<numbers_count {
        let firstValue = numbers[i]
        for j in i+1..<numbers_count {
            result.update(with: firstValue + numbers[j])
        }
    }
    
    return result.sorted(by: <)
}
```

- 배열의 `.count`는 배열의 크기를 반환해주는 프로퍼티이지만, 해당 `.count`의 시간 복잡도는 `O(N)`이므로 여러 번 사용해야하는 경우에 변수로 만들어두는 것이 시간적으로 효율적이라고 생각했다.

</br>


### Additional 📂
- 심심해서 풀어보았던 문제였다. 짧은 시간이지만 나름 재미있었던 문제였다.
