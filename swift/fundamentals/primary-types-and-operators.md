---
description: Swift is a very strict language about data types.
---

# primary types and operators

스위프트의 기본 타입은 구조체로 이루어져 있습니다. 즉, value type으로 복사된 값을 변경하더라도 원본 값에 영향을 주지 않습니다. 이를 깊은 복사가 되었다고 표현합니다.



* NsObject : only NS type
* AnyObject : only Class
* Any : All
* Bool : True or False
* Int : 64bit 정수
* Uint : 64bit 양의 정수
* Float : 32bit 부동 소수점
* Double : 64bit 부동 소수점
* Character : 유니코드
* String : 여러 문자를 담고 있는 문자





### Int, Int8, Int16, Int32, Int64

숫자 타입은 세분화되어있습니다. 뒤에 붙은 숫자는 비트의 갯수를 지칭합니다. 변수 또는 상수에 담을 숫자가 큰 수가 아니면 작은 비트를 가지는 Int 타입으로 선언하여 메모리를 절약할 수 있습니다.

* Int : 컴퓨터 운영체제의 아키텍쳐에 의존
* Int8 : -128 \~ -127
* Int16 : -32768 \~ 32767
* Int32 : -2147483648 \~ 2147483647
* Int64 : -9223372036854775808 \~ 9223372036854775807





### Operators

할당연산자, 동등연산자, 산술연산자, 논리연산 그리고 범위 연산자가 있습니다. 범위 연산자는 스위프트에서 값의 범위를 지정할 수 있는 특별한 연산자로 배열, for 문, case 문에서 유연하게 사용할 수 있습니다.



* Arithmetic operators (+, -, \*, /, %)
* Assignment operator (=)
* Compound Assignment Operators (+=, -=, \*=)
* Comparison operator (==, !=, >, <, >=, <=)
* Logical operator(&&, ||, !)
* Range operators(…, ..<)



다양한 연산을 포함하고 있을 경우에 대괄호, 제곱, 곱셈(나눗셈), 플러스(마이너스) 우선순으로 계산합니다. 만약 동일한 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산합니다. C 및 Objective-C의 산술 연산자와 달리 Swift 산술 연산자는 기본적으로 타입이 수용할 수 있는 범위 외 값이 오버플로되는 것을 허용하지 않습니다. 필요 시 ampersand(&)를 연산앞에 붙여 사용합니다.



```swift
// 문자열 연결
"hello, " + "world"


// 삼항 연산자(Ternary Conditional Operator)
n == 0 ? "none" : "something"


// index 2 이하를 순환하는 코드(One-Sided Ranges)
for name in names[...2] {
    print(name)
}


// 최대 / 최소
Int.min
Int.max


// 랜덤 메서드 활
Int.random(in:1...5)
Float.random(in:1..<5)
Bool.random()
Array.randomElement()
Array.suffle()


// 범위 연산자 메서드 활용
let range = ...5
range.contains(7)

```

