# Project 6 - Dean Frame, Daniel Susman

This is the source code for Project 6 of CS3700 Networks and Distributed Systems.
It holds the implementation of a Raft-based Key-Value Distributed Database.

## High Level Approach

For the milestone of this project, we used the "Implementing Raft" section
of the project description as a baseline/guide. We both read the Raft paper a couple
times through to get our groundings in Raft as a concept. Using the starter code,
we were able to quickly accomplish the first few steps. When things started getting
slightly more challenging conceptually, we went to the text and made use of the
blue boxes in the Raft paper to guide us to the solution.

Reaching the milestone goal was pretty straight-forward, and we hope our choices
have put us on the path to a solid final implementation. At the time of writing,
we are passing all milestone tests, most of the time with the Bonus points. Sometimes
the program is less performant than other times, but that is likely due to the
randomness we have employed throughout the module.

After the milestone, there was still much of the project to implement. Luckily, the code we
had written for the milestone set us well on our way towards success for the final submission.
We continued following similar steps from the milestone submission, utilizing the Raft paper
and the Project 6 guide.

## Challenges Faced

The largest challenge we faced for the milestone was grasping the Raft overarching
concepts. Once we had read the paper and discussed the details together, we felt
comfortable implementing this key-value store. Additionally, at first it wasn't
clear exactly how the simulator worked, i.e. GETs/PUTS/starting up multiple replicas.
The initial election was something that we debated handling in various ways, since
it is tough to know what to do when no leader election has occurred yet and the
simulator is starting up multiple replicas automatically. We chose to wait for a
timeout from some follower and start the election then.

Apart from conceptual challenges, getting our message frequency right was a bit
tough. We played around with heartbeat intervals for some time, eventually opting
to update our message frequency after a successful election has occurred. This means
we send more messages when the state of the system is not very stable, and slow things
down once we have had an election.

After the milestone, challenges became _much_ more prevalent. We faced issues with partitions,
leader crashes, performance, packet storms, etc. You name it, we likely faced it. Though this was
quite painful at times, we had various breakthroughs along the way that kept us going.

## Testing the Code

To test the code, we utilized print statements and the simulator. We ran our code
on our local machines and the Khoury servers multiple times to check that the
program was behaving as expected. As we incrementially added functionality, we
increased/modified our print statements to give us hints as to what the state of
the system was at any point in its execution.

Testing the code after the milestone followed the same procedure as before. We used print
statements to see the state of the system throughout the ./sim.py tests/... executions,
ran the code over and over looking for bugs or optimization opportunities, and honestly
just hoped for the best. This project was tough, for sure!
