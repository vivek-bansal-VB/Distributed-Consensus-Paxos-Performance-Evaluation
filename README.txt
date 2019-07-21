We will study optimizations of both Basic Paxos and Multi-Paxos. The goal is to better understand these algorithms.
1. Consider Basic Paxos as described using itemized steps by Lamport in his "Paxos made simple" paper.
(1) What liveness problems does the algorithm have? 
(2) What are possible methods for solving them?

2. Consider Multi-Paxos as described in pseudocode by van Renesse in his "Paxos made moderately complex" paper.
(1) What performance problems does the algorithm have? 
(2) What are possible methods for solving them?

3. Take the DistAlgo program for Lamport's Basis Paxos (under da/examples/lapaxos at http://github.com/DistAlgo/distalgo)
(1) Extend it into a version with preemption. You need to add correctness testing to check that executions with both the original and the extended versions are correct. There is no point to have a more live or faster program that is not correct.
(2) Measure the running times to learn a consensus value under varying values of 3 parameters: message loss rate, message delay, and wait time before a new round. You need to select the appropriate ranges of parameter values and their combinations to obtain interesting results.

Remember that, for performance evaluation, your measured results depend on the machine capacity you use. So do the ranges and combinations of parameter values.

The running times (both elapsed time and total CPU time) should be averaged over a number of repeated runs. Here, you should report the range and standard deviation too because the variation is expected to be large.

Program must run under Python 3.6.5 or higher. Your main program must be named "main.da", and must run with a command like the following, where

"p", "a", "l" are the number of proposers, acceptors, and learners, respectively,
"n" is the number of repetitions for each run,
"r" is the message loss rate, between 0 for 0% loss and 1 for 100% loss,
"d" is the message delay, up to the number of seconds specified,
"w" is the wait time, in seconds, before trying a new round,
"tp" and "tl" are the timeout, in seconds, by proposers and learners, respectively, when timeout is used.

python.exe -m da main.da p a l n r d w tp tl

and do the following:

(1) run both versions of Basic Paxos;
(2) report the running times, ranges, and standard deviations, for each of them.

For selecting the argument values: "p", "a", "l" are usually 3, or occasionally 5; and "n" is better at least 10 or more.

You should specify several combinations and ranges of "r", "d", "w", "tp" and "tl", and report the resulting curves or trends for varying each of them. For example, you can provide a combination of all argument values where "r" varies over 5 different values. Generally, you want to vary the values of one parameter at a time.

You have the freedom to decide what additional information to report and what table and/or figure format to use.

Your must write a "README.txt" file that includes an explanation of what you did (so that your experiments can be repeated) and what results you obtained (in terms of performance as well as correctness). Be brief and clear. (Reminder: give credits to exact sources for anything that is not your own creation; follow the requirements on the course syllabus.)

Extra credits:

1. Read Lamport's paper Paxos Made Simple, with the particular goal of understanding his description of the algorithm in two phases (end of Sec. 2.2) precisely. 

If you have any remaining questions about his description of the two phases, list each question precisely.
If you have no remaining questions, list the most puzzling questions you had while trying to understand and how you found the answers.
Write your descriptions in the most concise way you can. For example, as we have seen for Lamport's distributed mutex algorithm, you could list a question as: In rules 3 and 4, what does "any" mean? And you could list a solution as: Footnote 7 means there can be 0,1, or more requests in the queue. (And you could further list a question: If removing "any" request removed the wrong request, what are the consequences?)

2. Take the DistAlgo program for vRA Multi-Paxos (Multi-Paxos with preemption and reconfiguration) extended with state reduction and failure detection (at http://darlab.cs.stonybrook.edu/paxos), and fix the liveness violation in Replica in a simplest way. Do this in 2 steps:

(1) Describe the exact changes to add timeout, as precisely as the descriptions for state reduction and failure detection discussed in class.
(2) Design and compare runs with and without the fix, and report the results.
