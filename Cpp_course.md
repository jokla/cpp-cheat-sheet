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
