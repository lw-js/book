# Crockford Yahoo Lecture Notes

## History
- 1992, Oak, Gosling at Sun & FirstPerson
- 1995, HotJava, LiveScript, Eich at Nescape
- 1996, JScript at Microsoft
- 1998, ECMAScript

## Key Ideas

- load-and-go delivery
- loose typing
    - any type can be stored in any variable
    - any type can be passed to any function
    - language is not "untyped"
- objects as general containers
    - unification of Object and Hashtable
- prototypal inheritance
- lambda
- linkage through global variables

## Values

### Number

- only one type of number
    - 64-bit floating point
    - IEEE-754
    - aka "Double", from Fortran's "double-precision"
- does not map well to arithmetic
    - 0.1 + 0.2 = 0.30000000000000004
- NaN
    - special Number, Not a Number
    - result of undefined or erroneous operations
    - toxic: arithmetic operation with NaN as input will be NaN
    - NaN is not equal to anything, including NaN
- Number function
    - Number(value)
    - converts the value into a number
    - it produces NaN if it has a problem
    - similar to + prefix operator
- parseInt function
    - converts the value into a Number
    - stops at first non-digit character
    - the radix (10) should be required
        - parseInt("08") === 0
        - parseInt("08", 10) === 8

### String

- sequence of 0 or more 16-bit characters
    - UCS-2, not UTF-16
    - no awareness of surrogate pairs
- no separate character type
    - characters are just strings of length 1
- strings are immutable
- similar strings are equal (==)
- string literals can use single or double quotes
- length
    - String.length
    - the number of 16-bit characters in the string
- string methods
    - charAt
    - concat
    - indexOf
    - lastIndexOf
    - match
    - replace
    - search
    - slice
    - split
    - substring
    - toLowerCase
    - toUpperCase

### Boolean

- true or false
- Boolean function
    - Boolean(value)
    - returns true if value is truthy
    - returns false if value is falsy
    - similar to !! prefix operator
- falsy values
    - false
    - null
    - undefined
    - "" (empty string)
    - 0
    - NaN
- truthy values
    - all that isn't falsy
    - "0" and "false" are truthy

### Object

- new Object() produces an empty container of name/value pairs
- name can be any string
- value can be any value except undefined
- members can be accessed with dot notation or subscript notation
    - object.container
    - object["container"]
- no hash nature is visible (no hash codes or rehash methods)

### null

- a value that isn't anything

### undefined

- default value for variables and parameters
- value of missing members in objects

## Math

- Math object is modeled on Java's Math Class
- it contains
    - abs       absolute value
    - floor     integer
    - log       logarithm
    - max       maximum
    - pow       raise to power
    - random    random integer
    - round     nearest integer
    - sin       sine
    - sqrt      square root

## Identifiers

- starts with letter or _ or $
- followed by zero or more letters, digits, _ or $
- conventions
    - variables, parameters and members start with lower case
    - function names start with lower case
    - except constructors start with upper case
    - initial _ should be reserved for implementations
    - $ should be reserved for machines
- reserved keywords
    - abstract
    - boolean, break, byte
    - case, catch, char, class, const, continue
    - debugger, default, delete, do, double
    - else, enum, export, extends
    - false, final, finally, float, for, function
    - goto
    - if, implements, import, in, instanceof, int, interface
    - long
    - native, new, null
    - package, private, protected, public
    - return
    - short, static, super, switch, synchronized
    - this, throw, throws, transient, true, try, typeof
    - var, volatile, void
    - while, with

## Comments

- // for single line comments
- /* to start block comment
- */ to end block comment

## Operators

- arithmetic
    - addition +
        - if there's only one operand, convert to number
            - +"42" == 42
            - +"3" + (+"4") == 7
            - Number("42") == 42
            - parseInt("42", 10) == 42
        - else if both operands are numbers, addition
        - else convert them to strings and concatenate them
            - "$" + 3 + 4 = "$34"
    - subtraction -
    - multiplication *
    - division /
        - division of two integers can produce a non-integer
        - 10 / 3 = 3.3333333333333335
    - modulus %
- comparison
    - equal ==
        - can do type coercion
    - not equal !=
        - can do type coercion
    - less than <
    - greater than >
    - less than or equal <=
    - greater than or equal >=
- logical
    - AND &&
        - guard operator
        - if first operand is truthy, return second operand
        - else return first operand
        - can be used to avoid null references
            - return a && a.member;
    - OR ||
        - default operator
        - if first operand is truthy, return first operand
        - else return second operand
        - can be used to fill defaults
            - var last = input || numberOfItems;
    - NOT !
        - if the operand is truthy, return false
        - else return true
        - !! produces booleans
- bitwise
    - &, |, ^, >>, >>>, <<
    - implementation
        - slow
        - first converts to 32-bit signed integer
        - does the bitwise operation
        - converts the result to 64-bit floating point
- ternary
    - ?:


