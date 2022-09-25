# Terms

### FP(Functional Programming)

간결하게 프로그램을 작성할 수 있어 프로토타입을 만들고 검증하는 일련의 개발 과정이 빠르다. 또한 방대한 데이터를 효율적으로 처리하기 위해 동시성을 잘 지원할 수 있으며 기존에 작성된 모듈을 최대한 재사용하여 안정적인 런타임 환경을 구축할 수 있다.

함수를 작성할 때 주의할 점은 Side Effect를 허용하지 않도 순수함수로 작성하는 것이 중요하다.  그래야 동시에 여러스레드에서 문제 없이 동작하는 프로그램을 쉽게 작성할 수 있다. 함수형 프로그래밍이 가진 특징을 몇가지 살펴보자.

*   #### Immutability

    앞서 순수함수를 지향하면서 코드를 작성해야한다 했는데 변경 가능한 상태를 최대한 제거함을 의미한다. 함수 내부에 상태를 사용하지 않으며 함수의 출력은 항상 입력값에 영향을 받아야한다. 이를 통해 얻을 수 있는 장점은 예측가능한 코드를 작성할 수 있기에 테스트코드를 만들어 프로그램 검증이 쉽다. 또한 함수의 불변성이 보장되어야만 가능한 메모이제이션과 같은 최적화 작업이 가능하다. 메모이제이션이란 이전에 계산한 함수의 값을 캐싱하여 필요할 때 다시 사용하는 것을 의미한다.
*   **Concurrency Programming**

    함수형 프로그래밍은 동시성 프로그래밍이 가능하다. 그동안 명령형 프로그래밍에서는 상태를 공유하기때문에 멀티쓰레드를 활용한 동시성 프로그래밍이 힘들었다. 교착상태(데드락)에 빠지는 위험으로 고려해야할 요소가 많았는데, 함수형 프로그래밍에서는 side effect를 제거한 불변성 덕분에 동시성이 가진 문제를 원천적으로 봉쇄할 수 있다.
*   **First-class function**

    함수는 값처럼 사용될 수 있다. 함수의 인자로 전달할 뿐만아니라 반환할 수도 있다. 이로인해, 여러함수를 결합한 고차함수를 통 유연하고 간결한 코드를 작성할 수 있다.



### JSON(Javascript Object Notation)

인터넷에서 데이터를 가볍고 효율적으로 전달할 수 있는 방식이다. 코드의 형태를 문자열로 감싸서 전달한다. 자바스크립트 객체 형태를 스위프트에서 사용하기위해서는 스위프트 객체 형태로 Parsing 작업을 거쳐야한다. 먼저 구조체를 만들고 Decodable 프로토콜을 받으면 JSONDecoder를 사용하여 스위프트에서 사용할 수 있게 된다.

```swift
func parseJSON(weatherData: Data) {
        let decoder = JSONDecoder()
        do {
	    // 구조체의 실제 타입은 .self로 확인
            // decode 데이터는 
            let decodedData = try decoder.decode(WeatherData.self, from: weatherData)
            print(decodedData.name) 
        } catch {
            print(error)
        }
    }
```



### API(Application Programming Interface)

명령어, 함수, 프로토콜, 객체의 집합으로서 프로그래머는 소프트웨어를 만들거나 다른 외부 시스템과 소통하기 위해 사용한다. 예를 들어, 애플기기의 기능을 사용하고 싶을 때 혹은 외부 서버의 데이터가 필요할 때 API를 호출할 수 있다.



### Scope

중괄호로 감싸진 영역으로 코드를 실행할 수 있는 영역이다. 주의할 점은 같은 레벨의 서로 다른 스코프에서 선언된 변수, 함수는 외부에서 사용할 수 없다.



### Type Inference

스위프트에서 값을 할당하면 그 변수 타입을 지정하지 않아도 자동으로 타입을 추론하여 적용한다.



### String Interporation

“ \\( )” 문자열 속에서 스위프트 변수, 연산등을 사용할 수 있다.



### DispatchQueue

별도의 스레드에서 작업할 수 있다. 순차적/비동기식(동시)으로 코드를 실행할 수 있으나 과도한 스레드가 생성될 수 있어 주의가 필요하다.



### SF symbol

ios13부터 사용가능한 아이콘으로서 자동 스케일, 백터화하여 유저가 건드릴 필요가 없다.



### Catalyst Project

iPhone에서 개발한 것을 iPad, Mac에서 실행하고 빌드하는 것이 가능하다.



### Framework

메인 ViewController를 제외한 다른 화면을 구성하여 컨트롤하기 위해서 SecondController : UIViewController 의 상속을 받아서 처리한다. Kit은 IOS 개발자를 위해 미리 만들어놓은 소스코드의 모음으로 기존에 스토리보드로 하던 작업을 코드만 사용하여 라벨, 텍스트, 이미지뷰에 접근 수정가능하다.



### POP(Protocol Oriented Programming)

1.  가볍고 안전하다

    reference by value
2.  상속 효과

    common method
3.  수평 구조의 기능 확장

    not only related class
4.  유연한 처리

    generic



### OOP(Object Oriented Programming)
