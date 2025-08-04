## The term "greedy philosopher" in the context of the 42 project "Philosophers" refers 
## to a scenario or a potential issue within the simulation of the Dining Philosophers Problem.
## The Dining Philosophers Problem is a classic computer science problem used to illustrate 
## synchronization issues in concurrent programming, specifically dealing with resource 
## allocation and avoiding deadlocks and starvation.
A "greedy philosopher" would be a philosopher in the simulation who, due to the implemented 
logic or lack of proper synchronization, attempts to acquire both forks they need to eat 
without considering the availability of those forks for other philosophers. This "greed" can lead to:
Deadlock:
If all philosophers simultaneously pick up one fork (e.g., their left fork) and then wait indefinitely
for their right fork, no one can eat, and the simulation stalls. This is a common outcome of 
a "greedy" or unsynchronized approach.
Starvation:
While not necessarily a full deadlock, a "greedy" philosopher might repeatedly acquire forks 
and eat, preventing other philosophers from ever getting enough resources to eat, leading to 
their starvation and the simulation's end.
The project's goal is to implement a solution that prevents such "greedy" behavior and ensures 
all philosophers can eat without dying of starvation or causing a deadlock. This is typically 
achieved through synchronization mechanisms like mutexes, semaphores, or other resource management strategies.
