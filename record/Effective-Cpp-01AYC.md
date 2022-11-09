# Effective cpp 01

## Item01 View C++ as a federation of languages

**Things to Remember**

- Rules for effective C++ programming vary, depending on the part of C++ you are using.

Four sublanguages:

- C
- Object-Oriented C++
- Template C++
- STL

## Item02 Prefer consts, enums, and inlines to #defines

**Things to Remember**

- For simple constants, prefer const objects or enums to #defines
- For function-like macros, prefer inline functions to #defines.

### #defines disadvantages

- No type checking
- No scoping
- No redefinition checking
- No debugging support

### const replacement

```cpp
// double(float)
const double AspectsRatio = 1.653;

// string
const std::string authorName("Scott Meyers");

// class-specific  constants
class GamePlayer {
private:
    static const int NumTurns = 5;
    int scores[NumTurns];
    // ...
};
```

### enum hack

你的编译器（错误地）不允许“static整数型class常量”完成“inclass初值设定
可改用所谓的"theenum hack"补偿做法。

### template replacement

可以获得宏带来的效率以及一般函数的所有可预料行为和类型安全性(typesafety）

```cpp
template<typename T>
inline void callWithMax(const T& a, const T& b) {
    f(a > b ? a : b);
}
```



More see 
- [What is the difference between declaration and definition of a variable in C++? [duplicate]](https://stackoverflow.com/questions/29954191/what-is-the-difference-between-declaration-and-definition-of-a-variable-in-c)
- [What distinguishes the declaration, the definition and the initialization of a variable?](https://stackoverflow.com/questions/23345554/what-distinguishes-the-declaration-the-definition-and-the-initialization-of-a-v)
- [odr-used 是什么？为什么会存在这样的概念？ - d41d8c的回答 - 知乎](https://www.zhihu.com/question/307786707/answer/565058772)

> What  you  see  above  is  a declaration  for NumTurns,  not  a  definition.

What "addressable entity" refers here is "instance" of static const data type. No instance, no address, i.e its only a declaration.

## Item03 Use const whenever possible

**Things to Remember**
