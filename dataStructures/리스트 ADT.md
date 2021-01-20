# 리스트
* 저장할 데이터가 많지 않을 때 유용하다
* 일정한 순서로 항목을 집어넣을 필요가 없을 때 효과적
* 시간이 많이 소요되는 검색을 수행하거나, 복잡한 정렬을 원한다면 비추천
---------
## 리스트 ADT

전체 리스트 ADT | 설명
---- | ----
listSize (프로퍼티) | 리스트의 요소 수
pos (프로퍼티) | 현재 위치 
length (프로퍼티) | 리스트의 요소 수 
clear (함수) | 리스트의 모든 요소 삭제
toString (함수) | 리스트를 문자열로 표현해 변환
getElement (함수) | 현재 위치의 요소를 반환
insert (함수) | 기존 요소 위로 새 요소를 추가
append (함수) | 새 요소를 리스트의 끝에 추가
remove (함수) | 리스트의 요소 삭제
front (함수) | 현재 위치를 리스트 마지막 요소로 설정
end (함수) | 현재 위치를 리스트 마지막 요소로 설정
prev (함수) | 현재 위치를 한 요소 뒤로 이동
next (함수) | 현재 위치를 한 요소 앞으로 이동
currPos (함수) | 리스트의 현재 위치 반환
moveTo (함수) | 현재 위치를 지정한 위치로 이동
----------
## List 클래스 구현
```javascript
class List {
  constructor() {
    this.listSize = 0;
    this.pos = 0;
    this.dataStore = [];
  }
  // ... 이부분에 내부 메소드 구현
}
```
### Append - 리스트에 요소 추가
```javascript
append(element) {
  this.dataStore[this.listSize++] = element;
}
```
### Find - 리스트의 요소 검색
```javascript
find (element) {
    for (let i = 0; i < this.dataStore.length; i++) {
        if (this.dataStore[i] === element) {
            return i;
        }
    }
    return -1;
}
```
### Remove - 리스트의 요소 삭제
```javascript
remove (element) {
    const foundAt = this.find(element);
    if (foundAt > -1) {
        this.dataStore.splice(foundAt, 1);
        this.listSize--;
        return true;
    }
    return false;
}
```
### Length - 리스트의 요소 개수
```javascript
length () {
    return this.listSize;
}
``` 
### toString - 리스트의 요소 개수
```javascript
toString() {
    return this.dataStore;
}
```
### Insert - 리스트에 요소 삽입
```javascript
insert(element, after) {
    const insertPos = this.find(after);
    if (insertPos > -1) {
        this.dataStore.splice(insertPos + 1, 0, element);
        this.listSize++;
        return true;
    }
    return false;
}
```
