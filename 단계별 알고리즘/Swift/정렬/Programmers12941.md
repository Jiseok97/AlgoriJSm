# 12941 → 최솟값 만들기
### 문제 정리📝
1. 길이가 같은 배열 `A`, `B`가 주어진다.
2. 해당 배열들의 원소를 `한 개`씩 뽑아 두 수를 곱한다.
3. 위의 과정을 반복할 때 만들 수 있는 `최솟값`읇 반환해준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 두 배열을 곱하는데 `최솟값`을 만들기 위해선 곱하기의 특성으로 `작은 값 * 큰 값`으로 되어야하기에 `A`는 `오름차순`으로, `B`는 `내림차순`으로 정렬을 해준 뒤 `for문`을 통해서 값을 누적시켜 반환해주면 된다고 생각했다.

</br>

### 개선 전 코드👨🏻‍💻
```swift
import Foundation

func solution(_ A:[Int], _ B:[Int]) -> Int
{
    let a = A.sorted(by: <)
    let b = B.sorted(by: >)
    var ans: Int = 0
    
    for i in 0..<a.count {
        ans += a[i] * b[i]
    }
    
    return ans
}
```
</br></br>

### 개선 후 코드👨🏻‍💻
```swift
import Foundation

func solution(_ A:[Int], _ B:[Int]) -> Int
{
    let a = A.sorted(by: <)
    let b = B.sorted(by: >)
    var ans: Int = 0
    
    for (index, value) in a.enumerated() {
        ans += value * b[index]
    }
    
    return ans
}
```
</br></br>

### Additional 📂
- `enumerated`는 `Apple Developer`에서 보면 복잡도가 `O(1)`이라고 기재가 되어있다. 이번 문제는 쉬운 문제로 조금 더 효율적인 구현을 해보기 위해 여러 방법들을 찾아보았던 것 같다. 나름 여러 방법을 찾던 중 공식문서에서 PS에 가져다 쓰라고 만든(?) 기능으로 보여 실험을 한 결과 일반 `For문`은 평균 `5ms`초반으로 나왔고, `Enumerated`의 경우는 평균 `4ms 중후반`으로 나왔다. 

- 이번 문제와 같은 상황이 생긴다면 `.enumerated()`를 고려해볼만 한 것 같다. 나름 효율성을 고민하게 해준 고마운 문제이지만 너무 쉬운 문제여서 정리를 할까 말까 고민했었다..😅