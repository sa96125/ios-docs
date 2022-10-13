---
description: Swift is a very strict language about data types.
---

# primary types and operators

타입 선언과 연산방법은 일반적인 다른 프로그래밍 언어와 사용법이 비슷합니다. 차이점은 스위프트 타입은 구조체로 이루어져 있습니다. 구조체의 특징 중 하나는 **value type으로 값을 복사 할때 깊은 복사가 되어 기존 값에 영향을 주지않습니다**.



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

숫자타입의 종류는 다른 타입과는 달리 세분화되어있습니다. 뒤의 숫자는 비트의 갯수를 지칭합니다. 변수 또는 상수에 담을 숫자가 크지않다면 작은 비트를 가지는 Int타입으로 선언하여 메모리를 절약할 수 있습니다.

* Int : 컴퓨터 운영체제의 아키텍쳐에 의
* Int8 : -128 \~ -127
* Int16 : -32768 \~ 32767
* Int32 : -2147483648 \~ 2147483647
* Int64 : -9223372036854775808 \~ 9223372036854775807





### Operators

할당연산자, 동등연산자, 산술연산자, 논리연산 그리고 범위 연산자가 있습니다. 범위 연산자는 배열, for 문, case 문에서 유연하게 사용할 수 있습니다.

* Assignment operator (=)
* Equal to operator (==)
* Logical operator(&&, ||)
* Arithmetic operators (+, -, \*, /, %)
* Range operators(…, ..<)
* Check operators( !=, >, <, >=, <=)

계산식에 다양한 연산을 포함하고 있을 경우에 대괄호, 제곱, 곱셈(나눗셈), 플러스(마이너스) 우선순으로로 계산합니다. 만약 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산합니다. C 및 Objective-C의 산술 연산자와 달리 Swift 산술 연산자는 기본적으로 타입이 수용할 수 있는 범위 외 값이 오버플로되는 것을 허용하지 않습니다. 필요 시 ampersand(&)를 연산앞에 붙여 사용합니다.

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

// min, max value
Int.min
Int.max

// random
Int.random(in:1...5)
Float.random(in:1..<5)
Bool.random()
Array.randomElement()
Array.suffle()

```

