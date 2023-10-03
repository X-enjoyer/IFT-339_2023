Date: 2023-10-03
---

```cpp
class heure
{
    double temps;
public:
    heure(int h, int m, double s): temps(h*3600 + m*60 + s) {}
    heure ajouter(const heure& autre) const
    {
        return heure(0,0,temps + autre.temps);
    }
    bool vientAvant(const heure& autre) const
    {
        return temps < autre.temps;
    }
    void lire(istream& is)
    {
        char t;
        int h, m;
        double s;
        in >> h >> t >> m >> t >> s >> t;
        temps = h*3600 + m*60 + s;
    }

    void ecrire(ostream& out) const 
    {
        int h = (int) temps / 3600;
        int m = (int)(temps - h*3600) / 60;
        double s = temps - h*3600 - m*60;
        out << "[" << h << ":" << m << ":" << s << "]";
    }