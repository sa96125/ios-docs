# closure

이름이 없는 함수, Anonymous Function이라 부른다. func 키워드와 함수이름을 지우고 첫 번째 중괄호를 이동 후 In 키워드를 추가하여 작성한다. 컴파일러가 타입을 추론할 수 있어 인풋과 아웃풋의 타입을 생략할 수 있다. Return 키워드, 파라미터 또한 생략가능하다.

```swift
func calculator(n1: Int, n2: Int, operation:(Int, Int) -> Int) -> Int {
	return operation(n1, n2)
}

func add(n1: Int, n2: Int) -> Int {
	return n1 + n2
}

or

func calculator(n1: Int, n2: Int, operation:(Int, Int) -> Int) -> Int {
	return operation(n1, n2)
}

// 1. default
calculator(n1: 2, n2: 3, operation: {(no1: Int, no2: Int) -> Int in 
	return no1 * no2 
})

// 2. omit
calculator(n1: 2, n2: 3, operation: {$0 * $1})

// 3. trailing closure : 콜백함수가 마지막 파라메터일 경우 분리하여 작성
calculator(n1: 2, n2: 3) {$0 * $1}

// 4. 실전
// 배열의 각요소 1씩 더하기, 클로저가 마지막이라 () 생략.
array.map{$0 + 1}

// 배열의 각요소 문자열 변환
array.map{"\\($0)"}
```

보다시피 클로저를 사용하면 코드를 줄여 간단하게 작성할 수 있다는 것이다. 하지만 읽기 좋은 코드가 되기 힘들다. 읽기좋은 코드와 간결한 코드를 적절한 밸런스로 작성하는 능력은 중요하며 온전히 코드를 작성하는 사람에게 달렸다.
