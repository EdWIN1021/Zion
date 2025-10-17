# What are Coding Standards?

Most game companies have a Coding Standard that the company's programmers are expected to follow.

Some standards include high-level principles, such as "When in Rome, do as the Romans do" or "Write your code as if you are writing it for someone else."

Some standards include general rules of usage, such as "Always prefer constants to #defines" or "When in doubt, pass anything bigger than a pointer by const reference."

Other standards include blanket precepts, such as "Do not use smart pointers such as shared_ptr" or "Do not use Boost or STL".

Many standards also include code style and formatting rules such as "Use ProperCase verbs for function names" or "Use m_camelCase nouns for member variables."

Why have Coding Standards?

Professional programmers read and comprehend code faster and at a much higher level than do amateur and junior programmers.  Much like musicians read chords and phrases in a single thought (rather than note-by-note) - and you just read the word "musicians" as a single thought (rather than letter-by-letter), so do fluent programmers read code in whole "chunks" at a time.

Having a common coding standard - and consistent style - is part of what makes this possible.  It allows the programmer to acclimate to a codebase, becoming familiar with its idioms, its paradigms, its cadence, anticipating and recognizing its expressions at a pre-cognitive level, much like an athlete's "muscle-memory".

No coding standard makes all programmers happy on all points.  Few programmers personally agree with every single point of a coding standard - even a company's Technical Director might inherit an existing coding standard, or draft it based on consensus rather than personal beliefs.

Nevertheless, most veteran programmers strongly prefer the advantages of working under a common coding standard as the advantages are clear.

# A Coding Meta-Standard

The following is an attempt to cite and compare examples of each of these items from various game companies and other sources.

Standards items often provide reasoning behind them.  We will do so likewise and, in some cases, take sides and make recommendations on specific points.

Sources cited here include:

- Insomniac Games' core coding standard
- Input from various senior members of the game development community
- Specific input from Guildhall Software Development faculty (Eiserloh, Wofford, Wouter, Forseth, Butler)

**SD1** indicates coding standards used in the **Software Development for Games I (HGME 6311)** course at Guildhall.

## High-level principles

Keep in mind that these coding standards apply specifically to game programming, the needs of which may differ somewhat or diverge entirely from traditional software engineering needs.  For example, the ability to perform rapid iteration on features and gameplay ("finding the fun") is of paramount importance to game developers, but considerably less so outside of games where engineering requirements are typically more well-known and well-defined in advance.  All of these principles apply to the **SD1** coding standard.

Insomniac: Write your code as if you are writing it for someone else. Which, in fact, you are.

Wouter: Do not overgeneralize your code.  Do not undergeneralize your code.

Wofford: Don't mistake "it's working" for "I understand it."

Butler: if it looks like you fixed the bug, you don't understand how you fixed it, you did not fix the bug.

Wofford: "If it ain’t tested, it ain’t working."

Eiserloh: Favor readability first, maintainability second, optimizability third.

Wofford/Eiserloh: Code is communication; code is thought.

Eiserloh: Plan big, execute small.  Keep it simple, stupid!

Butler: If you choose a coding standard because you prefer it, you don't understand the point of coding standards.

Butler: Being consistent is more important than any of your opinions.

Butler: No matter how much you hate any coding standard, you will come to accept it if you use it for a while.

Butler: There is already a coding standard for most of the syntax in C++, and that standard is the written English language. Our eyes are already trained to recognize certain patterns with spacing and punctuation, so just go with those established rules when they apply.

## Use of External Code and Libraries

**SD1 (and beyond)**: No external code or libraries (including source-only libraries, .LIBs, .DLLs, etc.) should ever be added to your Engine or any of your projects or games without express explicit faculty permission.  We will add several external libraries to our Engines as part of class assignments, including: OpenGL, DirectX, fmod, TinyXml2, and stb_image.

## Naming conventions

**SD1,** Insomniac, Eiserloh: "When choosing a name, prefer long names to abbreviated names.  Prefer descriptive names to arbitrary ones."

**SD1**, Butler: If a consistent term for a certain thing is already commonly used in the code base, don't start using other terms just because they make more sense to you. For example, don't refer to "object space" if everywhere else in the code it is referred to as "local space".

Butler: "Snake case" is horrible because of the extra time it takes to type underscores.

### Namespaces and "using"

**SD1**, Insomniac, Eiserloh: Single-depth namespaces only; common core elements (math, color, assert, time) and game code can remain in public namespace.  **Do not use the the "using namespace" idiom**.  Explicitly scope all namespaced items in all contexts (e.g. always "std::string", never "string").  **SD1: Do not create additional namespaces** (such as Engine or Math, etc.) within your Engine code for now.

### File names

**SD1**: C++ Source files should have .cpp and .hpp extensions (to disambiguate vs. c-style headers, which also use .h), and are ProperCase which matches the name of the primary class in the file (e.g. Asteroid.cpp and Asteroid.hpp for class Asteroid).  Exception: Platform-specific files (rare!) should be named with a platform extension after the name, separated by underscore, e.g. InputSystem_Win32.cpp or RenderContext_OpenGL.cpp.  Non-class files (such as Main or MathUtils) are also ProperCase.

### Type names

**SD1**, Insomniac, Eiserloh: Use ProperCase (a.k.a. PascalCase) for names of Classes, Structs, Typedefs, and Namespaces.  Do not prefix such names with "C" or any other name decoration.

### Function and Method names

