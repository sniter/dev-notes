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

Function

        val f:A=>B = (a:A):B => ???

Functor

    val f:A

## Patterns

* Actors / FSM
* CQS/CQRS

## Languages

* Erlang
* Haskell
* Scala
* Python

