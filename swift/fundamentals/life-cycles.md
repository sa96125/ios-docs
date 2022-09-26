# life cycles

### ViewController life cycle

super 필수적으로 입력한다. 운영체제가 순서대로 호출하는 메서드 모음

* 화면이 사용자에게 보이는 시점 1, 2, 3
* 화면이 사라질려고 할 때 4
* 화면이 완전히 사라지면 5, 조금이라도 ViewController에 일부분이 보이면 동작하지 않는다.

1.  viewDidLoad()

    화면이 생성되었을 때 오직 한번 호출한다. 모든 UI 컴포넌트, 뷰와 관련된 오브젝트를 연동하고 접근할 수 있는 메서드 영역이다. 즉 이 영역에서 모든 UI과 관련된 태그 셋팅을 해야 이후의 라이프 사이클에서 사용할 수 있다. 현재 뷰의 로드된 직후를 의미한다. 만약 다른 뷰 컨트롤러를 조작한다면 에러가 날 수 있으니 이에 대한 부분은 viewWillApear에서 처리한다.
2.  viewWillApear()

    화면이 사용자에게 보이기 직전에 호출, 즉 스크린에 아무것도 보이지 않는 시간대에 호출, 화면이 구성하고 있는 요소들 중에 특정 부분을 보여 줄지 말지에 대한 결정을 내릴 때
3.  viewDidApear()

    스크린에 View가 보이는 시간 영역으로 타이머를 실행한다던지 사용자가 보는 즉시 해야할 일들을 구현할 수 있다.
4.  viewWillDisapear()

    화면에서 사라지기 직전에 호출
5.  viewDidDisapear()

    화면이 사라지고 난 후 호출, user Can’t see! 화면서에 사라진다는 의미가 삭제, 메모리 할당해제를 의미하는 것이 아니다.



### Application Lifecycle

운영체제는 CPU time, Memory와 같은 한정된 리소스를 할당할지 결정한다. 그렇다면 과연 이에 대한 우선순위는 어떨까? 여러앱을 교차적으로 사용할 때, 내가 입력하고 있는 데이터가 저장되고 있어야한다면 앱이 백그라운드로 들어가는 시점의 라이프사이클에 저장 작업이 수행 될 것이다.

프로젝트를 생성할 때, AppDelegate와 SceneDelegate 함수를 보았을 것이다. 앱 사이클 메서드가 위치하는 곳이 바로 이 파일들이다. 그렇다면 이 둘의 차이점은 뭘까? xcode 11전에는 AppDelegate 파일만 존재했었다. IOS13 이후 iPadOS와 같이 지금은 다양한 윈도우에서 여러 앱이 동작할 수 있게 되었는데, 각각의 윈도우 즉 Scene의 라이프사이클을 관리할 필요성이 생겼고 이를 위해 SceneDelegate가 생기게 되었다. 공통적인 이벤트는 AppDelegate에서 작동하고 윈도우를 위한 개별 콜백은 SceneDelegate에서 호출한다.

여러개의 ViewController는 하나의 Scene에 여러개의 Scene은 하나의 App에 있다. 이 모든 요소는 라이프사이클 메서드를 가지며 override해서 사용할 수 있게 된다.

```swift
// AppDelegate Life cycle methods
// 앱 실행하면 트리거되는 클래스, didFinishLaunchingWithOptions로 인해 런칭을 끝내면 웰컴 스크린을 볼 수 있다. 즉, func application에 포함된 함수가 정상적으로 실행되었다는 것을 의미합니다.
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
	        
	// 현재 함수명 출력, 언제???
	// 가장 먼저 호출,
	print(#function)

  return true
}

// SceneDelegate Life cycle methods
func sceneDidDisconnect(_ scene: UIScene) {
        // Called as the scene is being released by the system.
        // This occurs shortly after the scene enters the background, or when its session is discarded.
        // Release any resources associated with this scene that can be re-created the next time the scene connects.
        // The scene may re-connect later, as its session was not neccessarily discarded (see `application:didDiscardSceneSessions` instead).
    }

func sceneDidBecomeActive(_ scene: UIScene) {
    // Called when the scene has moved from an inactive state to an active state.
    // Use this method to restart any tasks that were paused (or not yet started) when the scene was inactive.
}

func sceneWillResignActive(_ scene: UIScene) {
    // Called when the scene will move from an active state to an inactive state.
    // This may occur due to temporary interruptions (ex. an incoming phone call).
}

func sceneWillEnterForeground(_ scene: UIScene) {
    // Called as the scene transitions from the background to the foreground.
    // Use this method to undo the changes made on entering the background.
}

func sceneDidEnterBackground(_ scene: UIScene) {
    // Called as the scene transitions from the foreground to the background.
    // Use this method to save data, release shared resources, and store enough scene-specific state information
    // to restore the scene back to its current state.
}
```



### Main Thread

실행 중인 앱을 디버그 콘솔에서 일시정지하면 CPU, Memory, Network, Threads등 실제 사용하고 있는 자원들의 상태를 확인할 수 있다. 구체적으로 살펴보면 우리의 앱은 하나 이상의 Thread를 사용하고 있는 것을 확인 할 수 있다.

실제 앱이 동작하는 동안 데이터를 가져와서 화면을 업데이트해야하는데, 네트워크 작업을 수행하고 있다면 데이터를 받아오는 동안 화면에서 수행할 수 있는 작업, 즉 사용자 인터렉션에 불편함을 가져올 수 있다. 따라서 이러한 요청은 백그라운드에서 다른 Thread에게 위임하고 실질적으로 보이는 화면에는 영향이 없어야한다. 이러한 책임을 맡고 있는 것이 Main Thread이다.

```swift
// Despatchqueue.main.async는 다른 쓰레드들에게 일을 할당 할 수 있는 관리자이다. 
// 네트워크 작업으로 백그라운드에서 실행되는 코드 중 일부를 메인에서 처리할 수 있다.
{
    loadItems()
    
    DispatchQueue.main.async {
        searchBar.resignFirstResponder()
    }
}
```

