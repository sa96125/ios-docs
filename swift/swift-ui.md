# SwiftUI

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

HVZStack (
    alignment: .center / .leading
)
{}

Spacer()


Text(String) 
.font(.largeTitle)
.font(.title)
.foregroundColor(.green)
.foregroundColor(.orange)
.padding(.all)
.lineLimit(nil)


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


Text(String) 
.font(.largeTitle)
.font(.title)
.foregroundColor(.green)
.foregroundColor(.orange)
.padding(.all)
.lineLimit(nil)


Image(””)
.resizable()
.aspectRatio(contentMode: .fit)
.clipShape(Circle())
.cornerRadius(20)
.padding(.all)
.frame(width: 100, height:100)


.onTapGesture { 
    withAnimation {
        self.zoomed.toggle()
    }
}


List(items, id: \.name) { item in
    Text(item.name)
} 

or

List(item) { 
    ForEach(tasks) { task in 
    }
}


NavigationView {
    .navigationBarTitle(String, displayMode: .inline)
    .navigationLink(destination:newView) {
        selectedView
    }
}

newView
.navigationBarTitle()


Button(action: func) {
    Text(String)
}


Toggle(isOn: .constant(true)) {
    Text(String)
}


TextField($name, placeholder: Text(String))
```



### 동작 과정

user interaction → action → mutate → state → update → view → render



### @State

구조체에서 self 접근하면 변경 불가능하지만 이 property wrapper를 사용하면 SwiftUI에서 var변수에 접근하여 값을 업데이트할 수 있다. 값을 변경할 때마다 해당 구조체를 다시 생성한다.

SwiftUI는 이렇게 접근가능한 상태의 리스트를 가지고 계속 모니터링하여 화면에 업데이트하는 작동방식을 가졌다.

@State private var zoomed: Bool = false

view → viewModel (unidirectial binding)

struct mutating을 대신하여 값을 수정하기 위함. swiftUI에서 상태를 사용하기 위해서 꼭 이 키워드를 사용한다. Bool값의 경우 .toggle()함 수 사용.

state가 변경되면 리 렌더링, 즉 화면을 다시 그린다.



### @Binding

@Binding $zoomed

view ↔ viewModel (bidirectional

같은 클래스안에 선언된 @state 변수를 변경해야한다면 $를 사용하여 변경되는 상태를 즉시 화면에 업데이트한다

만약 다른 클래스,구조체에서 @state 변수를 변경해야한다면 어떻게 해야할까? 심지어 private로 설정 되어 있으면 새롭게 선언해야할까? No, @Binding 으로 값을 제외하고 선언해주고 $로 값을 넘겨준다.



### ObsevableObject Protocol

@Published var

상태 및 비지니스 로직을 분리 시킬 수 있다. 그리고 이 오브젝트를 호출하기 위해서는 @observedObject로 선언한다.



### @enbironmentObject

global state , observedObject의 prop Drilling를 해결하기 위한 방법

1. sceneDelegate 파일에서 ContenView.environmentObject( view ) 로 변경
2. 선언된 @observedObject 를 @enbironmentObject로 바꾼다.



### Identifiable Protocol

리스트가 아이디에 따른 순서를 인식할 수 있게 하는 프로토콜이다.

:Identifiable

let id = UUID() 필수



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



### Custom Font

xcode13에서 plist파일이 제거 되었기때문에 targets > Info > Custom iOS Target Properties에서 Fonts provided by application를 추가한 후 디렉토리에 추가된 Info파일에서 <폰트이름>.ttf파일을 추가한다.





### Canvas

실제 배포에서 사용되는 에셋과 실제 개발환경에서 사용할 에셋을 구별해놓았다. preview Contet에 넣어 사용한다.



### 필

List

.toobar {

ToolbarItem

}

List > ForEach

.onDelete(perform: deleteItems)

Form {

Section(header: Text(String).font(.body)) {

TextField(String, text: String)

}

Section(header: Text(String).font(.body)) {

ForEach(items, id:\\.name) item in {

HStack {

Text(item.imageURL)

Text([item.name](http://item.name))

}

}

}

Section(header: Text(string), footer: Text(string)) {

Picker(””, selection: String) {

Text(String).tag(String)

Text(String).tag(String)

Text(String).tag(String)

}

.pickerStyle(SegmentedPickerStyle())

}

}

// 내장 이미지

Image(systemName: “checkmark”)

// 세부조정

.padding(EdgeInsets(top: leading: bottom: trailing))

// 모달

.sheet(isPresented: Bool) {

view()

}

* DateFormatter 처럼 특성을 변경하는 것은 외부로 빼서 설정하고 리턴해서 코드를 줄인다.
* @FetchRequest
* combine은 이벤트를 호출하거나, 구독자에게 데이터를 넘겨주기 위함.
