---
description: >-
  Constants and variables associate a name with a value of a particular type.
  The value of a constant can’t be changed once it’s set, whereas a variable can
  be set to a different value in the future.
---

# var and let

프로그램에서 데이터에 접근하려면 의미를 부여한 이름을 사용해야합니다. 개발자는 선언된 이름을 통해 데이터를 읽거나 수정할 수 있게 되는데요. 스위프트에서는 이를 위해 2가지 키워드를 사용합니다. _**var**_** 키워드는 언제든지 값의 변경을 허용하지만  **_**let**_**은 초기에 한번 값이 할당되면 절대 변경할 수 없습니다.**



```swift
let numberOfBond = 007
var numberOfAgent = 000


// error: 변경할 수 없지, 내 마음 속의 007은 제임스 본드니까 하악.
numberOfBond = 001 


// success: 009로 변
numberOfAgent = 009


// 009
print(numberOfAgent)


// 쉼표를 구분하여 한 줄에 여러 상수 또는 변수 선언 가능해요.
var a = 0, b = 1, c = 2


// 수학의 파이는 변경되지 않는 고유에 값이니 당연히 let으로 선언해야겠죠?
// 상수의 이름을 대문자로 표기하는 방식이 사용되기도 한답니다!
let PI = 3.14
```



위처럼 **스위프트에서는 초기 이름 선언과 동시에 값의 할당해야 합니다.** 그런데 말이에요. 저 처럼 “변수로 선언 해놓고 안바꾸면 되는거 아닌가?” 이런 생각이 들 수 있어요. 앞으로 지속적으로 설명하겠지만 스위프트는 엄격한 타입, 안전한 프로그래밍을 지향합니다. 예시를 들어 볼게요. 여기 연 매출 50억을 달성하는 짜장면의 특급 레시피가 있어요. 이 레시피에서 재료가 단하나라도 달라지면 맛이 변한다고 가정할게요. 주방장이 실수로 레시피에 일부를 잊어버려서 똑같은 짜장면을 더이상 만들 수 없게 되었어요. 당연히 가게를 찾아 주던 손님들의 방문은 점점 줄어들게 되었고 더 이상 운영할 수 없게 되었습니다. 이는 엄청난 타격이 레시피를 복구할 수 있겠지만 상당한 리소스와 시간이 필요합니다.



이 처럼 보존 되어야할 중요한 정보가 외부의 영향으로 훼손되었을 때 큰 문제를 발생 시킬 수 있습니다. 만약 내가 작성한 프로그램에서 데이터가 중요하다면 혹은 다양한 로직에서 사용된다면 애초에 _let_으로 선언하여 변경을 막 오류의 발생을 차단할 수 있겠네요! 이를 전문 용어로 불변성(_Immutability_)라고 합니다. 지금 당장은 상수는 imutable한 값, 변수는 mutable한 값이란 것만 이해하면 됩니다.



{% hint style="info" %}
_**`var`**_와 _**`let`**_중에 무엇을 사용해야하나라는 고민에 빠질 수 있습니다. 그럴 때는 고민하지말고 _**`let`**_으로 선언한 다음 필요에 따라_**`var`**_로 변경하여 사용하면 됩니다. 단, 이 데이터가 변경되었을 때 주위에 미치는 영향에 대해서 생각 한 후 사용하면 더욱 좋을 것 같네요:)
{% endhint %}



다음으로 눈여겨 볼 것은 변수의 타입입니다. 앞서 언급했듯이 스위프트 언어는 매우 엄격한 타입을 요구합니다. 예를 들어, 사람은 숫자와 문자를 더하는 행동을 했을 때 잘못되었다는 것을 인지하지만 컴퓨터는 숫자인지 문자인지 판별할 수 없으니 그러지 못하죠. 그래서 데이터가 경우에 따 올바른 행동을 할 수 있도록 데이터와 함께 타입을 알려줘야합니다. 데이터에 타입을 명시하면 잘못된 코드를 작성 하였을 때, 컴파일러가 에러를 조기 발견할 수 있습니다.



```swift
var menu1 : String = "짜장면"
var priceOfMenu1 : Int = 7000


// error : menu1 변수는 문자열의 자료형만 담을 수 있어요.
menu1 = 8500


// error : 문자열과 숫자는 곱셈 연산이 불가능해요. 
menu1 * priceOfMenu1

```

{% hint style="info" %}
사실 자료형 타입을 생략해도 에러를 발생하지 않습니다. 그 이유는 스위프트 컴파일러는 할당된 값으로부터 자료형을 추론할 수 있기 때문입니다. 이를 _Type Reference_라고 합니다.
{% endhint %}





### Computed Variable

스위프트의 변수에는 매뉴얼하게 할당하는 방법 외에도 자동으로 값을 할당 할 수 있습니다. C_omputerted variable_은 값 대신 코드를 작성합니다. **지정한 변수로 부터 계산된 값을 할당**하기 때문에 따로 메서드를 조작할 필요 없이 간편하고 빠르게 원하는 값을 저장할 수 있게 됩니다.

```swift
struct ExamModel {
    let score: Int
    var grade: String {
        switch score {
        case 90...100:
            return "1등"
        case 80...89:
            return "2등"
        case 70...79:
            return "3등"
        case 60...69:
            return "4등"
        default:
            return "5등"
        }
    }
}
```





### Lazy

