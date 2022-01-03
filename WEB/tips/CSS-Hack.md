# CSS Hack
레시피 같이 어디든 쓸 수 있다. 이상하지만 작동한다.

## 1. justify-content: space-between 대체
#### a. 문제 발생 이유
  side width가 상이하기에 space-between 적용 불가능
#### b. 해결 방법
  - 1 상위 박스 : justify-content: center;
  - 2 내부 박스 범위 : width: 33%;
  - 3 중앙에 위치할 박스 : display: flex; justify-content: center;
  - 4 오른쪽에 정렬할 박스 : *display*: flex; *justify-content*: flex-end; *align-items*: center;
#### c. 사례 status-bar
  ```
  .status-bar {
    display: flex;
    justify-content: center;
  }
  .status-bar__column {
    width: 33%;
  }
  .status-bar__column:nth-child(2) {
    display: flex;
    justify-content: center;
  }
  .status-bar__column:last-child {
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
  ```
