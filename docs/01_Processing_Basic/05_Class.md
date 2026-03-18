# 5. Class 사용하기

원 그리기를 Class를 사용해 표현하기

- abs() : absolute value, () 안에 있는 값의 절대값

```java title="proc-0105.pde" linenums="1"
myCircle c1, c2;

void setup() {
  size(800, 500);
  c1 = new myCircle(300, 200, 200);
  c2 = new myCircle(500, 150, 140);
}

void draw() {
  background(255);
  float color1, color2, color3;
  color1 = map(mouseX, 0, width, 0, 255);
  color2 = map(mouseY, 0, height, 255, 0);
  color3 = abs(color1 - color2);
  c1.update(color1, color3, color2);
  c2.update(color2, color1, color3);
  c2.update(mouseX, mouseY);
  c1.draw();
  c2.draw();
}

class myCircle {
  int x, y, d;
  float r, g, b;
  
  myCircle(int x, int y, int d) {
    this.x = x;
    this.y = y;
    this.d = d;
  }
  
  void draw() {
    fill(r, g, b);
    circle(x, y, d);
  }
  
  void update(float red, float green, float blue) {
    r = red;
    g = green;
    b = blue;
  }
  
  void update(int pos_x, int pos_y) {
    x = pos_x;
    y = pos_y;
  }
}
```