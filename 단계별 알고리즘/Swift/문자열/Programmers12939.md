# 12939 → 최댓값과 최솟값
### 문제 정리📝
1. 숫자들이 저장된 문자열 `s`가 주어지며, 해당 숫자들은 `공백`으로 구분되어있다.
2. `s`에 있는 숫자들 중 `최솟값`과 `최댓값`을 찾아 해당 순으로 반환해주면 된다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 크게 어려운 문제가 아니었기에 Int형 `배열`을 만들어 `s`를 `split`과 `map`을 통해 `Int`형으로 매핑해준 뒤, 해당 `배열`을 오름차순으로 정렬하여 `.first`와 `.last`를 반환해주면 된다고 생각했다.

</br>

### 내 코드👨🏻‍💻
```swift
func solution(_ s:String) -> String {
    let numLst = s.split(separator: " ").map { Int($0)! }.sorted(by: < )
    var answer = [String]()

    if let firstValue = numLst.first,
       let lastValue = numLst.last {
        answer.append(String(describing: firstValue))
        answer.append(String(describing: lastValue))
    }
    
    return answer.joined(separator: " ")
}
```

</br>

### Additional 📂
- 레벨 2로 골라서 풀었던 문제인데, 생각보다 너무 간단했다. 연습 문제라 그런가보다.
- 그래도 문제를 보자마자 어떻게 풀지 해결법을 찾은 내가 대견한다 😏