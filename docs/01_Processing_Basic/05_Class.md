# 5. Class 사용하기

원 그리기를 Class를 사용해 표현하기

```java title="proc-0105.pde" linenums="1"
myCircle c1, c2;

void setup() {
  size(800, 500);
  c1 = new myCircle(300, 200, 200, 200);
  c2 = new myCircle(500, 150, 240, 120);
}

void draw() {
  background(255);
  float myRed, myBlue;
  myRed = map(mouseX, 0, width, 0, 255);
  myBlue = map(mouseY, 0, height, 255, 0);
  c1.update(myRed, 0, myBlue);
  c2.update(myBlue, myRed, 0);
  c2.update(mouseX, mouseY);
  c1.draw();
  c2.draw();
}

class myCircle {
  int x, y, w, h;
  float r, g, b;
  
  myCircle(int x, int y, int w, int h) {
    this.x = x;
    this.y = y;
    this.w = w;
    this.h = h;
  }
  
  void draw() {
    fill(r, g, b);
    ellipse(x, y, w, h);
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