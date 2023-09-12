Date: 2023-09-12
---
```cpp
void test(...)
{
    int j = 0;
    if(...)
    {
        int i = 0;
        int j = 1; //j a maintenant cette valeur jusqu'à la fin du bloc
        cout << j << endl; //j = 1
    }
    cout << j << endl; //j = 0
}
```
```cpp
int main()
{
    int f = factoriel(3);
    cout << f << endl;
    return 0;
}
int factoriel(int n)
{
    if(n == 0)
    {
        return 1;
    }
    else
    {
        return n * factoriel(n-1);
    }
}
```
### Pointeurs
```cpp
int *ptr = nullptr; //nullptr = 0
int *ptr2 = new int[4]; 
int tab[4];

int tab[n]; //n doit être connu à la compilation sinon erreur

int *ptr3 = new int[n]; //n n'a pas besoin d'être connu à la compilation    

ptr3[2] = 3; //équivalent à *(ptr3 + 2) = 3;

ptr3[1] == *(ptr3 + 1); //true

int* tab = *ptr3[2];
tab[1] == *ptr3[3];
```
||0|1|2|3|
|---|---|---|---|---|
|ptr3 ->|0|1|2|3 (ptr3[3])|
|tab ->|||2|3 (tab[1])|

```cpp
int mat[4][4];
mat[8] = 1;
```
||0|1|2|3|4|5|6|7|8 (mat[8])|9|10|11|12|13|14|15|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|mat|(1) 0| (1) 1| (1) 2| (1) 3| (2) 0| (2) 1| (2) 2| (2) 3| (3) 0| (3) 1| (3) 2| (3) 3| (4) 0| (4) 1| (4) 2| (4) 3|

```cpp
int* ptr = new int[4];
int* ptr2 = new int[n];

delete ptr;
delete[] ptr2;
ptr = nullptr;
```

```cpp
const char* str = "Bonjour";
char* const str2;
char* str3 = "Allo";
const char* const str4;

str = str3; //ok
str2 = str3; //erreur
str3 = new char[8]; //ok

```
```cpp

vector(vector<T>&& v);
vector<T>& operator=(vector<int>&& v);

vector(vector<T>&& v)
{
    tab = v.tab;
    v.tab = nullptr;
}


