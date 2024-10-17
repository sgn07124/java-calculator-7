# java-calculator-precourse

### 문자열 덧셈 계산기

---

## 📚 구현 기능 목록

---

### 📌 문자열 입력

- [ ] 사용자는 문자열을 입력한다.
    - 구분자와 양수로 구성된 문자열을 입력한다. 양수 → 실수 포함 → ex) 구분자가 . 일 경우: ``"1.2.3.4`` → 1.2, 3, 4 인지 1, 2, 3.4 인지 모호해짐 → 양의 정수로 풀이 진행
    - 커스텀 구분자로는 문자(공백 포함)를 허용한다.
- [ ] 사용자가 입력하는 값은 ``camp.nextstep.edu.missionutils.Console``의 ``readLine()``을 활용한다.

#### 🚫 예외 처리

- [x] 공백으로 시작한 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``" "``, ``" 1,2,3,4"``
- [x] 커스텀 구분자의 형식이 "//"로 시작하나, "\n"이 존재하지 않는 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``"//;1;2;3"``
- [x] 커스텀 구분자의 형식에서 "//"와 "\n"의 사이에 커스텀 구분자 문자가 2개 이상 입력된 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``"//;%\n1;2;3"``
- [x] 입력된 문자열의 숫자가 들어가야 하는 부분에 숫자 이외의 문자(공백 포함)가 포함된 경우 ``IllegalArgumentException``을 발생시킨다.
  ex) ``"1,a,3"``, ``"1,2 ,3"``
    - [x] 입력된 문자열의 숫자 자리(양수)에 음수가 들어간 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``"1,-2,3"``
- [x] 구분자 없이 숫자만 연속으로 입력한 경우 ``IllegalArgumentException``을 발생시킨다.(입출력 요구사항에 구분자와 양수로 구성된 문자열: 숫자만 단독으로 입력 불가)
  ex) ``"123"``
- [x] 커스텀 구분자를 지정하지 않고 기본 구분자 이외의 다른 문자가 포함된 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``"1|2|3"``
- [x] 입력된 문자열에 숫자 0이 단독으로 포함된 경우(0이 연속으로 입력된 경우도 포함) ``IllegalArgumentException``을 발생시킨다. ex) ``"1,0,3"``, ``"1,000,3"``
- [x] 기본 구분자와 커스텀 구분자가 연속으로 사용된 경우 ``IllegalArgumentException``을 발생시킨다. ex) ``"//;\n1;;2;3"``

---

### 📌 문자열 처리

- [ ] 입력 문자열이 빈 문자열("")일 경우, 숫자가 없으므로 결과는 0으로 처리된다. ex) ``"" → 0``
- [ ] 구분자를 사용하여 입력한 경우, 쉼표(,) 또는 콜론(:)을 기준으로 문자열을 분리한 후, 각 요소는 숫자로 변환하여 반환한다.
  ex) ``"1,2,3" → [1, 2, 3]``, ``"1:2:3" → [1, 2, 3]``
- [ ] 커스텀 구분자를 사용하여 입력한 경우, "//"와 "\n" 사이에 위치한 구분자를 사용하여 "\n"뒤의 문자열을 분리한다.
  ex) ``"//;\n1;2;3" → [1, 2, 3]``, ``"// \n1 2 3 4" → [1, 2, 3, 4]``

---

### 📌 반환된 문자열을 정수로 변환

- [ ] 반환된 문자열 리스트에서 구분자를 기준으로 분리된 각 문자열을 정수형으로 변환하여 리스트로 반환한다.
  ex) ``["1", "2", "3"](String형 리스트) → [1, 2, 3](정수형 리스트) ``

---

### 📌 숫자 합산

- [ ] 반환된 정수형 리스트 내의 숫자들을 합산하여 최종 결과를 반환한다.

#### 🚫 예외 처리

- [ ] 합산을 수행하기 전, 반환된 리스트의 숫자(입력한 숫자)가 Integer 범위를 초과하면 ``IllegalArgumentException``을 발생시킨다.
- [ ] 합산된 결과가 Integer 범위를 초과하면 ``IllegalArgumentException``을 발생시킨다.

```text
덧셈할 문자열을 입력해 주세요.
1,2:3
결과 : 6
```