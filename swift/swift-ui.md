# Swift UI

### SwiftUI cheat sheet

스위프트UI는 아직까지 안정적이지 않고 대 격변기를 맞이하고 있기에 버그가 발생할 확률이 높다. 그러므로 배포단계의 앱같은 경우는 아직까지 UIKit을 사용하는 것이 여러므로 좋다.

```swift
// Extract subView로 구조체로 분리가능.

ZStack {}
VStack {}
HStack {}

Spacer()

Image("Background")
.resizable()
.edgesIgnoringSageArea(.all)
.aspectRatio(1, contentMode: .fit)

Button(action: {
    self.leftDiceNumber = Int.random(in: 1...6)
    self.rightDiceNumber = Int.random(in: 1...6)
}) {
    Text("Roll")
        .font(.system(size: 50))
        .fontWeight(.heavy)
        .foregroundColor(.white)
        .padding(.horizontal)
}
.background(.red)

NavigationView {
    List(posts) { post in
        Text(post.title)
    }
    .navigationTitle("H4XOR NEWS")
}
```



### @State

구조체에서 self 접근하면 변경 불가능하지만 이 property wrapper를 사용하면 SwiftUI에서 var변수에 접근하여 값을 업데이트할 수 있다. 값을 변경할 때마다 해당 구조체를 다시 생성한다.

SwiftUI는 이렇게 접근가능한 상태의 리스트를 가지고 계속 모니터링하여 화면에 업데이트하는 작동방식을 가졌다.

###

### Identifiable Protocol

리스트가 아이디에 따른 순서를 인식할 수 있게 하는 프로토콜이다.

### UIViewRepresntable Protocal

스위프트 UI에서 UIKit을 사용할 수 있다.

### WebView

uri이 가지고 있는 컨텐츠를 화면에 표현해주는 방법, 스위프트 UI에는 웹뷰 기능이 없었기에 UIKit에서 기능을 빌려와서 사용할 수 있다.

```swift
struct WebView: UIViewRepresentable {
    
    let urlString: String?
    
    func makeUIView(context: Context) -> WKWebView {
	       // WKWebView is UIKit comoponent
				return WKWebView()
    }
    
    func updateUIView(_ uiView: WKWebView, context: Context) {
        if let safeString = urlString {
            if let url = URL(string: safeString) {
                let request = URLRequest(url: url)
                uiView.load(request)
            }
        }
    }
}
```
