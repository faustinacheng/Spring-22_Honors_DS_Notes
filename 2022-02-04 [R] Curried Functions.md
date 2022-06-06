4 Feb 2022

Recitation 3

*Scala Exercise:*

> Write a function `def double(li : List[Int]) : List[Int]` that uses only recursion (no while or for loops allowed) to construct a new list in which each integer has been doubled.

```scala
object recitation3 {

  def double(x : List[Int]) : List[Int] = {
    return if (x == Nil) return Nil else (x.head * 2) :: double(x.tail)
  }

  def main(args: Array[String]): Unit = {
    val x = List(1,2,3,4)

    println(double(x))
  }

}
```

 

NB: `::` creates a new list, whereas `:+` appends to an existing list



**Function vs. Method**

Method:

`def test(a : Int, b : Int) = a + b`


Function:

`val addtwo : (Int => Int) = x => x + 2`

-or-

`val addtwo = (x : Int) => x + 2`



**Terminology:**

- **First Order Function: ** A function that can be passed around like other objects
- **Higher Order Function:** A function that takes at least one function as an argument/parameter or returns a function. (Java does not have higher order functions)



**Curried Function:**

A curried function that returns a curried version of the function f:

```scala
def curry2(f : (Int, Int) => Int) : (Int => (Int => Int)) = {
    (x : Int) => ((y : Int) => f(x,y))
}
```

- Then, can call `curry2(add)(1)(2)` to return 3

- ```scala
  val add = (x : Int, y : Int) => x + y
  ```

- For example, it's a way to call a function when you're getting the arguments one at a time



