# Tips

### Retrieve Stackoverflow

\[ Do ] \[ Language ] \[ Flatform ]



### Initial View Controller

메인 스토리보드에서 화살표로 조정하거나 에트리뷰트 인스트럭터에서 체크하여 설정



### Navigation Stack

editor > embeded-in > Navagatopm controller

세그먼트를 설정하여 화면의 순서를 설정할 수 있다.

컨트롤러의 컴포넌트에서 설정할 경우 액션에 따라 화면이 이동하지만

컨트롤러사이에 설정한 경우 아이덴티파이 즉 이름을 입력해서 코드로 로직을 입력해줘야한다.

따라서 꼭 이름을 설정한다.



### Third Party Labaries(Feat. [cocoapods.org](http://cocoapods.org))

cocoapods에서 필요한 기능을 검색해서 사용할 수 있다. 여러 패키지 매니저가 있다. 특히나 Swift package manager같은 경우 애플에서 구현한 의존성 관리 툴이다. 하지만! 다양한 써드파티라이브러리를 살펴보면 pod는 지원하지만 SPM을 지원하지 않는 경우가 허다하여 사용할 수 있는 라이브러리가 제한적이다.

```swift
// 설치방법
sudo gem install cocoapods

// master directory
pod setup --verbose

pod --version

// xcworkspace 변환
// 1. 디렉토리 이동
// 2. pod init
// 3. open podfile(ruby base)
// 4. set minimum IOS version & add pod

platform :ios, '9.0'

target 'Flash Chat iOS13' do
  use_frameworks!

  # Pods for Flash Chat iOS13
  
  pod 'CLTypingLabel'

end

// 5. pod install
// 6. xcworkspace 실행
// 7. 에러뜨면 깃험 문서에서 IOS 호환 버전 확인 후 재설치

platform :ios, '9.0'

target 'Flash Chat iOS13' do
  use_frameworks!

  # Pods for Flash Chat iOS13
  
  pod 'CLTypingLabel', '~ 0.4.0'

end


// 8. 일일히 깃헙에서 버전 업데이트 할 필요없이 설치된 프레임워크를 업데이트 할 수 있다.
pod update

```



### Constant File

String 데이터를 사용할 때 주의할 점은 오타로 인해 발생하는 오류를 Xcode는 대처해주지 않는다는 점이다. 따라서 항상 문자열을 사용해야하는 경우, constatant 파일에 기입하여 후에 발생될 수 있는 에러를 방지한다.
