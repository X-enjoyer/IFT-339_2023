Date : 2023-08-29
-----
```cpp
#include <iostream>

using namespace std;

int main()
{
    const double PI = 3.14159;
    int i = 0;

    cin >> i;
    cout << "Hello World" << endl;

    return 0;
}
```
- type de variable
```cpp
unsigned int i = 0;
short int i = 0;
long int i = 0;
float i = 0.0;
double i = 0.0;
char i = 'a';
bool i = true;
```
- short <= int <= long <= long long

```cpp	

//struct sont public par défaut
struct Point
{
    float x;
    float y;
};

//class sont privé par défaut
class Point2
{
    float x;
    float y;
};

int main()
{
    Point p;
    Point2 p2;

    p.x = 0;
    p.y = 0;

    p2.x = 0; // erreur ❌ 
    p2.y = 0; // erreur ❌
    return 0;
}

class Test
{
    float a;
    public:
        int a;
    private:
        int b;
}
```
----
### Fichier Point.h

```cpp
#ifndef POINT_H
#define POINT_H

class Point
{
    float m_x;
    float m_y;
    public:
        Point();
        Point(float x, float y);
        Point(const Point& p);
        Point& operator=(const Point& p);
        ~Point();
        Point translation_x(float x) const;
        void translation_x(float x);
        const float& getX() const;
        const float& getY() const;
        void setX(float x);
        void setY(float y);
            
};

#endif
```