# control flow, statements

### Loop

Swift에서는 for, while, repeat-while 문을 통해 일련의 작업을 순서대로 수행할 수 있습니다.



```swift

// 문자열 순서대로 순
let titleText = "Flash"
for latter in titleText {
    print(latter)
}


// 배열 각 구성 요소 순서대로 순회
let fruitBasket = ["Apple", "Orange", "Pear"]
for fruit in fruitBasket {
    print(latter)
}


// 효율적인 방식으로 순회(순서 보장 X)
let fruitBasket2: Set = ["Apple", "Orange", "Pear"]
for fruit in fruitBasket2 {
    print(fruit)
}


// 효율적인 방식으로 순회(순서 보장 X)
let contacts = ["Adam": 12345678, "James": 9876512]
for person in contacts {
    print(person.key)
    print(person.value)
}


// 범위 연산자 사
let closeRange = 1...5
for number in closeRange {
    // code
}


// 5번 순회
for _ in closeRange {
    // code
}


// isTrue가 false가 될때까지 무한 반복
// 사용시 주의가 필요하고 종료할 수 있는 원포인트를 꼭 지정해야한다.
// 얼마나 걸릴지 모르는 작업을 처리할 때 사용한다.
while isTrue {
    // code
}


// while문은 조건을 확인한 후, 코드를 실행하지만
// repeat while은 코드 실행 후 조건을 확인
var i = 7
repeat {
    i += 1
} while i < 7
```





### switch vs if

if 문에서 지정할 범위가 많을 수록 코드가 복잡해지는데, switch를 사용하면 효율적이고 읽기 쉬운 코드를 작성할 수 있습니다. switch 문 사용시 범위외의 사항에 대한 처리가 필요하며 이는 default에서 처리합니다. 또한 각각의 숫자의 범위는  to 대신 … / ..< 와 같은 범위 연산자를 사용할 수 있습니다.



```swift
 // if로 이렇게 선언하면 따귀 맞는다.
 var conditionName: String {
        switch conditionId {
        case 200...232:
            return "cloud.bolt"
        case 300...321:
            return "cloud.drizzle"
        case 500...531:
            return "cloud.rain"
        case 600...622:
            return "cloud.snow"
        case 700...781:
            return "cloud.fog"
        case 800:
            return "sun.max"
        case 800...804:
            return "cloud.bolt"
        default:
            return "cloud"
        }
}
```





### Guard

조건이 충족되지 않는 경우 다음 코드를 실행하지 않습니다. 프로그램 초입부에서 예외 처리를 먼저 진행하기 때문에 if를 사용한 optional binding보다 가독성이 좋아질 수 있습니다.



```swift
// nil이면 else 실행,
guard condition != nil else { fatalError() or return }


// optional binding
guard let safeCondition = condition else { fatalError("Error occured") }

```

