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
