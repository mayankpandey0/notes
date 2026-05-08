# Event Sourcing Architecture

## What is Event Sourcing?
Instead of storing just the current state of the data in a domain, Event Sourcing involves storing all changes to the application state as a sequence of events. 

### Core Concepts:
- **Events**: The source of truth. Every change in state is an event. Events are immutable and strictly append-only.
- **Event Store**: The database that stores the events. It acts as the system of record.
- **Projections/Views**: Since reconstructing the current state by replaying thousands of events is slow, systems create "read models" or "projections". These are updated asynchronously when new events arrive.

### Advantages:
- **Audit Trail**: You get a 100% reliable audit log for free.
- **Time Travel**: You can reconstruct the state of the system at any given point in time.
- **Debugging**: Easily replay events to see exactly how the system arrived at a bug.

### Disadvantages:
- **Complexity**: Requires a paradigm shift in thinking.
- **Eventual Consistency**: Read models are usually updated asynchronously, meaning the system is eventually consistent.
- **Event Versioning**: Schema changes in events can be very tricky to handle over time.

### Common Tooling:
- Apache Kafka
- EventStoreDB
- AWS Kinesis
