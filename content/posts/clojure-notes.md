---
title: Clojure Fundamentals
date: 2023-03-04
tags: [clojure]
---

Dialect of Lisp, that runs on JVM, CLR and also targets JavaScript (Can be transpiled to JS).
Many features were inherited from Lisp, but also adds on to it. Created by Rich Hickey. It has a big emphasis on concurrency, it is built into the language.

* Dynamic Language
  * Flexibility
  * Interactivity (Using REPL)
  * Consise (they tend to be easier to write, less verbose)
  * Exploration 
  * Focus on the problem
* Functional
* Hosted on the JVM
* Supports Concurrency
* Open Source

## Functional Programming Languages

* Functions as first class objects : Functions are the same as a integer or a string or any other data structure, they can be created and modified on the fly. They can be passed as parameters and be returned by another function. 

* Compose simple functions together to obtain a function, that targets a more complex purpose.

* Pure Function : A function for a set of arguements always returns the same output, and is not affected by anything else.

* Immutability : It can't be changed once it has been declared. It is important when concurrency comes into the picture. Avoids then need for locking a variable when multiple agents are needed to act on it.

* Laziness : A programming language will only do, as much work as it is asked to do. In haskell, if `i = 1+2` , the operation won't be performed until i is accessed. In clojure, it is not lazy in terms of mathematical operations, but it is in terms of sequences. We could generate a list of prime numbers.

## Who uses Clojure ? 

* Swym
* Boeing
* Cisco
* Netflix
* CitiGroup
* LinkedIn
* Walmart
* Salesforce
* HelpShift

## Why Clojure ?

* Expressive, Elegant
* Good Performance
  * Useful for the same tasks Java is
  * Wrapper-free Java Access
* Powerful Extensibility
* Functional Programming and Concurrency

### Clojure is a Lisp

* Dynamic
* Code as data
* Reader
* Small Core (Lesser Syntax)
* Sequences
* Syntactic Abstraction

### Dynamic Development

* REPL - read-eval-print-loop
* Define functions on the fly
* Load and Compile code at runtime
* Introspection
* Interactive Environment

### Atomic Data Types

* Arbitrary Precision Integers
* Doubles - 1.234
* BigDecimals - 1.234M
* Ratios - 22/7
* Strings - "fred" -> Only double quotes permitted
* Characters - \a \b \c
* Symbols - fred, ethel
* Keywords - :fred, :ethel
* Booleans - true false 
  * Only `false` and `nil` are logically false in clojure, everything else is logically true.
* Null - nil
* Regex Patterns - #"a*b"

### Data Structures

* Lists - singly linked (grows at front)
  * `(1 2 3 4 5) (fred ethel lucy) (list 1 2 3)`
* Vectors - indexed access, grow at end
  * `[1 2 3 4 5] [fred  ethel lucy]` // Anything can be a element of a vector
* Maps - key/value associations
  * Unordered (Hash Map)
  * Constant or Near Constant Time LookUp
  * `{:a 1, :b 1, :c 3} {1 "ethel" 2 "fred"}`
* Sets 
  * `#{fred ethel lucy}`
* Everything Nests
* All are heterogeneous

### Syntax

* Data Structures are the code
* Homoiconicity
* No more text-based syntax!

### Java Evaluation
![Java Evaluation](/media/clojure-notes/eval-java.png)

### Clojure Evaluation
![Clojure Evaluation](/media/clojure-notes/eval-cloj.png)

### Interactivity, Programs Writing Programs and Syntactic Abstractions
![Interacitivity and Programs Writing Programs](/media/clojure-notes/adv-clj.png)

The program generates the data structures and these data structures are then compiled. There are macros. 

## Expressions

* Everything is an expression
* All data literals represent themselves
  * Except: 
    * Symbols -> Looks for binding to value, locally then globally.
    * Lists -> A form of operation.

## Operations

* (op ...) -> general format of operations
* Clojure will try to evaluate the first thing inside the paranthesis as a function call.
* The open ends need not always be a data arguement and can be an expression or a function call, whose output is used.
* An op can be :
  * one of very few `Special Ops`
  * macro
  * expression which yields a function

  * Special Ops: (They may not be evaluated)
    * (`def` name value-expr)
      * establishes a global variable
    * (`if` text-expr then-expr else-expr)
      * Conditional, evaluates only one of then/else.
    * Other Special Ops:
     
        `fn let loop recur do new . throw try set! quote var`

## Macros

