---
description: >-
  코드가 길어질수록 잠재오류의 발생률이 올라간다는 것을 기억하자. 읽기 좋은 코드 명확하게 하기위해 코드를 길게 작성하는 것 또한 같은
  맥락이다. 짧게 작성하면서 읽기 좋은 코드를 위한 고민은 지속적으로 해야할 것이다.
---

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



### No Copy, Create Super class

부모 클래스에서는 자식 클래스에 대한 정보가 전혀 없기 때문에 구체적인 뷰 컨트롤러에 대한 사항은 구현할 수 없다. 하지만 자식이 내가 가진 환경을 잘 사용할 수 있도록 함수를 분리해 놓아야한다. 공통적인 모듈을 묶어 놓고 해당기능을 사용해야한다면 override를 통해 구현한다.
