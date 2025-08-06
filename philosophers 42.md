## Greedy Philosopher

The term "greedy philosopher" in the context of the 42 project "Philosophers" refers 
to a scenario or a potential issue within the simulation of the Dining Philosophers Problem.

The Dining Philosophers Problem is a classic computer science problem used to illustrate 
synchronization issues in concurrent programming, specifically dealing with resource 
allocation and avoiding deadlocks and starvation.

A **"greedy philosopher"** would be a philosopher in the simulation who, due to the implemented 
logic or lack of proper synchronization, attempts to acquire both forks they need to eat 
without considering the availability of those forks for other philosophers. 
This "greed" can lead to:

●**Deadlock** :
If all philosophers simultaneously pick up one fork (e.g., their left fork) and then wait indefinitely
for their right fork, no one can eat, and the simulation stalls. 
This is a common outcome of a "greedy" or unsynchronized approach.

●**Starvation** :
While not necessarily a full deadlock, a "greedy" philosopher might repeatedly acquire forks 
and eat, preventing other philosophers from ever getting enough resources to eat, leading to 
their starvation and the simulation's end.

The project's goal is to implement a solution that prevents such "greedy" behavior and ensures 
all philosophers can eat without dying of starvation or causing a deadlock.

This is typically achieved through synchronization mechanisms like **mutexes**, **semaphores**, or other resource management strategies.

## Race Condition

In the context of the 42 Philosophers project, **a race condition occurs when multiple threads (philosophers) attempt to access and modify shared resources (forks or status variables) concurrently without proper synchronization, leading to unpredictable and potentially incorrect program behavior**.

Here's a breakdown of how race conditions manifest in this project:
✘**Fork Acquisition**:

If two adjacent philosophers try to pick up the same shared fork at the exact same time, a race condition can occur.
Without synchronization mechanisms like mutexes, both philosophers might attempt to acquire the fork simultaneously, leading to a situation where only one successfully acquires it, while the other might incorrectly believe they also have it, or the state of the fork becomes inconsistent.

✘**Status Updates**:

Philosophers' states (eating, thinking, sleeping, or even "last meal eaten" timestamps) are often shared variables that need to be updated.
If multiple threads try to update these variables concurrently without protection, the final value might not be what's expected due to interleaved operations.
For example, if two philosophers try to update a shared "meals eaten" counter, the final count might be lower than the actual number of meals consumed if updates are not atomic.

✘**Starvation and Death Conditions**:

The project requires monitoring philosophers' hunger levels and detecting starvation. If the logic for checking and declaring a philosopher's death (based on time since last meal) is not properly synchronized, a race condition could lead to a philosopher being declared dead prematurely or not being declared dead when they should be, if multiple threads are checking and updating related timestamps.
Consequences of Race Conditions:

✘**Incorrect Behavior**:

The most direct consequence is that the simulation might not behave as intended. Philosophers might eat without truly possessing two forks, or the simulation might end prematurely or continue indefinitely due to inaccurate state tracking.

✘**Deadlock**:

While not a race condition itself, race conditions can contribute to deadlocks by creating inconsistent states that prevent philosophers from acquiring necessary resources.

✘**Unpredictable Outcomes**:

Race conditions can be difficult to debug because they are often non-deterministic, meaning they might not occur every time the program runs, or they might only appear under specific timing conditions.

✘**Mitigation**:

To prevent race conditions in the Philosophers project, synchronization primitives such as mutexes are essential. 
Mutexes ensure that only one thread can access a shared resource at a time, preventing concurrent modifications and ensuring data integrity. For example, a mutex can be associated with each fork, ensuring that only one philosopher can pick up a specific fork at any given moment.
