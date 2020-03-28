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
