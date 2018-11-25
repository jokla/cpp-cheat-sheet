# The basics

## 1.6	Constants
- *const* :	meaning	roughly	“I	promise	not	to	change	this	value”. The	value	of	a	 const 	can	be	calculated
at	run	time.
- *constexpr* :	meaning	roughly	“to	be	evaluated	at	compile	time”. The value	of	a	 constexpr 	must	be	calculated
by	the	compiler. The idea is to spend time in compilation and save time at run time.

## 1.7 For Loops
```c++
vod print()
{
    int v[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

    for (auto i = 0; i != 10; ++i)
        cout << v[i] << '\n';

    for (auto x : v) //	for	each	x	in	v
        cout << x << '\n';

    for (auto x : { 10, 21, 32, 43, 54, 65 })
        cout << x << '\n';
    //	...
}
```

## 1.7 The Null Pointer
- Use nullptr instead of NULL or 0

# Essential Operation

## Class Constructors 5.1

- `=default`  (force the compiler to use a constructor as default one) and `=delete` (disable the possibility to use certain functions) see [here](https://www.bogotobogo.com/cplusplus/C11/C11_default_delete_specifier.php) 

# Algoritms

- `find`
```c++
bool has_c(const string & s, char c) //	does s contain the character c?
{
  return find(s.begin(), s.end(), c) != s.end();
}
```   
   
- `find_if`: looking for element fulfilling a specified requirement. We can use a predicate
```c++
struct Greater_than {
    int val;
    Greater_than(int v): val{ v } { }
    bool operator()(const pair<string, int>& r) const { return r.second > val; }
};

(...)

map<string, int> m
auto p = find_if(m.begin(), m.end(), Greater_than{ 23 });
```
Or a lamba function:
```c++
auto p = find_if(m.begin(), m.end(), [](const pair<string, int>& r) { return r.second > 23; });
```


- `find_all`: (to implement) find all the occurences and return them.

```c++
vector<string::iterator> find_all(string& s, char c) //	find all occurrences of c in s
{
    vector<string::iterator> res;
    for (auto p = s.begin(); p != s.end(); ++p)
        if (*p == c)
            res.push_back(p);
    return res;
}
```
