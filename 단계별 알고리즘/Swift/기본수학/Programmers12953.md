# 12953 → N개의 최소공배수
### 문제 정리📝
1. 길이가 `1`이상 `15`이하의 배열 `arr`가 주어진다.
2. `arr`의 원소들의 `최소공배수`를 반환해준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 지문을 읽으면서 예전 백준에서 풀었던 `최대공약수와 최소공배수`문제가 생각이 났다. 당시 해당 문제를 풀 때 일반 구현의 시간복잡도는 `O(N)`이 걸리는걸 `유클리드 호제법`을 이용하면 `O(logN)`로 단축시키는 것을 알게 되었었다. 해당 문제도 `유클리드 호제법`을 이용해서 접근하면 쉽게 풀 수 있을 것이라고 생각했다.

- `최소공배수`를 구하기 위해선 `최대공약수`를 먼저 구해야하기에 각각을 구하는 `gcd(), lcm()` 함수를 만들어 구현하고, 본 함수(`solution`)에서 해당 함수를 이용해 풀면 될 것으로 보였다.

</br>

### 내 코드👨🏻‍💻
```swift
import Foundation

func gcd(_ x: Int, _ y: Int) -> Int {
    let temp = x % y
    return temp == 0 ? min(x, y) : gcd(y, temp)
}

func lcm(_ x: Int, _ y: Int) -> Int {
    return x * y / gcd(x, y)
}

func solution(_ arr:[Int]) -> Int {
    return arr.reduce(1) { lcm($0, $1) }
}
```

</br>

### Additional 📂
- 기존 `solution`에선 `for문`을 이용해 구현했으나 `reduce`를 이용해서 더 간단하게 구현할 수 있음을 알게 되었다. 고차함수를 더 경험할 수 있는 좋은 문제였다 👍