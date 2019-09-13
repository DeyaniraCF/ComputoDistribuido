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
Title: 7.-SLIs SLOs and SLAs
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
-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
Title: 8.-Class Project
I want you to be able to share what you're doing with the rest of the class. So by building a chat application you'll be able to chat with any classmates who have happen to have. We're also concurrently going through this series of videos. Also the end product I want it to be fun or maybe even useful if you want to use this chat application for your own Web site or for having conversations with your friends.

So let's dive into it and take a look at what it is we're building. So we go to distributed chat dog apps spot dot com. Let's click allow. The application then loads and once it loads it then queries the server and retrieves the most recent messages that have been sent and displays them on the screen.

Someone who likes bananas and if I send that message everyone else who's using the server at this point in time can see the message that I just sent I am someone who likes bananas. Now that you've come back to watch the video again let's go on and explain how this application works. It's a little bit more complicated than it looks but let's start with the basic outline. We're relying on Google's app engine infrastructure and Google's app engine infrastructure does a lot of the heavy lifting on our behalf.

The pieces that I had to create are there really are two pieces. It does things like once a user request the page it serves the web page tome and whenever user requests to either send or receive chat messages it distributes those messages to the user the messages themselves are stored in the data stored database. That's part of App Engine. Our code is actually executed in a way which it's scalable and fault tolerant as well.

This is something which standard HDP doesn't give you a necessarily an easy way of doing. In a standard configuration on top of that we're relying on all sorts of other infrastructure or relying on the user authentication infrastructure that Google provides. So I've shown you at a finished application were done right. It gives us reliable storage it gives us this multicast through the channel mechanism that allows us to send messages to all of the browsers that are currently using an application.

App Engine costs money if we use more than our free quota you can only log into our system using the Google log in mechanism because well that's the easiest one to implement. We have to do some code rewriting to use a different API that they provide instead. We don't have any load testing written. So we got to do that on our own and we also should probably if we want to build a really reliable service has some application level monitoring.

-.-.-.-.-.--.-.-.--.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.--..-.-..
Title: 9.-Paxos Simplified
In this video we're going to talk about the PACs those consensus algorithm which is used and distributed systems to achieve consensus or agreement between more than one computer. Now Texas is known for being a complicated topic of study. So I have to try and simplify it make it as easy as possible for you to understand and to help with that. I'm going to start by giving you a contrived example. You are in a marching band Haven't you always wanted to be in a marching band. Well at the end of practice the whole band likes to go out for dinner and there only are two places which are convenient to the marching band practice stadium which are a really good burger place and pizza but you want the whole band to go out to the same place for dinner because it's more fun if you have one big party than if you split the band up and you he half goes to one and half goes to the other it's just not nearly as much fun. So you need to get the band to agree on where you're going. Burgers or pizza. Well there are some complexities here. One is that the band director is lame. They've already gone home. And so there's no one in charge who's going to make the decision for you as a group. You have to achieve consensus between all the band members Where you going. Also these are band members who just finished a hard practice. They want to have fun. They're easily distracted done or not really paying attention to anyone who's trying to organize dinner plans. As I mentioned it's no fun if the group splits up. So you want everyone to come to an agreement on one place for dinner burger or pizza. Also the band is hungry. You can't go on trying to make this decision for ever. You have to terminate your algorithm whatever you use to make this decision and one artificial constraint. Yelling doesn't work well enough because no one's voice is loud enough to be heard by all the band members on the field. And so we're going to rely on person to person communication in order to achieve this consensus. And as I said what we want to achieve is a consensus amongst all animals. Are we going to go for burgers or we go for pizza. So think about it for a second. How would you solve this problem if you were just a lowly trumpet player in the band and you wanted to get the band to go somewhere anywhere for dinner one algorithm you might come up with is you might start by asking your friends Hey what's happening. Do we already have a plan. Are we going somewhere for dinner. What's going on. So that's the first phase your argument. Yes. What's happening. And if you don't hear anything from any of your peers if they don't tell you hey this is where we're going for dinner you then make a proposal. You say Hey let's go for burgers and if you can get a bunch of people going for burgers you might achieve critical mass. And then you go off and you enjoy your burgers as a group. That is the pack goes up in those two phases. 
because you've heard that understanding learning taxes is hard and you keep on telling me hey it's not that hard it's just burgers or pizza right. Well I'm actually pretty convinced that the basic Texas algorithm the mix lets you make one decision between a series of computers is not that complex and it should be relatively intuitive to wrap your head around. And it's actually a breakthrough when it first came out in the 1980s. Lesley Lampert came up with taxes and he did it while trying to prove that Parks's couldn't actually exist. He saw the existing research in building a redundant reliable destroyed system by Nancy Lynch. Bartolo scoff and he saw that this research although they'd successfully built reliable redundant distributed systems they didn't have a mathematical proof that their system was correct under every single corner case. And so Lampert being the theoretician that he is he's like great. I'm going to come up with a formalization of all this and then prove it is incorrect and prove that there is no correct way of doing this. And so he worked hard at it and he actually did the opposite. He came up with the formalization and he came up with a nice proof that shows that what he did was actually right. So this is a breakthrough. Not only can we build a reliable system we can prove with math that it's actually doing the right thing. Well here's the part where he dug himself a little bit of a hole. He came up with his own cute story about a bunch of parliamentarians in Greek islands and an imaginary group of islands called Pax oaks and he tried to get this published as a paper called the part time parliament and reviewers were really confused by this story which he wrapped the whole thing up in. And so they rejected the paper because they didn't really understand its significance. Lampert tried for a while to get it published didn't work. So he put on the shelf for a while and then he took it off the shelf and eventually he did get it published. Almost ten years after he originally wrote the paper and he got it published but people were still a little bit confused by the complicated story. He wrapped the whole thing up and he then was pressured by his peers to write another paper a few years later called tax was made simple and I can tell you since I've read this paper many many many times in preparing this talk Parks's made simple is simpler than the original paper but it was still rather challenging to read especially if you're not approaching it from a theoretical perspective but you want to approach it from the perspective of how do you build a real system. Good taxes need simple paper. It describes the basic tax goes out to them. How do you get agreement about amongst a bunch of computers and then it sort of has as an afterthought multiplexes which is us plus a bunch of complexity to allow you to build up a series of choices and it doesn't nearly as formally define all of the ways and all the decisions you need to make in implementing a multiplex US based system. As a result it's complicated and if you look at real implementations every real implementation of pixels makes different choices about the complicated things that are used to assemble a series of packs those instances into a log of decisions.
 -.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
 Title: 10.-How counterstrike works(time in distributed systems)