변수에 _lazy_ 키워드를 붙이면 해당 변수를 늦게 실행합니다. 혹시 레이지 로딩이라고 들어 보셨나요? 말그대로 늦게 로딩한다는 의미입니다. 만약 사진을 포함한 많은 리소스를 가진 웹페이지에 접근한다고 가정 해볼게요. 처음에 브라우저가 초기화면을 렌더링할 때 리소스가 많을 수록 사용자 경험은 떨어지게 됩니다.



이때 화면에서 보이지 않는 이미지가 있다면 초기 렌더링에 포함될 필요가 있을까요? 나중에 화면에서 필요하면 그때 이미지를 불러오면 됩니다. 레이지 로딩 덕분에 초기화면을 더 빨리 볼 수 있겠네요. 이처럼 레이의 개념은 “게으르다”라고 이해하기 보다 늦게, 필요할 때 실행 된다는 의미로 적절하게 사용하면 성능상의 이점을 가져올 수 있습니다.



다시 돌아와 스위프트에서는 _lazy_ 변수에 함수를 작성합니다. 중요한 것은 이 변수에 할당 함수는 메모리를 점유하고 있지 않습니다. 즉, 실행과 동시에 할당되기 때문에 **메모리상의 이점을 가진 함수를 선언**할 때 사용합니다.



```swift
/* 
    https://developer.apple.com/documentation/coredata/setting_up_a_core_data_stack)
    Core Data를 초기화할 때 사용되는 실제 예시 코드를 가져와봤어요.
    persistentContainer는 나중에 사용할 때, 실제 인스턴스화 된다는 것을 알 수 있네요.
*/

lazy var persistentContainer: NSPersistentContainer = {    
    let container = NSPersistentContainer(name: "DataModel")
    container.loadPersistentStores(completionHandler: { (storeDescription, error) in
        if let error = error as NSError? {
            fatalError("Unresolved error \\(error), \\(error.userInfo)")
        }
    })
    return container
}()
```





### Get, Set, DidSet, WillSet

클래스 내부에 선언하는 프로퍼티에 _get_과 _set_를 사용하면 변수를 읽거나 쓰는 동시에 값과 연관된 로직을 내부적으로 수행할 수 있습니다. 이를 _Computed properties_라 하며 데이터를 가공하여 사용할 수 있습니다. 뿐만아니라 _Observed properties_를 사용하면 프로퍼티에 값을 할당하는 시점의 전/후에 함수를 호출할 수도 있습니다. 먼저 _get_과 _set_을 활용한 실제 예시를 살펴보겠습니다.



```swift
@IBOutlet weak var displayLabel: UILabel!

private var displayValue: Double {
    get {
        guard let currentDisplayValue = Double(displayLabel.text!) else {
            fatalError("Connot convert display label text to a Double!")
        }
        return currentDisplayValue
    }
    set {
        // newValue는 set내부에서 사용할 수 있는 키워드로 새로운 값을 가지고 있습니다.
        displayLabel.text = String(newValue)
    }
}
```



위의 코드를 설명하자면, _displayValue_는 _displayLabel.text_에 있는 데이터를 가공하여 사용하는 _Computed property_입니다. _displayValue_의 값을 읽으면 _get_이 동작하는데 해당 코드는 _displayLabel.text_의 값이 _Double_ 자료형으로 변환이 불가능하면 에러를 발생시키는 검증의 로직이 추가 되어 있습니다. 그리고 _displayValue_에 _Double_ 타입의 새로운 값이 할당되면 _String_() 함수를 통해 자료형이 변환되어 _displayLabel.text_에 저장됩니다. 감이 오시나요? _displayValue_없이 _displayLabel.text_의 값을 사용한다면 그 때마다 코드를 반복해서 사용하게 될거에요. 하지 _get_과 _set_를 사용하면 중복적인 코드를 제거할 수 있을 뿐만아니 굳이 알필요 없는 코드를 내부에 감출 수 있게 되어 읽기 쉬운 코드를 작성할 수 있습니다.



```swift
var selectedBag: Bag? {

   // selectedBag에 값이 할당되었다면, 그 직전에 loadBagDetail() 함수를 호출 할 수 있구요.
   willSet { 
      loadBagDetail()
   }
   
   // selectedBag에 값이 할당된 직후에 검증을 추가할 수 있습니다.
   didSet {
      if selectedBag.name == "Chanel" {
         print("당장 놔라.")
      }
   }
}
```





### Access Control

프로퍼티와 메서드를 정의할 때, 키워드를 통해 접근 레벨을 부여할 수 있습니다.

1. _**private(only scope)**_\
   해당 스코프 내에서만 접근할 수 있도록 설정합니다. 상태의 안전을 보장할 수 있습니다.
2. _fileprivate(only file)_\
   파일 내에서만 접근할 수 있도 설정합니다.&#x20;
3. _internal(default)_\
   앱(모듈) 내에서 접근할 수 있도 설정합니다.&#x20;
4. _public(API, SDK, Frameworks and Libraries)_\
   모든 모듈에서 사용할 수 있게 설정합니다. 단, 오버라이팅을 통해 수정이 불가능합니다.
5. _open(ALL)_\
   _public+_, 오버라이팅이 가능하며 모든 곳에서 사용할 수 있도록 설정합니다.

{% hint style="info" %}
* let으로 변수를 선언하고 필요에 따라 var로 변경 한다.
* struct를 사용하다가 필요에 따라 class로 변경 한다.
* Acess level 또한 필요에 따라 단계를 높여 사용 한다.
{% endhint %}
