# Reliable, Scalable, and Maintainable Applications

A data-intensive application is built from standard building blocks that provide commonly needed functionality. Some of these standard building blocks are:
* **Databases**: used to store and retrieve information.
* **Caches**: remember the results for expensive operation, and speed up the reads.
* **Search Indexes**: allow users to search the data using keywords / search terms and filter the data in various ways.
* **Stream Processing**: send messages to another process to handle asynchronously.
* **Batch Processing**: periodically crunch a large amount of accumulated data.

Each of the above building blocks can be approached differently, for example - there are different types of databases, different caching strategies, several ways of building search indexes, and choices for stream / batch processing. Determining which building blocks are best suited for the task at hand requires tradeoff, which is what system design is all about.

An example architecture using these building blocks that shows application code is responsible for invalidating the cache and search indexes, and how async tasks go to a message queue for processing.

![alt text](images/01-01-example-architecture.png)


## Reliability

* The ability of system to work correctly (i.e. providing the correct functional result at a desired level of performance) even in the face of faults (hardware, software, or human errors).
* A reliable system is fault-tolerant or fault-resilient.
* Fault vs Failure
  * Fault is system deviating from what its specs.
  * Failure is the system stopping to provide the service to the user.
* It is impossible to have a system with zero faults so it's best to develop a fault tolerant system that can *prevent faults from causing failures*.
* Often faults are introduced intentionally (killing processes without warning, or terminating instances) to detect if introduction of faults does not cause the whole system failure. An example of such system is Chaos Monkey (used by Netflix).
