Date: 2023-09-27
---
```cpp
list<int> l1, l2;
auto it = l1.begin();
l2.insert(it, l2);
l1.size() == 0;
l2.size() == 1;

l1.erase(it);
std::cout << *it


list<int> *l1 = new list<int>();

auto it = l1->begin();
delete l1;
std::cout << *it;


list<int> *l1 = new list<int>();
auto it = l1->begin();
l1.reverse();
l1.splice_after(it, l2);
```

### Exercice 1
```cpp

class heure
{
public:
    heure(int h, int m, double s)
    void lire(istream& is); //[21:7:21.5]
    void ecrire(ostream& os) const;
    heure ajouter(const heure& autre) const;
    bool vientAvant(const heure& autre) const;
}