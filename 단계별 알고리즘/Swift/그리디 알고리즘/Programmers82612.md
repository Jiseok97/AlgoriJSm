# 82612 → 부족한 금액 계산하기
### 문제 정리📝
1. 지불해야 하는 금액 `price`과 몇 번 이용하는지 `count`와 현재 소지하고 있는 금액 `money`가 주어진다.
2. 지불해야하는 금액은 이용할 떄마다 배로 증가를 하는데 아래와 같이 증가한다고 하면, 현재 가지고 있는 금액보다 얼마가 부족한지 반환한다. 단, 금액이 부족하지 않으면 `0`을 반환해준다.
> 1번: 1배, 2번: 2배, 3번: 3배... etc

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 지문을 통해 `현재 가격`과 `몇 번 이용할지`에 대한 값을 미리 구해주는 함수를 만들고 해당 코드를 메인 구현부인 `solution` 함수에 넣어주면 될 것으로 보였다.

</br>

### 내 코드👨🏻‍💻
```swift
import Foundation

func fetchTotalPrice(_ price: Int, _ count: Int) -> Int {
    var ans: Int = 0
    for i in 1...count {
        ans += price * i
    }
    return ans
}

func solution(_ price:Int, _ money:Int, _ count:Int) -> Int64 {
    let payMoney = fetchTotalPrice(price, count)
    guard payMoney <= money else {
        return Int64(abs(money - payMoney))
    }
    return 0
}
```

</br></br>

### Additional 📂
- 이 문제는 나의 `reduce`를 공부하게 해주는 좋은 문제였다. `.reduce()` 고차 함수를 이용해 `fetchTotalPrice`의 기능을 대신해주려고 끝내 구현을 하지 못했다..

- 다른 사람들의 풀이를 보면 수학적인 접근 코드도 있지만 내가 찾던 고차함수를 이용한 더 간결한 구현은 보지 못했다.. 고차 함수가 그렇게 효율적인 코드는 아니라고 생각은 하지만 기존 `for문` 및 `while`문 등 반복문을 구현할 때 끝까지 루트를 돌아야하는 거라면 더 간결하게 구현하는 고차함수가 더 좋다고 생각은 한다.. 공휴일 겸 PS 성공 😅