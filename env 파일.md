# .env

**환경 변수 파일**

DB 관련 정보 / API_KEY 등등 git 오픈소스에 올리면 안되는 값들을 저장함!

env를 사용하면? 보안과 유지보수에 용이하고 하드코딩 하지 않고 사용~

## 사용 방법 (React)

1. `.env` 파일을 프로젝트 최상위에 생성
2. `gitignore` 파일에 .env 텍스트 추가 ⭐️

```jsx
// .env
// REACT_APP_원하는이름 으로 key를 작성
REACT_APP_API_KEY = Aa1Bb2Cc3Dd4Ee5Ff6Gg7Hh8Ii9Jj0
PUBLIC_API_URL = https://api_url

// index.js
// process.env.생성한 키로 사용
const key = process.env.REACT_APP_API_KEY
const url = process.env.PUBLIC_API_URL
```

**nodeJS 에서 사용하려면?**

<aside>
<img src="https://www.notion.so/icons/code_gray.svg" alt="https://www.notion.so/icons/code_gray.svg" width="40px" /> npm install dotenv

</aside>

`dotenv` 환경 변수 파일을 외부에 만들어 값들을 저장 시킴