When you take a Distributed Systems course you'll always have at least one lecture on how distributed systems designers think about time. I'm not going to do that so I don't want to talk about videogames. The more fun anyways how does the game counterstrike work if we can figure that out. We should have a good understanding of time and distributed systems. So to start off what is counter strike. Basically you're a soldier and you have a team of soldiers you're trying to kill everyone on the other team. Sort of like paintball but without all of the exercise it's a bit more complicated than that. But let's just look at one round here. I take off running looking for the other team because I want to shoot them but. I haven't quite found them yet. I pull out my gun because I think I'm getting close. I turn left turn right. I should shoot. I'm dead. It turns out that I'm not good at this game. As you can see the players are both moving try to dodge and weave out of the way of each other shots aiming and firing but how does it work. I've never worked in the game industry so I can't give you every last detail but there's plenty of information out there so we'll use that to come up with a set of possible designs and use those to learn more about how time works and distributed systems. So let's start with the simplest possible design. The client server model each player sitting at a computer and that computer records the keystrokes and the most motions of that player and sends those is a series of keystrokes up to a server over the network the server runs the game engine which takes all the keystrokes from all the players and simulates the next step in time or the next tick of the game clock and it computes where all the players are now and who's shot whom and any relevant information and it sends that information back to the clients as a sequence of snapshots the client computers then take those snapshots and update their displays to show what's happening in the game. Simple enough. This is actually how real time strategy.
 -.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-
Title: 11.-Introduction to blockchain consensus
The block chain just like the title lets talk. It's received way too much hype. Proponents of the block chain are convinced that it solves the Byzantine Generals Problem. This implies that consensus and distributor systems. It's solved. You no longer have to understand complicated things like the pax OS algorithm or even how the Byzantine Generals Problem itself works right. Well not really true. Some problems are well suited to block chain based solutions and other problems are a terrible match. And you don't want that block chain to get within miles of them. So to understand which kind of problem you have you need to really understand how block chain consensus works. That's what this series of videos will explain in the first video I explain the bitcoin block chain data structure. So you would understand how to do a block chain on a single computer in the second video. Explain how you replicate that block chain from one computer to another forming a consensus. And then the third video will look at that Bitcoin block chain consensus algorithm we just developed and compare it to other consensus algorithms such as Pax O's raft and PBF T or practical Byzantine fault tolerance. Now if this is your first time looking at the block chain it's really helpful to understand where they're used which is typically crypto currencies. So I'd recommend going in watching an introduction to those first. Grant Sanderson has an excellent introduction on his channel three blue on Brown. I have a link to it down below. Go watch that and then come back and you can learn about block chain consensus.

