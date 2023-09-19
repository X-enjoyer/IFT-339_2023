Date: 2023-09-19
---

```cpp
template<typename T>
class Vector{
    T* tab;
    size_t cap;
    size_t size;
    public:
        Vector();
        Vector(const Vector<T>&);
        Vector<T>& operator=(const Vector<T>&);
        ~Vector();
        void push_back(const T&);
        T pop_back();
        T& operator[](size_t);
        const T& operator[](size_t) const;
        T& at(size_t);
        const T& at(size_t) const;
        iterator begin();
        iterator end();
        const_iterator begin() const;
        const_iterator end() const;
        size_t size() const;
        void reserve(size_t);
        void resize(size_t);
        void clear();
}

template<typename T>
Vector<T>::Vector(): size(0), cap(0), tab(nullptr) {
    delete[] tab;
    tab = nullptr;
    size = cap = 0;
}

template<typename T>
void Vector<T>::Clear()
{
    delete[] tab;
    tab = nullptr;
    size = cap = 0;
}

template<typename T>
Vector<T>::vector(const Vector<T>& v): size(v.size()), cap(v.size())
{
    tab(new T[cap])
    for(auto it = v.begin(); it != v.end(); it++)
    {
        push_back(*it);
    }
}

template<typename T>
Vector<T>::~Vector()
{
    Clear();
}

template<typename T>
Vector<T>::vector():vector(0)
{
}

template<typename T>
Vector<T>& vector<T>::operator=(const Vector<T>& v)
{
    reserve(v.size());
    for(size_t i = 0; i < v.size(); i++)
    {
        tab[i] = v[i];
    }
    size=v.size();
}

int main()
{
    Vector<int> v;
    Vector<int> v2(v);
    v2.push_back(4);
    cout << v1.back() << endl;
    v2.pop_back();
    v2.push_back(5);
    cout << v1.back() << endl; //valeur de v1 va changer alors que c'est v2 qui a été modifié ❌
    Vector<int> v3;
    v3 = v2;
    return 0;
}

```