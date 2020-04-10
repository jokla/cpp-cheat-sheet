# Automatic Type Deduction: auto
- The auto keyword can be used to let the compiler decide the data type itself.
-  To get the data type from the compiler, we have used the typeid operator that is defined in the header typeinfo.
# decltype
- decltype is used to determine the type of an expression or entity.
- We can use auto to create variables, but decltype returns the type of an expression containing variables.
# Automatic Return Type
- Using auto and decltype together, a function template is able to automatically deduce its return type.
```c++
template <typename T1, typename T2>
auto add(T1 fir, T2 sec) -> decltype( fir + sec ) 
{ 
  return fir + sec;
}
```
C++14 makes things even simpler
```c++
template <typename T1, typename T2>
auto add(T1 fir, T2 sec){
    return fir + sec;
}
```
# 5) Explicit cast

## dynamic_cast [*](https://www.bogotobogo.com/cplusplus/dynamic_cast.php)
`dynamic_cast` converts a pointer or reference of a class to a pointer or reference in the same inheritance hierarchy.
- It can only be used with polymorphic classes. With dynamic_cast, we cast up, down, and across the inheritance hierarchy.
- Type information at run time is used to determine if the cast is valid.
- If the cast is not possible, we will get a nullptr in case of a pointer, and an std::bad_cast-exception in case of a reference.
- Mostly used when converting from a derived class to a base class.
## static_cast
- It can only perform all the conversions that are well-defined by the compiler
- Performed duting compile time
## const_cast
- It allows us to remove or add the const or volatile property from a variable.
## reinterpret_cast
- It allows us to convert a pointer of a particular type to a pointer of any other type, regardless of whether the types are related or not.
- It also allows conversion between a pointer and an integral.
- If a pointer is cast into another type, casting it back would return the original value.

## typeid 
It can be used to retrieve the type of a variable or object at runtime. To use typeid, we must include the <typeinfo> header. The operator returns a type_info object that has various methods of its own.

# 6) Unified Initialization with {}
Variables can be declared directly with {}
```c++
std::string str{"my String"};
int i{2011};
```

# 7) const, constexpr, and volatile
## const
- Any variable initialized with the const keyword cannot be modified later on. It is constant.
- Const Variables or attributes of a class must always be initialized.
- Const class methods can only be invoked by const instances of the class.
- Both the pointer and the data being pointed to can be const.
  - `int const* ip = &i;` the value being pointed to is constant.
  - `int* const p = &i;` the pointer is constant. It cannot point to a different pointer.
  - `const int* const p = &i;` `p` is a constant pointer, `* const` points to an int that is const.
  ## constexpr
A constant expression:
- can be evaluated at compile time
- gives the compiler deep insight into the code
- is implicitly thread-safe
- can be constructed in the read-only memory (ROM-able)
## Variables
A `constexpr` variable:
- is implicitly const.
- has to be initialized.
- requires a constant expression for initialization.
```c++ constexpr double myDouble= 5.2;```
## User-Defined types
Objects are created by the invocation of the constructor. The constructor has a few special rules.
A constexpr constructor:
- can only be invoked with constant expressions.
- cannot use exception handling.
- has to be declared as default or delete or the function body must be empty (C++11).
```c++
struct MyDouble{
  double myVal;
  constexpr MyDouble(double v): myVal(v){} 
  constexpr double getVal(){return myVal;}
};
```
## Functions
`constexpr` functions are functions that have the potential to run at compile time. This means we can perform a lot of calculations at compile time, with the results available at runtime and stored as a constant in the ROM. In addition, constexpr functions are implicitly inline.
# volatile
The volatile variable is one whose value may change due to an external event.


