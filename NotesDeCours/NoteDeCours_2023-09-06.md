Date: 2023-09-06
-----
Conteneurs séquentiels
```cpp
Array<T, N>;
Array<int, 4>;
//Array on ne peut pas changer la taille mais on peut acceder a chaque element en temps constant

vector<T>;
//vector on peut changer la taille mais on ne peut pas acceder a chaque element en temps constant

deque<T>;


list<T>;

forward_list<T>;

stack<T>;

queue<T>;

priority_queue<T>;
```
Conteneurs associatifs ordonnés
```cpp
set<T>;
multiset<T>;
map<K, V>
multimap<K, V>;
bitset;
```

Conteneurs associatifs non ordonnés
```cpp
unordered_set<T>;
unordered_multiset<T>;
unordered_map<K, V>;
unordered_multimap<K, V>;
```


||Indexage|Ajouter/enlever fin|Ajouter/enlever début| Inserer/supprimer|Rechercher|
|---|---|---|---|---|---|
|array|O(1)|X|X|X|X|
|vector|O(1)|O(1)c|X|X|X|
|deque|O(1)|O(1)c|O(1)c|X|X|
|list|X|O(1)|O(1)|O(1)|X|
|set|X|X|X|O(log n)|O(log n)|
|multiset|X|X|X|O(log n)|O(log n)|
|map|X|X|X|O(log n)|O(log n)|
|multimap|X|X|X|O(log n)|O(log n)|
|unordered_set|X|X|X|O(1)|O(1)|
|unordered_map|X|X|X|O(1)|O(1)|

![i love c++](https://pbs.twimg.com/media/FgCDFV_UAAEwGYC.png)