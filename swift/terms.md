# Terms

### API(Application Programming Interface)

명령어, 함수, 프로토콜, 객체의 집합으로서 프로그래머는 소프트웨어를 만들거나 다른 외부 시스템과 소통하기 위해 사용한다. 예를 들어, 애플기기의 기능을 사용하고 싶을 때 혹은 외부 서버의 데이터가 필요할 때 API를 호출할 수 있다.





### App thinning

앱 스토어와 운영체제가 디바이스의 특성에 맞게 설치되도록 하는 최적화 기술을 의미한다. 최소한의 디스크 사용과 빠른 다운로드를 제공할 수 있다.

{% hint style="info" %}
* _slicing :_ 디바이스 특성에 따라 다양한 번들을 미리 준비
* _bitcode_ :  기계어로 번역되기 이전 상태 코드 준
* _on-demand resource_ : 부분 설치 (선택적 다운로드)&#x20;
{% endhint %}





### ARKit

AR이란 실제 세상에 가장의 오브젝트를 적재하여 병합하는 기술이다. ARKit 프레임워크를 이용하면 애플 생태계에서 AR를 구현할 수 있다.

Requirements

* min A9 chip
* after iPhone 6
*   real divice can access live camera session( not work in Simulator )

    ```swift
    print(ARSessionConfiguration.isSupported)
    print(ARWorldTrackingSessionConfiguration.isSupported)
    ```

Content Technology Options

* Metal : GPU 컨트롤하는 것에 초점
* SpriteKit
* SceneKit
* RealityKit





### Catalyst Project

iPhone에서 개발한 것을 iPad, Mac에서 실행하고 빌드하는 것이 가능하다.





### Cocoa touch class file vs swift file

테이블뷰와 같이 xcode에 포함된 클래스를 사용한다면 cocoa touch로 만들고 커스텀으로 만드는 클래스는 swift로 생성한다.





### DispatchQueue

별도의 스레드에서 작업할 수 있다. 순차적/비동기식(동시)으로 코드를 실행할 수 있으나 과도한 스레드가 생성될 수 있어 주의가 필요하다.





### Framework

메인 ViewController를 제외한 다른 화면을 구성하여 컨트롤하기 위해서 SecondController : UIViewController 의 상속을 받아서 처리한다. Kit은 IOS 개발자를 위해 미리 만들어놓은 소스코드의 모음으로 기존에 스토리보드로 하던 작업을 코드만 사용하여 라벨, 텍스트, 이미지뷰에 접근 수정가능하다.





###



### Frame vs Bounds

공통적으로 UIView의 위치와 크기를 나타날 때 사용한다. 하지만 Frame의 경우 superView의 좌표를 기점으로 위치하지만 Bound의 경우 생성된 좌표를 기점으로 위치한다. 또한 Frame의 크기는 실제 UIView를 포함한 사각 영역을 의미하지만 Bound의 경우는 UIView의 고유 크기를 표시한다.

꼭 기억해야할 점은 Bound의 크기는 현재 UIView의 Viewport를 나타낸다는 것이다. bound를 위치를 이동하면 UIView의 위치를 이동하는 것이 아니라, UIView의 내부 컨텐츠의 이동을 의미한다.





### In App purchases

30% 수수료 낸다. 인앱 구매 등록 조건은 Full apple Developer 자격이 있어야한다. 매년 $99의 결제가 필요하다. 이를 테스팅하기 위해서 실제 아이폰 장비가 필요하다, 시뮬레이터에서 인앱 결제는 동작하지 않는다.





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





### OOP(Object Oriented Programming)





### POP(Protocol Oriented Programming)

{% hint style="info" %}
POP의 특징은 무엇일까?

* 가볍고 안전 (reference by value)
* 상속 효과 (common method)
* 수평 구조의 기능 확장 (not only related class\_
* 유연한 처리 가능 (generic)
{% endhint %}





### SF symbol

ios13부터 사용가능한 아이콘으로서 자동 스케일, 백터화하여 유저가 건드릴 필요가 없다.





### String Interporation

“ \\( )” 문자열 속에서 스위프트 변수, 연산등을 사용할 수 있다.





### Type Inference

스위프트에서 값을 할당하면 그 변수 타입을 지정하지 않아도 자동으로 타입을 추론하여 적용한다.





### UIViewController

앱 화면의 콘텐츠를 표시하는 로직과 관리는 담당한다.





### Xcode Simulator

프로토타입을 가상 디바이스로 만들어 테스팅, 디버깅을 할 수 있는 환경이다. 실제 디바이스와는 엄연히 다르고 기능적인 차이가 존재한다.
