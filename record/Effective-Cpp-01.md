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
