Date: 2023-09-26
---
```cpp
template <typename T>
struct cellule
{
    T val;
    cellule<T>* suiv;
    cellule<T>* prec;
};
```
- `cellule<T>* suiv;` : pointeur vers la cellule suivante
- `cellule<T>* prec;` : pointeur vers la cellule précédente
- `T val;` : valeur de la cellule

```cpp

main(){
    cellule* r = new cellule;
    r->val = 0;
    r->suiv = ptr;
    r->prec = ptr->prec;
    ptr->prec->suiv = r;
    ptr->prec = r;
}
```

```cpp
template <typename T>
struct cellule
{
    T val;
    cellule<T>* suiv;
    cellule<T>* prec;
    cellule(const T& val, cellule<T>* suiv, cellule<T>* prec) : val(val), suiv(suiv), prec(prec) {}
};

main(){
    cellule* r = new cellule(0, ptr, ptr->prec);
    ptr->prec->suiv = r;
    ptr->prec = r;
}
```

```cpp
template <typename T>
class Pile
{
    vector<T> tab;
    public:
        void push(const T& val)
        {
            tab.push_back(val);
        }
        void pop()
        {
            tab.pop_back();
        }
        T& top()
        {
            return tab.back();
        }
        bool empty()
        {
            return tab.empty();
        }
};  
```
## Retour de la pause
- bon ca va faire les criss de retardataires 
```cpp

template <typename T>
class List
{
    struct cellule
    {
        T val;
        cellule* suiv;
        cellule* prec;
        cellule(const T& val, cellule* suiv, cellule* prec) : val(val), suiv(suiv), prec(prec) {}
    };

    cellule* debut;
    size_t dim;
    public:
    List();
    List(const List& autre);
    ~List();
    iterator insert(iterator pos, const T& val);
    iterator erase(iterator pos);
    size_t size() const;
    iterator begin();
    iterator end();
    reverse_iterator rbegin();
    reverse_iterator rend();
}

```