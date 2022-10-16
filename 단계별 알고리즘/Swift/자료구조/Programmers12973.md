# 12973 → 짝지어 제거하기
### 문제 정리📝
1. 문자열 `s`가 주어진다.
2. 문자열에서 같은 알파벳이 연속적으로 2개가 붙어 있는 짝을 찾아 그 둘을 제거하고, 앞뒤로 문자열을 이어 붙힌다.
3. 위의 과정을 반복했을 때 문자열이 성공적으로 다 지워진다면 `1`을 반환하고, 문자열이 남아있다면 `0`을 반환해준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 처음엔 막연하게 `while문`에서 `.first`와 `.removeFirst()`를 이용해 하면 될 것으로 보였으나 여러 번 반복하면서 앞뒤로 문자열을 이어 붙힌 문자열에서도 짝이 있다면 제거를 해줘야 하기 떄문에 많은 시간이 소요 될 것으로 판단이 되어 `for문`을 이용해서 `stack`을 구현하여 비어있을 경우 값을 넣어준 뒤, `stack.last`의 값과 `현재 인덱스 원소`가 같을 경우 `stack`을 다시 비워주는 형식으로 진행을 하여 짝이 없는 문자가 남아 있다면 `stack`은 비어있지 않으니 해당 조건을 통해 반환해주면 될 것으로 보였다. 

</br>

### 내 코드👨🏻‍💻
```swift
import Foundation 

func solution(_ s:String) -> Int{
    let s = Array(s)
    var stack = [Character]()
    let sCount = s.count

    for i in 0..<sCount {
        if s.isEmpty { stack.append(s[i]) }
        
        if stack.last == s[i] { stack.removeLast() }
        else { stack.append(s[i]) }
    }

    return stack.isEmpty ? 1 : 0
}
```

- 그 전 구현으로는 조건문을 아래와 같이 구현을 했었다.

```swift
if !s.isEmpty && stack.last == s[i] {
    stack.removeLast()
} else {
    stack.append(s[i])
}
```

- 위의 방법에서 나름 백트래킹과 비슷한 느낌으로 비어있을 경우는 `stack`을 채워야하므로 굳이 다음 조건까지 확인하지 않도록 구현하여 시간을 조금 더 줄일 수 있었다.

</br></br>

### 시간 코드👨🏻‍💻
```swift
import Foundation

func solution(_ s:String) -> Int{
    let s = Array(s)
    var stack = [Character]()

    for (_, value) in s.enumerated() {
        if s.isEmpty { stack.append(value) }

        if stack.last == value { stack.removeLast() }
        else {stack.append(value) }
    }

    return stack.isEmpty ? 1 : 0
}
```
- 시간초과가 난 이유는 `.enumerated()`를 이용해도 해당 `배열의 크기`를 계속해서 계산을 해서 넣어주기 때문에 시간초과가 난 것으로 보인다.

</br></br>


### Additional 📂
- 나름 시간을 줄이기 위해 노력을 했었던 것 같다. 여러 번 생각을 해보다가 결국은 `.count`의 문제인가 싶어서 시도를 했는데 `.count` 문제가 맞았다.. 다른 분들의 코드를 봐도 나와 같이 `.count`를 이용해 미리 변수로 빼두셨다. 내 풀이가 나름 올바른 풀이?와 비슷해서 뿌듯했다 😏
