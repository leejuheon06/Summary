**:closed_book:리스트(List)**  
- 여러 개의 값을 순서대로 저장하는 자료형  
- 순서가 의미가 있음→ 인덱싱 가능, 특정 위치의 요소를 가져올 수 있음  
- 변경 가능 (Mutable) → 값 추가, 수정, 삭제 가능  
- 다양한 데이터 저장 가능 → 정수, 문자열, 리스트 등  
  :book: `append(값)`: 리스트 끝에 요소 추가  
  :book: `insert(인덱스, 값)`: 특정 위치에 요소 추가  
  :book: `extend(리스트)`: 여러 개의 요소 추가  
  :book: `del 리스트[인덱스]`: 특정 요소 삭제  
  :book: `remove(값)`: 특정 값을 찾아 삭제  
  :book: `pop(인덱스)`: 특정 위치의 요소를 꺼내면서 삭제  

**:closed_book: 튜플(Tuple)**  
- 한 번 생성하면 변경할 수 없는(Immutable) 자료형  
- 변경 불가능 (Immutable) → 값을 수정하거나 추가, 삭제할 수 없음  
- 연산 속도가 빠름  

**:closed_book: 딕셔너리(Dictionary)**  
- 키(Key)와 값(Value)의 쌍으로 이루어진 자료형  
- Key로 데이터 접근 → 따라서 Key는 유일해야 함  
- Key는 변경 불가능한 자료형만 가능  
- 값은 변경 가능 (Mutable) → 값 추가, 수정, 삭제 가능  
  :book: `del/ .pop()` : 딕셔너리 값 삭제  
  :book: `dict[key값]/ .get(key값)` : 딕셔너리 값 가져오기  
