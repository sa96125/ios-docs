# Issue

*   메인 화면 타이틀이 한글자씩 나타나도록하는 애니메이션을 구현하였다. 아래의 코드를 빌드시 0.1초 딜레이 시켰음에도 불구하고 변화가 보이지 않는다 왜 일까?

    ```swift
    titleLabel.text = ""
    let titleText = "Hell Voice"
    for letter in titleText {
        Timer.scheduledTimer(withTimeInterval: 0.1, repeats: false) { (timer) in
            self.titleLabel.text?.append(letter)
        }
    }
    ```

    > for문이 순회하는 시간이 엄청 빠르기에 거의 모든 문자가 동시에 시작하게되어 각 타이머가 끝나는 시점이 거의 동시에 완료되기 때문이다. 각 문자의 인덱스를 추출하여 딜레이 시간에 곱하여 시간을 조절하여 해결할 수 있다.



*   **\[boringssl] boringssl\_metrics\_log\_metric\_block\_invoke(153) Failed to log metrics** 메세지는 무엇을 의미할까?

    > 이 에러는 https 요청에 대한 API 응답을 받을 때 발생하였다. 문제의 원인이 시뮬레이터에서 앱을 실행하거나 API를 호출할 때 인터넷에 연결되지 않을 수도 있다는 답변을 받았다. 현재 프로젝트의 호환 운영체제 > 스키마 편집, OS\_ACTIVITY\_MODE : disable 환경 변수를 추가함으로서 해결할 수 있다. 하지만 이 방법은 NSLog() 중요한 메세지도 콘솔에서 사라지게 만들기에 완전한 비활성화는 결코 완전한 해결책이 될 수 없다. 두번째 방법은 특정 시뮬레이터의 특정 로그를 표시하지 않는 방법이다. `xcrun simctl spawn booted log config --subsystem com.apple.network --category boringssl --mode level:off` 중요하지 않은 메세지를 생략함으로서 해당 오류를 안보이게 할 수 있다. 시뮬레이터에서만 발생하는 오류로 명확한 이유를 찾을 때까지 해당 오류를 무시하면서 작업해도 될듯하다.



*   현재 위치 정보를 받아오는 코드를 작성하였다. 현재 클래스를 위임하였음에도 불구하고 빌드시 오류가 발생된다 왜 일까?

    ```swift
    // ERROR 'Delegate must respond to locationManager:didUpdateLocations:'
    locationManager.requestWhenInUseAuthorization()
    locationManager.requestLocation()
    locationManager.delegate = self
    ```

    > .requestLocation() 메서드를 호출하면 위치값을 얻어 locationManager(_:didUpdateLocations:) 를 즉시 호출하는 함수로 위의 코드에서는 locationManager(_:didUpdateLocations:)을 호출할 수 있게 하는 위임이 늦게 할당되었기 때문에 발생하였다. 따라서 둘의 순서를 바꿔주면 문제는 해결된다.



*   #### nib must contain exactly one top level object which must be a UITableViewCell instance'

    Cell.xib 파일 안에 한개이상의 뷰가 있어서 발생하는 에러, TableCell 외의 뷰는 삭제함으로서 에러 해결가능.



*   #### TableView cell bug.

    dequeueReusableCell을 사용하면 cell가 화면에서 사라지면 없어진 셀의 옵션을 그대로 데이터와 함께 재사용된다. 그렇다고 UITableViewCell을 쓸수 없는 게 UITableViewCell로 생성한 셀은 화면에서 사라지면 메모리에서 해제되고 다시화면에 보이면 새로운 셀을 생성하기 때문에 셀에 적용한 옵션이 사라진다. 따라서 셀과 셀의 특성을 연결하지 않고 데이터와 셀의 특징을 연결하여 사용하여 이 문제를 해결해야한다.



*   **\[Assert] UINavigationBar decoded as unlocked for UINavigationController, or navigationBar delegate set up incorrectly. Inconsistent configuration may cause problems.**

    ios16 업데이트 후 발생하는 이슈.



*   **iOS 13에서 Navigation controller의 bar tint를 바꿔도 navigation bar 색이 변하지 않는 문제**

    코드로 틴트를 변경하여 문제 해결



*   #### 키보드 뜨면 입력창이 가려지는 문제

    각각의 디바이스가 가진 키보드 디자인이 달라 일일히 하드코딩해야할까? nope IQKeyboardManager 라이브러리를 사용해보자.



*   #### Main.storyboard에 포함된 ViewController에서 assistant 코드파일이 나오지 않을 때,

    보통 자동으로 추적하지만 별로도 추가한 경우에는 StoryBoard에 추가한 viewController의 클래스네임과 컨트롤러 파일의 이름이 같도록 수정한다.



*   #### UISearchDisplayController is unavailable when deploying to iOS 13.0

    스토리보드에 있는데 SearchDisplayController를 제거한다.



* #### According to the [release notes for Xcode 14b3](https://developer.apple.com/documentation/xcode-release-notes/xcode-14-release-notes), the diagram view has been removed
