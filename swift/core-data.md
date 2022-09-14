# Core Data

### Retrieve Stackoverflow

\[ Do ] \[ Language ] \[ Flatform ]



### Scope

중괄호로 감싸진 영역으로 코드를 실행할 수 있는 영역이다. 주의할 점은 서로다른 스코프에서 선언된 변수, 함수는 외부에서 사용할 수 없다.



### Type Inference

스위프트에서 어떤 타입의 값을 할당하면 그 변수에 자동으로 추론하 적용된다.



### String Interporation

“ \\( )” 문자열 속에서 스위프트 변수, 연산등을 사용할 수 있다.



### DispatchQueue

별도의 스레드에서 작업할 수 있다. 순차적/비동기식(동시)으로 코드를 실행할 수 있으나 과도한 스레드가 생성될 수 있어 주의가 필요하다.



### if vs Switch

범위가 클수록 패턴 매칭이 보다 효율적이고 읽기 쉬운 코드가 된다. swich를 사용할 때, 꼭 범위 외의 사항에 대한 처리가 필요하며 이는 default에서 처리한다. 또한 각각의 범위는 … / ..< 와 같은 키워드를 사용하여 설정할 수 있다.



### Function

Input과 output이 없을 경우, () {}

Input만 있을 경우 (parameter: DataType)

Output만 있을 경우 () returnArrow DataType { return Keyword value } 로 정의할 수 있다.



### Structure

커스텀 데이터 타입을 만들어 사용할 수 있다. 기존 데이터 타입들은 이 구조를 활용되어 만들어졌고 이미 Prebuilt 되어 있어 사용할 수 있는 것이다. 내가 필요한 타입들을 모아 스트럭쳐를 구성할 수 있고 초기화하여 사용할 수 있다. 객체를 생성하는 블루프린트로 불리기도 한다. 이 구성은 프로퍼티 혹은 메서드로 구성 될 수 있다.

structure에 사용할 데이터를 모두 담아둘 수도 있지만, initialize를 통해 생성과 동시에 데이터를 담아 둘 수 있다는 장점이 있다. 하지만 굳이 생성자가 필요없는 경우는 생략하는 것이 정석이다. 블루프린트라는 의미는 프로퍼티, 메서드를 통해 그 형태를 만들어 놓는다는 것이고 생성자를 통해 고유한 특징을 입힘으로서 특정 객체를 나타낼 수 있는 것이다. 예를 들어 다양한 자동차, 국가라는 형태를 잡고 색, 성향, 리소스 즉 데이터를 추가함으로서 고유한 객체를 생성할 수 있게 된다.



### Self keword

자바스크립트의 this와 같다. 즉 실제 생성될 객체를 가르킨다. 블루프린트를 통해 생성된 객체는 각기 다른 특성을 가지고 있다. self를 통해 각각 생성된 객체의 프로퍼티 또는 메서드에 접근할 수 있게 된다.



### Immutability

let과 같은 키워드를 사용하면 값의 수정이 불가능한데 이를 immutable이라고 한다. 앞서 설명한 구조체를 예로들면, 구조체를 구성하는 프로퍼티 변수를 수정하는 일이 있을 수 있다. 실제 인스턴스에서 이 변수를 수정하는 일이 발생하면 메서드를 사용해야하는데 이때 메서드 속에는 self 키워드로 구조체 변수에 접근하는 로직이 작성된다. 주의할점은 이 self는 인스턴스 생성시 let으로 생성되기 때문에 변수를 수정하는 것이 불가능하다. 이때 구조체에서 var로 선언된 변수를 수정하기 위해서는 mutating이라는 키워드로 메서드를 선언해야한다. 이때는 self 키워드를 사용하지 않아도 변수에 접근할 수 있다. 주의해야할 또 한가지 사항은 구조체의 인스턴스를 생성할 때 let를 사용하게 되면 이를 구성하는 요소 프로퍼티, 메서드에 대한 변경이 불가능해진다.



### Optional

nil 크러싱으로 인한 런타임 오류가 유일한 이슈 사항이다.

1. Force Unwrapping never gonna be NIL , 하지만 값이 할당되지 않은 옵셔널을 경우 Nil만 가지고 있어 런타임 오류가 발생한다.
2.  Check for nil value

    ```swift
    if optional != nil {
    	optional!
    } else {
    	print("myOptional was found to be nil")
    }
    ```
3.  Optional Binding

    ```swift
    // !을 사용하지 않고 check nil
    if let safeOptional = myOptional {
    	let text:String = safeOptional
    } else {
    	print("myOptional was found to be nil")
    }
    ```
4.  Nil Coalescing Operator

    ```swift
    // more clear way
    optional ?? defaultValue
    ```
