Date: 2023-09-20
---
```cpp	
template <typename T>
class deque
{
    T** tab;
    size_t debut;
    size_t dim;
    size_t cap;   
}

T& deque<T>::operator[](size_t i)
{
    i += debut;
    size_t pos = i % dimAlv;
    size_t noAlv = i / dimAlv;
    return tab[noAlv][pos];
}
```
# À l'examen
### deque circulaire par alveole*** 
### savoir qui faire pour push front / push back / savoir quand c'est plein

```cpp

iterator
{
    deque<T>* ptr;
    size_t index;
}

operator*()
{
    return (*ptr)[index];
}

operator++()
{
    ++index;
    if(index == ptr->dimAlv)
    {
        index = 0;
        ++ptr;
    }
    return *this;
}

operator--()
{
    if(index == 0)
    {
        index = ptr->dimAlv;
        --ptr;
    }
    --index;
    return *this;
}

```