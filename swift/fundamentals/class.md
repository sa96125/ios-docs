# class

구조체와 마찬가지로 객체를 생성하는 설계도입니다. 다만, OOP의 주요 특징인 상속이 가능합니다. 이는 슈퍼클래스의 기능을 읽거나(super) 수정(override)할 수 있습니다. 코드를 재사용할 수 있어 반복되는 작업은 제거할 수 있습니다.



클래스는 구조체와 비슷하지만 다릅니다.

1. **passed by reference로 안전성이 떨어집니다.**&#x20;
2. **초기값을 설정하려면 생성자 함수를 작성해야합니다.**&#x20;
3. **데이터를 힙에 저장하고, 해당 레퍼런스를 스택에 저장합니다.**
4. **let에 클래스 인스턴스를 할당하더라도 프로퍼티를 수정할 수 있습니다.**



{% hint style="danger" %}
클래스의 passed by reference 특징 때문에 멀티플 레퍼런스를 가질 수 있습니다. 이는 의도치 않게 값을 변경할 수 있는 매우 큰 위험으로 다중 스레드 환경에서는 주의가 필요합니다.
{% endhint %}





### Static(feat. Singlton)

Static 키워드는 보통 싱글톤 패턴을 채택할 때 사용 됩니다. **클래스** 인스턴스가 한개 이상 할당되지 않기를 원할 때, 상수 내부에 공유 인스턴스에 대한 참조를 저장하고 초기화 프로그램을 숨깁니다.



```swift
class Singleton {
    static let sharedInstance = Singleton()

    private init() { }

    func doSomething() { }
}

Singleton.sharedInstance.doSomething()
Singleton.sharedInstance.doSomething()
Singleton.sharedInstance.doSomething()
```

