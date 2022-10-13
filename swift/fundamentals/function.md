# function

특정 기능을 수행하는 코드의 묶음입니다. 코드를 식별할 수 있는 이름과 입력값(parameters), 출력값(return)의 타입과 함께 정의합니다. 함수의 이름을 작성할 때 작성한 코드의 역할이 잘 드러나도록 작성하는 것이 중요합니다. 그 이유는 내부를 보지 않고도 그 내용을 파악하게 되면 코드 전체를 이해하기 쉽고 시간을 절약할 수 있어 생산성 또는 함수의 재사용성을 높일 수 있습니다.



```swift
// Input과 output이 없을 경우,
func sayHelloWorld() -> String {
    return "hello, world"
}

// Input만 있는 경우
func greet(person: String) {
    print("Hello, \\(person)!")
}

// Output만 있을 경우
func sayHelloWorld() -> String {
    return "hello, world"
}

// default input value
func greet(person: String = "Jake") {
    print("Hello, \\(person)!")
}
```





### Scope

함수의 { 중괄호 } 로 감싸져있는 영역을 말합니다. 서로 다른 scope에서 선언된 변수, 함수는 독립적으로 다른 곳에서 접할 수 없습니다.





### External Parameter Name & \_

함수를 호출할 때 사용할 파라미터 이름을 재정의하거나 생략할 수 있습니다.



```swift
// func performRequest(urlString: String)
// performRequest(urlString: urlString)
// more readable
func performRequest(with urlString: String) { ... }
performRequest(with: "https://")

func performRequest(_ urlString: String) { ... }
performRequest("https://")
```





### Error Handling

프로그램 실행 중에 발생할 수 있는 오류 조건을 함수 내에 작성함으로서 호출한 곳에서 정확하게 오류를 응답할 수 있게 됩니다. 작성된 에러에 대한 핸들링이 필요하다면 try catch 구문을 사용합니다.



```swift
// 오류가능성이 있는 함수는 throws 키워드를 입력
func canThrowAnError() throws {
}

// 에러 가능성이 있는 함수 호출할 경우, do, try, catch 구문 사
do {
    try canThrowAnError()
} catch {
    print(error)
}
```





### Functional Programming(FP)

프로그램의 상태 변화 없이 데이터 처리를 수학적 함수 계산으로 취급하는 방식의 패러다임으로 값의 변화에 집중하지 않고 순수 기능 자체를 중요하게 생각하는 방식입니다.\


* **Immutability** \
  함수 내부에 상태를 사용하지 않습니다. 함수의 출력은 항상 입력값에 영향을 받음을 의미합니다. 이를 통해 얻을 수 있는 장점은 예측가능한 코드를 작성할 수 있기에 테스트코드를 만들어 프로그램 검증이 쉽습니다. 또한 함수의 불변성이 보장되어야만 가능한 메모이제이션과 같은 최적화 작업이 가능합니. 메모이제이션이란 이전에 계산한 함수의 값을 캐싱하여 필요할 때 다시 사용하는 것을 의미합니다.
* **Concurrency Programming** \
  함수형 프로그래밍은 동시성 프로그래밍이 가능합니다. 그동안 명령형 프로그래밍에서는 상태를 공유하기때문에 멀티쓰레드를 활용한 동시성 프로그래밍이 어려웠습니다. 교착상태(데드락)에 빠지는 위험으로 고려해야할 요소가 많았는데, 함수형 프로그래밍에서는 side effect를 제거한 불변성 덕분에 동시성이 가진 문제를 원천적으로 봉쇄할 수 있습니다.
* **First-class function** \
  함수는 값처럼 사용될 수 있습니다. 함수의 인자로 전달할 뿐만아니라 반환할 수 있는데 여러함수를 결합한 고차함수가 대표적인 예시입니다. 이를 통해, 유연하고 간결한 코드를 작성할 수 있습니다.\


간결하게 프로그램을 작성할 수 있어 프로토타입을 만들고 검증하는 일련의 개발 과정이 빨라집니다. 또한 방대한 데이터를 효율적으로 처리하기 위해 동시성을 잘 지원할 수 있으며 기존에 작성된 모듈을 최대한 재사용하여 안정적인 런타임 환경을 구축할 수 있게 됩니다. 주의할 점은 Side Effect를 허용하지 않도 순수함수로 작성되어야 합니다. 그래야 동시에 여러스레드에서 문제 없이 동작하는 프로그램을 쉽게 작성할 수 있습니다.

