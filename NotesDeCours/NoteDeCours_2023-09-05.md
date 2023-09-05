Date : 2023-09-05
---
## Pile
- LIFO (Last In First Out)
- Ajout et retrait d'éléments à la fin de la pile
- Exemple: Pile d'assiettes

```cpp
Pile<T>
{
    empiler(T element);
    T depiler();
    T sommet();
    vider();
    detruire();
    creer();
}
```

## File
- FIFO (First In First Out)
- Ajout à la fin de la file et retrait au début de la file
- Exemple: File d'attente

```cpp
File<T>
{
    enfiler(T element);
    T defiler();
    T premier();
    vider();
    detruire();
    creer();
}
```
---
### À L'EXAMEN **********
Exercice : Définnissez les opérations du type abstrait PU selon la nomenclature définie plus haut. (Voir doc. "Annexe: Type de données abstrait (TDA)")

