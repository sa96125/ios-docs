# Terms

### JSON(javascript object notation)

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



### API(Application Programming Interface)

명령어, 함수, 프로토콜, 객체의 집합으로서 프로그래머는 소프트웨어를 만들거나 다른 외부 시스템과 소통하기 위해 사용한다. 예를 들어, 애플기기의 기능을 사용하고 싶을 때 혹은 외부 서버의 데이터가 필요할 때 API를 호출할 수 있다.

####
