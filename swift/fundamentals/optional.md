# optional

값의 불확실성을 컨트롤하는 방법입니다. nil은 값이 없음을 의미하며 nil을 할당하게 되면 기존 값을 삭제하는 행위와 같습니다. Swift에서는 런타임 중에 nil을 발견하면 오류를 발생시킵니다. 따라서 optional로 선언되어 있다면 nil crushing으로 인한 런타임 오류가 발생하지 않도록 추가적인 처리방법이 항상 고려해야합니다.



1.  Force Unwrapping never gonna be NIL

    ```swift
    // 값이 할당되지 않은 옵셔널을 경우 Nil만 가지고 있어 런타임 오류가 발생한다. 
    optional!
    ```


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
    </strong>    let text:String = safeOptional
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

else 를 사용하지 않는 optional binding으로 항상 nil을 피하는 것은 지양해야합니다.&#x20;

예를 들어, 숫자를 문자로 변환하면 항상 문자가 되지만 문자를 숫자로 변형했을 때, 이는 항상 성립하지 않습니다. “+”를 숫자로 변경한 후 사칙연산이 불가능하기 때문입니다.

따라서, 실수를 미연에 방지하기 위해 optional binding else 구문을 사용하거나 gaurd 구문을 사용하여 에러를 색출할 수 있어야 합니다.
{% endhint %}

