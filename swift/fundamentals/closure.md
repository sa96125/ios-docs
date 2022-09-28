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



### @autoclosure

클로저는 본질적으로 함수의 형태로 사용해야하지만 autoclosure 키워드를 선언시 함수 앞에 붙이게 되면 일반 구문도 사용할 수 있게 된다. 지연된 실행이 가능하여 메모리상 이점이 있지만 클로저 함수에 파라미터가 있을 시 에러가 발생할 수 있다.

```swift
func doSomething(closure: @autoclosure () -> ()) {
    closure()
}

doSomething(closure: 1 > 2)
```

###

### @escaping

기존 클로저(**non-escaping closure**) 사용에 불가능했던 것을 가능하게 한다.

* 클로저가 포함된 함수의 실행이 끝난 후에도 클로저를 실행 할 수 있다.
* 변수 또는 상수에 할당할 수 있다.
* 중첩함수에서 사용하여 반환 할 수 있다.
