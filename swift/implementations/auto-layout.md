# auto Layout

각기 다른 스크린 해상도에 알맞게 위치나 방향을 조절하여 디자인하는 규칙을 정의합니다.



### Pin and Align Constraints

* top, left, right, bottom 상대적 위치를 결정할 수 있습니다.
* safe area .leading / .trailing / .top / .bottom / .relative to margin 기본적인 기능 배터리, 홈정보에 영향을 끼치지 않는 라인을 세이프 영역이라고 합니다. 이 세이프 영역을 기준으로 조절합니다.
*   superview .leading / .trailing / .top / .bottom / .relative to margin

    컴포넌트가 포함된 부모의 뷰를 기준으로 조절합니다.
*   alignment .vertical / .horizontal

    상대적인 위치가 아닌 스크린의 수직, 수평적 위치를 조절합니다.





### Size Constraints

* fit contents(디폴트), 텍스트 크기가 변경되면 그에 알맞게 크기가 결정됩니다.
* .width / .hight 사이즈가 고정되면 만약 컨텐츠 내용이 사이즈보다 클 경우 clip될 수 있기때문에 경고를 발생시킵니다. 이 경우 Relation(.maxWidth / .minWidth)으로 크기를 설정하여 컨텐츠 내용에 영향을 미치지 않도록 조정할 수 있습니다.





### StackView

서로다른 뷰 컨테이너를 묶어 alignment를 일치하도록 만듭니다.

* Distribution .Fill Equally / .spacing
* sub view의 alignment를 조절할 때 super view의 Contraints가 정의되어 있지 않을 경우 오류가 발생합니다.
* safe area 옵션을 선택할 수 없는 경우, 위치를 살짝 조절하거나 atrributes inspector에서 constaint 위치를 0으로 변경합니다.
