# 4. Function 사용하기

## 4-1. 원 그리기와 인터랙티브

- 원 그리기
- 마우스 움직임으로 색깔 변화 나타내기

```java title="proc-010401.pde" linenums="1"
void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  fill(255, 0, 0);          // 이제부터 그리는 도형은 빨간색으로 채운다
  circle(300, 200, 150);    // 좌표 (300, 200) 위치에 지름 150인 원 그리기
}

```

```java title="proc-010402.pde" linenums="1"
//
// 마우스를 이용해 인터랙티브 그림으로 만들자
//
void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  fill(mouseX, 0, 0);       
  circle(300, 200, 150);
}

```

```java title="proc-010403.pde" linenums="1"
//
// 색깔을 표현하는 값은 0~255 라서 mouseX 값이 범위를 벗어난다
// 변수를 사용해 mouseX 값을 색깔 표현 범위로 맞추는 방법 1
//
void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  float myRed = 0;          // 내빨강 이라는 변수를 만들어 쓴다
  myRed = mouseX;           // 마우스 x 좌표가 내빨강색이 된다
  fill(myRed, 0, 0);        // 내빨강으로 앞으로 만들 도형의 색을 채운다
  circle(300, 200, 150);    // 좌표 (300, 200) 위치에 지름 150인 원 그리기
}

```

```java title="proc-010404.pde" linenums="1"
//
// 색깔을 표현하는 값은 0~255 라서 mouseX 값이 범위를 벗어난다
// 변수를 사용해 mouseX 값을 색깔 표현 범위로 맞추는 방법 2
//
void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  float myRed = 0.0;        // 내빨강 이라는 변수를 만들어 쓴다
  myRed = map(mouseX, 0, width, 0, 255);    // mouseX 값을 색 표현 범위인 0~255 사이값으로 변경한다
  fill(myRed, 0, 0);
  circle(300, 200, 150);    // 좌표 (300, 200) 위치에 지름 150인 원 그리기
}

```

## 4-2. 함수(Function) 하기

```java title="proc-010405.pde" linenums="1"
//
// 자주 사용하는 명령어 몇개를 모아서 나만의 명령을 만들어 쓸 수 있다
//

void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  float myRed = 0.0;
  myRed = map(mouseX, 0, width, 0, 255);
  myCircle(300, 200, 200, myRed, 0, 0);
}

void myCircle(int x, int y, int d, float red, float green, float blue) {
  fill(red, green, blue);
  circle(x, y, d);
}
```

```java title="proc-010406.pde" linenums="1"
//
// 함수로 만들면 원을 여러개 만들면서, 알아 보기도 좋다
//

void setup() {
  size(800, 500);
}

void draw() {
  background(255);
  float myRed = 0.0;
  myRed = map(mouseX, 0, width, 0, 255);
  myCircle(300, 200, 150, myRed, 0, 0);
  myCircle(500, 300, 200, 0, myRed, 0);
  myCircle(600, 400, 250, 0, 0, myRed);
}

void myCircle(int x, int y, int d, float red, float green, float blue) {
  fill(red, green, blue);
  circle(x, y, d);
}
```