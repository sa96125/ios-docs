# function

특정 기능을 수행하는 코드의 묶음이다. 이 코드를 식별할 수 있는 이름과 입력값(params), 출력값(return)을 유연하게 표현할 수 있다. 함수의 이름을 작성할 때는 호출할 때, 이 함수의 역할이 잘 드러나도록 작성하는 것이 중요하다. 그 이유는 내부를 보지 않고도 그 내용을 파악하게 되면 코드 전체를 이해하기 쉬운 클린코드를 만들 수 있을 뿐만아니라 시간을 절약하여 생산성 또는 함수의 재사용성을 높일 수 있다.

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



### External Parameter Name & \_

함수를 호출할 때 사용할 파라미터 이름을 재정의하거나 생략할 수 있다.

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

프로그램 실행 중에 발생할 수 있는 오류 조건을 함수 내에 작성하면 함수를 호출한 곳에서 정확하게 오류를 응답할 수 있게 된다. 만약 작성된 에러에 대한 핸들링이 필요하다면 아래의 키워드를 사용한다.

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

