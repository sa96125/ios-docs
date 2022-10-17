# cheet sheet

### Play Audio

<figure><img src="../../.gitbook/assets/avfoundation.png" alt=""><figcaption></figcaption></figure>

```swift
import AVFoundation

var player: AVAudioPlayer!

func playSound() {

	// bundle is resources in the Disk
	guard let url = Bundle.main.url(forResouce: "", withExtension: "wav") { return }
	
	player = try! AVAudioPlayer(contentsOf: url)
	
	player.play()

}
```





### Timer

```swift
// 여러 타이머가 계속 생성되지 않도록 주의합니다.
var timer = Timer()

func startBtnPressed() {
	timer.invalidate()
	
	Timer.scheduledTimer(
		timeInterval: 1.0,
		target: self, 
		selector: #selector(updateTimer), 
		userInfo:nil, 
		repeats: true
	)
}

@objc func updateTimer() {
	if secondsRemaining > 0 {
		print("\\(secondsRemaining) seconds.")
		secondsRemaining -= 1
	} else {
		timer.invalidate()
	}
}
```





### Progress Percentage

```swift
// secondsPassed, totalTime는 Float type 이여야합니다.
percentageProgress = secondsPassed / totalTime
```





### Execute thread

```swift
DispatchQueue.main.async {
    // code
}

DispatchQueue.main.asyncAfter(deadline: .now() + 0.25) {
    // code
}
```





### type conversion

```swift
let pi: Double = 3.14159265

String(format: "%.f", pi)
// output: 3

String(format: "%.2f", pi)
// output: 3.14

String(format: "%.3f", pi)
// output: 3.142

```





### PreferenceKey

부모와 자식간에 공유하는 데이터를 key로 설정하여 자식에서도 부모의 데이터를 변경할 수 있는 방법입니다.

1. define prefereceKey + extension View
   1. static var defaultValue: Type
   2. static func reduce(value: nextValue)
2.  update prefereceKey(자식)

    .preferemce(key:, value:)
3.  perform prefereceKey(부모)

    .onPreferenceChange(key, perform:)





### GeometryReader

실제 크기를 읽을 수 있습니다.

```swift
GeometryReader { g in 
    Rectangle()
        .overlay {
        Text("\\(g.size.width)")
        }
}
```





### @ViewBuilder

View를 리턴하는 클로저를 만들 수 있습니다. 코드 블럭안에 여러 뷰를 컨트롤할 수 있는 로직을 작성 할 수 있다는 것이 특징입니다.



```swift
struct viewBuilderView<Content: View> : some View {

	private var content: Content

	init(@ViewBuilder content: () → Content) {
		self.content = content()
	}

	var body() : some View {
		content
	}
}

viewBuilderView {
	// 최상단 View를 묶지않아도 오류가 나지 않는다.
	VStack {
		// views
	}
	
	VStack {
		// views
	}
}
```



