# Implementations

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



### Dark mode

시스템 컬러를 사용하면 운영체제가 지원하는 다크모드를 사용할 수 있다. 커스텀 컬러를 다크모드와 사용하기 위해서는 Assets에서 플러스 버튼을 눌러 Color Set을 지정하면 된다.

####

### Avoid of pixelate Background

Asset에서 1x 2x 3x이미지 변환하는 방법, 벡터 파일을 사용하는 방법이 있다. 백터파일을 사용할 때 Vector Resizing이 가능하게하고 Single scale이 되도록 옵션을 변경한다. 벡터파일로 모든 해상도를 커버할 수 있으니까.

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



### Cocoa Touch

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



### CoreLocation

현재 사용하고 있는 기기에 접근하여 위치 정보 얻을 수 있다. 이 기능을 사용하기 위해서는 먼저 사용자의 접근 허가 승인을 필요로 한다. .Info파일에서 `Privacy - Location When In Use Usage Description` 키를 등록하여 용도에 대한 디스크립션을 추가할 수 있다.

```swift
import CoreLocation

let locationManager = CLLocationManager()

locationManager.requestWhenInUseAuthorization()

// 한번만 사용할 경우
locationManager.requestLocation()

// 계속 정보 모니터링
locationManager.startUpdatingLocation()
```



### TableView

데이터를 리스트형태로 보여주는 오브젝트이다. 메일, 챗뷰로사용된다.
