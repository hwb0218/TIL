# Node.Js mysql2
* 콜백지옥을 해결하기 위해서 promise를 지원하는 mysql2

## connection pool
* connection을 미리 생성한 후 pool에 보관했다가 필요할 때 connection을 가져와 사용한 후 반납함
* 필요할때 마다 connection을 생성하고 닫지 않아도 되기 때문에 자원이 절약되고 성능향상을 기대할 수 있음

```javascript
let someRows, otherRows;
  connection.getConnection().then(conn => {
      return conn.query(firstQuery, [token])
          .then(([firstRows, fields]) => {
              conn.release();
              someRows = firstRows;
              return conn.query(secondQuery, [token])
          })
          .then(([secondRows, fields]) => {
              conn.release();
              otherRows = secondRows;
          }).then(() => {
          // do something with someRows and otherRows
          });
  });
```
