# Swift UI

### Swift UI

2019 wwdc에서 공개된 선언형 스위프트 코드 UI 프레임워크다. 더 쉽게 IOS개발을 돕기위해 만들어졌다. 메인 목표 중 하나는 IOS APP의 레이아웃을 drag on drop 하여 더 쉽게 만들 수 있다는 점이다. Easy Layouts VHZ stack (vertical, horizontal, z-axis stack), Highly reusable, Live on Screen 그리고 Cross Apple Platform Interface와 같은 특징을 가졌다.

최소 macOS V 10.15, Xcode 11.0에서 사용할 수 있고 IOS 13, IPhone 6s, Ipad Air2와 같은 기기에서 동작한다. 따라서 이전 버전을 사용하는 오래된 기기에서는 스위프트UI로 만들어진 앱을 다운로드할 수 없다.

```swift
struct ContentView: View {
    var body: some View {
        ZStack{
            Color.blue
                .edgesIgnoringSafeArea(/*@START_MENU_TOKEN@*/.all/*@END_MENU_TOKEN@*/)
            VStack {
                Text("Hello, world!")
                    .font(.system(size: 40))
                    .fontWeight(.bold)
                    .foregroundColor(Color.white)
                Image("diamond")
										.resizable()
										.aspectRatio(contentMode: .fit)
                    .frame(width: 200, height: 200, alignment: .center)
            }
        }
    }
}

// Device Model 변경
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView().previewDevice(PreviewDevice(rawValue:"iPhone SE"))
    }
}
```



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