* Supplied with Clojure
* Arguement forms are passed as data to the macro function, which returns a new data structure as a replacement for the macro call.
* Macro handling occurs at compile time.
```clj
(or x y) ; or is not primitive it can be defined in terms of if

becomes

(let [or__158 x]
    (if or__158 or__158 y))
```
Many things built into other languages are just macros in Clojure.

## Functions

* First Class Values
* Maps, Vectors and Sets and all are functions in Clojure

```clj
    (def five 5)
    (def sqr (fn [x] (* x x)))
    (sqr five)
    >>> 25
    (def m{:fred :ethel :ricky :lucy})
    (m :fred)
    :ethel
```

## Syntax Summary clj // java

```clj
(def i 5) ; int i = 5;

(if (zero? x) y z) ; if(x == 0)
                   ;        return y;
                   ;   else
                   ;         return z;

(* x y z) // x * y * z

(foo x y z) // foo(x, y, z); 

(. foo bar x) // foo.bar(x)
```

## Sequences

* Abstraction of Lisp Lists
* (seq coll)
  * if collection is non-empty, return seq object on it, else nil
* (first seq)
  * returns first element
* (rest seq)
  * returns a seq of the rest of the elements, or nil if no more. All but the first.

## Sequence Library

```clj
(drop 2 [1 2 3 4 5])
>>> (3 4 5)

(take 9 (cycle [1 2 3 4]))
>>> (1 2 3 4 1 2 3 4 1)

(interleave [:a :b :c :d :e] [1 2 3 4 5])
>>> (:a 1 :b 2 :c 3 :d 4 :e 5)

(partition 3 [1 2 3 4 5 6 7 8 9])
>>> ((1 2 3) (4 5 6) (7 8 9))

(map vector [:a :b :c :d :e] [1 2 3 4 5])
>>> ([:a 1] [:b 2] [:c 3] [:d 4] [:e 5])

(apply str(interpose \, "asdf"))
>>> "a,s,d,f"

(reduce + (range 100))
>>> 4950
```

## Java Interoperability

```clj
(. Math PI)
>>> 3.14159265

(.. System getProperties (get "java.version"))
>>> "1.5.0_13"

(new java.util.Date)
>>> Thu Jun 05 12:37:32 EDT 2008

(doto (JFrame.) (add (JLabel. "Hello World")) pack show)

;expands to:
(let* [G__1837 (JFrame.)]
    (do (. G__1837 (add (JLabel. "Hello World")))
        (. G__1837 pack)
        (. G__1837 show))
    G__1837)
```

## REPL

* Read Eval Print Loop
* Interactive Shell
* Used for exploratory Programming
* Provided a quick feedback cycle
* Connect to the application running in production

```clj
Clojure 1.11.1
>> "i am a string"
"i am a string"

; Equality
>> (= 1 2)
false

; Add
>> (+ 1 2 3 4)
10

; Multiply
>> (* 1 2 3 4)
24

; Return first element
>> (first [1 2 3 4])
1

; apply a function to all element in a sequence and return the resulting sequence
>> (map inc [1 2 3])
(2 3 4)

; Remove based on a condition (here zero? checks for = 0)
>> (remove zero? [1 0 2 0 3 0])
(1 2 3)

; Comments look like this

; if statement
>> (if true "hello" "bye")
"hello"

>> (if false "hello")
nil ; the else part returns nil automatically (if test-form then-form else-form)

>> (if (zero? 1) (inc 1) (dec 1))
0 ; 1 not equal to 0, so (dec 1) = 0

>> (if (zero? 0) (inc 1) (dec 1))
2 ; 0 equal to 0, so (inc 1) = 2

; do operator (allows us to wrap multiple forms together and run them as one expression)
>> (if true (do (println "hello") (println "world")) (do (println "bye") "good bye"))
hello ; this is a side effect of println
world ; this is a side effect of println
nil ; this is a return value of (println "world") and the return value of (println "hello") is ignored.
; in do, the return value is the return value of the expression that is evaluated last.

>> (do "clojure" "is fun")
"is fun" ; "clojure" is avoided and only "is fun" is returned by do, since it is the last form to be evaluated.

;when operator - used when there is no else part. Combination of if and do. It can also be written just using 'if' and 'do'.
>> (when true (println (+ 1 2)) (+ 1 4))
3 ; side effect of println
5 ; return value of 'when'
```
A valid clojure expression is called a form, every form returns a value. By convention, if a function returns a true/false(predicate function), we suffix it with a question mark. A function that does a mutataion, we suffix an exclamation mark.

```
CTRL + L is used to clear REPL

```
