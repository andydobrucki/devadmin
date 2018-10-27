---
description: >-
  This document describes the devadmin Java coding & code documentation style,
  standards, etc.
---

# Java Coding Playbook

## **Formatting**

### **Braces**

* Braces are used with if, else, for, do and while statements, even when the body is empty or contains only a single statement
* No line break before the opening brace.
* Line break after the opening brace.
* Line break before the closing brace

```text
return new MyClass() { 
    @Override public void method() { 
        if (condition()) { 
            //something() 
        } else { 
            lastThing(); 
        }
    };
    
```

### Blank line

Blank line added before return

```text
Public int method(){
  int a = method2();
  return
```

Blank line added after some logical block is finished

```text
public void method(){
  int a = getA();
  Int b = getB();  // initialization block finished,  next block is some operation block

  extract(a, b)

}

```

Blank line added before loop states

```text
public void method(){
  int a = getA();
  Int b = getB();  // initialization block finished,  next block is some operation block

  if(a > b){
    //todo
  }

  for(int c = 0; c <= b; c++){
    //todo
  }
}

```

### Empty blocks

An empty block or block-like construct may be in K & R style **.** Alternatively, it may be closed immediately after it is opened, with no characters or line break in between \({}\), unless it is part of a multi-block statement \(one that directly contains multiple blocks: if/else or try/catch/finally

#### **Examples**

```text
// This is acceptable
  void doNothing() {}
```

```text
// This is equally acceptable
  void doNothingElse() {
  }
```

```text
 // This is not acceptable: No concise empty blocks in a multi-block statement
  try {
    doSomething();
  } catch (Exception e) {}
```

### **One statement per line**

Each statement is followed by a line break.

* Java code has a column limit of 150 characters

#### Exceptions

* Lines where obeying the column limit is not possible \(for example, a long URL in Javadoc, or a long JSNI method reference\).
* package and import statement
* Command lines in a comment that may be cut-and-pasted into a shell

### Method size limit

Try to avoid methods whose length is more than 100 row

### **Horizontal whitespace**

* Separating any reserved word, such as if, for or catch, from an open parenthesis \(\(\) that follows it on that line
* Separating any reserved word, such as else or catch, from a closing curly brace \(}\) that precedes it on that line
* Before any open curly brace \({\), with two exceptions:
  * * `@SomeAnnotation({a, b})` \(no space is used\)
    * `String[][] x = {{"foo"}};` \(no space is required between {{, by item 8 below\)
* On both sides of any binary or ternary operator. This also applies to the following "operator-like" symbols:
  * * the ampersand in a conjunctive type bound: `<T extends Foo & Bar>`
    * the pipe for a catch block that handles multiple exceptions: catch `(FooException | BarException e)`
    * the colon \(:\) in an enhanced for \("foreach"\) statement
    * the arrow in a lambda expression: `(String str) -> str.length()`
* but not
  * * the two colons \(::\) of a method reference, which is written like `Object::toString`
    * the dot separator \(.\), which is written like `object.toString()`
* After ,:; or the closing parenthesis \(\)\) of a cast
* On both sides of the double slash \(//\) that begins an end-of-line comment. Here, multiple spaces are allowed, but not required.
* Between the type and variable of a declaration: `List<String>` list
* Optional just inside both braces of an array initializer
  * * new int\[\] {5, 6} and new int\[\] { 5, 6 } are both valid between a type annotation and \[\] or ...**.**



### **Variable declarations**

*  One variable per declaration
  * Every variable declaration \(field or local\) declares only one variable: declarations such as `int a, b;` are not used.
  * Exception: Multiple variable declarations are acceptable in the header of a for loop.

### **Horizontal alignment: never required**

Here is an example without alignment, then using alignment:

```text
private int x; // this is fine
private Color color; // this too
```

```text
private int   x;      // permitted, but future edits
private Color color;  // may leave it unaligned
```

### **Naming**

Rules common to all identifiers

* Identifiers use only ASCII letters and digits, and, in a small number of cases noted below, underscores. Thus each valid identifier name is matched by the regular expression `\w+`
* Identifiers should be meaningfull, and explain what they contain, or what will be done in method \(e.x: model, `extractModel()`, etc\)

Rules by identifier type

* Package names
  * Package names are all lowercase, with consecutive words simply concatenated together \(no underscores\). For example, `com.example.deepspace`, not `com.example.deepSpace` or `com.example.deep_space`.
* Class names are written in UpperCamelCase.
  * Class names are typically nouns or noun phrases. For example, Character or ImmutableList. Interface names may also be nouns or noun phrases \(for example, List\), but may sometimes be adjectives or adjective phrases instead \(for example, Readable\).
* Method names are written in lowerCamelCase.
  * Method names are typically verbs or verb phrases. For example, `sendMessage()` or `stop()`
* Constant names use `CONSTANT_CASE`: all uppercase letters, with each word separated from the next by a single underscore.
* Non-constant field names \(static or otherwise\) are written in lowerCamelCase.
  * These names are typically nouns or noun phrases. For example, computedValues or index
* Parameter names are written in lowerCamelCase
* Local variables are written in lowerCamelCase

