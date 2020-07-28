# Functional Programming

Decralative paradigm that treats computation like evaluation math functions

* avoid changing state and mutable data
* functions are first-class objects
* higher order functions (passing type as parameters)
* no side effects
* no inheritance
* use recursion instead of loops
* higher order functions allow compile to increase optimization and also provide lazy initialization

## Pros

* better reliability for code
* unit testing is simpler
* compiler optimisation
* scalable

## Cons

* Memory consuption, required high perfomance garbage collector
* lazy initialization may lead to unpredictable order of functions call, that can affect the input/output

## Theory

Look for Theory of Categories

### Semigroup

Monoid is a typeclass with method that combines two parameters of type `A` into result of type `A`

```scala
trait Semigroup[A]{
    def combine(a: A, b: A): A
}
```

I.e.

```scala
trait Sum[Int]{
    def combine(a Int, b: Int): Int = a + b
}
```

### Monoid 

```scala
trait Monoid[A] extends Semigroup[A]{
    def empty: A
}
```

#### Monoid laws

** Associativity **

```scala
val x: A = ???
val y: A = ???
val m: Monoid[A] = ???

m.combine(x, y) == m.combine(y, x)s
```

** Identity **

If combine any value of type `A` with `Monoid[A].empty` the result will be equal inital value 

```scala
val x: A = ???
val m: Monoid[A] = ???
m.combine(x, m.empty) == x && m.combine(m.empty,x) == x // true
```

let's look throug algebraic analogy

```scala
2 + 0 == 0 + 2 == 2 // true
```

### Functor

```scala
trait Functor[F[_]]{
    def map[A,B](fa: F[A])(f: A => B): F[B]
}
```

#### Functor laws

** Identity **

```scala
val fa: Functor[F[A]] = ???

fa.map(a => a) == fa // true
```

** Composition **

```scala
val fa: Functor[F[A]] = ???
val f: A => B = ???
val g: B => C = ???

fa.map(g(f(_))) == fa.map(f).map(g)
```

### Applicative Functor

```scala
trait Applicative[F[_]] extends Functor{
    def pure[A](v: A) => F[A]
}
```

### Monad

```scala
trait Monad[F[_]] extends Applicative{
    def flatMap[A,B](fa: F[A])(f: A => F[B]): F[B]
}
```

#### Monad Laws

** Left identity **

```scala
val a: F[A]
val m: Monad[F[A]]
val func: A => F[B]

m.pure(a).flatMap(func) == func(a) // true
```

** Right identity **

```scala
m.flatMap(m.pure) == m // true
```

** Associativity **

```scala
val m: Monad[F[A]] = ???
val f: A => F[B] = ???
val g: B => F[C] = ???

m.flatMap(f).flatMap(g) == m.flatMap(x => f(x).flatMap(g))
```

TODO: Complete it

## Patterns

* Actors / FSM
* CQS/CQRS

## Technologies

* MQ

## Languages

* Erlang
* Haskell
* Scala
* Python
* Javascript

