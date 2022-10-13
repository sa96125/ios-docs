# optional

값이 있을 수도 없을 수도 있는 불확실성을 컨트롤하는 방법입니다. nil은 값이 없음을 의미하며 nil을 할당하면 기존 값을 지우는 것과 같습니다. 런타임에서 nil을 발견하면 오류를 발생시킵니다. 따라서  옵셔널 타입은 nil crushing으로 인한 런타임 오류가 발생하지 않도록 추가적인 처리방법이 항상 고려해야합니다.



1.  Force Unwrapping never gonna be NIL&#x20;

    ```swift
    // 값이 할당되지 않은 옵셔널을 경우 Nil만 가지고 있어 런타임 오류가 발생한다.
    optional!
    ```

    \

2.  Check for nil value

    ```swift
    if optional != nil {
    	optional!
    } else {
    	print("myOptional was found to be nil")
    }
    ```


3.  Optional Binding

    <pre class="language-swift"><code class="lang-swift">// !을 사용하지 않고 check nil
    <strong>if let safeOptional = myOptional {
    </strong>	let text:String = safeOptional
    } else {
    	print("myOptional was found to be nil")
    }</code></pre>


4.  Nil Coalescing Operator

    ```swift
    // more clear way
    optional ?? defaultValue
    ```


5.  Optional Chaining

    ```swift
    // : Struct? , : Class? 에서도 사용 가능
    // nil이 아니면 프로퍼티 또는 메서드 실행, nil이면 실행하지 않음.
    optoinal?.pro
    ```



{% hint style="warning" %}
#### Optional control

항상 nil만을 피하는 것이 올은 일은 아니다. 필요에따라 테스트가 필요하면 우리는 오류를 검출해내고 그에 대한 수정을 할 수 있어야한다. 예를 들어, 숫자를 문자열로 변환하면 항상 올바른 값이 나오지만 문자를 숫자로 변형했을 때는 이 부분이 성립하지 않는다. “+”를 숫자로 변경한 후 숫자끼리 계산하면 우리는 nil coalasing, optional binding을 사용하여 구체적인 에러를 색출 해낼 수 있을까? 아니다. if let number = Double(text)은 nil이 아니면 실행하고 nil이면 그냥 무시한다. 즉 중단하지 않는 다는 것이다.

이때 gaurd 키워드를 사용할 수 있다. nil일 경우, S해당 코드가 올바르게 동작하는지 판단하여 잘못되었을 시 해당 지점에서 발생한 에러를 즉시 색출해내고 fatalerror() 호출로 에러 발생에 대한 구체적인 메세지를 기입할 수 있다.
{% endhint %}

