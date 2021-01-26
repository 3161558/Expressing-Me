# Expressing-Me
float x;
float y;
float easing = 0.0005;

void setup(){
  smooth();
  size(1500, 1500);
  background(102,102,0);
  frameRate(60);
  noStroke();
}
void star(float x, float y, float radius1, float radius2, int npoints) 
{
  float angle = TWO_PI / npoints;
  float halfAngle = angle/2.0;
  beginShape();
  for (float a = 0; a < TWO_PI; a += angle) {
    float sx = x + cos(a) * radius2;
    float sy = y + sin(a) * radius2;
    vertex(sx, sy);
    sx = x + cos(a+halfAngle) * radius1;
    sy = y + sin(a+halfAngle) * radius1;
    vertex(sx, sy);
  }
  endShape(CLOSE);
}
void draw()
{ 
  fill(0, 4);
  rect(0, 0, width, height);
  
  fill(98.04, 99.22, 92.55);
  ellipse(random(width), random(height), 8, 8);

  fill(102,102,0);
  translate(mouseX, mouseY);
  float targetX = mouseX;
  float dx = targetX - x;
  x += dx * easing;
  
  float targetY = mouseY;
  float dy = targetY - y;
  y += dy * easing;
  star(0, 0, 30, 70, 5);
}
