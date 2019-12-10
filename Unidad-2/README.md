**Table of contens**

[An Introduction to Asynchronus Programming in Python](#an-introduction-to-asinchronus-programming-in-python)
[3. Coroutines using yield](#coroutines-using-yield)

# **An Introduction to Asynchronous Programming in Python**

Asynchronous programming is a type of parallel programming in which a unit of work is allowed to run separately from the primary application thread.
When the work is complete, it notifies the main thread about completion or failure of the worker thread. There are numerous benefits to using it, such as improved application performance and enhanced responsiveness.

With asynchronous programming, you allow your code to handle other tasks while waiting for these other resources to respond.


**1. Multiple Processes**

The most obvious way is to use multiple processes. From the terminal, you can start your script two, three, four…ten times and then all the scripts are going to run independently or at the same time. The operating system that’s underneath will take care of sharing your CPU resources among all those instances. Alternately you can use the multiprocessing library which supports spawning processes.
This is a code, create in python "Multiple processes"
from multiprocessing import Process

#a function to print with, the continent word or attribute is 
#created to then change that attribute to some other desired
def print_func(continent='Asia'):
    print('The name of continent is : ', continent)
#a condition is created to add names where the continent is sent to print
if __name__ == "__main__":  # confirms that the code is under main function
    names = ['America', 'Europe', 'Africa']
    procs = []
    proc = Process(target=print_func)  # instantiating without any argument
    procs.append(proc)
    proc.start()

    # instantiating process with arguments
    for name in names:
        # print(name)
        proc = Process(target=print_func, args=(name,))
        procs.append(proc)
        proc.start()

    # complete the processes
    for proc in procs:
        proc.join()

In this practice we can see how a multiprocess is clearly seen when carrying out an overload of data in the containing variable by adding the desired information.


**2. Multiple Threads**

The next way to run multiple things at once is to use threads. A thread is a line of execution, pretty much like a process, but you can have multiple threads in the context of one process and they all share access to common resources. 
import threading

def print_cube(num):
    """
    function to print cube of given num
    """
    print("Cube:{}".format(num * num * num))
    
    def print_square(num):
        """
        function to print square of given num
        """
        print("Square: {}".format(num * num)
        
        if_name_=="_main_":
            #Creating thread
            t1 = threading.Thread(target=print_square, args+(10,))
            t2 = threading.Thread(target=print_cube, args+(10,))
            
            #Initial thread 1 and thread 2
            t1.start()
            t2.start()
            
            #the thread wait for complete
            t1.join()
            t2.join()
            
            #completely executed
            print("Done!")


 **3. Coroutines using yield**

Coroutines are generalization of subroutines. They are used for cooperative multitasking where a process voluntarily yield (give away) control periodically or when idle in order to enable multiple applications to be run simultaneously. Coroutines are similar to generators but with few extra methods and slight change in how we use yield statement. Generators produce data for iteration while coroutines can also consume data.

def print_name(prefix):
    print("Searching prefix:{}".format(prefix))
    try :
        while True:
            #yeild used to create coroutine
            name=(yield)
            if prefix in name:
                print(name)
    except GeneratorExit:
        print("CLosing coroutine!!")
        
corou = print_name("Dear")
corou._next_()
corou.send("James")
corou.send("Dear James")
corou.close()


**4. Asynchronous Programming**

The fourth way is an asynchronous programming, where the OS is not participating. As far as OS is concerned you’re going to have one process and there’s going to be a single thread within that process, but you’ll be able to do multiple things at once.
The answer is asyncio is the new concurrency module introduced in Python 3.4. It is designed to use coroutines and futures to simplify asynchronous code and make it almost as readable as synchronous code as there are no callbacks.

Asyncio uses different constructs: event loops, coroutinesand futures.
- An event loop manages and distributes the execution of different tasks. It registers them and handles distributing the flow of control between them.
- Coroutines (covered above) are special functions that work similarly to Python generators, on await they release the flow of control back to the event loop. A coroutine needs to be scheduled to run on the event loop, once scheduled coroutines are wrapped in Tasks which is a type of Future.
- Futures represent the result of a task that may or may not have been executed. This result may be an exception.

Using Asyncio, you can structure your code so subtasks are defined as coroutines and allows you to schedule them as you please, including simultaneously. Coroutines contain yield points where we define possible points where a context switch can happen if other tasks are pending, but will not if no other task is pending.

A context switch in asyncio represents the event loop yielding the flow of control from one coroutine to the next.

**Using Redis and Redis Queue RQ**

Using asyncio and aiohttp may not always be in an option,  Also, there will be scenarios when you would want to distribute your tasks across different servers. In that case we can leverage RQ (Redis Queue). It is a simple Python library for queueing jobs and processing them in the background with workers. It is backed by Redis — a key/value data store.

"Flavio was here"
Setting up your Environment


**Async IO in Python: A Complete Walkthrough**

Async IO is a concurrent programming design that has received dedicated support in Python, evolving rapidly from Python 3.4 through 3.7, and probably beyond.

**Where does Async IO fit in?**

The concurrence and the parallelism are expansive subjects in which it is not easy to get into. The parallelism consists of performing multiple operations at the same time. Multiprocessing is a means to achieve parallelism and involves the distribution of tasks over the central processing units (CPUs or cores) of a computer. Multiprocessing is very suitable for tasks related to the CPU. Concurrency is a slightly broader term than parallelism. It suggests that multiple tasks have the ability to execute in an overlapping manner.
Threading is a concurrent execution model in which several threads take turns executing tasks. A process can contain multiple threads.The important thing to know about threads is that it is better for tasks linked to IO.

To be clear, async IO is not a newly invented concept, and it has existed or is being incorporated into other languages ​​and runtime environments ,, Python asynciodocumentation bills the package as a library to write concurrent code. However, asynchronous IO is not threading, nor is it multiprocessing. It is not built on any of these. In fact, async IO is a single process and single thread design: it uses cooperative multitasking.
Python asynciodocumentation bills the package as a library to write concurrent code. However, asynchronous IO is not threading, nor is it multi-processing, async IO is a single-process and single-threaded design: it uses cooperative multitasking.
To reiterate, asynchronous IO is a concurrent programming style, but it is not parallel.

**The asyncio Package and async/await**

The Python asyncio package and its two keywords, async and await, serve different purposes but come together to help you declare, build, execute, and manage asynchronous code ..
In the heart of async IO there are corutinas: a corutina is a function that can suspend its execution before arriving return, and can indirectly pass the control to another corutina for some time.

**The rules of Async IO**

The async syntax defines a native corutin or an asynchronous generator.
The await keyword returns the function control to the event loop.
Using await and / or return creates a coroutine function. To call a coroutine function, you must await it to get its results.
To use yielden an async defblock. This creates an asynchronous generator, with which you iterate async for ..
Anything defined with async defno can be used yield from, which will raise SyntaxError.
Just as it is a SyntaxErroruso yield out of a deffunction, it is a SyntaxErroruso await out of a defunct async. You can only use awaiten the body of corutins.


**Async IO Design Patterns**

Chaining Corutinas
A key feature of corutins is that they can be chained together. (Remember, an object of corutina is waiting, so that another corutina can await it). This allows you to divide the programs into smaller, manageable and recyclable corutins.
Using a tail
The asynciopackage provides queue classes that are designed to be similar to the classes of the queuemodule. There is an alternative structure that can also work with asynchronous I / O: several producers, which are not associated with each other, add elements to a queue. Each producer can add several elements to the queue at staggered, random moments and without prior notice. A group of consumers pull items out of the queue as they appear, greedily and without waiting for any other signal.

**Async IO's Roots in Generators**

The result of calling a coroutine on its own is an awaitable coroutine object.
what other feature of Python looks like this? coroutines are enhanced generators under the hood. The behavior is similar in this regard:Generator functions are, as it so happens, the foundation of async IO
One critical feature of generators as it pertains to async IO is that they can effectively be stopped and restarted at will.
Keep in mind that yield, and by extension yield from and await, mark a break point in a generator’s execution.

This is the fundamental difference between functions and generators. A function is all-or-nothing. Once it starts, it won’t stop until it hits a return, then pushes that value to the caller. A generator, on the other hand, pauses each time it hits a yield and goes no further. Not only can it push this value to calling stack, but it can keep a hold of its local variables when you resume it by calling next() on it.
There’s a second and lesser-known feature of generators that also matters. You can send a value into a generator as well through its .send() method. This allows generators (and coroutines) to call (await) each other without blocking.
here are some key points on the topic of coroutines as generators:
Coroutines are repurposed generators that take advantage of the peculiarities of generator methods.
Old generator-based coroutines use yield from to wait for a coroutine result. Modern Python syntax in native coroutines simply replaces yield from with await as the means of waiting on a coroutine result. The await is analogous to yield from, and it often helps to think of it as such.
The use of await is a signal that marks a break point. It lets a coroutine temporarily suspend execution and permits the program to come back to it later.

**Other Features: async for and Async Generators + Comprehensions**

Python also enables async for to iterate over an asynchronous iterator. The purpose of an asynchronous iterator is for it to be able to call asynchronous code at each stage when it is iterated over.
A natural extension of this concept is an asynchronous generator.Recall that you can use await, return, or yield in a native coroutine.
Python enables asynchronous comprehension with async for. Like its synchronous cousin, this is largely syntactic sugar:
This is a crucial distinction: neither asynchronous generators nor comprehensions make the iteration concurrent. All that they do is provide the look-and-feel of their synchronous counterparts, but with the ability for the loop in question to give up control to the event loop for some other coroutine to run.
asynchronous iterators and asynchronous generators are not designed to concurrently map some function over a sequence or iterator. They’re merely designed to let the enclosing coroutine allow other tasks to take their turn. The async for and async with statements are only needed to the extent that using plain for or with would “break” the nature of await in the coroutine. This distinction between asynchronicity and concurrency is a key one to grasp.

**The Event Loop and asyncio.run()**

You can think of an event loop as something like a Truebucle while monitoring routines. It is capable of waking an inactive corutina when anything you are waiting for is available.
asyncio.run (), is responsible for obtaining the event loop, executing tasks until they are marked as complete and then closing the event loop.
If you need to interact with the loop event loop, it supports introspection with loop.is_running () and loop.is_closed (). You can manipulate it if you need more tight control, such as programming a callback by passing the loop as an argument.
The most important thing is to understand a little below the surface about the mechanics of the event loop.
#1: Routines do not do much by themselves until they are linked to the event loop.
#2: By default, an asynchronous IO event loop is executed in a single thread and in a single CPU core. Generally, executing a single thread event loop in a CPU core is more than enough.
#3 Event loops are connectable.

**Procesamiento paralelo en Python: una guía práctica con ejemplos**

Parallel processing is a mode of operation where the task runs simultaneously on multiple processors on the same computer. It is intended to reduce the total processing time.
However, there is usually a bit of overhead when communicating between processes, which can actually increase the total time needed for small tasks instead of decreasing it.

In python, the multiprocessing module is used to execute independent parallel processes by using threads (instead of threads), it means that processes can be run in completely separate memory locations.

2. How many maximum parallel processes can you execute?
The maximum number of processes you can run at once is limited by the number of processors on your computer. If you don't know how many processors are in the machine, the cpu_count () multiprocessing function will show it.

3. What is synchronous and asynchronous execution?
In parallel processing, there are two types of execution:
Synchronous: it is one in which the processes are completed in the same order in which it started. This is achieved by blocking the main program until the respective processes are finished.
Asynchronous: on the other hand, it does not imply blocking. As a result, the order of the results can be confused, but generally it becomes faster.
There are 2 main multiprocessing objects to implement the parallel execution of a function: the Poolclass and the Processclass.


4. Problem statement: Count how many numbers exist between a given range in each row
Solution without parallelization


5. How to parallelize any function?
The general way to parallelize any operation is to take a particular function that must be executed several times and have it run in parallel on different processors. To do this, initialize Poolcon n number of processors and pass the function you want to parallelize to one of Pool paralysis methods.
multiprocessing.Pool () provides the apply (), map () and starmap () methods to make any function run in parallel.
To do this, initialize to Poolcon n number of processors and pass the function that you want to parallelize to one of Pool's paralyzing methods.
multiprocessing.Pool () provides the apply (), map () and starmap () methods to make any function run in parallel.Therefore it is better map ()

5.1. Parallelization using Pool.apply ()
Let's parallel the function using .howmany_within_range () multiprocessing.Pool ()
5.2. Parallelization using Pool.map ()
Pool.map () accepts only one iterable argument.
5.3. Parallelization using Pool.starmap ()
starmap ()
Like, it also accepts only one iterable as an argument, but in, each element in that iterable is also iterable. You can provide the arguments to the 'function to be parallelized' in the same order in this internal iterable element, in turn it will be unpacked during execution.Pool.map () Pool.starmap () starmap ()
 
6. Asynchronous parallel processing
Asynchronous equivalents, and allow you to execute processes in parallel asynchronously, that is, the next process can begin as soon as the previous one is completed without taking into account the starting order.
As a result, there is no guarantee that the result will be in the same order as the entry.apply_async () map_async () starmap_async ()
6.1 Parallelization with Pool.apply_async ()
apply_async () is very similar to except that you need to provide a callback function that tells you how the calculated results should be stored.
It is possible to use without providing a function. Only that, if you do not provide a callback, you will get a list of objects that contains the calculated output values ​​of each process.
 
6.2 Parallelization with Pool.starmap_async ()
CODE
 
7. How to parallel a panda data frame?
Pandas, which are the most used objects (in addition to numpy matrices) to store tabular data. When it comes to parallelizing DataFrame, you can make the function parallel to take as input parameter:
a row of the data frame
a column of the data frame
the whole data frame itself
The first 2 can be done using the multiprocessing module itself. But for the latter, which is the parallelization in a complete data frame, we will use the pathospackage that is used dill for serialization internally.
CODE


