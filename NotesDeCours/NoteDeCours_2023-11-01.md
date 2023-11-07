```cpp
template<typename T>
struct noeud
{
    T contenu;
    noeud<T> *gauche;
    noeud<T> *droite;
    noeud(const T& val, noeud<T> *gauche = nullptr, noeud<T> *droite = nullptr)
        : contenu(val), gauche(gauche), droite(droite)
    {}
};


template<typename T>
class Arbre
{
    noeud<T> *racine;
    size_t taille;
    bool contient(const T& val, noeud<T> * const &) const,
    void detruire(noeud<T> * const &, T&),
    void eleverMin(noeud<T> * const &, T&),
    void eleverMax(noeud<T> * const &, T&),
    void copier(noeud<T> *, noeud<T> *&),
    void vider(noeud<T> * const &),
    void inserer(const T&, noeud<T> *&),
public:
    ~Arbre()
    {
        vider(racine);
    }
    void vider()
    {
        vider(racine);
    }
    Arbre & operator=(const Arbre &)
    {
        if(this != &autre)
        {
            vider();
            copier(autre.racine, racine);
        }
        taille = autre.taille;
        return *this;
    }
    bool contient(const T& val) const
    {
        return contient(val, racine);
    }
};

template<typename T>
bool Arbre::Contient(const T& val, noeud<T> * const & n) const
{
    if(n == nullptr)
    {
        return false;
    }
    else if(val < n->contenu)
    {
        return contient(val, n->gauche);
    }
    else if(val > n->contenu)
    {
        return contient(val, n->droite);
    }
    else
    {
        return true;
    }
}

template<typename T>
void Arbre::copier(noeud<T> *n, noeud<T> *& cible)
{
    if(n == nullptr)
    {
        cible = nullptr;
    }
    else
    {
        cible = new noeud<T>(n->contenu);
        copier(n->gauche, cible->gauche);
        copier(n->droite, cible->droite);
    }
}

void Arbre::vider(noeud<T> * const & n)
{
    if(n != nullptr)
    {
        vider(n->gauche);
        vider(n->droite);
        delete n;
    }
}