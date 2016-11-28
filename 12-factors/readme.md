# The 12 Factors

## Codebase

One Codebase tracked in revision control

## Dependencies

Explicitly declare and isolate dependencies

## Configuration

Store Configuration in ENV

## Backing services

All the backing services should be treat like attachable resources

## Build, Release, Run

Separate build and run stages

## Processes

Execute app as on or mor stateless processes

## Port binding

Export service via port binding

## Concurrency

Using Loose Coupling, Low Cohension principle for Orcchestrate task. Each type of work should have
specific Process Type. 

## Disposability

Fast startup and graceful shutdown

## Dev/prod parity

Keep development, staging and production as similar as possible. Unifying envs allow unify testing, deployment

## Logs

Treat logs as Event Streams

## Admin processes

Admin code must be shipped together with application code to avoid sync issues