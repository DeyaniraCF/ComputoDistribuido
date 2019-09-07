"""Initial commit flavio"
Title: 1.-Whats is a distributed system?
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
"Initial commit Deyanira"
Title: 2.-Why build a distributed system?

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
"""Initial commit flavio"
Title: 3.-How to learn distributed system?
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
"""Initial commit Deyanira"
Title: 6.-Byzantine fault tolerance
In this video we are going to talk about teenagers' strange fault tolerance or how they design and build a distributed system that can survive the worst possible failures in their system.That is a useful mental definition of business behavior, but it is not so useful for mathematical tests. So, when we define business behavior more formally, what we really like to say is that some node in your system that exhibits visits and failures is a traitorous node and that merchant sends contradictory messages, sends a response to one of his peers and Another different response to a different partner.That is also a design team failure and a business team failure. And we want to learn to design systems that can tolerate these failures. So why would you study design team? It seems that it is really difficult to design a computer that can survive even a malicious actor who takes over part of your computer. Well, you may have to do it for the application what you are building. Bitcoin is an example of that.Another example is if you need extreme reliability, flight control systems fly by cable on the Boeing 777 and 787. And because they are very concerned about reliability systems and that a hardware failure could exhibit behaviors similar to those of the Commercial team, they have built a business. Fault-tolerant flight control system of the equipment in these aircraft. But most people are not solving problems in that category. . The document we will talk about later on the problem of the Byzantine generals was written in 1982 and this is an ongoing investigation to this day. . Therefore, you want to create a distributed system that has been tolerance to thematic failures. What assumptions are you making about your system and how can your opponent attack it? Are you assuming that your adversary can see all the messages between his nodes because, for example, he could be using Wi-Fi and all his notes are very close or he is assuming he has a switched Ethernet network? And so, all your messages are private, assuming that the network itself is not attacked.