**SD1**, Eiserloh: All function and method names begin with a primary action verb, e.g. "Draw" or "Get" or "Load" or "Update", etc.

**SD1**: All function names use ProperCase or camelCase (your choice - I prefer ProperCase).  However, you must be consistent.

### Standard types

**SD1**, Insomniac, Eiserloh: Use naked standard type names (e.g. float, double, size_t).  Use of specific-sized integer types (e.g. uint8_t, int64_t) is both allowed and encouraged.

### Local variables

Insomniac: Use snake_case for local variables (e.g. points_scored).

**SD1**, Eiserloh: Use camelCase for local variables (e.g. pointsScored).  Variable names are generally nouns.  Array/collection names are usually plural nouns.

### Member variables

Insomniac: Use m_ProperCase for member variables (e.g. m_PointsScored).

Eiserloh: Use m_camelCase for member variables (e.g. m_pointsScored).  Member variable names are generally nouns (e.g. m_position), with arrays/collections as plural nouns (e.g. m_bullets).

**SD1**: Choose either of the above (m_camelCase or m_ProperCase), but be consistent.  I recommend m_camelCase for member variables.

### Global variables

Insomniac: Use g_ProperCase for global variables (e.g. g_PointsScored).

Eiserloh: Use g_camelCase for global variables (e.g. g_pointsScored).  Global variable names are generally nouns.  Unique singleton-like global variables are named "g_theSomething" (e.g. g_theApp).

**SD1**: Use the same as your standard for member variables, but with a "g_" prefix (for "global") instead of "m_" (for "member").

### Static variables

Insomniac: Use s_ProperCase for file static, class static, and function-static variables (e.g. s_RegisteredTextures).

