---
description: >-
  Constants and variables associate a name with a value of a particular type.
  The value of a constant can’t be changed once it’s set, whereas a variable can
  be set to a different value in the future.
---

# var and let

프로그램에서 데이터에 접근하려면 의미를 부여한 이름을 사용해야합니다. 개발자는 선언된 이름을 통해 데이터를 읽거나 수정할 수 있게 되는데요. 스위프트에서는 이를 위해 2가지 키워드를 사용합니다. 바로 _<mark style="color:red;">**`var`**</mark>_ 과 _<mark style="color:red;">**`let`**</mark>_ 입니다. _<mark style="color:red;">**`var`**</mark>_ 키워드를 덧붙인 이름에 값을 할당하면 그 이름을 사용하여 언제든지 값을 변경할 수 있지만 _<mark style="color:red;">**`let`**</mark>_의 경우 초기에 한번 값이 할당되면 절대 변경할 수 없습니다.



```swift
// MARK - 변수와 상수 예시 코드 1

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



이 처럼 보존 되어야할 중요한 정보가 외부의 영향으로 훼손되었을 때 큰 문제를 발생 시킬 수 있습니다. 만약 내가 작성한 프로그램에서 데이터가 중요하다면 혹은 다양한 로직에서 사용된다면 애초에 _<mark style="color:red;">**`let`**</mark>_으로 선언하여 변경을 막 오류의 발생을 차단할 수 있겠네요!



이를 전문 용어로 불. 변. 성(_Immutability_)라고 합니다. 더 깊게 설명할 필요성이 있지만, 이제 시작한 스위프트 공부를 어렵게 만들고 싶지 않네요ㅎ. 이미 중요한 내용을 알게 되었고, 현재는 상수는 imutable한 값, 변수는 mutable한 값이란 것만 이해하면 됩니다.



{% hint style="info" %}
_**`var`**_와 _**`let`**_중에 무엇을 사용해야하나라는 고민에 빠질 수 있습니다. 그럴 때는 고민하지말고 _**`let`**_으로 선언한 다음 필요에 따라_**`var`**_로 변경하여 사용하면 됩니다. 단, 이 데이터가 변경되었을 때 주위에 미치는 영향에 대해서 생각 한 후 사용하면 더욱 좋을 것 같네요:)
{% endhint %}



다음으로 눈여겨 볼 것은 변수의 타입입니다. 앞서 언급했듯이 스위프트 언어는 매우 엄격한 타입을 요구합니다. 예를 들어, 사람은 숫자와 문자를 더하는 행동을 했을 때 잘못되었다는 것을 인지하지만 컴퓨터는 숫자인지 문자인지 판별할 수 없으니 그러지 못하죠. 그래서 데이터가 적절한 경우에 올바른 행동을 할 수 있도록 데이터와 함께 타입을 알려줘야합니다. 데이터에 타입을 명시하면 잘못된 코드를 작성 하였을 때, 컴파일러가 에러를 조기 발견할 수 있습니다.



```swift
// MARK - 변수와 상수 예시 코드 2

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

스위프트의 변수에는 매뉴얼하게 할당하는 방법 외에도 자동으로 값을 할당 할 수 있습니다. computerted variable은 값 대신 코드를 작성합니다. **지정한 변수로 부터 계산된 값을 할당**하기 때문에 따로 메서드를 조작할 필요 없이 간편하고 빠르게 원하는 값을 저장할 수 있게 됩니다.

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

변수명과 함께 사용되는 키워드이다. 호출할 때, 동작하는 코드를 담고 있다. 처음부터 코드를 셋업할 필요가 없다는 의미로 비록 늦게 실행될 수 있지만 실행과 동시에 메모리에 할당되어 이점을 가질 수 있다.

```swift
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





### get, set, didSet, willSet

프로퍼티를 다채롭게 활용하는 방법이다.

```swift
// computed properties
// 값을 읽고/쓸때 사용하는 로
var myProperty: Int {
   get {
      return _myProperty
   }
   set {
      _myProperty = newValue
   }
}

// observed properties
// 값이 입력된 직전/후에 수행할 로직
var myProperty: Int = 10 {
   willSet {
      print(myProperty) // 10
      print(newValue) // newValue
      loadItems()
   }
   didSet {
      print(oldValue) // 10
      print(myProperty) // newValue 
      loadItems()
   }
}

// 실전
var myProperty: Int = 10 {
   didSet {
      if myProperty > 18 {
         print("invalid value, Set myProperty to 18")
         myProperty = 18
      }
   }
}
```





### Access Control

1. private\
   해당 스코프 내에서만 접근할 수 있는 변수. 항상 변수를 선언할 때 이 키워드를 붙이는 습관을 들인다. 상태의 안전을 보장할 수 있다.
2. fileprivate\
   파일 내에서만 접근할 수 있는 변수.
3. internal\
   default, 앱(모듈) 내에서 사용할 수 있는 변수
4. public\
   다양한 모듈에서 사용할 수 있는 변수, 오버라이팅을 할 수 없다.\
   API, SDK, Frameworks and Libraries
5. open\
   public+, 오버라이팅이 가능하며 모든 것을 사용할 수 있다.

{% hint style="info" %}
구조체를 사용하다가 필요에 따라 클래스로 변경하는 것처럼, Acess level 또한 필요에 따라 단계를 높여 사용하는 습관을 기르자.
{% endhint %}
