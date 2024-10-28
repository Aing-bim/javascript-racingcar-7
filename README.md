# javascript-racingcar-precourse

# 초간단 자동차 경주 게임

## 목차
1. [프로젝트 개요](#프로젝트-개요)
2. [기능 요구사항](#기능-요구사항)
3. [프로젝트 구조](#프로젝트-구조)
4. [개발 및 실행 방법](#개발-및-실행-방법)
5. [기능 설명](#기능-설명)
6. [테스트 가이드](#테스트-가이드)

---

## 프로젝트 개요
본 프로젝트는 우아한테크코스 프리코스 과제로, 사용자가 입력한 자동차들이 경주를 통해 우승자를 결정하는 간단한 콘솔 게임입니다. 사용자는 자동차 이름과 이동 횟수를 입력하여 게임을 진행할 수 있으며, 게임의 조건에 따라 우승자가 결정됩니다.

---

## 기능 요구사항
1. **자동차 이동 조건**
   - 0에서 9 사이의 무작위 값을 생성하고, 4 이상일 경우 자동차가 전진합니다.
2. **자동차 이름 설정**
   - 자동차 이름은 쉼표(,)로 구분하며, 이름은 5자 이하로 제한합니다.
3. **사용자 입력**
   - 사용자로부터 경주할 자동차 이름과 이동 횟수를 입력받습니다.
4. **우승자 결정**
   - 게임이 종료된 후 가장 멀리 이동한 자동차(들)를 우승자로 설정합니다.
5. **오류 처리**
   - 잘못된 값이 입력되면 "[ERROR]" 메시지를 출력하고 애플리케이션을 종료합니다.

---

## 프로젝트 구조
```
📦 프로젝트 루트
├── 📂 __tests__                  # 테스트 코드가 포함된 폴더
│   └── ApplicationTest.js        # 주요 애플리케이션 테스트 파일
├── 📂 src
│   ├── 📂 types                   # 타입 정의 파일 폴더
│   │   └── index.d.ts            # 타입스크립트 지원을 위한 파일
│   ├── 📂 constants               # 상수를 정의한 폴더
│   │   ├── messages.js           # 출력 메시지 상수
│   │   ├── constraints.js        # 입력 조건 상수
│   │   └── errorMessages.js      # 에러 메시지 상수
│   ├── 📂 utils                   # 유틸리티 파일을 모아놓은 폴더
│   │   ├── randomUtils.js        # 랜덤 값 생성 유틸리티
│   │   └── validationUtils.js    # 입력값 검증 유틸리티
│   ├── 📂 controllers             # 컨트롤러 폴더
│   │   ├── GameController.js     # 게임의 전반적인 흐름 제어
│   │   └── InputController.js    # 사용자 입력 제어
│   ├── 📂 models                  # 모델 폴더
│   │   ├── Car.js                # 자동차 데이터 모델
│   │   └── Race.js               # 경주 데이터 모델
│   ├── 📂 views                   # 뷰 폴더
│   │   ├── GameView.js           # 게임 진행 상황 출력
│   │   └── ResultView.js         # 최종 결과 출력
│   ├── App.js                    # 애플리케이션의 시작점
│   └── index.js                  # 메인 실행 파일
└── package.json                  # 프로젝트 설정 파일
```

---

## 개발 및 실행 방법

### 환경 설정
- Node.js 20.17.0 버전을 설치합니다.
- `@woowacourse/mission-utils` 라이브러리를 사용하여 무작위 값 생성 및 콘솔 입력/출력을 처리합니다.

### 프로젝트 실행
```bash
npm install         # 패키지 설치
npm run start       # 애플리케이션 실행
```

### 기능 테스트
```bash
npm run test        # 테스트 실행
```

---

## 기능 설명

- **App.js**
  - 애플리케이션의 진입점으로, `GameController`를 통해 전체 게임 흐름을 관리합니다.

- **GameController.js**
  - 게임 초기화, 진행, 종료 및 결과 출력을 담당합니다.
  - 각 라운드마다 `Race` 모델을 통해 자동차 이동을 처리하고, `GameView`를 통해 진행 상황을 출력합니다.

- **InputController.js**
  - 사용자로부터 입력을 받으며, `validationUtils.js`를 사용하여 입력을 검증합니다.
  - 잘못된 입력이 들어올 경우 에러 메시지를 출력하고 프로그램을 종료합니다.

- **Car.js**
  - 자동차의 이름과 위치를 관리하며, 자동차의 이동을 위한 메서드를 제공합니다.

- **Race.js**
  - 경주 라운드를 관리하고, 각 라운드 종료 후 우승자를 결정하는 로직을 포함합니다.

- **GameView.js**
  - 각 라운드 결과를 출력하여 사용자에게 자동차들의 현재 위치를 보여줍니다.

- **ResultView.js**
  - 경주가 끝난 후 최종 우승자를 출력합니다.

- **randomUtils.js**
  - `Random.pickNumberInRange()`를 사용하여 0에서 9 사이의 무작위 값을 생성하는 함수가 포함됩니다.

- **validationUtils.js**
  - 자동차 이름의 길이 및 이동 횟수의 유효성을 검증하는 함수가 포함됩니다.

---

## 테스트 가이드

### Node.js 버전 확인
```bash
node --version
```
- Node.js 버전이 20.17.0 이상인지 확인합니다.

### 테스트 실행
```bash
npm run test
```
- 모든 기능이 올바르게 동작하는지 `Jest`를 이용하여 테스트합니다.
- `test.each()` 및 `describe.each()`와 같은 Jest의 파라미터화 테스트를 활용하여 다양한 입력 조건을 테스트합니다.

--- 

이 문서를 통해 프로젝트의 개요, 구조, 실행 방법, 기능 설명, 테스트 방법을 명확히 이해할 수 있습니다.