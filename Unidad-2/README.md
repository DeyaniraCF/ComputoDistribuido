**An Introduction to Asynchronous Programming in Python**

Asynchronous programming is a type of parallel programming in which a unit of work is allowed to run separately from the primary application thread.
When the work is complete, it notifies the main thread about completion or failure of the worker thread. There are numerous benefits to using it, such as improved application performance and enhanced responsiveness.

With asynchronous programming, you allow your code to handle other tasks while waiting for these other resources to respond.


**1. Multiple Processes**
The most obvious way is to use multiple processes. From the terminal, you can start your script two, three, four…ten times and then all the scripts are going to run independently or at the same time. The operating system that’s underneath will take care of sharing your CPU resources among all those instances. Alternately you can use the multiprocessing library which supports spawning processes.

**2. Multiple Threads**
The next way to run multiple things at once is to use threads. A thread is a line of execution, pretty much like a process, but you can have multiple threads in the context of one process and they all share access to common resources. 

**3. Coroutines using yield**
Coroutines are generalization of subroutines. They are used for cooperative multitasking where a process voluntarily yield (give away) control periodically or when idle in order to enable multiple applications to be run simultaneously. Coroutines are similar to generators but with few extra methods and slight change in how we use yield statement. Generators produce data for iteration while coroutines can also consume data.

**4. Asynchronous Programming**
The fourth way is an asynchronous programming, where the OS is not participating. As far as OS is concerned you’re going to have one process and there’s going to be a single thread within that process, but you’ll be able to do multiple things at once.
The answer is asyncio is the new concurrency module introduced in Python 3.4. It is designed to use coroutines and futures to simplify asynchronous code and make it almost as readable as synchronous code as there are no callbacks.

Asyncio uses different constructs: event loops, coroutinesand futures.
-An event loop manages and distributes the execution of different tasks. It registers them and handles distributing the flow of control between them.
-Coroutines (covered above) are special functions that work similarly to Python generators, on await they release the flow of control back to the event loop. A coroutine needs to be scheduled to run on the event loop, once scheduled coroutines are wrapped in Tasks which is a type of Future.
-Futures represent the result of a task that may or may not have been executed. This result may be an exception.

Using Asyncio, you can structure your code so subtasks are defined as coroutines and allows you to schedule them as you please, including simultaneously. Coroutines contain yield points where we define possible points where a context switch can happen if other tasks are pending, but will not if no other task is pending.

A context switch in asyncio represents the event loop yielding the flow of control from one coroutine to the next.

**Using Redis and Redis Queue RQ**
Using asyncio and aiohttp may not always be in an option,  Also, there will be scenarios when you would want to distribute your tasks across different servers. In that case we can leverage RQ (Redis Queue). It is a simple Python library for queueing jobs and processing them in the background with workers. It is backed by Redis — a key/value data store.