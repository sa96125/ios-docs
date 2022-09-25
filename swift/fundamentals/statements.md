# statements

### Loop

일련의 작업을 순서대로 수행한다.

```swift
let fruitBasket = ["Apple", "Orange", "Pear"]
let fruitBasket2: Set = ["Apple", "Orange", "Pear"]
let contacts = ["Adam": 12345678, "James": 9876512]
let titleText = "Flash"
let closeRange = 1...5

// 배열, 문자열 각 구성 요소 순서대로 순회
for latter in titleText {
}

// 효율적인 방식으로 순회(순서 보장 X)
for fruit in fruitBasket2 {
}

// 효율적인 방식으로 순회(순서 보장 X)
for person in contacts {
	print(person.key)
	print(person.value)
}

// use range operator
for number in 1...5 {
}

// 5번 순회
for _ in closeRange {
}

// isTrue가 false가 될때까지 무한 반복
// 사용시 주의가 필요하고 종료할 수 있는 원포인트를 꼭 지정해야한다.
// 얼마나 걸릴지 모르는 작업을 처리할 때 사용한다.
while isTrue {
}
```



### switch vs if

범위가 클수록 패턴 매칭이 if구문보다 효율적이고 읽기 쉬운 코드가 된다. swich를 사용할 때, 꼭 범위 외의 사항에 대한 처리가 필요하며 이는 default에서 처리한다. 또한 각각의 범위는 … / ..< 와 같은 범위 연산 키워드를 사용하여 설정할 수 있다.

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

조건이 충족되지 않는 경우 범위 밖으로 프로그램 제어를 전송하는 데 사용된다 .

```swift
// nil이면 else 실행,
guard condition != nil else {
    code
}

// optional binding
guard let safeCondition = condition else {
    code
}

```

