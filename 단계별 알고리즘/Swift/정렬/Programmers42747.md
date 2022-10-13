# 42747 → H-Index
### 문제 정리📝
1. `H-Index`는 발표한 논문 `n`편 중, `h`번 이상 인용된 논문이 `h`편 이상이고, 나머지 논문이 `h`번 이하 이용되었을 때 `h`의 최대값이다.
2. `인용된 논문의 횟수`를 담은 `citations`라는 `[Int]`형 배열이 주어졌을 때, `H-Index`를 반환해준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 지문을 이해하는 것이 제일 문제였지만 나름 이해를 해보았다. 결론적으론 `h`는 `citations`의 크기부터 `1`씩 감소하면서 `h`의 값 이상인 원소들이 `h`개 이상인지에 포커싱을 두면 되는 것 같았다. 해당 문제는 `.filter`라는 고차함수를 이용해 필터링을 해준 뒤에 해당 개수가 `h`이상인지 체크를 해주어 큰 순서부터 감소했기 때문에 바로 반환을 해주면 될 것으로 보였다.

</br>

### 내 코드👨🏻‍💻
```swift
import Foundation

func solution(_ citations:[Int]) -> Int {
    var h: Int = citations.count
    while h > 0 {
        let passCitation = citations.filter { h <= $0 }.count
        guard passCitation < h else { return h }
        h -= 1
    }
    return 0
}
```
</br></br>

### 잘못 이해한 코드👨🏻‍💻
```swift
import Foundation

func solution(_ citations:[Int]) -> Int {
    var h: Int = citations.count
    while h > 0 {
        let passCitation = citations.filter { h <= $0 }.count
        let remainingCitation = citations.filter { h >= $0 }.count
        if passCitation >= h && remainingCitation >= h {
            return h
        }
        h -= 1
    }
    return 0
}
```

- "`h`번 이상 인용된 논문이 `h`편 이상이고, 나머지 논문이 `h`번 이하 인용되었다면" 이라는 말에 `remainingCitation`이라는 변수를 만들어 이하인 개수를 같이 카운팅하여 조건문에 넣어줬었다..

</br></br>

### Additional 📂
- 알고리즘을 늘 풀면서 느끼는 한 가지는 아무리 구현력이 뛰어나도 지문을 제대로 이해하지 못하면 구현할 수가 없다는 것이다. 실력을 늘리려고만 노력했었는데 지문이 어떤 것을 요구하는지 정확히 파악하는 연습도 해야겠다는 생각이 들었다. 답은 독서를 많이 하는것이라고 판단이 나왔다..😂

- 약간의 시행착오가 있었지만 나름 재밌는 문제였다 👍