# Design Patterns - Lecture 2

## Value Object

#### Equality : equal if all members are equal

```
Point a = new Point(1, 2)
Point b = new Point(1, 2)

a.equals(b) => true!
```
With the help of case class and immutable(`val`) definition  
Very useful in concurrent programming! Ex. money, transactions, ....

#### Value Object in Scala
```
val point = (1, 2)
case class Rectangle() {}
```
Use tuples and case classes, because equals(), hashCode(), toString() is automatically generated.  
It is much better to keep the items immutable.

#### Value object in JAVA  
-> requires overriding of 2 functions, `equals` and `hashCode`
```
class A() {
  bool equals()   => error prone!
  int hashCode()  => error prone!
}
```
> Object Equality is very very tricky to implement!

## Null Object

in scala, use `Option[T]`.  
in other languages, use `NullObject`.

## Strategy Pattern

- Defines a family of interchangeable algorithms
- Selects an algorithm at runtime
  - in Scala, simply pass first-class functions
  - in C, use function pointers
  - in Java/C++, use base class and subclasses
  
In Java, make `Base class`, `Strategies classes`, and `Context class`.
In Scala
```
type Strategy = (Int, Int) => Int
val add: Strategy = _+_
val multiply: Strategy = _*_

class Context(c: Strategy) {
  def use(a, b) { c(a, b) }
}
new Context(multiply).use(2, 3)
```


