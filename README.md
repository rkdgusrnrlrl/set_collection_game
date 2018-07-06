## 목적
- [배틀라인](http://boardlife.co.kr/bbs_detail.php?bbs_num=581&tb=boardgame_strategy) 게임을 온라인으로 구현할 예정

## 사용 기술
- 웹 컴포넌트 : Vue.js
- CSS : flex box 를 적극 사용 할 예정
- Node.js

## 기능
- 우선 오프라인 구현(로테이션으로 할 수 있게 개발)
- 카드 드래그 드랍
- 특수 기능 카드는 우선 없음
- 간단한 셋 컬렉션 게임 형태로 구현
- 우선 이미지 없이 진행

## 프로젝트 관련 내용

### 개발 가이드
- 초기에 의존성 있는 라이브러리 설치를 위해 `npm i` 로 라이브러리 설치
- 개발 서버를 띄우기 위해서 `npm run serve` 입력 히면 `localhost:8080`에 개발 페이지를 확인 할 수 있음
- [vue cli](https://cli.vuejs.org/guide/) 참조

### 폴더 구조
```
├── .gitignore          # git에서 제외 파일 목록
├── babel.config.js     # babel 설정
├── package.json        # 의존성 및 npm 스크립트
├── package-lock.json
├── node_modules        # yarn 또는 npm으로 설치한 의존성
├── dist                # 빌드 결과물, yarn build 전까지 없음
├── public              # 정적 파일을 넣음(js, css, html)
│   └── index.html      # 시작파일(진입점)
├── README.md
└── src                 # 소스 파일(vue 컴포넌트, 관련 리소스)
    ├── App.vue
    ├── assets
    ├── components
    └── main.js
```