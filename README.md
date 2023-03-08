Last Update: 2023-03-08

# 🪜 사다리 게임

- 미션 기간(1주차): 23-03-06 ~ 23-03-10 [5d]
- 2023 코드스쿼드 BE max에서 진행한 `사다리 게임`을 구현하는 미션

<br/>

## 🔍 진행 방식

- 미션은 단계별로 구성되어 있다. 한꺼번에 다 구현하려고 하지 말고 천천히 제대로 학습하며 단계별로 진행한다.
- 미션 2단계와 4단계는 이전 단계에 구현한 프로그램의 리팩토링이며, 미션 6단계는 선택사항이다.
- `제출방법`, `기능 요구사항`, `프로그래밍 요구사항`을 최대한 만족하기 위해 노력하며 미션을 진행한다.

<br/>

## 📤 제출 방법

- 미션 단계별로 PR을 생성하여 제출한다.
    - PR에 대한 자세한 내용은 [가이드](https://github.com/code-squad/codesquad-docs/blob/main/codereview/README.md)를 참고한다.
- PR 보낼때 다음 요구사항을 지킨다.
    - 미션의 각 단계를 마무리 한 후 PR을 보낸다.
    - PR 보낼때 label 설정: 각 단계별 라벨 (ex: step-1) 을 지정해서 보낸다.
    - 하루에 PR 1개만 보낸다.

<br/>

## 🖥 출력 예시

### 1단계

```
참여할 사람은 몇 명인가요?
3
최대 사다리 높이는 몇 개인가요?
5

|-| |
| |-|
|-|-|
| |-|
|-| |
```

### 3단계

```
참여할 사람 이름을 입력하세요. (이름은 쉼표(,)로 구분하세요)
pobi,honux,crong,jk

최대 사다리 높이는 몇 개인가요?
5

실행결과

  pobi  honux crong   jk
    |-----|     |-----|
    |     |-----|     |
    |-----|     |     |
    |     |-----|     |
    |-----|     |-----|
```

<br/>

## ⌨️ 프로그래밍 요구사항

- 메서드의 크기가 최대 10라인을 넘지 않도록 구현한다.
    - 메서드가 한 가지 일만 하도록 최대한 작게 만들어라.
- 들여쓰기(indent) depth를 2단계에서 1단계로 줄여라.
    - depth의 경우 if 문을 사용하는 경우 1단계의 depth가 증가한다. if 문 안에 while 문을 사용한다면 depth가 2단계가 된다.
- else를 사용하지 마라.
- 배열 대신 ArrayList와 Generic을 활용해 구현한다.
- 구현 순서를 고려하면서 프로그래밍한다.
- naming convention을 지키면서 프로그래밍한다.
- 로직을 구현하는 코드에 단위 테스트가 존재해야 한다. 단, UI 처리 로직(System.in, System.out)은 테스트에서 제외한다.

<br/>

---

<br/>

# 🧑🏻‍💻 미션 구현 Log

- 단계별 기능 요구사항 작성 후, 기능별로 commit
- 매일 오후 8시 이전 PR 진행

<br/>

## ✏️ 1단계 - 기본 기능 구현

### 💬 Brief 계획 및 회고

- 기능 요구사항을 만족하며, 프로그램의 전체적인 구조 설계를 진행함
- 고민했던 부분은 `사다리 구현` 부분인데, 로직이 마음에 들지 않았음
- 그룹 리뷰 시간에 다른 팀원의 코드를 보며 로직이 좋다고 느낀 부분이 있었음

> 1. 사다리 파츠 랜덤 생성을 TRUE/FALSE 기반으로 진행한 점
> 2. 짝수/홀수 기준으로 `|` or `-`을 생성할지 판단한 점
> 3. 전체 사다리를 생성하고 랜덤 값에 따라 사다리 `-` 부분 값을 replace한 점
> 4. 파츠 생성 확률을 설정한 점

### ✔️ 기능 요구사항

- [X] n명의 사람을 입력하는 기능
- [X] n개의 사다리 개수를 입력하는 기능
- [X] 랜덤으로 사다리를 생성하는 기능
    - 사다리가 있으면 `-` 표시, 없으면 `" "`(공백문자) 표시, 양옆에는 `|`로 표시
- [X] 사다리를 출력하는 기능

<br/>

## ✏️ 2단계 - 리팩토링 맛보기

### 💬 Brief 계획 및 회고

- 2단계 요구사항을 미리 보고 진행하지는 않았지만 1단계 구현할 때 대부분 요구사항을 만족하여 3단계를 바로 진행함

<br/>

## ✏️ 3단계 - 사다리 모양 개선

### 💬 Brief 계획 및 회고

- 추가로 요구하는 기능이 있어 기능 요구사항 정리 후 기능 구현을 진행함
- 사다리 구현할 때 라인이 겹치지 않도록 요구하는 부분이 있었는데,  
  해당 부분 로직을 어떻게 처리해야 할지 바로 떠오르지 않아서 시간이 오래 걸림
- 1단계 때 구현한 사다리 구현 로직이 깔끔하지 않아서 추가 로직이 들어가니 더욱 마음에 들지 않았음

> 💡요구사항 참고:
> - 사다리 타기가 정상적으로 동작하려면 라인이 겹치지 않도록 해야 한다.
> - |-----|-----| 모양과 같이 가로 라인이 겹치는 경우 어느 방향으로 이동할지 결정할 수 없다.

### ✔️ 기능 요구사항

#### 입력 기능

- [X] 플레이어의 이름을 입력하는 기능(최대 5자)
    - [X] 예외처리:
        - 이름이 6자 이상일 시
        - 쉼표로 구분하지 않았을 시
        - 1명 참여 시(2명 이상 참여 가능)
        - 이름 중복 시

#### 출력 기능

- [X] 사다리 출력 시 이름도 같이 출력하는 기능

#### 사다리 기능

- [X] 사다리 생성 시 라인이 겹치지 않도록 생성하는 기능

<br/>

## ✏️ 4단계 - 리팩토링2

### 💬 Brief 계획 및 회고

1. 앞 선 단계에서 계속 마음에 들지 않았던 사다리 구현 부분을 리팩토링 해보려고 함

| AS-IS | `LadderMaker` 클래스에서 사다리를 만들어 이중 List 형태로 보유                              |
|:------|:-------------------------------------------------------------------------|
| TO-BE | 사다리의 가로 한 줄을 의미하는 `Line` 클래스를 만들어 `LadderMaker`에서 사다리를 List<Line> 형태로 보유 |

2. TC(테스트케이스) 작성 후, 단위 테스트 코드를 짜보려고 함

### ✔️ Test Case

| No. | 분류                  | 내용                                               | 통과 여부 |
|:----|:--------------------|:-------------------------------------------------|:------|
| 01  | 랜덤 숫자 생성 테스트        | 숫자 0/1만 생성되는지                                    | ✅     |
| 02  | 사다리 생성 테스트          | 0/1 값에 매핑되는 사다리 파츠가 만들어지는지                       | ✅     |
| 03  | 사다리 생성 테스트          | 사다리 가로 한 라인이 제대로 만들어지는지                          | ✅     |
| 04  | 사다리 생성 테스트          | 사다리 가로 한 라인이 중복되는 라인이 없는지                        |       |
| 05  | 입력 값/Players 예외 테스트 | 플레이어 이름 입력 값이 없을 때 예외가 발생하는지                     | ✅     |
| 06  | 입력 값/Players 예외 테스트 | 플레이어 이름이 6자 이상일 때 예외가 발생하는지                      | ✅     |
| 07  | 입력값 예외 테스트          | 플레이어 이름을 쉼표로 구분하지 않았을 때 예외가 발생하는지                | ✅     |
| 08  | 입력값 예외 테스트          | 플레이어가 1명만 참가했을 때 예외가 발생하는지                       | ✅     |
| 09  | 입력 값/Players 예외 테스트 | 플레이어 이름이 중복되었을 때 예외가 발생하는지                       | ✅     |
| 10  | 사다리 생성 테스트          | 플레이어 이름이 출력되는지                                   |       |
| 11  | 사다리 예외 테스트          | 사다리 길이가 0보다 작고 Integer.Max.Value보다 클 때 예외가 발생하는지 ||

숫자가 아닐 때 예외가 발생하는지
