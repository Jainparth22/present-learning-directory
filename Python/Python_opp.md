### Notes on Python OOP (Object-Oriented Programming) from the Video

#### **What is a Class?**
- A **class** is a **blueprint** for creating objects. It defines what attributes (data) and methods (functions) the objects will have.
  - **Example**: Before building a house, you create a blueprint. Similarly, a class serves as the blueprint for creating objects.
- **Syntax**:
  ```python
  class ClassName:
      pass
  ```
  - Class names conventionally use **UpperCamelCase or PascalCase**.
  - **Attributes** (data members) and **methods** (functions) are defined within a class


  - **Example Analogy**: A blueprint of a house defines the design and features of a house but is not itself a house.

 #### **What is an Object?**
- An **object** is an instance of a class that holds actual data and can perform actions (via methods).
-  Use the **constructor** to create an instance of a class.
- **Explicit Declaration**:
  Objects are explicitly created using the class constructor.
  ```python
  obj = ClassName()
  ```
  Here, `obj` is an instance of `ClassName`.

- **Type Annotations**:
  - Optional hints to editors or IDEs for better clarity and debugging.
```python
  instance: Classname = ClassName()
  ```

#### **Attributes and Methods**
- Attributes store data in an object.
- Methods define behaviors.




#### **The `__init__` Method (Initializer)**
- The `__init__` method is called automatically when an object is instantiated.
  ```python
  def __init__(self, arg1, arg2):
      self.arg1 = arg1
      self.arg2 = arg2
  ```
- `self` is a **reference to the current instance of the class**.
- It ensures that attributes and methods belong to the correct object.
- When a method is called using an instance, `self` automatically refers to that instance.

**Example:**
```python
class Example:
    def set_value(self, value):
        self.value = value

obj1 = Example()
obj1.set_value(10)  # Here, self refers to obj1
```

**Key Notes**:
1. The name `self` is a **convention**, not a rule.
   - You can replace it with any valid variable name (e.g., `this`, `instance`, or even `s`), but it is not recommended for readability.
   - **Example**:
     ```python
     class Example:
         def set_value(this, value):
             this.value = value
     ```


#### **Methods**
- Define class functionality.
  ```python
  def method_name(self, parameters):
      # method body
  ```
#### **Methods**
- Methods are functions defined within a class to operate on objects.
- Types of methods:
  1. **Instance Methods**:
     - Operate on instance attributes.
     - Always take `self` as their first parameter.
  2. **Class Methods**:
     - Operate on class attributes.
     - Use `@classmethod` decorator and take `cls` as their first parameter.
  3. **Static Methods**:
     - Do not operate on instance or class attributes.
     - Use `@staticmethod` decorator.

**Example**:
```python
class Example:
    class_attr = "Shared"

    def __init__(self, instance_attr):
        self.instance_attr = instance_attr  # Instance attribute

    @classmethod
    def class_method(cls):
        return cls.class_attr

    @staticmethod
    def static_method():
        return "Static Method"
```
---

#### **Attributes (Properties)**
- **Instance Attributes**: Specific to an object; defined using `self`.
- **Class Attributes**: Shared across all instances of the class.

**Example:**
```python
class Microwave:
    company = "HomeAppliances"  # Class attribute

    def __init__(self, brand, power_rating):
        self.brand = brand        # Instance attribute
        self.power_rating = power_rating
```
#### **Example Class**
```python
class Microwave:
    def __init__(self, brand, power_rating):
        self.brand = brand
        self.power_rating = power_rating
        self.is_on = False
    
    def turn_on(self):
        if not self.is_on:
            self.is_on = True
            print(f"{self.brand} microwave is now ON.")
        else:
            print(f"{self.brand} microwave is already ON.")
    
    def turn_off(self):
        if self.is_on:
            self.is_on = False
            print(f"{self.brand} microwave is now OFF.")
        else:
            print(f"{self.brand} microwave is already OFF.")
    
    def run(self, seconds):
        if self.is_on:
            print(f"Running {self.brand} microwave for {seconds} seconds.")
        else:
            print("Turn on the microwave first.")
```

#### **Dunder Methods**
- Also called **magic methods**, these allow you to define or override default Python behaviors for objects.

