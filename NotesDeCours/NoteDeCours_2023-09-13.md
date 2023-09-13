Date: 2023-09-13
---
(Chapitre 6 "array")<br>
### Fichier Array.h
```cpp
#ifndef _ARRAY_H
#define _ARRAY_H

template <typename T, size_t N>

class Array {
    T m_data[N];
    public:
        class iterator;
        class const_iterator;
        //constructeurs
        Array() = default;
        Array(const T& val);
        //constructeur de copie
        Array(const Array<T, N>& a);
        //destructeur
        ~Array();
        //opérateur d'affectation
        Array<T, N>& operator=(const Array<T, N>& a);
        //retourner valeur à l'index i
        T& operator[](size_t i);
        const T& operator[](size_t i) const;
        //avoir la taille
        size_t size() const {return N;}
        //avoir le premier et le dernier élément
        const T& front() const {return (*this)[0];}
        T& front() {return (*this)[0];}
        const T& back() const {return (*this)[N - 1];}
        T& back() {return (*this)[N - 1];}

        T& at(size_t i);
        const T& at(size_t i) const;

        iterator begin();
        iterator end();
        const_iterator begin() const;
        const_iterator end() const;
}

class iterator {
    T* m_ptr;
    public:
        iterator(T* ptr): m_ptr(ptr) {}
        iterator(const iterator& it): m_ptr(it.m_ptr) {}
        ~iterator() = default;
        iterator& operator=(const iterator& it);
        iterator operator++();
        iterator& operator++(int);
        iterator operator--();
        iterator& operator--(int);
        T& operator*();
        const T& operator*() const;
        T* operator->();
        const T* operator->() const;
        bool operator==(const iterator& it) const;
        bool operator!=(const iterator& it) const;
}

template <typename T, size_t N>
Array<T, N>::Array(const T& val)
{
    for(size_t i = 0; i < N; i++)
    {
        (*this)[i] = val[i];
    }
}

template <typename T, size_t N>
Array<T, N>::Array(const ArrayT& a)
{
    for(auto it = a.begin(); it != a.end(); it++)
    {
        *it = a;
    }
}

template <typename T, size_t N>
T& Array<T, N>::at(size_t i)
{
    if(i >= N)
    {
        throw std::out_of_range("Index out of range");
    }
    return (*this)[i];
}

template <typename T, size_t N>
Array<T, N>::iterator Array<T, N>::begin(size_t i)
{
    return iterator(m_data);
}

template <typename T, size_t N>
Array<T, N>::iterator Array<T, N>::end()
{
    return iterator(&(m_data[N]));
}

template <typename T, size_t N>
iterator& Array<T, N>::iterator::operator=(const iterator& it)
{
    m_ptr = it.m_ptr;
    return (*this);
}

template <typename T, size_t N>
iterator Array<T, N>::iterator::operator++()
{
    m_ptr++;
    return (*this);
}

template <typename T, size_t N>
iterator Array<T, N>::iterator::operator++(int)
{
    ++m_ptr;
    return (*this);
}

template <typename T, size_t N>
iterator Array<T, N>::iterator::operator--()
{
    m_ptr--;
    return (*this);
}

template <typename T, size_t N>
iterator Array<T, N>::iterator::operator--(int)
{
    --m_ptr;
    return (*this);
}

template <typename T, size_t N>
T& Array<T, N>::iterator::operator*()
{
    return *m_ptr;
}