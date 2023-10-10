Date: 2023-10-10
---
```cpp
template<typename T>
size_t set<T>::tirer_couches()
{
    //
    static auto seed = std::chrono::system_clock::now().time_since_epoch().count();
    static std::minstd_rand0 gen (static_cast<unsigned int>(seed));
    size_t i = 1;
    auto g = gen();
    for(; g % 2 != 0; ++i)
    {
        g /= 2;
    }
    return i; 
    
}