# Event Sourcing

## Example Project

* [johnbywater/eventsourcing](https://github.com/johnbywater/eventsourcing/tree/master)

## Concept

Current View

```
                               +------------------+
                               |                  |
                               |   Application    |
                               |                  |
                               +--------+---------+
                                        |
                                        | Operates
                                        |
                               +--------v---------+
                               |                  |
                               |   Domain Models  |
                               |                  |
                               +--------+---------+
                                        |
                                        | Generates
                                        |
                                 +------v-----+
                                 |            |
                                 |   Events   |
                                 |            |
                                 +------^-----+
                                        |
                                        | Listen for
                                        |
                              +---------+----------+
                              |                    |
                              |  Storage Service   |
                              |                    |
                              +--+--------------+--+
                                 |              |
                                 |              |
                     Operates    |              |    Operates
                                 |              |
                                 |              |
                    +------------v----+    +----v--------------+
                    |                 |    |                   |
                    |  Domain Models  |    | Models Changelog  |
                    |                 |    |                   |
                    |     Database    |    |    Database       |
                    |                 |    |                   |
                    +-----------------+    +-------------------+

```