# 에러발생
- 다른 라우트로 이동하여 컴포넌트가 렌더링 되는 도중에 에러가 발생했다.

```
Warning: Can't perform a React state update on an unmounted component.
This is a no-op, but it indicates a memory leak in your application.
To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.

언마운티드 된 컴포넌트에 대해서는 상태 업데이트를 수행할 수 없다.
해당 작업은 수행되지 않지만 메모리 누수가 발생한다.
해결하기 위해서 useEffect의 cleanup function을 이용해라.
```

## 해결과정
일단 검색을 해봤다. 갓구글~      
보아하니 비동기 처리를 하는 과정에서 발생한다는데 나의 경우 custom hooks를 사용해     
비동기 작업 수행전 setter함수 setLoding의 파라미터 값으로 true가 전달되면 로딩 스피너가 브라우저에 보여지고       
비동기 작업이 수행되고 난 후 스피너가 사라지고 setLoding 파라미터로 false가 전달된다.       
헌데 다른 라우트로 화면 전환을 하면 이동 전 컴포넌트에서 loading state를 변경하려던 시도가 있었기 때문에 
오류가 발생했다.

  <details>
  <summary><b>해결코드</b></summary>
  <div markdown="1">
  - react에서 알려준 방법인 useEffiect의 cleanup 함수를 사용했다
 
  ```javascript
  useEffect(() => {
    const fetchProducts = async () => {
      setSearchedProducts([]);
      showLoader();
      const res = await axios.post("/api/product/products", { filters });
      hideLoader();
      if (res.data.success) {
        setCurrentPage(query.page ? Number(query.page) : 1);
        setProducts(res.data.productInfo);
      }
    };
    fetchProducts();
    return () => hideLoader();
  }, [filters]);
  ```
  </div>
  </details>  
