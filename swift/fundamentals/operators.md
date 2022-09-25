# operators

대괄호, 제곱, 곱셈 or 나눗셈, 플러스 or 마이너스 우선순로 계산한다. 주의할점은 컴퓨터가 같은 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산하게 된다. C 및 Objective-C의 산술 연산자와 달리 Swift 산술 연산자는 기본적으로 값이 오버플로되는 것을 허용하지않는다. 필요에 따라 ampersand(&)로 시작하는 연산 사용해야한다.(&+)

* Assignment operator (=)
* Equal to operator (==)
* Arithmetic operators (+, -, \*, /, %)
* Range operators(…, ..<)

```swift
// string 연결 가능
"hello, " + "world"

// Ternary Conditional Operator
n == 0 ? "none" : "something"

// One-Sided Ranges
// index 2이하 전부
for name in names[...2] {
    print(name)
}

// 1~5까지 랜덤 숫
Int.random(in:1...5)
```

