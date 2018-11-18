# The basics

## 1.6	Constants
- *const* :	meaning	roughly	“I	promise	not	to	change	this	value”. The	value	of	a	 const 	can	be	calculated
at	run	time.
- *constexpr* :	meaning	roughly	“to	be	evaluated	at	compile	time”. The value	of	a	 constexpr 	must	be	calculated
by	the	compiler. The idea is to spend time in compilation and save time at run time.

## 1.7 For Loops
```
void print()
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