Eiserloh: Use s_camelCase for file static, class static, and function-static variables (e.g. s_registeredTextures.  Static variable names are generally nouns.

**SD1**: Use the same as your standard for member variables, but with a "s_" prefix (for "static") instead of "m_" (for "member").

Butler: Using mProperCase, gProperCase, and sProperCase is just as readable as the above and avoids the underscores.

### Static constants

**SD1**, Eiserloh: Where possible and when appropriate, hardcoded constants should belong to a class, as static const member variables declared inside the class and defined in the .CPP.  Alternatively, they may be defined constexpr in a header file (including GameCommon.hpp) or as const global variables declared in GameCommon.hpp and defined in GameCommon.cpp.  Constant names should be ALL_CAPS, and generally be referred to by their scoped names as appropriate, e.g. Bullet::DEFAULT_RADIUS.  Gameplay "constant" data values intended to become data-driven should be held in variables instead.

### **Enumerated values and constants**

Insomniac: Use kProperCase for constants and enumeration values.  Enumerations should typically be scoped within a class or namespace.

**SD1**, Eiserloh, Butler: For constants and enumeration values, use UPPER_CASE_WITH_UNDERSCORES; you may alternatively use eProperCase for enum values and/or kProperCase for standalone constants.

**SD1**, Eiserloh: Most enumerations should be named types, with enumerated values in all caps, e.g. enum DamageType { DAMAGE_TYPE_FIRE };

**SD1**, Eiserloh: Prefer enum class for enumerations whose numeric values are irrelevant (e.g. game state); prefer traditional enums (or constexpr, or const variables) for constants/enumerations intended to be used primarily as numbers (e.g. indexes, array sizes, wraparounds, arithmetic constants).  Plain enum (non enum classes) should ideally be declared inside a class's definition namespace in cases where ownership is clear.

**SD1**, Eiserloh: You may use **enum** or **enum class**, per your choice.  Enums are preferred where values will be used as numbers; enum classes are preferred where the actual values of the items do not matter (just mutually exclusive choices).

**SD1**, Eiserloh: Most simple enumerations should have a "NUM_" enumeration at their end and, where appropriate, an INVALID enumeration (equal to -1) at their start.  This facilitates automatic looping through enumeration list values, sizing of arrays indexed by the enumeration, and a clear value for uninitialized / illegal items.  For example:

enum Direction  
{  
    DIRECTION_UNKNOWN = -1,  
    DIRECTION_EAST,  
    DIRECTION_NORTH,  
    DIRECTION_WEST,  
    DIRECTION_SOUTH,  
    NUM_DIRECTIONS // automatically equals 4  
};

or, alternatively, you can use enum class (recommended for cases where you don't intend to use the numeric value of the enum, and just want mutually-exclusive options):

enum class Direction  
{  
    UNKNOWN = -1,  
    EAST,           // used as Direction::EAST; must be explicitly cast to an integer if you intend to use it for its actual numeric value  
    NORTH,  
    WEST,  
    SOUTH,  
};

### Pointers

**SD1**, Insomniac, Eiserloh: Prefer naked pointers or smart indexes; avoid shared_ptr, make_shared, and similar "smart pointer" classes (though unique_ptr is fine).

**SD1**, Insomniac, Wofford, Eiserloh: Pointer types should always have an asterisk, and the asterisk is grouped with the type, not the variable (e.g. float* f;).

- Correct:
    - int* p = nullptr;  // type is pointer-to-int; pointer asterisk is always left-aligned, with the type
        
    - int x = *p;        // dereference is always right-aligned, with the pointer variable being derefereneced
        
    - int a = b * c;     // multiplication is always spaced equally on both sides: "b * c" or "b*c"  
          
        
- Incorrect: 
    - int *p = nullptr; // BAD: looks like a dereference, but it isn't; also, looks like type is "int"
        
    - int x =* p;       // BAD: looks like an operator, but it isn't
        
    - int a = b *c;     // BAD: looks like c is getting dereferenced, but it isn't
        

Insomniac, Eiserloh, Butler: : Do not typedef pointers into types, including function pointer types (Eiserloh exception: pointer-to-member-function typedefs)

- Correct: 
    
        typedef int (FunctionType)(int, float);  
        FunctionType* myFunctionPointer = nullptr; // makes sense, pointers can be null
    

- Incorrect:
    
        int (*FunctionPointerType)(int, float);  
        FunctionPointerType myFunctionPointer = nullptr; // wait, this is a pointer? (without the name, I wouldn't know)  
      
    

Butler: : Don't use typedefs unless you really can't think of a better alternative, and never ever use a typedef just because you like your names better than the data types. Data types are already a common part of the language and it makes code confusing for others to read if you typedef away all the native data types.

  

#define Macros

**SD1**, Insomniac, Eiserloh, Butler: Use #define only when nothing else would suffice.  Use UPPERCASE_WITH_UNDERSCORES for both NAKED_DEFINES as well as MACRO_FUNCTIONS().  _See below for additional standards relating to the use of #define._  For constants, prefer the use of (strongly-typed) **constexpr**, or **enum** (or **enum class**) where possible.

### Accessors and Mutators

**SD1**, Insomniac, Eiserloh: Mutators start with "Set" (e.g. "void SetSpeed( float speed )").  Accessors start with "Get" (e.g.  "float GetSpeed() const"), except boolean accessors which should begin with "Is" or "Does" or "Has" (etc.), for more natural reading (e.g. "bool IsActive() const").  Do not create non-verb-named accessors, e.g. Speed() { return m_speed; }

In general, classes should typically have private/protected member data with accessors and mutators, whereas structs often have naked public data members and few or no trivial accessors.

## Style and formatting conventions

### Bracing

Insomniac, Eiserloh, Butler: Opening curly braces are generally on a separate line, and are equally indented as their corresponding closing curly brace.  Code within curly braces is indented out from the curly braces.  (Allman-style)

**SD1**: Use either the "[Allman](https://en.wikipedia.org/wiki/Indent_style#Allman_style)" style (above) or the "[1TBS](https://en.wikipedia.org/wiki/Indent_style#1TBS)" style, your choice.  Be consistent!

### Indentation

Insomniac: Use two spaces per indent, no tab characters.

Eiserloh, Butler:: Use tab characters, with tab-stop width of 4.  Alternative: use tabs-as-spaces, with a tab-stop width of 4.  Note: I used to advocate for spaces ("looks the same in all browsers", but the practical value of using actual tabs (for a variety of reasons) has long since swayed me back to using actual tabs, not spaces.

**SD1**, Insomniac, Eiserloh: Do not add extra start-of-line indentations.  For example, if methods in a class start 1 tab in, do not have some methods start 2 or 3 extra tabs or spaces in.

### Line length

**SD1**, Insomniac, Eiserloh: Prefer lines less than 100 characters long.  Wrap at 98-100 characters, or not at all.

### Use of whitespace

**SD1**, Insomniac, Eiserloh, Butler:: Commas are usually followed by a space, and are usually NOT preceded by a space.

**SD1**, Insomniac, Eiserloh: The last line in any source code or text data file should be a linefeed (empty line).

**SD1**, Eiserloh, Butler:: Use a single blank line as a "pause" (comma in English) in reading comprehension between separate chunks of thought in code; use a double blank line as a "stop" (period in English) between each function.

Butler:: Don't use varying numbers of blank lines in your code as your way of delimiting sections of code. Vertical screen real estate is a precious commodity.

### Variable definition & declaration

**SD1**, Insomniac, Eiserloh: Do not declare more than one variable on a single line, e.g. float a, b, c;

**SD1**, Insomniac, Wofford, Eiserloh: Pointer (and reference) declarations always have whitespace to the right of the asterisk (or ampersand), and never have whitespace to the left (between the asterisk/ampersand and the type).

**SD1**, Eiserloh, Butler: Do not use the "auto" keyword when defining variables (with a few exceptions, e.g. STL container iterator types, lambdas); prefer explicit type declaration for fewer bugs and increased data-oriented awareness.

- Correct:   float f = 3.14f;
    
- Correct:   float* f = nullptr;
    
- Correct:   float& f = someOtherFloatVariable;
    
- Incorrect: float *f;               // reads like dereference
    
- Incorrect: float*f;                // reads like multiplication, and hard to read
    
- Incorrect: float * f;              // reads like multiplication
    
- Incorrect: float &f = something;   // reads like "address of"
    
- Incorrect: float & f = something;  // reads like "bitwise and"
    
- Incorrect: float&f = something;    // reads like "bitwise and", and hard to read
    
- Incorrect: auto f = 3.14;          // oops! Are you aware you actually declared 'f' as a double and not a float?
    

  

Switch statements

Insomniac, Eiserloh, Butler: The "case" keyword is indented one level above the switch statement (and its curly braces).

Insomniac, Eiserloh, Butler: Every case should use curly braces, with the "break" keyword as the last line inside the curly braces. (Eiserloh: switches with only single-line case statements can omit curly braces (and each line ends in either "break;" or "return;", but consistency and caution are encouraged.)

Insomniac, Eiserloh: Specifically comment intentional "fall-through" cases (when omitting a "break" in a switch case) after the falling-through case's closing curly brace.

### Spelling

**SD1**, Insomniac, Eiserloh: Prefer American spelling ("color", "serialize") to English spelling ("colour", "serialise").  Non-English comments and names are not permitted.

## Coding conventions

### Exceptions

**SD1**, Insomniac, Eiserloh: We do not throw or handle exceptions.  Rationale: Assertions and fatal errors are superior to exceptions in every way, and do not cause any additional code to be executed, nor call stack to be modified, and give the programmer the best possible chance to see the actual symptom, and perhaps direct cause, of the error.

### auto

**SD1**, Eiserloh: Do not use the "auto" keyword in C++.  Its stated intent is to hide underlying types from the reader, which is directly antithetical to our first principle.  (Additionally, auto is problematic as the majority of programmers misapprehend / incorrectly assume how it behaves, especially with regard to references and const.)  Exception: using auto for STL container iterator types in a for-loop statement is acceptable.  Exception: declaring lambda expressions (which themselves may or may not be an anti-pattern depending on the context).

Butler: I have been at companies where the use of "auto" or "var" was required to be used everywhere it could be used. 

### Classes vs. Structs

Insomniac, Eiserloh, Butler: Structs should be simple, dumb, and public-only, with no trivial member-variable accessors nor mutators (e.g. Vec2::GetX(), Vec2::SetX()), and only construction and/or other convenience methods.

**SD1**, Eiserloh, Forseth, Butler: Use "struct" exclusively for POD (Plain Old Data) structures which can be memcopied, memset, and do not require construction nor store any "secret" internal data (e.g. vtable).  This means, for example, that structs should NEVER have virtual functions, nor inherit from any class which (directly or indirectly) has virtual functions.  Use "class" for everything else.

### Public, Protected, Private

Insomniac: All class data members must be private (not public nor protected).  All struct data members must be public.  Prefer private member variables with protected accessors over protected member variables.

**SD1**, Insomniac, Eiserloh: "Aggregates where a specific memory layout is required and instances are intended to be worked with in an aliased way may have public data members. For example, four-float vector objects should have public x, y, z, w."

**SD1**, Eiserloh: Class data should generally be private or protected, unless (a) the data in question is fundamental to the very existence of the class (e.g. x,y, for 2D Vectors, center,radius for 2D Discs) AND (b) there is no chance a well-meaning programmer could misunderstand / misuse the variable to cause inadvertent harm or side-effects.  Data intended by the superclass to be used directly by subclasses may be "protected"; data internal to the workings of the superclass should remain private (rare).  In general, 95-99% of data members should be protected or private.  (Vec2 and similar classes are an exception as we view them as "pseudo-fundamental types" due to their extensive and pervasive use; limiting write access to Vec2 x,y members should be achieved with "const" (on the Vec2 itself, ala "Vec2 const& argument"), rather than "private".

**SD1**, Eiserloh: Methods used internally by a class (and intended only for internal use) should also be protected or private.

Eiserloh, Butler: In a "class" definition, we list:  (1) public methods, (2) public data (usually none, sometimes public static const data members), (3) protected and/or private methods, then (4) protected and/or private data members (which should be most of them).  Rationale: if you go to a class definition, you should see, right at the top, the public interface that class offers to outside users.

Eiserloh, Butler: In a "struct" (POD) definition, on the other hand, we list:  (1) public data (all struct members should be public), (2) public methods, then (3) protected and/or private methods (used only internally by other struct methods, very rare).  Rationale: if you go to a struct definition, you should see, right at the top, the public data structure it offers to outside users; struct memory layout / alignment / aliasing is considered critical public knowledge.

### The friend keyword

Insomniac: No friend declarations.  All external work must be possible using the public interface.

**SD1**, Eiserloh, Butler: Use friend functions only to create "class methods" which take something other than "this" as the lhs (left-hand-side) argument (e.g. friend Vector2 operator *( float scale, Vector2 const& rhs )).

Eiserloh: Use friend classes to **increase encapsulation** by tightly coupling two closely-related classes together, thus avoiding unnecessarily exposing as public what should otherwise be intimate details of either cooperative class.

### Construction, Initialization, and Destruction

Insomniac: Constructors should not do any real work.  A constructor should only be used to initialize member variables. It should do nothing that can fail. It should not have any side effects. A "side effect" is any change outside the object itself (ex: memory allocation (because it changes a heap, which is outside the object), acquisition of any resource, registration with a manager, updating a counter).  Real initialization is done in the Create function.  Rationale: Since we don't use exception handling, it's not possible to handle errors in constructors. If an error occurs in a constructor, you end up with an invalid object. Exceptions: For debugging purposes during development, it may be desirable to track construction and destruction of a particular class of objects. That usually involves the registration of the object in the constructor.  Classes that are specifically designed to use scope lifetime to invoke side-effect functions (such as profiling timers).

Insomniac: All destructors should be empty.  The object must be deinitialized, memory freed, resources released, in the Destroy() function, and not in the destructor. There is nothing for a destructor to do. However, the destructor is a good place for debug code to assert that Destroy() has indeed been called, and all resources have been released.  Perform object clean up in Destroy().  Objects should have an explicit Destroy method which performs the shutdown code matching that in Create (or TryCreate).  Do not put shutdown code in the object destructor, or in a method with a name other than Destroy.

**SD1**, Eiserloh: Constructors _of global and static objects_ should not do any significant work (such as loading files or allocating memory).  Rationale: global/static-scope objects are constructed in random order, before Main, making them difficult to manage and unable to use engine subsystems or memory pools.  Objects which do such "significant work" at construction time (rare) must trigger a fatal error if unsuccessful ("succeed or die" / simple RAII paradigm).  

### Integer types (size and signed/unsigned)

**SD1**, Insomniac, Eiserloh: Integer scalars should be signed.  Signed integers should be used unless you're relying on unsigned semantics explicitly or using an integer type in a non-numeric way (ex: using a uint32_t as a bit pattern, or set of bit flags, or relying on a specific representation to allow optimized transformations).  Rationale: Even though your index or counter may never be negative, you (or someone else) may want to test it for underflow, use it in an expression, subtract it from another index or counter, etc. Also, unsigned integers don't mix well with signed integers. For example if a number of elements in an array is presented as an unsigned integer, any loop counter for it must be unsigned also. That would make it very hard to iterate backward. Unsigned integers have no benefit other than that they can represent values larger than 2,147,483,647. (If you need that kind of range, use int64_t.)

Insomniac, Eiserloh: Only specify integer width on data members (and always do so then).  Where storage and value range of an integer scalar are not a concern, use native type int. In aggregates, use explicitly-sized integer types (e.g. int32_t) for data members.  int is preferred for parameters, return values, and local variables.  Rationale:  Specifying int32_t where plain int can be used restricts steps that a compiler can take to optimize the compiled code.

**SD1**, Eiserloh: Use size_t (rather than unsigned int or int) wherever appropriate - in particular, in cases where functions return or take a size_t.  size_t is not the same as unsigned int; this coincidence is only true when compiling in 32-bit (x86/Win32) configurations.

### Use of enumeration types

Insomniac: Do not use enum types as data members. Use an explicitly sized integer type instead. Rationale: Enum types are of implementation dependent width. Their use as data members can lead to complications maintaining alignment and aggregate size across platforms.

**SD1**: Where size of enum may matter, one should explicitly size the enum with the syntax "enum Direction : unsigned char" etc.

### Function arguments

Insomniac: Parameters passed by reference must be const.  Never use a reference parameter for output. Parameters that are used for output must be passed in by pointer.  Some programmers describe a reference as "a pointer that can't be NULL". If you must make sure that a pointer is not NULL, simply assert that it isn't.  Rationale: References can be confusing. They have value syntax but pointer semantics. On the caller's side, the code looks like you are passing the argument by value, therefore it should also behave like you are passing the argument by value.

**SD1**, Eiserloh, Butler: Simple primitive types (int, float, pointer) may be passed by value.  Parameters _larger than a pointer_ should be passed by const reference.  Pass-by-const-pointer implies an optional input variable.  Pass-by-non-const-reference implies a required output variable, and should be named "out_parameterName".  Pass-by-non-const-pointer implies an optional output variable, and should be named "out_parameterName".  Rationale: while in theory it sounds good to say "pass outputs by pointer" (hoping for code to read as "DoStuff( a, &b )" if "a" is an input and "b" is an output), in practice most pointers passed in originate as already-pointers (typically passed in from above), so the code still ends up reading as "DoStuff( a, b )".  Examples:

- float x  // no bigger than a pointer, should pass by value (adding "const" here is often considered pedantic)
- Actor const& targetPlayer  // 90% of parameters passed like this; a read-only input _(equivalent to: const Actor& targetPlayer)_
- Actor const* targetPlayer  // optional input, may be nullptr _(equivalent to: const Actor* targetPlayer)_
- Actor& out_traceResult  // required output
- Actor* out_traceResult  // optional output, to be filled in by function if non-nullptr

Insomniac, Eiserloh: Function parameter order: outputs, updates (in/outs), inputs. Place output parameters on the left, followed by update parameters (i.e. those that are input as well as output), and put input parameters at the end.  Rationale: This provides a predictable order for arguments (and places outputs closest to the return value).

**SD1**, Eiserloh: Function names should generally reference parameters in the same order in which they are passed (with the return-value, if any, being named first, e.g. "Cost" here):

- Correct: float Get**Cost**For**Actor**ToEnter**Tile**( Actor const& **actor**, Tile const& **tile** );
- Correct: float Get**Cost**ToEnter**Tile**For**Actor**( Tile const& **tile**, Actor const& **actor** );
- Incorrect: float Get**Cost**ToEnter**Tile**For**Actor**( Actor const& **actor**, Tile const& **tile** );

### #include guards / #pragma once

**SD1**, Insomniac, Eiserloh: Header files must begin with #pragma once.  This replaces the traditional #ifndef FOO_INCLUDED include guards.  Rationale: It's supported on all our platforms and universally faster.

### #include practices

**SD1**, Insomniac, Eiserloh, Butler: Don't use #include if a forward declaration would suffice.  If a particular header dependency can be fulfilled with a forward declaration instead of the full definition, use the forward declaration. Rationale: You can significantly minimize the number of header files you need to include in your own header files by using forward declarations. For example, if your header file uses the File class in ways that do not require access to the declaration of the File class, your header file can just forward declare **class File**; instead of having to #include "file/base/file.h".  When you include a header file you introduce a dependency that will cause your code to be recompiled whenever the header file changes. If your header file includes other header files, any change to those files will cause any code that includes your header to be recompiled. Therefore, we prefer to minimize includes, particularly includes of header files in other header files.

**SD1**, Eiserloh, Butler: Generally, you should **only** need to #include one header file from another if: (a) You inherit from it, or (b) you own (compose) or use members defined in it by value.  In particular, pointer and reference members, and functions which pass or return by pointer or reference DO NOT require header inclusion.

**SD1**, Insomniac, Eiserloh: Never include <windows.h> in a header. If you must include it in a .cpp source file, try to limit the number of files which do this, and always define WIN32_LEAN_AND_MEAN before including it.

Butler: I would include <windows.h> in a header if that was limited to a platform-specific library or interface so that Windows data types could be passed around freely within it, provided the header including the Windows header was not required by other external users of that library or interface.

Eiserloh: Wrapping platform-specific headers in an abstraction (e.g. PlatformSpecificHeaders.hpp) is encouraged, in which case the same rules apply for #including that header from other headers as would <Windows.h> itself.

### #defines and constants

**SD1**, Insomniac, Eiserloh: No control flow macros: do not use macros to hide control flow logic, for example, FOR_EACH.

**SD1**, Eiserloh, Butler: **Only use #define where no other alternative can suffice**.  Prefer inline functions to macro functions, and (typed) const or constexpr variables to (untyped) macro constants.

Insomniac: Don't use named number constants like kTwoFloat = 2.0f or kOneOverTen = 0.1f. Use the literal instead.  Exceptions: Named number constants for well known constants, or those with more than one significant digit, can be named. For example, PI or MATH_PI, etc.

**SD1**, Eiserloh: Use named constants for transcendental numbers (e.g. PI, SQRT_OF_2).  Literal constants should generally not appear directly in code; instead, create constants which name the purpose or meaning of that (what would otherwise be a) magic number.  For example:

- Incorrect:
    - DealDamage( attackerStrength * 0.1f ); // Why the 0.1?  what happens if I change it?
    - constexpr float ONE_OVER_TEN = 0.1f; // This states the obvious and tells me nothing.  Better to have just left it alone.
- Correct:
    - constexpr float DAMAGE_PER_STRENGTH = 0.1f;  // Equally fast as having hardcoded the value, but we've injected meaning into the code, and can now reason about the value of the constant (and whether to change it).

### Byte, Size, Count

Insomniac: When referring to the size of something in bytes (or otherwise), a variable or type name should contain the word "bytes" or "words" or "dwords" or "qwords", as appropriate. 

**SD1**, Eiserloh: When referring to memory sizes, always use bytes, and use the word "bytes" in your name(s).  When referring to the size of something in elements, a variable or type name should contain the prefix "num" or the suffix "count".  For sizes of memory in larger units, use explicitly clear names which do not rely upon a specific platform's interpretation of their meaning, e.g. "int GetNum32BitDwordsInFile() const".

### Singletons

Eiserloh: Many things that seem like they should be singletons (e.g. Renderer, Window, NetworkSystem, PhysicsSystem, EventSystem) often have cases where more than one instance may be required.  Don't architect out this possibility just because you can't think of those cases now.

**SD1**, Insomniac, Eiserloh: Globally accessible singletons should be explicitly constructed (either by pointer or by value), and made accessible via an "extern" declaration in its header file.  Singleton constructors should never do any real work nor have any external side effects.

**SD1**, Eiserloh: Do not use "Meyers-style" singletons (i.e. returning the address of a static local variable inside a Get() method), as they allow singleton objects to be created in random order (based on first access) and are never destructed (until after main() exits).  These are some of the same justifications given for why we do not create global objects of significant types (or that perform significant activity upon construction).  Prefer instead explicit creation of singleton objects - either via new, or an explicit static Create() method.

### Casting

Insomniac: Prefer C-style casts. Do not use C++ style (static_cast, dynamic_cast, reinterpret_cast).  Do not use void*. Use char* for untyped data.  Rationale: The brevity of the C-style cast outweighs the semantic benefits of explicitness of C++-style casts.  Data pointed through to char* is guaranteed to alias any other data type. Also, it avoids having to explicitly convert to a sized type when address arithmetic is required.

Eiserloh: Use C++ style casts (e.g. static_cast) with pointers or custom types.  Construction-style casts – e.g. **`float f = float(someInt);`** – are preferred for primitive types for clarity/brevity in most obvious cases.  Always use const_cast to call attention to the (very dubious) casting-away of const-ness.  Use static_cast when manually downcasting pointers (from Base* to Derived*) where we have expert knowledge of the validity of such a cast (e.g. we've asked the object if it can be converted, via an enumeration member or polymorphic virtual function call).  The use of dynamic_cast is permitted if RTTI is enabled and no simpler substitute is available.

**SD1**, Butler**:** Prefer static_cast for primitive type conversions and pointer type conversions. Always use const_cast (instead of C-style casts) when casting away const-ness (**which you should almost never do**).  You may use dynamic_cast when necessary, if RTTI is enabled.  Avoid C-style casts in general.

### Booleans

Insomniac: No Booleans in aggregates.  Do not use bool or an equivalent boolean type in an aggregate. Prefer a bit set in an integer type instead.  Rationale: It's rare for only one boolean state to be present on something. Generally we need to encode more than one. Also it encourages processing of elements where the boolean is continually checked. Also, bool types are of implementation dependent width. Their use as data members can lead to complications maintaining alignment and aggregate size across platforms.

Insomniac: No bools in function parameter lists.  Rationale: Boolean function arguments hide important information in the calling code. They can almost always be expressed more clearly with explicit constants.  [http://blogs.msdn.com/b/oldnewthing/archive/2006/08/28/728349.aspx](http://blogs.msdn.com/b/oldnewthing/archive/2006/08/28/728349.aspx)  Exception: Really simple accessors can take one boolean argument (e.g. void SetLightingEnabled( bool isLightingEnabled ); ).

Insomniac: Bools are acceptable in local scope.  Bools are acceptable return values; however, they imply an unsorted data set and a branch at every caller. That should be carefully considered and fixed at the data design instead, where appropriate.

Eiserloh: I agree with the above rationale, and mostly agree with the conclusions (though I don't always practice them).  One option to consider is creating a fixed-size boolean typedef, e.g. typedef unsigned char Boolean.

**SD1,** Eiserloh: Do NOT use **std::vector<bool>**.  It is a special case, and poorly defined, and it almost certainly not what you think it is.

### C bit fields (explicit bit-width integers)

**SD1,** Insomniac, Eiserloh: Don't use use C-style "manual width" integer bit fields (e.g. "int x:3;"). For data that must be tightly packed, prefer explicit flags stored in integers or a higher-level structure (like a MemAllocBitSet) instead. Rationale: The code generated from C bit fields is usually much worse than explicit bit manipulation and the specific memory layout is implementation dependent.

### Heap memory allocation (new and malloc)

Insomniac: Do not use malloc, calloc, memalign, or free. Do not use any new operator except for placement new. Use an Insomniac memory allocator dedicated for the purpose that you need memory or the stack.  Do not use functions which implicitly allocate memory using these functions if at all possible.  Rationale: We have custom allocators for different allocation patterns for performance, auditing, and fragmentation reasons. Use of the CRT memory allocators circumvents our memory allocation schemes and in most cases is a poorer alternative.  Exceptions: Some middleware will not offer the ability to override their memory allocators, or implicitly use CRT memory through libc functions.

**SD1,** Eiserloh: For large-scale games which are high-performance-critical, this is sound advice.  We will write our own pooled memory allocators later; until then, you should use new and delete exclusively for allocation (and not malloc/free).

### Shared_ptr and make_shared

Game studios generally either _require_ the use of shared_ptr (and forbid most uses of naked pointers), or they _forbid_ the use of shared_ptr.  More studios forbid it, so we shall forbid it as well (in SD1, anyway).

**SD1,** Eiserloh: Don't use shared_ptr or make_shared.  Rationale is fivefold:

1. While these reference-counted "smart pointers" are excellent for solving junior-level coding headaches, they often exchange this for the creation of more subtle senior-level coding headaches, such as quasi-leaked resources.
2. Explicitness and clarity in terms of object lifespan and memory allocation are high-value items, both of which are masked by the use of shared pointers.
3. Shared_ptr often does NOT help us solve the most difficult problems of memory management, but rather forces us to be safe by reducing or removing our ability to actually solve those problems (e.g. deregistration, etc.).
4. All C++ programmers understand the behavior of new and delete (but many do not understand shared_ptr), so we prefer the simpler mechanism for comprehension.
5. new and delete wire effortlessly into custom memory pool allocation schemes (see above), which is extremely valuable for high performance code in large-scale games.  Keep it simple, stupid.

Butler: I have worked in studios where the use of unique_ptr and shared_ptr was preferred over the use of raw pointers.

### Const and mutable

**SD1,** Insomniac, Eiserloh: Member functions should be declared const unless there is a reason to do otherwise. If it is possible to trivially rewrite a member function to allow it to be const, it should be.

Insomniac: Under no circumstances should the keyword 'mutable' be used.

**SD1,** Eiserloh: All variables and methods at any scope should be declared const unless there is a reason to do otherwise.  We want to give the compiler (and the reader!) every hint we can to give it the best chance to generate the best possible code.  Exception: primitive-typed function arguments (e.g. float, int) can omit const for readability.

### Conditionals and braces

Insomniac: Use explicit braces with conditional blocks, even in cases with one-statement. This applies to if and while (and for) statements.  Rationale: It's possible for someone to mistake indentation for control flow and neglect to include a conditional statement in the right block.

**SD1,** Eiserloh: Use explicit braces with conditional blocks in general.  A few minor allowable exceptions exist for simple conditions whose result is a break, continue, or return statement, in which case there must be no code on the line following (i.e. must be followed by a blank line or closing brace).  You're probably better off just always using curly braces, period.  An example of an acceptable exception:

`void PlayerShip::Render() const   {`  
    `if( m_isDead )`  
        `return;     // This sort of common one-line early-out return is acceptable in SD1, if followed by a blank line afterward`  
  
    `// Normal behavior follows...`  
`}`

### Inline functions

**SD1,** Insomniac, Eiserloh: Non-trivial code should be kept out of headers.  By default, code should not be in header files. It should be in source files.  Rationale: Maintaining code in header files instead of source files increases the number of files which must be recompiled. In addition, the extent to which the compiler can and will inline code is implementation and configuration dependent, which can result in multiple definitions across translation units which increases link time. Exceptions: Code which is extremely trivial – simple accessors, for example – are acceptable in headers.  Exceptions (Eiserloh): Very simple low-level math functions (e.g. Vector2::operator+) can be inlined after the class definition (but NOT inside the class definition), as they can be pervasively performance-critical AND tend to change less far less often than most code.

**SD1,** Eiserloh: When in doubt, do not inline functions.  For functions which are inlined (see above), function bodies should be written separately outside / below the class definition (i.e. NOT inside the class definition) - or in a separate file.  Rationale: the class definition is a crucial - and sacred - component of code communication and user comprehension, and should be kept clean and clear, maximizing signal-to-noise ratio.  Code or comments which spread this out or break it up reduce readability and time-to-comprehension.  Exception: truly trivial accessors or mutators are permissible inside the class definition (all on one line, so as not to disrupt flow).

### Templates

**SD1,** Eiserloh: Use of function and class templates is permitted (starting in the second half of SD1), but discouraged.  Templates have a large inherently negative value; they complicate debugging, cripple build times, and decimate reader comprehension rate and speed.  However, there are some problems which are either only solvable through the use of templates, or in which the non-template alternative is pathological, and in these cases we absolutely will embrace them.

Resist using templates for the sole purpose of "elegance", and never use them for "cleverness".  More often than not, junior programmers' instincts to use templates in any given situation are wrong.  In each case, the problem bears a heavy burden of proof that the use of the template (a) solves an actual, significant problem; and (b) is appropriate for all types (not just 2 or 3 intended-use types); and (c) is the lesser evil as compared with the best possible non-template solution.

In all cases, prefer "typename" to "class" in the <template> parameter declaration section, and prefer "T_SomeActualTypeName" to "T" for all but trivial templates, or in any case where a meaningful name can be given to the type.

### Lamba Expressions

**SD1,** Eiserloh: Use of Lambda expressions is permitted (starting in SD2), but strongly discouraged.  In a very few extremely simple cases, Lambdas can make the code more obvious and self-documenting, but generally they have the opposite effect.  Prefer a named function, even an inline function or a CPP-only function.  Do not use a Lambda expression unless the alternative is pathologically worse.

Butler, Eiserloh: The vast majority of Lambda usage I see is laziness to avoid writing a proper function, which is absolutely the wrong reason and just makes code unreadable.

### STL (Standard Template Library)

**SD1**, Eiserloh: Use of STL containers is permitted (starting in the second half of SD1).  In general, use the simplest thing possible that solves your problem.  If a known-fixed-size array is required, prefer a literal (c-style) fixed-size array.  For dynamic arrays (that grow), prefer std::vector with judicious use of the .reserve() and .resize() methods, and/or "recycle" vectors by allowing them to persist.  Prefer emplace_back to push_back when adding complex objects to a std::vector by value.  Prefer std::vector to all other containers (especially std::list and std::set) 90% of the time, unless you are certain you have an actual problem that will actually be solved better by the other container type.  (rationale: std::vector is simpler, more cache-friendly, and outperforms almost everything else in 90% of cases.)  Prefer fixed-size c-style arrays (or std::array) to std::vector where sizes are fixed and known at compile time.

**SD1**, Butler: Be extra wary of STL containers in code that is "closer to the hardware", such as rendering code, where the data may need to be passed off via pointers or copied in to a buffer.

# General Best Practices

**SD1,** Eiserloh: All member variables that require construction (including all primitive types - especially bools and pointers) should be initialized in the class constructor initializer list OR in the class definition itself at member variable declaration.

Insomniac, Eiserloh: Avoid "magic values": avoid overloading integer or float variables which take a range of values with a magic number. For example, having a number which represents a length of time with -1 meaning infinite.  Rational: It's generally not obvious that magic numbers have special significance. Also, they harm the discoverability of interfaces.  Exceptions: For things with discrete enumerated values, like IDs, having a sentinel for "invalid" is okay, but keep make it an explicit constant (e.g. const INVALID_SOUND_ID = -1;).

**SD1,** Insomniac, Eiserloh: Keep implementation details out of the public interface.  Unless a detail is necessary for the use of the public interface, it should not be visible by a programmer using the interface.  Rationale:  By presenting a concise interface, the user will be more likely to use it correctly, and the implementer will have more freedom to change internal implementation details without worrying about harming calling code.

**SD1,** Insomniac, Eiserloh: Avoid negative flags.  When possible, make the boolean value true equivalent to enable, or execute, or success. Avoid flags that have negative meanings, where a boolean value of true means "disable", "skip", or "failure".  Rationale: Negative (and therefore, double-negative) logic hampers readability.  Eiserloh: Also, if possible, prefer boolean variable names such that false is the reasonable default value; this affords greater POD/struct compatibility (e.g. ={} or memset(0) to (re)initialize ).

**SD1,** Insomniac, Eiserloh, Butler: Compile without warnings.  Generally speaking, your code shouldn't have warnings. You should make every effort to change the offending code until it compiles and links without warnings. Exceptions: If you believe a warning to be spurious, it may be acceptable to turn it off under certain circumstances. Before you do please talk to someone who knows about these things. When using middleware, it may be unavoidable to avoid warnings. It may be possible to suppress the warnings before including code via header; you should make the effort to do so if necessary. Eiserloh: Compile with the highest possible warning level set by default (e.g. "Warning Level 4" in Visual Studio), but **do not use "treat warnings as errors"** as that directly impedes iteration times for experimental and in-progress code.  **In most SD classes, including SD1, each build warning in a Rebuild Solution can deduct up to 1 point from your assignment grade.**

Insomniac, Eiserloh: Add comments to identify #else/#elif/#endif statements.  Any #endif, #else or #elif statement associated with a #if or #ifdef statement should be commented with the relevant condition unless it is extremely obvious.



