Unidad 1 Introduction t Distributed Systems

**Table of contens**
[Prueba](#prueba1)
-[Lesson1](#Lesson1) |
-[2.-Why build a distributed system?](#what-build-a-distributed-system) |
-[3.-How to learn distributed system?](#how-to-learn-distributed-system) |
-[4.-What could go wrong?](#what-could-go-wrong) |
-[5.-The many tapes of fail](#the-many-tapes-of-fail) |
[6.-Byzantine fault tolerance](#byzantine-fault-tolerance) |
[7.-SLIs SLOs and SLAs](#slis-slos-and-slas) |
[8.-Class Project](#class-project) |
[9.-Paxos Simplified](#paxos-simplified) |
[10.-How counterstrike works(time in distributed systems)](#how-counterstrike-works-(time-in-distributed-systems)) |
[11.-Introduction to blockchain consensus](#introduction-to-blockchain-concensus)
[12.-What is a blockchain?](#what-is-a-blockchain) |
[13.-Bitcoin blockchain consensus](#bitcoin-blockchain-concensus) |
[14.-Should you use bitcoin consensus?](#should-you-use-bitcoin-concensus) |
[15.-Distribuited System Design Example(Unique ID)](#distributed-system-design-example-(unique-id)) |
[16.-The CAP Theorem](#the-cap-theorem) |
[Authors](integrants)

### Lesson1
# **1.-Whats is a distributed system?**
Centralized system: state stored on a single computer
- Simpler.
- Easier to understand.
- Can be faster for a single user.
Distributed system: State divided over multiple computers
- More robust (can tolerate failures)
- More Scalable (often supports many users)
- more complex
¿Complexity is bad?
- Complex systems can be less reliable!
- Getting a distributed system right is hard
- Getting them wrong can be bad
- Because they are often important
Well worth using when their power is needed
 Examples
- DNS
- Distributed lookup table of hostname to ip address
- Facebook and google
- Massive scale
- Fast enough
- Very reliable
- Email servers (SMTP)
https://www.youtube.com/watch?v=7VbL89mKK3M&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A
# **2.-Why build a distributed system?**
Top 10 style:
- Scaling
- Reliability
- Dependency on cloud
- Performance
- Uptime requirements
- Aligning cost incentives
- Legal/privacy/politics
- You needed a server
- Its fun
- Your boss told you to
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=2
# **3.-How to learn distributed system?**
This is a system discipline. An experimental science, no just theory, learn most by taking apart, debugging, modifying an existing system. Topics in these videos just help you with understanding.
Topics in distributed system
- How systems fal.
- How to express your goals: SLIs, SLOs, and SLAs
- How to combine unreliable components to make a more reliable system
- How nodes communicate --RPCs
- How nodes find each other-- naming
Topics in distributed system cont.
- How to use time in distributed world
- How get agreement--consensus
- How to persist data--distributed storage
- How to secure your sistem
- How to operate your distributed system-the art of SRE
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=3
# **4.-What could go wrong?**
If you design a system that can discover the failure of any of its components, you must understand the type of failures that may occur in case of an error, such as DOS atack, broken dependency, data corruption, etc.
As well as natural disasters that can ruin your equipment, or even the government is waiting for you through your equipment.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=4
# **5.-The many tapes of fail**
It shows how it is that you learn from the mistakes that were made in previous programs and that there are a lot of ways in which distributed systems can fail. And it makes no sense to try to design a system that is resistant to all possible failure modes, If you don't think about what you should consider to reinvent it, it shows you a list of faults such as network versus node.
In network failures can occur such as:
- Lost of connectivity
- Packet loss
- Routing
- Problems of multiple routes.
 How do you choose what kind of things you want to build to make your system more robust? We live in the real world, where something new is probably being built that does not yet exist, so you will find the assumption about what the frequency and impact distribution will be. What is not really handled well is safety. You will have to rely on encryption or some form of cryptography.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=5
# **6.-Byzantine fault tolerance**
In this video we are going to talk about teenagers' strange fault tolerance or how they design and build a distributed system that can survive the worst possible failures in their system.That is a useful mental definition of business behavior, but it is not so useful for mathematical tests. So, when we define business behavior more formally, what we really like to say is that some node in your system that exhibits visits and failures is a traitorous node and that merchant sends contradictory messages, sends a response to one of his peers and Another different response to a different partner.That is also a design team failure and a business team failure. And we want to learn to design systems that can tolerate these failures. So why would you study design team? It seems that it is really difficult to design a computer that can survive even a malicious actor who takes over part of your computer. Well, you may have to do it for the application what you are building. Bitcoin is an example of that.Another example is if you need extreme reliability, flight control systems fly by cable on the Boeing 777 and 787. And because they are very concerned about reliability systems and that a hardware failure could exhibit behaviors similar to those of the Commercial team, they have built a business. Fault-tolerant flight control system of the equipment in these aircraft. But most people are not solving problems in that category. . The document we will talk about later on the problem of the Byzantine generals was written in 1982 and this is an ongoing investigation to this day. . Therefore, you want to create a distributed system that has been tolerance to thematic failures. What assumptions are you making about your system and how can your opponent attack it? Are you assuming that your adversary can see all the messages between his nodes because, for example, he could be using Wi-Fi and all his notes are very close or he is assuming he has a switched Ethernet network? And so, all your messages are private, assuming that the network itself is not attacked.
 :'c
 https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=6
# **7.-SLIs SLOs and SLAs**
In this video we're going to talk about ESA lies ESA Lowes and ESA lays. Well why are we talking about this. Well this is all about measuring the reliability performance of your system. If you don't measure how well you're doing you'll never know whether you've achieved this goal or not.
So if we're going to measure reliability performance we need a vocabulary we need common words which are understood by other people. Nor to describe how well we're doing. So that brings us to ESA lies ESA Lowes and SL A's and ESA lie is what we're measuring. What are you going to do if you miss it.The consequences could be severe. The consequences might be more like a slap on the hand you might promise your customers if we meet our US A. All right you are really apologetic. Email and I'll describe exactly what went wrong and what we're going to do to make sure that that never happens ever again. Well a teal is a three letter record and I have to apologize.
This talk is full of them. The second reason to study this is because unless you measure it it's really difficult to learn what matters. That sounds like a good SLA but it's incomplete it doesn't give you enough information to really evaluate whether or not they've hit their goal. For example they need to tell you how often do they check if their system is up.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=7
# **8.-Class Project**
I want you to be able to share what you're doing with the rest of the class. So by building a chat application you'll be able to chat with any classmates who have happen to have. We're also concurrently going through this series of videos. Also the end product I want it to be fun or maybe even useful if you want to use this chat application for your own Web site or for having conversations with your friends.
So let's dive into it and take a look at what it is we're building. So we go to distributed chat dog apps spot dot com. Let's click allow. The application then loads and once it loads it then queries the server and retrieves the most recent messages that have been sent and displays them on the screen.

Someone who likes bananas and if I send that message everyone else who's using the server at this point in time can see the message that I just sent I am someone who likes bananas. Now that you've come back to watch the video again let's go on and explain how this application works. It's a little bit more complicated than it looks but let's start with the basic outline. We're relying on Google's app engine infrastructure and Google's app engine infrastructure does a lot of the heavy lifting on our behalf.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=8
# **9.-Paxos Simplified**
In this video we're going to talk about the PACs those consensus algorithm which is used and distributed systems to achieve consensus or agreement between more than one computer. Now Texas is known for being a complicated topic of study. So I have to try and simplify it make it as easy as possible for you to understand and to help with that. I'm going to start by giving you a contrived example. You are in a marching band Haven't you always wanted to be in a marching band. Well at the end of practice the whole band likes to go out for dinner and there only are two places which are convenient to the marching band practice stadium which are a really good burger place and pizza but you want the whole band to go out to the same place for dinner because it's more fun if you have one big party than if you split the band up and you he half goes to one and half goes to the other it's just not nearly as much fun. So you need to get the band to agree on where you're going. Burgers or pizza. Well there are some complexities here. One is that the band director is lame. They've already gone home. And so there's no one in charge who's going to make the decision for you as a group. You have to achieve consensus between all the band members Where you going. Also these are band members who just finished a hard practice. Tbreakthrough. Not only can we build a reliable system we can prove with math that it's actually doing the right thing. Well here's the part where he dug himself a little bit of a hole. He came up with his own cute story about a bunch of parliamentarians in Greek islands and an imaginary group of islands called Pax oaks and he tried to get this published as a paper called the part time parliament and reviewers were really confused by this story which he wrapped the whole thing up in. And so they rejected the paper because they didn't really understand its significance. Lampert tried for a while to get it published didn't work. So he put on the shelf for a while and then he took it off the shelf and eventually he did get it published. 
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=9
# **10.-How counterstrike works(time in distributed systems)**
When you take a Distributed Systems course you'll always have at least one lecture on how distributed systems designers think about time. I'm not going to do that so I don't want to talk about videogames. The more fun anyways how does the game counterstrike work if we can figure that out. We should have a good understanding of time and distributed systems. So to start off what is counter strike. Basically you're a soldier and you have a team of soldiers you're trying to kill everyone on the other team. Sort of like paintball but without all of the exercise it's a bit more complicated than that. But let's just look at one round here. I take off running looking for the other team because I want to shoot them but. I haven't quite found them yet. I pull out my gun because I think I'm getting close. I turn left turn right. I should shoot. I'm dead. It turns out that I'm not good at this game. As you can see the players are both moving try to dodge and weave out of the way of each other shots aiming and firing but how does it work. I've never worked in the game industry so I can't give you every last detail but there's plenty of information out there so we'll use that to come up with a set of possible designs and use those to learn more about how time works and distributed systems. So let's start with the simplest possible design. The client server model each player sitting at a computer and that computer records the keystrokes and the most motions of that player and sends those is a series of keystrokes up to a server over the network the server runs the game engine which takes all the keystrokes from all the players and simulates the next step in time or the next tick of the game clock and it computes where all the players are now and who's shot whom and any relevant information and it sends that information back to the clients as a sequence of snapshots the client computers then take those snapshots and update their displays to show what's happening in the game. Simple enough. This is actually how real time strategy.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=10
# **11.-Introduction to blockchain consensus**
The block chain just like the title lets talk. It's received way too much hype. Proponents of the block chain are convinced that it solves the Byzantine Generals Problem. This implies that consensus and distributor systems. It's solved. You no longer have to understand complicated things like the pax OS algorithm or even how the Byzantine Generals Problem itself works right. Well not really true. Some problems are well suited to block chain based solutions and other problems are a terrible match. And you don't want that block chain to get within miles of them. So to understand which kind of problem you have you need to really understand how block chain consensus works. That's what this series of videos will explain in the first video I explain the bitcoin block chain data structure. So you would understand how to do a block chain on a single computer in the second video. Explain how you replicate that block chain from one computer to another forming a consensus. And then the third video will look at that Bitcoin block chain consensus algorithm we just developed and compare it to other consensus algorithms such as Pax O's raft and PBF T or practical Byzantine fault tolerance. Now if this is your first time looking at the block chain it's really helpful to understand where they're used which is typically crypto currencies. So I'd recommend going in watching an introduction to those first. Grant Sanderson has an excellent introduction on his channel three blue on Brown. I have a link to it down below. Go watch that and then come back and you can learn about block chain consensus.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=11
# **12.-What is a blockchain?**
What is a blockchain a blockchain is actually a rather simple data structure. Let's assume that you have a bunch of data and you want to form a block chain out of it. How do we do that. Well we'll just carve a chunk of that data off and we'll call it. I don't know a block and we'll put an empty header on it. And now we've got a one block block chain when more data comes along we can form a second block. And in the header of it we'll put the hash of the entire first block this hash will you have to be a cryptographic hash which means it has two important properties. One is it's really cheap and easy for us to re compute it which means that we can at any time validate that the first block is OK by Rican puting it's hash and comparing it to the hash we've stored in the second block. The second property has is its next to impossible for an attacker to go and corrupt our first block in a way which will pass our hash validation. So any corruption will be detected and we won't be fooled. And then when we want to add a third block for a blockchain we just use the hash of the second block and for a fourth block we use the hash of the third block and so on. So it's just a chain of blocks chained together by the hashes of the prior blocks. So why are we using hashes instead of pointers to changes together. Well it means that the blockchain is actually kind of has this really useful property which is we only need to find one trusted friend to give us the very last block in the blockchain. And as long as we get a good copy of that. Any other blocks we get from any other computers in the network whether they are our best buddies computers or whether their computers owned by hackers we don't trust. It doesn't matter. We can validate by validating all these hashes that our block chain is intact that it hasn't been corrupted by anyone. And we've got a perfect copy of the blockchain all starting from just having one block which we got from a trusted partner.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=12
# **13.-Bitcoin blockchain consensus**
How do you get about you Computers took on this book well in previous previews we studied Consensus over them such as packs Jobs Ratchet and PDF Watch. Let us get Consensus Belocopitt us what do we just want to thoughts now and as we actually didn't Study PBA without practical visiting fault and we still need to visit full Towers Watson PDF just as criptográfica to make the solutions. Little more efficient the problem with using a trivial Consensus help and for something like Coyne is that Bitcoin allows putter to join everything that work and he is actually what they want the script. You have one to many other so that means that if there are reevaluation of the ofertones approach to keep them with you may never Keep conceptos because you dont have a majority of Books available to complete the outer heaven works.
What's the Self we're going to invest and new hope for them together coming step by step. We're going to start up something very simple and then text the box as we discover the box and eventually we're going to read Develop Coin over time together. Well one we get Ori and new blog that new blog eventually needs to be Ripple get it to all the good know how to nurses and other words we need to be able to have a consensus. When and even know where Block is generated that needs to point to this new black or blockchain Browns.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=13
# **14.-Should you use bitcoin consensus?**
Many of us make comment to the office Ancic Christ and get the cool problem. What if you have a false where thousands of computers you might be called the function of the same time on to different Computers so we need a way of those ideas to come from different putter so we need to make it to some all the identity of the computer and the identity Computer. Ok so now we got a solution that works and the question is it is the best solution for Generation Apple you need Guidi aspects of How is it for computer to generate the time of the day with it and if start looking at the latest that it's not actually the fastest function called the world. So maybe we want to do something Tissot what we do that the World Vision what we are just incriminen a Colter So about every time you call the única function.
It takes them infinity and then just reads Memory location in comments says This is your new uadi work well ya that will generic mycoides and as well known as your Don't never walk Peoples close to the Wii Sports System. What happens quiero reboots if your computer reboots the counter resets this year again and then you might Keep reputation as well. So we need something better and so we can do instead Issey every thousand or Count thousand or Milli and Implications of this function we right to disco What are you need. We just Grounded in the penalty owned Computer and would on it actually Design if all you need is Unitas but then many of us make the real chill out what you said is ya that give you something new Nek.
We sincronice at any time in the sky with all its and the book is in Coordination these are you might not generic Montalbetti increasing ideas so time would of course to get the hacker internas. We really want to trying to solve the problem Cookson transaction. I don't want to use it so that the solutions doesnt Singer as. Well if you're not going to see the clocks and wanting to get over.We need to save to more than one disc one more than one computer where maybe Save the foul system but now we know how we going to have Mark Fell in Love with Love and more than one Serfor at some time we love.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=14
# **15.-Distribuited System Design Example(Unique ID)**
Many of us make comment to the office Ancic Christ and get the cool problem. You see what did databases dont have to run Across Computers and Cheung mastitis and Brittney Protocol that were allowed to do Transactions across those Computers but that practical asume every time you want to transaction you could to some transaction única Lovely UNIACC Haiti and his problem is used as Macross What's the best way to the function and see that every time you could give you would be different Numb different Lovely UNIACC identifiqué Susan actually problem. How do you write the best goebbeliana Dunphy function past to think about it and that when you come back will talk about the full process that when you designing this function. So. The first thing is a global Unitec. Well it's a number which is tweak it seems pretty obvious but I mean is every time all this function will never ever Joyner at the same but not on the same Computer and not only different better not for the entire spinning your system so that you can use it to you Nicoli identified you are Transactions and so since it has been next time you first Integration might be used time for us so may be able to call it time of day and then every Bakker saqueen all of generated and new global única it and a far from Get time of day and get the kids on their right. Well actually work if you will we have a single Computer. What if you have a falseen where thousands of computers you might be called the function of the same time on to different Computers so we need a way of those ideas to come from different putter so we need to make it to some all the identity of the computer and the identity Computer.
https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=15
# **16.-The CAP theorem**
It's because you're trying to build something that is more than a Santalices Trust Weeds Computer signed used to Stoned The Theory of the possible. If your system Evers offers perceptions we can explain what is all means by using an example. What's your starting your own vec with all great start ups you decided to start Small with only one cost Markham and to attempts your item support three different operations. You can the post opponent with Euromoney and you also have an Hembery you never want to Bells to get it was here because you love distributed systems and you don't want to build more Computers you Storani campeones and the items themselves ehhhh as a couple of the Campalans.
When youre Customer walks up to an team and in search of everything is working system is very simple. Through the script system has suffered a partition in this case. So what does the team doing next one this partition happens. This is the design saying that the chapter and talks about the system Mimic choice to be consistent tildo Books and So Long explained.

https://www.youtube.com/watch?v=pMQzLVK39Kk&list=PLOE1GTZ5ouRPbpTnrZ3Wqjamfwn_Q5Y9A&index=16

**Integrants:**
**_Castro Arenas Flavio Daniel_**
**_Coronado Felipe Deyanira_**
