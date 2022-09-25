# debugging

print는 단지 값을 인쇄하는 역할이지만 assertion을 사용하면 프로그램을 종료시킬 수 있어 디버깅에 적합한 명령어다. 런타임에 발생하는 검사로 필수 조건을 충족하였는지 확인할 때 사용할 수 있.

```swift
// 성공 조건, 실패 문구를 기입
// age < 0 종료
assert(age >= 0, "A person's age can't be less than zero.")

// 이미 실패 조건일 경우, 강제 종료 가능
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```

{% hint style="info" %}
추가적으로 Xcode 에서 Break Point 지정 시, 콘솔 창에 print varName을 쳐서 중단 지점에서의 변수 값을 확인할 수 있다. 중단 점 이전과 이후를 가시적으로 비교할 수 있어 좀 더 세련된 방법이다.
{% endhint %}
