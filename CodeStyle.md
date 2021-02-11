# C++ Style Guide
Last update: 29.04.2020

## Table of Contents
| Title | |
|:--|:--|
| [Naming](#naming) | [File naming](#file-naming) &nbsp;&nbsp; [Variable naming](#variable-naming) &nbsp;&nbsp; [Constants naming](#constants-naming) &nbsp;&nbsp; [Type naming](#type-naming) &nbsp;&nbsp; [Enums naming](#enums-naming) &nbsp;&nbsp; [Class members naming](#class-members-naming) &nbsp;&nbsp; [Plural form naming](#plural-form-naming) &nbsp;&nbsp; [Function and methods naming](#function-and-methods-naming) &nbsp;&nbsp; [Boolean naming](#boolean-naming) |
| [Formatting](#formatting) | [Spaces vs. Tabs](#spaces-vs-tabs) &nbsp;&nbsp; [Compound statement](#compound-statement) &nbsp;&nbsp; [Switch statement](#switch-statement) &nbsp;&nbsp; [Whitespace](#whitespace) &nbsp;&nbsp; [Line Breaks](#line-breaks) &nbsp;&nbsp; [Preprocessor idents](#preprocessor-idents) |
| [Code structure](#code-structure) | [Order of includes](#order-of-includes) &nbsp;&nbsp; [Class structure](#class-structure) &nbsp;&nbsp; [Keep lines a reasonable length](#keep-lines-a-reasonable-length) |
| [C++ Features](#c-features) | [Initialize list](#initialize-list) &nbsp;&nbsp; [Const](#const) &nbsp;&nbsp; [Comments](#comments) &nbsp;&nbsp; [Pointers and references](#pointers-and-references) &nbsp;&nbsp; [Casts](#casts) &nbsp;&nbsp; [Namespaces](#namespaces) &nbsp;&nbsp; [Getter and setter](#getter-and-setter) &nbsp;&nbsp; [Passing by value or const reference](#passing-by-value-or-const-reference) &nbsp;&nbsp; [Lambdas](#lambdas) &nbsp;&nbsp; [Smart Pointers](#smart-pointers) &nbsp;&nbsp; [Auto](#auto) &nbsp;&nbsp; [R-value references](#r-value-references) |
| [References](#references) |  |

## Naming


### File naming
```c++
FilenameForClass.hpp
FilenameForClass.cpp

// For Wrapper:
SDL2_H.hpp
Optional_H.hpp
```

### Variable naming
```c++
int name = 0;
int veryLongName = 1;
```

### Constants naming
```c++
const int NUMBER_ENEMY_TEXTURES = 10;
const int NES = 2302;
```

### Type naming
```c++
class Texture;
template<typename HashValue>;
```

### Enums naming
```c++
enum Colors {
    WHITE = 0,
    BLACK,
    RED,
    GREEN,
    BLUE
};
```

### Class members naming
```c++
int m_myVariable;
int m_otherVariable;
```

### Plural form naming
```c++
vector<Point> points;
std::array<int, 20> values;
```

### Function and methods naming
```c++
int calculateSomething(int n);
void toUpper(std::string& someStr);

void exportHtmlSource(); // NOT: exportHTMLSource();
void openDvdPlayer(); // NOT: openDVDPlayer();
```

### Boolean naming
```c++
bool isOk = false;
bool isKeyTriggered = false;

bool isCorrectString() const;
// or
bool hasLicense() const;
bool canEvaluate() const;
bool shouldSort() const;
```

## Formatting


### Spaces vs. Tabs
Use only spaces, and indent 2 spaces at a time.

### Compound statement
```c++
if (isComplete) { a = 0; } // Good
if (isComplete) { // Good
  a = 1;
} else {
  a = 2;
}
if (isComplete) a = 3; // Bad
```

### Switch statement
Switch statements are usually very verbose and thus they are often subject of various shortening and whitespace tricks. The goal is to make them as readable as possible without wasting too much vertical space.
```c++
// Bad
std::size_t size;
switch (type) {
  case Type::Byte:     size = 8;   break;
  case Type::Short:    size = 16;  break;
  // Type::Int missing but the compiler doesn't warn so it fails at runtime
  case Type::Long:     size = 64;  break;
  case Type::LongLong: size = 128; break;

  default:
    Error() << "Unknown type";
    size = 0;
}

// Good
std::size_t size = 0;
switch (type) {
  case Type::Byte:     size = 8;   break;
  case Type::Short:    size = 16;  break;
  case Type::Long:     size = 64;  break;
  case Type::LongLong: size = 128; break;
} // warning: Type::Int not handled in switch statement

if (!size) { Error() << "Unknown type"; }
```

### Whitespace
Whitespace is not allowed inside parentheses and between function name or branch/loop statement and left parenthesis (or between constructed variable name and left brace) and before semicolon. It must be around block braces if the block is not empty. It must not be space before, but after the comma.
```c++
if ( statement&&! other ){foo ( a ,b ) ;} // Bad
if (statement && !other) { foo(a, b); }   // Good

doSomething(a, b, c, d); // NOT: doSomething(a,b,c,d);
for (i = 0; i < 10; i++) // NOT: for(i=0;i<10;i++)
```

Whitespace should be around operators with low precedence (namely `+`, `-`, `<<`, `>>` but not on unary `-`), around all boolean and comparison operators (`&&`, `||`, `==`, `!=`, `<`, `<=`, `>=`, `>`), around = and related operators and around ternary operator. Whitespace shouldn't be around `/`, `*`, `%` to indicate they have precedence before addition and subtraction. Whitespace can or need not to be around binary operators (`&`, `|`, `^`), whichever looks better in particular content.
```c++
r = a*3 + b/2;
```

### Line Breaks
Operators start at the beginning of the new line

```c++
if (longExpression
    || otherLongExpression
    || otherOtherLongExpression) { // Good
}

if (longExpression ||
    otherLongExpression ||
    otherOtherLongExpression) { // Bad
}
```

### Preprocessor idents
```c++
#ifdef NDEBUG
 #define OUT OutputHelper::release
#else
 #define OUT OutputHelper(__FILE__, __LINE__, "\033[32m"/*Green*/).debug
#endif // NDEBUG
```

## Code structure


### Order of includes
For `Test.cpp` file, order your includes as follows:

1. `Test.h` header
2. C system headers (`<cstdio>`, `<cstdlib>`)
3. C++ system headers (`<string>`, `<vector>`)
4. Other libraries headers
5. Your projects headers

Separate each non-empty group with one blank line.

```c++
#include "Test.h"

#include <sys/types.h>
#include <unistd.h>

#include <string>
#include <vector>

#include "base/basictypes.h"
#include "base/commandlineflags.h"

#include "foo/server/bar.h"
```

### Class structure
For `MyClass` class, order visibility:
1. `public`
2. `protected`
3. `private`

Order constructors, destructor, methods, variables:
1. default constructor / `instance()`
2. constructors
3. destructor
4. copy constructor and assignment operator
5. move constructor and move operator
6. static methods
7. methods
8. variables

```c++
class MyClass {
public:
  MyClass();
  MyClass(float a, float b);
  ~MyClass();

  MyClass(MyClass const&);
  MyClass& operator=(MyClass const&);
  
  void static someStaticMethod();
  
  void setPrivateValue(int value);
  int getPrivateValue() const;

private:
  void privateMethod();
  
  int m_privateValue;
};
```

### Keep lines a reasonable length
Many projects and coding standards have a soft guideline that one should try to use less than about 80 or 100 characters per line. Such code is generally easier to read. It also makes it possible to have two separate files next to each other on one screen without having a tiny font.

```c++
// Bad Idea
// Hard to follow
if (x && y && myFunctionThatReturnsBool() && caseNumber3 && (15 > 12 || 2 < 3)) {
}

// Good Idea
// Logical grouping, easier to read
if (x && y && myFunctionThatReturnsBool()
    && caseNumber3
    && (15 > 12 || 2 < 3)) {
}

// Also nice
SDL_SetRenderDrawColor(m_renderer,
                       color.red,
                       color.green,
                       color.blue,
                       color.alpha);
```

## C++ Features


### Initialize list
Use all members class with default constructors too.
```c++
EventHandler::EventHandler() :
  m_event(),
  m_mouse(),
  m_keyboard(),
  m_isRun(true),
  m_isWindowFocus(true)
{

}
```

### Const
Write `const` everywhere is needed. Prefer first keyword `const`. Example: `const Type&` or `const Type*`

```c++
int getCode() const {} // Getter
for (const auto& item : items) {}
```

### Comments
Comment blocks should use `//`, not `/**/`. Using `//` makes it much easier to comment out a block of code while debugging.

```c++
// Good
// TODO State where button pressed and not hovered, but left mouse key not released
if ((isLeftMousePressed || isKeyPressed) && isHover) {
    m_state = PRESSED;
}

// Good, but avoid if possible
bool isKeyPressed = Core::keyboard().isPressed(KEY(SPACE)); // NOTE Careful with TextEdit and SPACE

// Comment style
// Prefer double slash
// And whitespace before comment text
```

### Pointers and references
```c++
int a = 10;
int* pInt = &a; // Good
int& refInt = a; // Good
int *pInt2 = &a; // Bad
```

### Casts
Don't use C-style casts

```c++
int* blockOfMemory = static_cast<int*>(malloc(100)); // Good
int* blockOfMemory = (int*)malloc(100); // Bad

auto tick = static_cast<std::chrono::duration<double> >(1.0 / fps); // Good
```

### Namespaces
Names representing namespaces should be all lowercase. For long namespace names use alias. Don't use global function then possible.

```c++
namespace timer = std::chrono; // Good

using namespace std; // Bad (Using in global scope)

if (true) { // Good
    using namespace std;
    cout << 1 << endl;
}

exit(1); // Bad
std::exit(1); // Good
```

### Getter and setter
Preffer getter with word 'get'. Don't compute in getter methods. In setter using name 'value' or typename.

```c++
Point getCenter() const;
Point getPosition() const;

void setPosition(Point value);
// or
void setPosition(Point point);
```

*Exceptions:*
```c++
static Core& instance();

EventHandler& event();
Window& window();
Renderer& renderer();
```

### Passing by value or const reference
The general rule of thumb for passing by value is when you would end up making a copy anyway. That is to say that rather than doing this:

```c++
// https://stackoverflow.com/questions/24543330/when-is-a-const-reference-better-than-pass-by-value-in-c11

void f(const std::vector<int>& x) {
    std::vector<int> y(x);
    // stuff
}
```

where you first pass a const-ref and then copy it, you should do this instead:

```c++
void f(std::vector<int> x) {
    // work with x instead
}
```

### Lambdas
Place the capture-list, parameter list, return type, and opening brace on the first line, the body indented on the following lines, and the closing brace on a new line.
Optionally, place the lambda completely on one line if it fits.

```c++
[]() -> bool {
    something();
    return isSomethingElse();
}

foo( [] { return true; } );
```

Avoid default mode for capture list.
```c++
int hp = 42;
[&hp]() -> bool { // Don't use [&] or [=]
    something();
    return isSomethingElse();
}
```

### Smart Pointers
Preffer `std::make_shared` or `std::make_unique`

```c++
m_window = std::make_unique<Window>(titleName, width, height);
```

### Auto
Remember `auto` reset cv qualifiers and references. If type simple avoid `auto`.

```c++
auto& player = GET_RESOURCE(Player, "player");

for (const auto& button : m_buttons) {
    button.draw();
}
```

### R-value references
```c++
for (auto&& item : items) {}
```

## References
* [Google]( https://google.github.io/styleguide/cppguide.html )
* [GeoSoft]( https://geosoft.no/development/cppstyle.html )
* [C++ Core Guidelines]( https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines )
* [Qt]( https://wiki.qt.io/Qt_Coding_Style )
* [PVS-Studio]( https://www.viva64.com/ru/b/0391 )
* [Mozilla]( https://firefox-source-docs.mozilla.org/code-quality/coding-style/index.html )
* [Cpp Best Practices]( https://github.com/lefticus/cppbestpractices/blob/master/03-Style.md )
* [LLVM]( https://llvm.org/docs/CodingStandards.html )
* [Corrade]( https://doc.magnum.graphics/corrade/corrade-coding-style.html )