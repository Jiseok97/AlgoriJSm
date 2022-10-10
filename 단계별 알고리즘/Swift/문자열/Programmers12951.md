# 12951 → JadenCase 문자열 만들기
### 문제 정리📝
1. `JadenCase`는 모든 단어의 첫 문자가 `대문자`이고, 그 외의 알파벳은 `소문자`인 문자열이다.
2. 문자열 `s`가 주어졌을 때 `JadenCase`로 바꾼 문자열을 반환해준다.
> 단 공백문자가 연속해서 나올 수 있습니다.

</br>

## 접근🚶🏻
### 나의 생각 ▾
- 지문을 읽었을 때 가장 간단한 방법으로 문자열을 `공백` 기준으로 `[String]`형 배열을 만들어서 넣어준 뒤, 해당 배열을 `for문`으로 돌리고, 그 안에서 `lowercased()`를 통해서 모든 문자를 소문자로 바꿔준 뒤, 가장 처음만 대문자로 바꿔주면 된다고 생각했다.

</br>

### 내 코드👨🏻‍💻
```swift
import Foundation

func solution(_ s:String) -> String {
    let s = s.components(separatedBy: " ").map{ String($0) }
    var result = [String]()
    
    for word in s {
        var UpperString: String = ""
        let temp = word.map{ String($0).lowercased() }
        
        for i in 0..<temp.count {
            UpperString += i == 0 ? temp[i].uppercased() : temp[i]
        }
        result.append(UpperString)
    }
    
    return result.joined(separator: " ")
}
```

* `split`이 아닌 `components`를 사용한 이유는 `연속적인 공백문자`케이스 때문이다.
    * `split`은 `separator`를 이용하는데 해당 `separator`은 연속적인 공백도 `하나의 공백`으로 처리해버리기 때문에 연속적인 공백문자가 나와도 하나의 공백만 보이게 된다. 아래의 예시를 보면 더 쉽게 이해할 수 있을 것 같다.

```swift
let s = "hello  my name  is jiseok"
let str = s.split(separator: " ").map{ String($0) }
// hello my name is jiseok

let s = "hello  my name  is jiseok"
let str = s.components(separatedBy: " ").map{ String($0) }
// hello  my name  is jiseok
```

</br>

### Additional 📂
- 레벨2 문제치고는 너무 쉬운 문제라고 생각했는데, 연속적인 공백 처리를 어떻게 할 것인지가 가장 큰 관건이었던 것 같다. 다행히 `components`를 알고 있어서 쉽게 구현할 수 있었다. 다른 사람들 풀이에선 아스키 코드를 이용해서 푸는 경우나 첫번쨰 문자인지 플래그 변수를 세워 구현하는데 나름 간결하게 구현은 했으나 아스키 코드로 구현하는 경우 시간복잡도에서 더 좋은 결과를 보여주고 있다. 

- 시간을 더 아껴야되는 문제에선 아스키 코드로 접근해 구현하는것도 하나의 방법이 될 수 있을 것 같다.