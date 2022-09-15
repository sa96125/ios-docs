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

cocoapods에서 필요한 기능을 검색해서 사용할 수 있다.

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
```

