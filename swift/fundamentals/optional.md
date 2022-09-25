# optional

값이 있을 수도 없을 수도 있는 변수의 타입을 의미한다. nil을 할당하면 기존 값을 없애는 것과 같은 행동이고 결국 실행해 다다랐을 때 런타임 오류가 발생한다. 옵셔널로 할당 된 값은 값이 존재할 때의 처리와 nil일 경우의 처리를 해야한다. 결, nil crushing으로 인한 런타임 오류가 유일한 이슈 사항이니 주의가 필요하.

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



###
