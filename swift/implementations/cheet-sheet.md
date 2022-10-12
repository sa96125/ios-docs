# cheet sheet

#### 메인스레드 늦게 실행하기

```swift
DispatchQueue.main.asyncAfter(deadline: .now() + 0.25) {
    // code
}
```



#### 타입 변환하기

```swift
let pi: Double = 3.14159265

String(format: "%.f", pi)
// output: 3

String(format: "%.2f", pi)
// output: 3.14

String(format: "%.3f", pi)
// output: 3.142

```
