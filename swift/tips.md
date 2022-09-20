# Tips

### Git

```swift
// git 설치
git init

// 히든 파일까지 볼 수 있다.
ls -a

// working directory에 있는 파일을 보여주며
// 커밋이 가능한 상태인지 아닌지를 나타낸다.
git status

// into Staging area
// 커밋할 파일들을 준비해놓은 공간, 파일 추적의 시작점
git add 
git add .

// undo 전체 파일 in Staging area
git rm --cached -r .

// into Local Respository
// 나중에 프로젝트 구현 일부분은 추적하거나,
// 동료와 원할한 협업을 하기위해서는 메세지를 잘 적어놔야한다.
git commit -m "메세지"

// 커밋 완료된 파일 확인
git log

//  modified가 있을 경우, 세부사항 확인
git diff <파일네임>

// 수정전 레포에 저장되었던 파일로 다시 되돌리고 싶을 때,
git checkout <파일네임>

// remote repository to Github
// 내가 만든 커밋들을 전송하겠다.
git remote add origin <URL>

// into Remote Respository
// host commited resources
git push -u origin main

// clone project to local
git clone <URL>

// 새로운 브랜치 생성
git branch <new branch name>

// 확인(항상 git을 사용하기 전에 확인하는 습관)
git branch

// 변경
git checkout <branch name>

// 메인 브랜치에서 병합
git merge <branch name>

//
```



### .gitignore

secretkey와 같은 민감한 정보를 담은 파일을 담지 않도록 리스트를 작성하는 파일, git/gitignore/swift 샘플을 다운 받아 사용할 수 있다.

```swift
// 히든 파일로 만들기
touch .gitignore

// rule
.DS_Store
secrets.txt
#PodFile
*.txt
```



### Fork vs Clone

클론과 달리 Git 포크 작업은 대상 리포지토리의 완전히 새로운 복사본을 생성한다. 새로운 복사본에서 Pull Request를 요청하면 승인에 따라 본 프로젝트에 병합된다. Git 포크 또는 클론 중에서 선택하는 것은 코드베이스에 대해 얼마나 많은 제어가 필요한지와 다른 기여자와 얼마나 협력적으로 작업하고 싶은지에 달려 있. 분산 및 협업 개발 워크플로가 원활하게 실행되도록 현명하게 선택하여 작업한다.



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



### Swift Package Manager 사용하는 방법

Pod 패키지랑 사용할 수 잇는데, Pod install 한다음에 SPM를 설치하길 바란다. SPM은 cocoapod위에서 동작하지만 그 반대는 작동하지 않는다.

1. PROJECT Main 파일
2. Package Dependecies
3. \+버튼
4. 라이브러리 URL 주소 입력
5. 설치



### Command Line

운영체제가 피스타치오 넛이라고 예를 들면, 커널은 하드웨어와의 인터페이스 할 수 있는 실제 프로그램이라 말할 수 있다. 즉 core of Operating system이라 할 수 있다. 이를 실제 알맹이라 여길 수 있을 것이다. 반면에 껍질은 유저인터페이스라 생각할 수 있는데 껍질을 벗겨야 알맹이를 먹을 수 잇는 것처럼, 컴퓨팅에서는 Bash shell을 이용하여 커널과 상호작용할 수 있는 것이라 생각할 수 있다. Bash는 사람의 이름을 딴 Bourne Again Shell의 줄임말이다. 유닉스 시스템의 커맨드 라인 인터프리터로 리눅스, 맥OS, 유닉스환경에서 사용된다.

우리가 매일 사용하는 Finder은 Graphical user interface가 있고 command line interface처럼 명령어로 파일에 접근하거나 읽을 수 있는 방법이 존재한다. 개발자로서 그래픽적인 인터페이스의 절차를 거치지않고 툴을 잘 다루는 능력, 더 빠르게 동작할 수 있는 방법, 유연하게 대처할 수 잇는 방법에 숙달될 필요가 있다. 더 파워풀하고 더 컨트롤적으로 동작할 수 있지만 위험한 시도가 될 수도 있으니 항상 현재 경로를 유심히 보고 명령어를 사용해야한다.

```swift
ls
cd <dirName>/, ~, ..
mkdir <dirName>
rm -r <dirName>

// 커서 이동
alt + click 

// 커서 처음, 끝, 삭제
ctr + E, A, U

// 텍스트 파일 만들고 열기, 삭제
touch textFileName.txt
open textFileName.txt
open -a VScode textFileName.txt
rm textFileName.txt
rm *
```
