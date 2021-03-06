# CORS
프론트 서버와 백앤드 서버의 서로 다른 도메인간에 API 요청시 브라우저가 보안상의 이유로 제한을 한다.

## 해결방법

1. Node에서의 해결       

* cors 패키지 이용
```javascript
// npm install cors
const express = require('express')
const cors = require('cors')
const app = express()

// 미들웨어로 사용
app.use(cors())
```
<br>

2. React에서의 해결

* proxy를 이용하여 데이터 통신하기
```javascript
// package.json
"proxy": "http://localhost:5000"
```

* http-proxy-middleware 패키지 이용
```javascript
// src 폴더 아래에 setupProxy.js 생성
const { createProxyMiddleware } = require('http-proxy-middleware');

module.exports = function (app) {
    app.use(
        '/api',
        createProxyMiddleware({
            target: 'http://localhost:5000',
            changeOrigin: true,
        })
    );
};
```