5.  Optional Chaining

    ```swift
    // : Struct? , : Class? 에서도 사용 가능
    // nil이 아니면 프로퍼티 또는 메서드 실행, nil이면 실행하지 않음.
    optoinal?.pro
    ```

####

### External Parameter Name & \_

함수를 호출할 때 사용할 파라미터 이름을 재정의하거나 생략할 수 있는 방법

#### Order of mathematical operations

대괄호, 제곱, 곱셈 or 나눗셈, 플러스 or 마이너스 순서로 계산한다. 주의할점은 컴퓨터가 같은 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산하게 된다

####

### Class

구조체와 유사하지만 클래스의 경우 슈퍼클래스로부터 상속이 가능하다는 점이 다르다. 상속이란 부모가 가진 특징을 그대로 물려받아 사용할 수 있을 뿐만 아니라 추가적인 능력을 추가할 수 있는 것을 의미한다. 미리 작성된 코드를 사용하게 되어 코드를 생성, 반복하는 작업을 줄일 수 있다. 개인적으로 클래스를 한단어로 표현한다면 **파생**이라 말할 수 잇을 것 같다. 물려받은 능력을 그대로 사용하거나 변형되거나 마치 진화하는 모습처럼. 서브클래스로 만든 인스턴스로 부모로 부터 물려받은 변수를 변경하거나 메서드를 호출하는 것이 가능하다. 부모는 자식을 위해 모든 것을 해주는 모습처럼 여길 수 있을 것 같다. 서브 클래스내에서의 메서드를 변경할때 override, super 키워드를 사용한다.

* passed by reference //의도치 않게 변경할 수 있는 위험요소 발생 가능성(다중 스레드 환경에서 주의)
* inheritance
* init is necessary
* mutable

공식문서에서는 객체를 만들 필요성이 있을 때 먼저 구조체 형식으로 만드는 것을 권장한다. 클래스를 let으로 선언할 경우, 구성하고 있는 프로퍼티와 메서드의 접근이 불가능하다.

####

### Framework

메인 ViewController를 제외한 다른 화면을 구성하여 컨트롤하기 위해서 SecondController : UIViewController 의 상속을 받아서 처리한다. Kit은 IOS 개발자를 위해 미리 만들어놓은 소스코드의 모음으로 기존에 스토리보드로 하던 작업을 코드만 사용하여 라벨, 텍스트, 이미지뷰에 접근 수정가능하다.

####

### Create Label with UIKit

```swift
override func viewDidLoad() {
	super.viewDidLoad()

	// viewController의 view 객체 접근 가능
	// UIcolor.red 생략 가능 .red는 UIcolor리턴하고
	// .backgoundColor는 UIcolor를 받기 때문에 쉬위프트가 자동으로 인식
	view.backgroundColor = .red
	
	let label = UILabel()
	label.text = "hello"

	// 배치 및 크기 필요
	label.frame = CGRect()

	// viewController의 최상위가 view이므로 view에 할당
	view.addSubview(label)
}
```

####

### Navigating viewController

```swift
// 다른 페이지(VC) 보기
self.present(secondVC, animated:ture, completion: nil)
```

####

### CoCoa Touch

UIKit 뿐만 아니라 애플에서 만든 라이브러리를 사용할 수 있다. 이를 활용하여 멀티 페이지를 설정하고 세그웨이 및 네비게이팅할 수 있게 된다. 세그웨이는 스크린에 나타날 화면을 애니메이션하는 방법을 말한다.

디자인 된 View Controller를 클릭(노란색네모 클릭)하고 Tab(identify)에서 커스텀 클래스를 CoCoa파일로 만든 클래스를 연동한다.

or

```swift
// one page
self.performSegue(withIdentifier: "goToResult", sender: self)
```

or

```swift
// multi page
// mainController(cocoa페이지를 호출하는)
override func prepare() {
	if segue.identifier == "goToResult {

		// downcasting by as, 왜냐면 prepare를 호춣하면 기본적으로 UIController를 가져오는데
		// 이때 우리가 ResultViewController나 bmiValue가 있는지 모르기 때문
		let destinationVC = segue.destination as! ResultViewController
		destinationVC.bmiValue = "0.0"
}

// secondController(cocoa페이지에서)
// go back to previous page
self.dismiss(animated: true, completion: nil)
```

####

### SF symbol

ios13부터 사용가능한 아이콘으로서 자동 스케일, 백터화하여 유저가 건드릴 필요가 없다.

####

### Dark mode

시스템 컬러를 사용하면 운영체제가 지원하는 다크모드를 사용할 수 있다. 커스텀 컬러를 다크모드와 사용하기 위해서는 Assets에서 플러스 버튼을 눌러 Color Set을 지정하면 된다.

