Date: 2023-08-30
-----
### Suite d'hier 
Fichier Point.h
```cpp
#ifndef POINT_H
#define POINT_H
#include <iostream>

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
        Point translation_y(float y) const;
        void translation_y(float y);
        const float& getX() const;
        const float& getY() const;
        void setX(float x);
        void setY(float y);
        bool operator==(const Point& p) const;
        bool operator!=(const Point& p) const;
        friend std::istream& operator>>(std::istream& in, Point& p);
};

std::ostream& operator<<(std::ostream& out, const Point& p);
std::istream& operator>>(std::istream& in, Point& p);


#endif
```

Fichier Point.cpp
```cpp
#include "Point.h"

Point::Point() : Point(0,0)
{
}

Point::Point(float x, float y)
{
    m_x = x;
    m_y = y;
}

Point::Point(const Point& p)
{
    Point(p.getX(), p.getY());
}

Point::~Point()
{
}

Point& Point::operator=(const Point& p)
{
    m_x = p.getX();
    m_y = p.getY();
    return (*this);
}

Const Point& Point::getX() const
{
    return m_x;
}

Const Point& Point::getY() const
{
    return m_y;
}

Point Point::translation_x(float dx) const
{
    return Point(m_x + dx, m_y);
}

bool Point::operator==(const Point& p) const
{
    return (m_x == p.m_x && m_y == p.m_y);
}

bool Point::operator!=(const Point& p) const
{
    return !(*this == p);
}

std::ostream& operator>>(std::ostream& out, const Point& p)
{
    out << "(" << p.getX() << ", " << p.getY() << ")";
    return out;
}

std::istream& operator>>(std::istream& in, Point& p)
{
    in >> p.m_x >> p.m_y;
    return in;
}

```
Templates 
```cpp
#ifndef POINT_H
#define POINT_H
#include <iostream>
¸
template <typename T>
class Point
{
    float m_x;
    float m_y;
    public:
        Point();
        Point(T, T);
        Point(const Point& p);
        Point& operator=(const Point& p);
        ~Point();
        const T& getX() const;
        const T& getY() const;
        Point<T> translation_x(T) const;
}

template <typename T>
Point<T>:: Point(T x, T y)
{
    m_x = x;
    m_y = y;
}

template <typename T>
const T& Point<T>::getX() const
{
    return m_x;
}

```

```cpp
#ifndef Fuite_H
#define Fuite_H

template <typename T>
class Fuite
{
    T m_val;
    static int compteur;
    public:
        Fuite(const T& val);
        Fuite(const Fuite&);
        ~Fuite();
        Fuite& operator=(const Fuite&);
        const T& getVal() const;
        void setVal(const T& val);
        T& valeur();
        const T& valeur() const;
};

template <typename T>
int Fuite<T>::compteur = 0;

template <typename T>
Fuite<T>::Fuite(const T& val)
{
    m_val = val;
    compteur += 1;
}

template <typename T>
Fuite<T>::Fuite(const Fuite<T>& f)
{
    m_val = f.m_val;
    compteur += 1;
}

template <typename T>
Fuite<T>::~Fuite()
{
    compteur -= 1;
}

template <typename T>
Fuite<T>& Fuite<T>::operator=(const Fuite<T>& f)
{
    m_val = f.m_val;
    return (*this);
}

int main()
{
    Fuite<int> f1;
}

```