| **Method**   | **Purpose**                              |
|--------------|------------------------------------------|
| `__init__`   | Initializes the object's attributes.     |
| `__str__`    | Returns a user-friendly string.          |
| `__repr__`   | Returns a developer-friendly string.     |
| `__add__`    | Implements addition (`+`) operator.      |
| `__mul__`    | Implements multiplication (`*`) operator.|
| `__eq__`     | Implements equality comparison (`==`).   |
| `__len__`    | Returns the length of an object.         |

#### **Example: Dunder Methods**
```python
def __str__(self):
    return f"{self.brand} Microwave with {self.power_rating} power rating."

def __add__(self, other):
    return f"Combined Microwave: {self.brand} & {other.brand}"
```

#### **Applications of Dunder Methods**
1. **Readable Output**:
   - Use `__str__` and `__repr__` to make objects user- or developer-friendly.
   ```python
   print(object)  # Calls __str__
   repr(object)   # Calls __repr__
   ```
2. **Custom Operations**:
   - Implement `__add__` to define what happens when objects are added.
3. **Polymorphism**:
   - Override behavior for different data types.

#### **Python OOP Advantages**
1. **Modularity**: Encapsulates data and functionality.
2. **Reusability**: Use classes to create multiple similar objects.
3. **Maintainability**: Easier debugging and extension.

#### **Extra Notes**
- **Best Practices**:
  - Always use `self` for instance methods.
  - Follow PEP 8 for class and method naming.
- **Common Use Cases**:
  - Classes are widely used in GUI applications, data handling scripts, and simulation programs.

#### **Quick Reference for Dunder Methods**
```python
# Arithmetic
__add__(self, other)    # +
__sub__(self, other)    # -
__mul__(self, other)    # *
__truediv__(self, other) # /

# Comparison
__lt__(self, other)     # <
__le__(self, other)     # <=
__eq__(self, other)     # ==
__ne__(self, other)     # !=
__gt__(self, other)     # >
__ge__(self, other)     # >=

# String Conversion
__str__(self)           # str(obj)
__repr__(self)          # repr(obj)

# Length
__len__(self)           # len(obj)
```




#### **Reasons for Using `self`**
1. **Unique Identification**:
   - `self` ensures each object has its own set of data.
2. **Instance Method Access**:
   - Used to access attributes and methods belonging to the instance.
3. **Customization**:
   - Enables per-instance data modifications.

**Can `self` be changed?**
- Yes, you can rename it, but **do not do this unless absolutely necessary**.

---

#### **Advantages of Using Classes**
1. **Modularity**:
   - Keeps related data and methods together.
2. **Reusability**:
   - Create multiple objects using the same class.
3. **Scalability**:
   - Easy to expand functionality by adding more methods and attributes.
4. **Encapsulation**:
   - Keeps data safe from external interference.

---

#### **Object-Oriented Programming Example**
**Problem**: Simulate a microwave's basic functionality.

**Solution**:
```python
class Microwave:
    def __init__(self, brand, power_rating):
        self.brand = brand
        self.power_rating = power_rating
        self.is_on = False

    def turn_on(self):
        if not self.is_on:
            self.is_on = True
            print(f"{self.brand} Microwave is now ON.")
        else:
            print(f"{self.brand} Microwave is already ON.")

    def turn_off(self):
        if self.is_on:
            self.is_on = False
            print(f"{self.brand} Microwave is now OFF.")
        else:
            print(f"{self.brand} Microwave is already OFF.")

    def run(self, seconds):
        if self.is_on:
            print(f"Running {self.brand} Microwave for {seconds} seconds.")
        else:
            print("Turn on the microwave first.")
```

**Usage**:
```python
microwave1 = Microwave("Samsung", "800W")
microwave1.turn_on()
microwave1.run(30)
microwave1.turn_off()
```

---

#### **Summary of Key Points**
1. **Class**: Blueprint for creating objects.
2. **Object**: Instance of a class.
3. **`self`**: Reference to the current object.
4. **Attributes**: Data stored in objects.
5. **Methods**: Functions to define object behavior.
6. **Dunder Methods**: Special methods for customizing Python operations.
7. **Advantages**: Modularity, reusability, scalability, and encapsulation.