####

### Avoid of pixelate Background

Asset에서 1x 2x 3x이미지 변환하는 방법, 벡터 파일을 사용하는 방법이 있다. 백터파일을 사용할 때 Vector Resizing이 가능하게하고 Single sacle이 되도록 옵션을 변경한다. 벡터파일로 모든 해상도를 커버할 수 있으니까.

####

### TextField

사용자에게 입력을 받을 수 있다. 현재 ViewController에서 TextField를 인지하기 위해 delegate를 사용하여 참조해주어야한다.

```swift
// : UITextFieldDelegate(프로토콜)
searchTextField.delegate = self
```

검색 버튼, 키보드 버튼에서 입력이 끝날때의 처리를 해야한다.

```swift
@IBAction func searchPressed(_ sender: UIButton) {
        searchTextField.endEditing(true)
    }
    
    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        searchTextField.endEditing(true)
        return true
    }
    
    // 입력 끝내기 직전 -> 성공, 실패
    func textFieldShouldEndEditing(_ textField: UITextField) -> Bool {
        if searchTextField.text != "" {
            return true
        } else {
            searchTextField.placeholder = "Type something"
            return false
        }
    }
    
    // 입력 끝낸 직후
    func textFieldDidEndEditing(_ textField: UITextField) {
        searchTextField.text = ""
        searchTextField.placeholder = "Search"
    }
```

####

### Protocol(certificate)

프로토콜의 기능을 알기 전에 먼저 어떤 문제가 있었는지에 대해 알 필요가 있다. 클래스간 상속을 통해 코드의 중복을 피하고 슈퍼클래스의 특성을 서브클래스에서 재사용할 수 있고 뿐만 아니라 그 기능을 재 정의할 수 있다는 것을 배웠다. 하지만 특수한 예로, 부모의 기능을 사용하지 않는 경우라면 어떻게 해야할까? 상속의 특성상 서브클래스는 무조껀 슈퍼클래스의 기능을 사용할 수 있다. 이처럼 불필요한 동작의 기능을 막기 위해 그 기능을 분리 시켜야할 경우 프로토콜을 사용하여 구조체, 혹은 클래스에서 정의하도록 도와준다.

프로토콜을 정의할 때, 메서드의 이름만 작성해야하고 프로토콜을 호출하는 구조체와 클래스에서 무조껀 그 메서드 이름에 해당하는 기능을 작성해야한다. 뿐만아니라 해당 기능을 가진 오브젝트를 파라메터로 사용할 수 있는 변수의 타입으로도 지정할 수 있다. 이를 통해 알수 있는 것은 프로토콜의 기능을 활용하면 쓸대없는 클래스 상속을 피할 수 있고 데이터타입을 확장된 형태로도 나타낼 수 있게 된다. 또한 프로토콜이 사용된 클래스와 구조체에서는 해당하는 기능이 무조껀 들어있다는 것도 명시적으로 알 수 있다. 여러개를 사용할 수 있고, 상속과 함께 그 다음에 붙여서 사용할 수도 있다.

여기서 알 수 있는 부분은 모든 능력을 물려줘야하는 상속이 필요하다면 클래스를 사용하고, 어디에서든 사용할 수 있는 기능을 구현해야할 필요가 있을 때 프로토콜을 사용, 그외에 여러 변수를 담는다던지, 객체를 만들어야할 때는 기본적으로 구조체를 할용할 수 있다. 구조체의 경우 값의 복사 참조의 특성을 가져 안전한 사용이 가능한데 프로토콜덕분에 클래스의 상속 개념을 사용하여 모듈화할 수 있습니다.



### POP(Protocol Oriented Programming)

1.  가볍고 안전하다

    reference by value
2.  상속 효과

    common method
3.  수평 구조의 기능 확장

    not only related class
4.  유연한 처리

    generic



### API(Application Programming Interface)

명령어, 함수, 프로토콜, 객체의 집합으로서 프로그래머는 소프트웨어를 만들거나 다른 외부 시스템과 소통하기 위해 사용한다. 예를 들어, 애플기기의 기능을 사용하고 싶을 때 혹은 외부 서버의 데이터가 필요할 때 API를 호출할 수 있다.

####

### URLsession

네트워킹 작업을 수행하는 오브젝트.

```swift
func performRequest(urlString: String) {
    
    // 1. Create a URL
    if let url = URL(string: urlString) {
        
        // 2. Create a URLsession
        let session = URLSession(configuration: .default)
        
        // 3. Give the session a task
        let task = session.dataTask(with: url, completionHandler: handle(data:response:error:))
        
        // 4. Start task
        task.resume()
    }
}
```

####

### Closures

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

