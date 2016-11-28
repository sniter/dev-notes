# Reactive Programming

It is set of programming patterns and techniques.

Being reactive means readily responsive to a stimulus.

## Global Product Requirements

* Response time: seconds -> milliseconds
* nodes: 10 -> 1000
* maintenance downtime: hours -> never
* data volume: GB -> PB

## Application requirements

### React on events

Application should be event driven

* application is composed from loosely coupled event handlers
* events can be handled asynchronously

### React to load

Application should have scalable architecture

* scale up: make use of parallelism in multi-core system
* scale out make use of multiple server nodes
* important key for scalability: minimize shared mutable state
* important key fro scale out: location transparency, resilience

### React to failure: 

Be resilient (possibility to recover from failures)

* Software failures
* Hardware failures
* Connection failures
* Resilience cannot be added as an afterthought; it needs to be part of design from the beginning

####  Resilient Design requirements:

* loose coupled
* strong encapsulation of state
* pervasive supervisor hierarchies

### React of users, be responsive 

Provide rich, real-time interaction with its users under load and in presence  of failures

## Callbacks

### Cons

* sometimes needs to shared mutable state
* cannot be composed
* leads quickly to callback-hell

### How to improve

* Composable event abstractions
* Events are first class
* Events are represented as messages
* Handlers of events are also first class
* Complex handlers can be composed from primitive ones