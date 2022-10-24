# Effective cpp 00

## Introduction

### Terminology

### signature differences when read this book

每个函数的声明揭示其签名式(signature)，也就是参数和返回类型。一个函数
的签名等同于该函数的类型。

**Sometimes signature includes the return type, sometimes it doesn't.**

More see [Is the return type part of the function signature?](https://stackoverflow.com/questions/290038/is-the-return-type-part-of-the-function-signature)

C++对签名式的官方定义并不包括函数的返回类型，不过本书把返回类型视为签名的一部分，这样比较有帮助。

### keyword `explicit`

explicit关键字只能用于构造函数的声明中，用于阻止隐式转换。

```cpp
class B{
public:
    explicit B(int x = 0, bool b = true); // default constructor;
}
```

```cpp
class C{
public:
    explicit C(int x);
}
```

The constructors for classes B and C are declared explicit here. That
prevents them from being used to perform implicit type conversions,
though they may still be used for explicit type conversions

More see [What does the explicit keyword mean?](https://stackoverflow.com/questions/121162/what-does-the-explicit-keyword-mean)

### the “=” syntax can also be used to call the copy constructor

```cpp
Widget w3 = w2;
```

Fortunately,  copy  construction  is  easy  to  distinguish  from  copy  as-
signment. If a new object is being defined (such as w3 in the statement
above), a constructor has to be called; it can’t be an assignment. If no
new object is being defined (such as in the “w1= w2” statement above),
no constructor can be involved, so it’s an assignment.

The copy constructor is a particularly important function, because it
defines how an object is passed by value. For example, consider this:

```cpp
bool asAcceptableQuality(Widget w);
// ...
Widget aWidge;
if (hasAcceptableQuality(aWidget))
    // ...
```

The parameter w is passed to hasAcceptableQuality by value, so in the
call above, aWidget is copied into w. The copying is done by Widget’s
copy  constructor.

### function  objects

objects that act like function.

STL

### undefined behavior

The C++ standard doesn’t define what happens when you do something

```cpp
int *p = 0; // p is a null pointer
std::cout << *p; // dereference a null pointer
                 // yields undefined behavior

char name[] = "Darla"; // name is an array of size 6(don't for get the trailing null!)
                       // yields undefined behavior
```

### Cpp without interface(language element)

when talking about interfaces in cpp as a fairly general de-sign idea.
