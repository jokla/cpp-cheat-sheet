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
[] is the capture list. It can be: [] capture nothing, [&] capture all local names by reference, [=] capture all by copy, [=x] or [&] to capture only one variable.


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

- for_each(first_iterator, last_iterator, function) - For each element do function (element)
- sort(first_iterator, last_iterator) – To sort the given vector.
- reverse(first_iterator, last_iterator) – To reverse a vector.
- *max_element (first_iterator, last_iterator) – To find the maximum element of a vector.
- *min_element (first_iterator, last_iterator) – To find the minimum element of a vector.
- accumulate(first_iterator, last_iterator, initial value of sum) – Does the summation of vector elements
- count(first_iterator, last_iterator,x) – To count the occurrences of x in vector.
- count_if (first_iterator, last_iterator, predicate)
- find(first_iterator, last_iterator, x) – Points to last address of vector ((name_of_vector).end()) if element is not present in vector.
- find_if(first_iterator, last_iterator, predicate)
- binary_search(first_iterator, last_iterator, x) – Tests whether x exists in sorted vector or not.
- lower_bound(first_iterator, last_iterator, x) – returns an iterator pointing to the first element in the range [first,last) which has a value not less than ‘x’.
- upper_bound(first_iterator, last_iterator, x) – returns an iterator pointing to the first element in the range [first,last) which has a value greater than ‘x’.
- arr.erase(position to be deleted) – This erases selected element in vector and shifts and resizes the vector elements accordingly.
- arr.erase(unique(arr.begin(),arr.end()),arr.end()) – This erases the duplicate occurrences in sorted vector in a single line.
- next_permutation(first_iterator, last_iterator) – This modified the vector to its next permutation.
- prev_permutation(first_iterator, last_iterator) – This modified the vector to its previous permutation.
- distance(first_iterator,desired_position) – It returns the distance of desired position from the first iterator.This function is very useful while finding the index.


# Polymorphism

## Compile time polymorphism:

- Function Overloading
- Operator Overloading

# Runtime polymorphism: 
- Function overriding (derived class and virtual functions)

# Format output
```c++
#include <iomanip>
// Print with spaces
std::cout<<"Ints"<<std::setw(15)<<"Floats"<<std::setw(15)<<"Doubles"<< "\n";

// Print with tabs
std::cout<<"Int"<<"\tFloats"<<"\tDoubles\n";
std::cout<< a <<"\t"<< b <<"\t"<< c <<"\n"
```
# Print a vector
```c++
std::vector<int> v;

// Fill vector

std::copy(v.begin(), v.end(), std::ostream_iterator<int>(std::cout, " "));
```

# Reading and writing to a file
File IO Steps:

 - Include the `<fstream>` library 
 - Create a stream (input, output, both)
      - `ofstream myfile;` (for writing to a file)
      - `ifstream myfile;` (for reading a file)
      - `fstream myfile;` (for reading and writing a file)
 - Open the file  `myfile.open(“filename”)`;
 - Write or read the file
 - Close the file `myfile.close()`;

```c++ 
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main () {
    string line;
    //create an output stream to write to the file
    //append the new lines to the end of the file
    ofstream myfileI ("input.txt", ios::app);
    if (myfileI.is_open())
    {
        myfileI << "\nI am adding a line.\n";
        myfileI << "I am adding another line.\n";
        myfileI.close();
    }
    else cout << "Unable to open file for writing";
  
    //create an input stream to write to the file
    ifstream myfileO ("input.txt");
    if (myfileO.is_open())
    {
        while ( getline (myfileO,line) )
        {
            cout << line << '\n';
        }
        myfileO.close();
    }
    
    else cout << "Unable to open file for reading";
    
    return 0;
}
```
- Get a string from input and convert to a number

```c++
 #include <iostream>
 #include <string>
 #include <sstream>

 int main ()
 {
   std::string stringLength;
   float inches = 0;

   std::cout << "Enter number of inches: ";
   std::getline (std::cin,stringLength);
   std::stringstream(stringLength) >> inches;
   return 0;
 }
 ```
 
 # C++11

 ## Decltype And Typeid
 
* **decltype** is a way to specify a type: it gives you back a type which corresponds to the type of the expression
 
```c++ 
int foo();
int n = 10;
decltype(n) a = 20;             // a is an "int" [id-expression]
decltype((n)) b = a;            // b is an "int &" [(n) is an lvalue]
decltype(foo()) c = foo();      // c is an "int" [rvalue]
```
* decltype can be useful to define the return type of a function with auto
```c++ 
#include <iostream>
using namespace std;

template<class T, class S>
auto test(T value1, S value2) -> decltype(value1 + value2) {
	return value1 + value2;
}

int get(){
	return 555;
}

auto test2() -> decltype(get()){
	return get();
}

int main() {
	auto value = 6;
	auto text = "Hi";

	cout << test(4, 5) << endl;
	cout << test2() << endl;
	return 0;
}
```
