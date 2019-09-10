"""Initial commit flavio
Title: 1.Whats is a distributed system?
Centralized system: state stored on a single computer
Simpler.
Easier to understand.
Can be faster for a single user.
Distributed system: State divided over multiple computers
More robust (can tolerate failures)
More Scalable (often supports many users)
more complex
¿Complexity is bad?
Complex systems can be less reliable!
Getting a distributed system right is hard
Getting them wrong can be bad
Because they are often important
Well worth using when their power is needed
 Examples
DNS
Distributed lookup table of hostname to ip address
Facebook and google
Massive scale
Fast enough
Very reliable
Email servers (SMTP)"""
-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.
"""Initial commit Daniel
Title: 2.Why build a distributed system?

Top 10 style:
Scaling
Reliability
Dependency on cloud
Performance
Uptime requirements
Aligning cost incentives
Legal/privacy/politics
You needed a server
Its fun
Your boss told you to
.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
Title: 3.-How to learn distributed system? 'Deyanira A3'
Learn by doing!
This is a system discipline. An experimental science, no just theory, learn most by taking apart, debugging, modifying an existing system. Topics in these videos just help you with understanding.
Topics in distributed system
How systems fal.
How to express your goals: SLIs, SLOs, and SLAs
How to combine unreliable components to make a more reliable system
How nodes communicate --RPCs
How nodes find each other-- naming
Topics in distributed system cont.
How to use time in distributed world
How get agreement--consensus
How to persist data--distributed storage
How to secure your sistem
How to operate your distributed system-the art of SRE
.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
<<<<<<< HEAD
Title: 4.-What could go wrong? 'Deyanira A4'
If you design a system that can discover the failure of any of its components, you must understand the type of failures that may occur in case of an error, such as DOS atack, broken dependency, data corruption, etc.
As well as natural disasters that can ruin your equipment, or even the government is waiting for you through your equipment.
.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
Title: 5.-The many tapes of fail 
It shows how it is that you learn from the mistakes that were made in previous programs and that there are a lot of ways in which distributed systems can fail. And it makes no sense to try to design a system that is resistant to all possible failure modes, If you don't think about what you should consider to reinvent it, it shows you a list of faults such as network versus node.
In network failures can occur such as:
Lost of connectivity
Packet loss
Routing
Problems of multiple routes.

 How do you choose what kind of things you want to build to make your system more robust? We live in the real world, where something new is probably being built that does not yet exist, so you will find the assumption about what the frequency and impact distribution will be. What is not really handled well is safety. You will have to rely on encryption or some form of cryptography.

-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
Title: 6.-Byzantine fault tolerance
In this video we are going to talk about teenagers' strange fault tolerance or how they design and build a distributed system that can survive the worst possible failures in their system.That is a useful mental definition of business behavior, but it is not so useful for mathematical tests. So, when we define business behavior more formally, what we really like to say is that some node in your system that exhibits visits and failures is a traitorous node and that merchant sends contradictory messages, sends a response to one of his peers and Another different response to a different partner.That is also a design team failure and a business team failure. And we want to learn to design systems that can tolerate these failures. So why would you study design team? It seems that it is really difficult to design a computer that can survive even a malicious actor who takes over part of your computer. Well, you may have to do it for the application what you are building. Bitcoin is an example of that.Another example is if you need extreme reliability, flight control systems fly by cable on the Boeing 777 and 787. And because they are very concerned about reliability systems and that a hardware failure could exhibit behaviors similar to those of the Commercial team, they have built a business. Fault-tolerant flight control system of the equipment in these aircraft. But most people are not solving problems in that category. . The document we will talk about later on the problem of the Byzantine generals was written in 1982 and this is an ongoing investigation to this day. . Therefore, you want to create a distributed system that has been tolerance to thematic failures. What assumptions are you making about your system and how can your opponent attack it? Are you assuming that your adversary can see all the messages between his nodes because, for example, he could be using Wi-Fi and all his notes are very close or he is assuming he has a switched Ethernet network? And so, all your messages are private, assuming that the network itself is not attacked.
>>>>>>> 5c3037b79324549547cbaf9f704b8684643bf187

 :'c
-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
7.-SLIs SLOs and SLAs
In this video we're going to talk about ESA lies ESA Lowes and ESA lays. Well why are we talking about this. Well this is all about measuring the reliability performance of your system. If you don't measure how well you're doing you'll never know whether you've achieved this goal or not.

So if we're going to measure reliability performance we need a vocabulary we need common words which are understood by other people. Nor to describe how well we're doing. So that brings us to ESA lies ESA Lowes and SL A's and ESA lie is what we're measuring. What are you going to do if you miss it.

The consequences could be severe. The consequences might be more like a slap on the hand you might promise your customers if we meet our US A. All right you are really apologetic. Email and I'll describe exactly what went wrong and what we're going to do to make sure that that never happens ever again. Well a teal is a three letter record and I have to apologize.

This talk is full of them. The second reason to study this is because unless you measure it it's really difficult to learn what matters. That sounds like a good SLA but it's incomplete it doesn't give you enough information to really evaluate whether or not they've hit their goal. For example they need to tell you how often do they check if their system is up.

Am I up now am I up now and you need to know the sampling frequency. Are they checking once a second once a minute once an hour. What does it mean to be up. In other words what domain of responsibility are they assuming.

Are they measuring it based from the edge of their network to their system. Back out to the edge of their network in which case any problem between their network and your computers can cause you to go down and it's not their problem. Under the SLA or are they getting the full end to end guarantee. It's good to know exactly where their responsibility ends and your responsibility picks up over what time interval.

Are they promising and ninety nine percent uptime. Are they promising that for every second. Ninety nine percent of that second it will be up every minute every hour every day every month every year. Basically when this promises made it's based on a monthly billing cycle.

And so ninety nine percent of the time over one month would be what they're promising. They could be down and still be hitting their targets. If they happen in the middle of a critical time when you're getting most of your sales you don't want seven hours of downtime on whatever you're building three nights. Now we're getting into the territory of things that are actually more challenging to hit because that means 43 minutes of downtime per month maximum four nines is a seriously reliable system with only four minutes downtime per month and five nines is considered to be the gold standard where you only have 25 seconds a month of downtime.

If you look at compute engine an outage has to be at least five minutes long before they even counted as an outage. What is it they have to do in order to meet this three and a half nines SLA or ninety nine point ninety five percent. They've built a really reliable hardware and software stack. And so they expect failures to be ratably in frequent.

This actually has been known to happen.
They maybe do better than that if they're trying to emphasize their great customer service. So as long as you have a robust easy to avoid system you can pick a reliable service on top of this with all those constraints. You got to wonder is the SLA contract or is it marketing. When you read these isolates the first thing they emphasize is how incredibly reliable whatever service you're buying is provided.

Ninety nine point ninety five sounds really hard to achieve and trust me it is. None of the providers ever wanted to have an outage. And when they do have an outage they want to make it as painless as possible for their customers. So they worked their butts off to make sure that it doesn't hurt them or it hurts them as little as possible.

 