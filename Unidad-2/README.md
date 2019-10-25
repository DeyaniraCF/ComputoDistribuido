**An Introduction to Asynchronous Programming in Python**

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

****LINK2****

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

This isn’t very interesting on its surface. The result of calling a coroutine on its own is an awaitable coroutine object, Hopefully you are thinking of generators as an answer to this question, because corutins are improved generators under the hood.
A critical feature of generators with regard to asynchronous IO is that they can be effectively stopped and restarted at will.
The fundamental difference between functions and generators. A function is all or nothing. Once it starts, it won't stop until it reaches a return, then it pushes that value to the caller, a generator, on the other hand, stops every time it hits yieldy it doesn't go further. Not only can you push this value to the call stack, but you can also keep your local variables when you resume it by calling it next (). There is a second less known feature of generators that is also important. You can also send a value to a generator through its .send () method.

Other Features: async for and Async Generators + Comprehensions
Along with plain async / await, Python also allows async to foriterate over an asynchronous iterator. The purpose of an asynchronous iterator is that it can call asynchronous code at each stage when it is repeated. A natural extension of this concept is an asynchronous generator.
Neither asynchronous generators nor understandings make the iteration concurrent. All they do is provide the appearance of their synchronous counterparts, but with the ability of the cycle in question to yield control of the event cycle so that some other routine is executed.
In other words, asynchronous iterators and asynchronous generators are not designed to simultaneously assign some function over a sequence or iterator. They are simply designed to allow the closing routine to allow other tasks to take their turn.

