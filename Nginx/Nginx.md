# Nginx (웹 서버)의 역할

- 정적 파일을 처리하는 HTTP 서버로서의 역할
  * 서버의 역할은 HTML, CSS, Javascript, 이미지와 같은 정보를 웹 브라우저에 전송하는 역할을 한다.

- 응용프로그램 서버에 요청을 보내는 리버스 프록시로서의 역할
  * 클라이언트는 가짜 서버에 요청을 하면, 프록시 서버(Nginx)가 배후 서버(응용프로그램 서버)로부터
데이터를 가져오는 역할을 한다.

웹 응용프로그램 서버에 리버스 프록시를 두는 이유는 요청에 대한 버퍼링이 있기 때문이다.     
클라이언트가 직접 서버에 요청하는 경우, 프로세스 1개가 응답 대기 상태가 되어야만 한다.      
따라서 프록시 서버를 둠으로써 요청을 배분하는 역할을 한다.


## Nginx 도메인 등록
__`nginx 환경설정`__

```
/etc/nginx/sites-available/default
sudo nano default
```

__`nano 텍스트 에디터에 다음 작성`__

```
server{
listen 80;
server_name goodchoice.gq www.goodchoice.gq;

location / {
        proxy_pass      http://127.0.0.1:3030/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
	}
}
```

__`저장 후, 정상 입력 되었는지 확인 `__

```
sudo nginx -t
```

__`정상 입력시 다음 출력`__

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

__`nginx 재부팅`__

```
 sudo service nginx restart
```
