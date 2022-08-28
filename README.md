#MEAN Environment



##React + Express 
1. React 설치
`npx create-react-app client`

2. express 설치  
`npm install express`

<img src="https://user-images.githubusercontent.com/57519789/187075204-2143bb38-0b15-4fe5-93e7-c7409470e4d2.png">

<br><br>
<hr>
##Node.js 서버 구축##

1. server 폴더 생성 후, Router파일, test.js, server.js 생성


2.  server.js
```
const express = require('express');
const app = express();
const test = require('.//Router/test');

app.use('/', test);

const port=5000; //React가 3000번 포트를 사용하기 때문에 node 서버가 사용할 포트넘버는 다른 넘버로 지정해준다.
app.listen(port, ()=>{console.log(`Listening on port ${port}`)});
```

3. test.js
```
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
    res.send({ test: "hi" });
});

module.exports = router;
```
4. 최상단 폴더에서 `node ./server/server.js` 실행

*만약 port 사용중이라고 오류나면 `sudo killall -9 node` 입력 후 비밀번호 입력

<img  src="https://user-images.githubusercontent.com/57519789/187075788-86a882ab-9f04-4df1-8a96-921b2a407139.png">

5. `http://localhost:5000/` 접속후 hi 나타나면 성공

<img src="https://user-images.githubusercontent.com/57519789/187075847-400b0893-d673-4a10-940e-e3f1d1d613f4.png">

6. nodemon, concurrently 설치 
`npm install nodemon --save`
`npm install concurrently --save`

7.  package.json에 추가 작성
```
{
  "scripts": {
    "server": "cd server && nodemon server",
    "client": "cd client && npm start",
    "start": "concurrently --kill-others-on-fail \"npm run server\" \"npm run client\""
  },
    "devDependencies": {
    "nodemon": "^2.0.7"
  },
  "dependencies": {
    "concurrently": "^7.3.0",
    "express": "^4.18.1",
    "nodemon": "^2.0.19"
  }
}
```
8. `npm start` 실행 후 
localhost:3000, localhost:5000 정상 작동

<br><br>
<hr>