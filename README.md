# Python Cheat Sheet

## 1. Python Data Types Cheat Sheet: Mutable vs. Immutable

#### => Mutable Data Types:

1. **List:**

   - Ordered collection of items.
   - Mutable: Elements can be changed.
   - Defined using square brackets `[ ]`.
   - Example: `my_list = [1, 2, 3]`
2. **Dictionary:**

   - Unordered collection of key-value pairs.
   - Mutable: Keys and values can be modified.
   - Defined using curly braces `{ }`.
   - Example: `my_dict = {'key1': 'value1', 'key2': 'value2'}`
3. **Set:**

   - Unordered collection of unique elements.
   - Mutable: Elements can be added or removed.
   - Defined using curly braces `{ }` or the `set()` function.
   - Example: `my_set = {1, 2, 3}`
4. **Byte Array:**

   - Mutable sequence of bytes.
   - Elements can be modified after creation.
   - Defined using the `bytearray()` function.
   - Example: `my_bytearray = bytearray(b'hello')`

#### Immutable Data Types:

1. **Integer:**

   - Whole numbers without decimal points.
   - Immutable: Value cannot be changed after creation.
   - Example: `my_int = 5`
2. **Float:**

   - Floating-point numbers with decimal points.
   - Immutable: Value cannot be changed after creation.
   - Example: `my_float = 3.14`
3. **String:**

   - Sequence of characters.
   - Immutable: Characters cannot be modified after creation.
   - Defined using single `' '` or double `" "` quotes.
   - Example: `my_string = 'hello'`
4. **Tuple:**

   - Ordered collection of items.
   - Immutable: Elements cannot be changed after creation.
   - Defined using parentheses `( )`.
   - Example: `my_tuple = (1, 2, 3)`
5. **Frozen Set:**

   - Immutable version of a set.
   - Elements cannot be added or removed after creation.
   - Defined using the `frozenset()` function.
   - Example: `my_frozen_set = frozenset({1, 2, 3})`
6. **Bytes:**

   - Immutable sequence of bytes.
   - Elements cannot be modified after creation.
   - Defined using the `bytes()` function or prefixing `b''`.
   - Example: `my_bytes = b'hello'`
7. **Boolean:**

   - Represents truth values `True` or `False`.
   - Immutable: Value cannot be changed after creation.
   - Example: `my_bool = True`
8. **NoneType:**

   - Represents the absence of a value.
   - Immutable: Value cannot be changed after creation.
   - Example: `my_none = None`

## 2. Python Numbers Cheat Sheet

#### Numeric Types:

1. **int (Integer):**

   - Represents whole numbers, positive or negative, without decimal points.
   - Example: `x = 5`
2. **float (Floating-point):**

   - Represents real numbers with decimal points or exponential notation.
   - Example: `y = 3.14`

#### Arithmetic Operators:

