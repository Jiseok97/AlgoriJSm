# 118667 → 두 큐 합 같게 만들기
### 문제 정리📝
1. 정수가 담겨 있는 `queue1, queue2`가 주어진다.
2. 두 개의 큐를 이용해 작업을 할 수 있는데 작업은 하나의 큐를 골라 원소를 `추출(pop)`하고, 추출된 원소를 다른 큐에 `삽입(insert)` 해준다.
3. 위에 행위가 작업 `1회`로 수행한걸로 간주가 된다.
4. 두 개의 큐의 원소의 `총 합의 절반 되는 값`이 각 큐의 원소의 `총 합`이 되게 하려고 할 때, 최소 몇 번의 작업을 수행해야 하는지 `횟수`를 반환해준다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 각 큐를 `.reduce(0, +)`를 통해 `큰 큐`와 `작은 큐`로 나눈 뒤, `큰 큐`에 있는 원소를 `작은 큐`에 넣어주려고 했으나 해당 문제는 `정확성`이 포함된 문제로 일일이 작업하는 것으로 풀면 안되겠다고 생각했다.

- 목표는 `하나의 큐는 두 개의 큐의 원소들의 총 합의 절반값`만 들어가면 만족이 되는 문제였길래 `원소들의 합`을 이용하며, `투 포인터` 알고리즘으로 접근하면 될 것 같았다. 정확성을 요구하는 문제일수록 그에 걸맞는 알고리즘은 따로 있을 것으로 판단되었기 때문이다. 

</br>


### 내 코드👨🏻‍💻
```swift
import Foundation

func solution(_ queue1:[Int], _ queue2:[Int]) -> Int {
    let twoQueue: [Int] = queue1 + queue2
    var leftIndex: Int = 0, rightIndex: Int = queue1.count
    var count: Int = 0

    var queue1_sum: Int = queue1.reduce(0, +)
    let queue2_sum: Int = queue2.reduce(0, +)

    guard (queue1_sum + queue2_sum) % 2 == 0 else { return -1 }

    let target: Int = (queue1_sum + queue2_sum) / 2

    while rightIndex < twoQueue.count && leftIndex <= rightIndex {
        guard queue1_sum != target else { return count }
        
        if queue1_sum < target {
            queue1_sum += twoQueue[rightIndex]
            rightIndex += 1
        }
        else if queue1_sum > target {
            queue1_sum -= twoQueue[leftIndex]
            leftIndex += 1
        }
        count += 1
    }
    return queue1_sum == target ? count : -1
}
```

- `guard queue1_sum != target else { return count }`를 통해 불필요한 연산을 더 시키지 않고 바로 반환할 수 있도록 구현했다.

- while문의 조건 중 `and` 연산자로 접근하기에 우리가 조건이 충족이 안되고도 `leftIndex <= rightInext` 조건에서 `break`될 수 있기 때문에 마지막 반환문은 삼항 연산자를 넣어주었다.

</br>


### Additional 📂
- 이번 문제를 통해 더 효율적인 구현을 하기 위해 많은 노력을 했던 것 같다. `guard`문을 통해 뒤에 구현부로 가기 전에 `return`을 시키는 문을 많이 넣어준 것 같다.

- 아직은 많이 부족하다는 것을 느낀다. 하지만 알고리즘 공부가 요새는 흥미롭게 다가오고 있기에 시간날 때 꾸준히 풀어보려고 한다. 화이팅 🌝