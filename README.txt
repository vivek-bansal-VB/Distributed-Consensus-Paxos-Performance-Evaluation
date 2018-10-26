
Ans 3. 1) To add preemption, when acceptor got a request of lower proposal number and any of the request accepted by that acceptor is of higher proposal number, it sends the preempt message to the process who just send its request with lower proposal number. To check correctnesss of this extended basic paxos and original paxos algorithm, I am checking 2 things in the code:
	i)  Learned values by all learners should be same.
	ii) If timeout occurs at any of the learner, then there should be no learner who learned any value of the consensus.

	2) To evaluate performance times under varying values of 3 parameters : message loss rate, message delay, and wait time, I have created csv files and graphs using matplotlib and pandas. Steps for 	   these are mentioned below:
	   i)  To create CSV files, I evaluated standard deviation, mean and range for each varying parameter under n number of repetitions. The CSV file contains parameter I am varying and other columns 	       of Average Process time, Standard_Deviation_Process_time, Range_Process_time, Average Elapsed time, Standard_Deviation_Elapsed_time, Range_Elapsed_time, Correctness and timeout.
	   ii) To create graphs, I used pandas and matplotlib to plot average process time and average elapsed time against each parameter. Thus there are 5 CSV files and 5 graphs for each of the 	
	       parameter : message loss rate, message delay, wait time, timeoutproposer and timeoutlearner. I have added CSV files and graphs in main_da folder for extended version and in orig_da folder 	       for the original version. 

	Results obtained (shown only for 3 varying parameters only):
		a)   for varying message loss rate(r):
			Input : 3 3 3 10 0.8 0 0 1 1
			Basic Paxos : Sometimes increasing message loss rate is increasing the process time and elapsed time and sometimes it is decreasing both of them.
			Extended Paxos : Sometimes increasing message loss rate is increasing the process time and elapsed time and sometimes it is decreasing both of them. Generally, both process time 					 and elapsed time are more than basic paxos version.
		b)  for varying message delay (d):
			Input : 3 3 3 5 0 0.8 0 1 1
			Basic Paxos : Increasing message delay is increasing both the process time and the elapsed time.
			Extended Paxos : Increasing message delay is increasing both the process time and the elapsed time. But here the process time is more than the process time in basic paxos.
		c) for varying wait time for each round(w):
			Input : 3 3 3 5 0 0 0.8 1 1
			Basic Paxos : Generally, increasing wait time is increasing the elapsed time and decreasing the process time. 
			Extended Paxos :Generally, increasing wait time is increasing the elapsed time and decreasing the process time. 

References:
1.	https://github.com/DistAlgo/distalgo/blob/master/da/examples/lapaxos/orig.da
2.	https://arxiv.org/pdf/1704.00082.pdf
3.	https://github.com/DistAlgo/distalgo/tree/master/benchmarks/lapaxos