- **Addition (+):** Adds two numbers.
- **Subtraction (-):** Subtracts one number from another.
- **Multiplication (*):** Multiplies two numbers.
- **Division (/):** Divides one number by another (returns a float).
- **Floor Division (//):** Divides one number by another and returns the integer part of the result.
- **Exponentiation (**):** Raises a number to the power of another.
- **Modulo (%):** Returns the remainder of the division of one number by another.

#### Built-in Functions:

- **abs(x):** Returns the absolute value of x.
- **pow(x, y):** Returns x raised to the power of y.
- **round(x, n):** Rounds x to n decimal places (default is 0).

#### Math Module (import math):

- **math.sqrt(x):** Returns the square root of x.
- **math.floor(x):** Returns the largest integer less than or equal to x.
- **math.ceil(x):** Returns the smallest integer greater than or equal to x.
- **math.sin(x), math.cos(x), math.tan(x):** Returns the trigonometric sine, cosine, and tangent of x (in radians).
- **math.pi:** Mathematical constant pi (3.141592...).
- **math.e:** Mathematical constant e (2.718281...).

#### Complex Numbers:

- **complex(real, imag):** Creates a complex number with the real part `real` and the imaginary part `imag`.
- **z.real:** Returns the real part of the complex number `z`.
- **z.imag:** Returns the imaginary part of the complex number `z`.
- **z.conjugate():** Returns the complex conjugate of `z`.

#### Type Conversion Functions:

- **int(x):** Converts x to an integer.
- **float(x):** Converts x to a float.
- **complex(x):** Converts x to a complex number with a real part `x` and zero imaginary part.

#### Constants:

- **True:** Represents the boolean value true (equivalent to 1).
- **False:** Represents the boolean value false (equivalent to 0).
- **None:** Represents the absence of a value.
- **sys.maxsize:** Returns the maximum size of a list or string that can be handled by Python.

## 3. Difference between `repr()`, `str()`, and `print()` in Python ?

**=>** `repr()`, `str()`, and `print()` are three different functions in Python that serve different purposes when it comes to representing and displaying data. Here's a breakdown of each:

1. **repr( ) Function:**

   - The `repr()` function returns a printable representation of an object.
   - It is intended to produce output that is as unambiguous as possible.
   - The string returned by `repr()` is typically valid Python syntax that could be used to recreate the object.
   - It is commonly used for debugging and logging purposes.
   - If an object has a `__repr__()` method defined, Python will call this method to obtain the representation.
   - Example:
     ```python
     >>> x = 10
     >>> repr(x)
     '10'
     ```
2. **str( ) Function:**

   - The `str()` function returns the "informal" or "pretty" string representation of an object.
   - It is intended to produce output that is readable to humans.
   - The string returned by `str()` may not necessarily be valid Python syntax.
   - If an object has a `__str__()` method defined, Python will call this method to obtain the string representation.
   - It is commonly used for displaying information to end-users.
   - Example:
     ```python
     >>> x = 10
     >>> str(x)
     '10'
     ```
3. **print( ) Function:**

   - The `print()` function is used to output text or other objects to the console.
   - It converts the objects passed to it into strings using the `str()` function, and then displays those strings.
   - It is commonly used for debugging, logging, or displaying information to users.
   - The `print()` function does not return any value; it simply outputs the given objects to the console.
   - Example:
     ```python
     >>> x = 10
     >>> print(x)
     10
     ```

In summary, `repr()` and `str()` are functions used to obtain string representations of objects, with `repr()` focusing on unambiguous, machine-readable output, while `str()` focuses on human-readable output. `print()` is used to display text or other objects to the console and internally uses the `str()` function to convert objects to strings before printing them.

## 4. Python Math Functions

**=>**  Python Math Functions Cheat Sheet

#### Basic Math Functions:

1. **abs(x):**

   - Returns the absolute value of x.
2. **pow(x, y):**

   - Returns x raised to the power of y.
3. **round(x, n):**

   - Rounds x to n decimal places (default is 0).

#### Trigonometric Functions (from the `math` module):

4. **math.sin(x), math.cos(x), math.tan(x):**

   - Returns the trigonometric sine, cosine, and tangent of x (in radians).
5. **math.asin(x), math.acos(x), math.atan(x):**

   - Returns the inverse trigonometric sine, cosine, and tangent of x, respectively.
6. **math.degrees(x), math.radians(x):**

   - Converts angles from radians to degrees and vice versa.

#### Exponential and Logarithmic Functions:

7. **math.exp(x):**

   - Returns e raised to the power of x (where e is Euler's number, approximately 2.71828).
8. **math.log(x, base):**

   - Returns the natural logarithm of x (base e) or the logarithm of x with the specified base.
9. **math.log10(x):**

   - Returns the base-10 logarithm of x.

#### Constants:

10. **math.pi:**

    - Mathematical constant pi (approximately 3.14159).
11. **math.e:**

    - Mathematical constant e (approximately 2.71828).

#### Others:

12. **math.ceil(x):**

    - Returns the smallest integer greater than or equal to x.
13. **math.floor(x):**

    - Returns the largest integer less than or equal to x.
14. **math.factorial(x):**

    - Returns the factorial of x (x!).
15. **math.gcd(x, y):**

    - Returns the greatest common divisor of x and y.
16. **math.sqrt(x):**

    - Returns the square root of x.
17. **math.isqrt(x):**

    - Returns the integer square root of x (floor of the square root).

#### Notes:

- Import the `math` module to use these functions: `import math`.
- Many of these functions operate on radians, not degrees. Use `math.degrees()` and `math.radians()` to convert between radians and degrees.

## 5. Octal and Hexadecimal

**=>** In Python, octal and hexadecimal are two different numerical notations used to represent integers.

1. **Octal Notation:**

   - Octal notation represents numbers using base-8 digits (0-7).
   - Octal literals in Python are prefixed with a leading `0o` or `0O`.
   - For example:
     ```python
     oct_num = 0o10  # Represents the decimal number 8
     ```
2. **Hexadecimal Notation:**

   - Hexadecimal notation represents numbers using base-16 digits (0-9 and A-F).
   - Hexadecimal literals in Python are prefixed with a leading `0x` or `0X`.
   - For example:
     ```python
     hex_num = 0x10  # Represents the decimal number 16
     ```
3. **Binary Notation (since Python 3.6):**

   - Python 3.6 introduced a new binary literal notation.
   - Binary literals in Python are prefixed with a leading `0b` or `0B`.
   - For example:
     ```python
     bin_num = 0b10  # Represents the decimal number 2
     ```

These notations can be useful when working with numbers in different bases, especially in contexts such as bitwise operations or when specifying certain numeric values explicitly.

It's important to note that these notations are for representing integers in code; they don't fundamentally change how numbers are stored or processed by the computer. They're simply different ways to express numeric values in a human-readable format within the context of a programming language.

## 6. Bitwise Operations

**=>** In Python, bitwise operations manipulate individual bits of integers. These operations can be useful for tasks such as low-level programming, cryptography, and optimizing code. Here's an overview of bitwise operators in Python:

### Bitwise Operators:

1. **AND (`&`):**

   - Sets each bit to 1 if both bits are 1.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     b = 13    # 13 = 0000 1101
     result = a & b  # 12 = 0000 1100
     ```
2. **OR (`|`):**

   - Sets each bit to 1 if at least one of the bits is 1.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     b = 13    # 13 = 0000 1101
     result = a | b  # 61 = 0011 1101
     ```
3. **XOR (`^`):**

   - Sets each bit to 1 if exactly one of the bits is 1.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     b = 13    # 13 = 0000 1101
     result = a ^ b  # 49 = 0011 0001
     ```
4. **NOT (`~`):**

   - Inverts all the bits.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     result = ~a  # -61 = 1100 0011
     ```
5. **Left Shift (`<<`):**

   - Shifts the bits to the left by a specified number of positions.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     result = a << 2  # 240 = 1111 0000
     ```
6. **Right Shift (`>>`):**

   - Shifts the bits to the right by a specified number of positions.
   - Example:
     ```python
     a = 60    # 60 = 0011 1100
     result = a >> 2  # 15 = 0000 1111
     ```

### Notes:

- Bitwise operators work on integers at the binary level.
- Bitwise operations are typically used for tasks such as masking, setting, or clearing specific bits in a binary representation.
- Be careful when using bitwise operations, as they can lead to unexpected results if not used correctly.
- Python integers have a fixed width, so left shifting can result in the loss of higher-order bits and right shifting can result in the loss of lower-order bits.

These bitwise operators provide powerful tools for manipulating binary data and performing low-level operations in Python.

## 7. Python's `random` module

**=>** Python's `random` module provides functions for generating random numbers and performing random selections. Here's an overview of some of the most commonly used functions in the `random` module:

### Random Number Generation:

1. **`random()`**:

   - Returns a random floating-point number in the range [0.0, 1.0).
   - Example:
     ```python
     import random
     rand_num = random.random()  # Generates a random float between 0.0 and 1.0
     ```
2. **`randint(a, b)`**:

   - Returns a random integer in the range [a, b] (inclusive).
   - Example:
     ```python
     import random
     rand_int = random.randint(1, 10)  # Generates a random integer between 1 and 10
     ```
3. **`uniform(a, b)`**:

   - Returns a random floating-point number in the range [a, b) with uniform distribution.
   - Example:
     ```python
     import random
     rand_float = random.uniform(1.0, 2.0)  # Generates a random float between 1.0 and 2.0
     ```

### Random Sequence Operations:

4. **`shuffle(sequence)`**:

   - Randomly shuffles the elements of a list in place.
   - Example:
     ```python
     import random
     my_list = [1, 2, 3, 4, 5]
     random.shuffle(my_list)  # Shuffles the elements of my_list randomly
     ```
5. **`sample(population, k)`**:

   - Returns a random sample of k elements from the population without replacement.
   - Example:
     ```python
     import random
     my_list = [1, 2, 3, 4, 5]
     rand_sample = random.sample(my_list, 3)  # Returns a random sample of 3 elements from my_list
     ```
6. **`choice(sequence)`**:

   - Returns a random element from a non-empty sequence.
   - Example:
     ```python
     import random
     my_list = [1, 2, 3, 4, 5]
     rand_choice = random.choice(my_list)  # Returns a random element from my_list
     ```

### Setting Random Seed:

7. **`seed(x)`**:
   - Initializes the random number generator with a seed value.
   - Useful for generating reproducible random sequences.
   - Example:
     ```python
     import random
     random.seed(42)  # Sets the seed value to 42
     ```

These are some of the most commonly used functions in the `random` module. They provide a wide range of functionalities for generating random numbers and performing random selections in Python.

## 8. Overview of the `decimal` module

**=>** In Python, the `decimal` module provides support for decimal floating-point arithmetic. This module is particularly useful when precision is critical, such as in financial applications or when working with decimal numbers that cannot be accurately represented using binary floating-point arithmetic. Here's an overview of the `decimal` module:

### Basic Usage:

1. **Importing the Module:**

   ```python
   from decimal import Decimal
   ```
2. **Creating Decimal Numbers:**

   ```python
   num1 = Decimal('10.5')  # Decimal from a string
   num2 = Decimal(10.5)     # Decimal from a float
   ```
3. **Performing Arithmetic Operations:**

   ```python
   result = num1 + num2
   ```

### Decimal Context:

The `decimal` module allows you to control the precision and rounding behavior through the `getcontext()` function and the `Context` object. Here's how you can customize the context:

```python
from decimal import Decimal, getcontext

getcontext().prec = 10  # Set the precision to 10 decimal places
```

### Example:

```python
from decimal import Decimal, getcontext

getcontext().prec = 10  # Set the precision to 10 decimal places

num1 = Decimal('10.123456789')
num2 = Decimal('20.987654321')

result = num1 + num2
print(result)  # Output: 31.111111110
```

### Notes:

- Decimal objects can represent numbers with arbitrary precision.
- Arithmetic operations on Decimal objects maintain precision and rounding according to the current context.
- Decimal arithmetic avoids the precision issues inherent in binary floating-point arithmetic (e.g., with `float`).
- Decimal arithmetic may be slower than binary floating-point arithmetic, so it's best suited for applications where precision is critical.

Using the `decimal` module ensures accurate representation and manipulation of decimal numbers, making it suitable for applications where precision is paramount.

## 9. Overview of the `fractions` module

**=>** In Python, the `fractions` module provides support for rational numbers, allowing you to work with fractions accurately and precisely. This module is particularly useful when dealing with exact fractional arithmetic, such as in financial calculations or when precise fractions are required. Here's an overview of how to use the `fractions` module:

### Basic Usage:

1. **Importing the Module:**

   ```python
   from fractions import Fraction
   ```
2. **Creating Fractions:**

   ```python
   frac1 = Fraction(3, 4)     # Fraction from numerator and denominator
   frac2 = Fraction('1.5')     # Fraction from a string representation
   ```

### Arithmetic Operations:

```python
result = frac1 + frac2
```

### Accessing Fraction Components:

```python
numerator = frac1.numerator
denominator = frac1.denominator
```

### Example:

```python
from fractions import Fraction

frac1 = Fraction(3, 4)
frac2 = Fraction('1.5')

result = frac1 + frac2
print(result)               # Output: 9/4
print(result.numerator)     # Output: 9
print(result.denominator)   # Output: 4
```

### Notes:

- Fractions created with the `Fraction` class are automatically reduced to their simplest form.
- Fractional arithmetic operations preserve precision and return results as fractions whenever possible.
- Fractions can be initialized from integers, floats, or strings representing rational numbers.
- The `Fraction` class provides properties like `numerator` and `denominator` for accessing the components of a fraction.

Using the `fractions` module allows you to work with rational numbers in a precise and accurate manner, making it suitable for applications where exact fractional arithmetic is required.
