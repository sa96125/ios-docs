# Clean code

### MARK

파일안에 작성된 코드들을 섹션별로 나눌 수 있다. 또한 커스텀 코드 스니펫을 만들어 활용하기도 한다.

```swift
// Devide section 
//MARK: - UITextFeildDelegate

// create code snnipet
1. //MARK: - 
2. 오른쪽 클릭
3. create code snnipet
```



### Constant File

String 데이터를 사용할 때 주의할 점은 오타로 인해 발생하는 오를 Xcode는 대처해주지 않는다는 점이다. 따라서 항상 문자열을 사용해야하는 경우, constatant 파일에 기입하여 후에 발생될 수 있는 에러를 방지한다.
