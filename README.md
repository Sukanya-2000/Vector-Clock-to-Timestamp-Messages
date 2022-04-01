# SUKANYA BHATTACHARYYA 

# Vector-Clock-to-Timestamp-Messages
In this programming project, I developed develop an n-node distributed system that implements vector clock. The distributed system uses logical clock to timestamp messages sent/received between nodes. At first, each node should synchronize their logical clocks to the same initial value, based on which the ordering of events can be determined among the machines. used the Berkeley Algorithm to obtain an initial agreement on the logical clocks. You can use any programming language. To simplify the design and testing, the distributed system will be emulated using multiple processes on a single machine. Each process represents a machine and has a unique port number for communication.

# Part 1

Problem : Suppose the logical clock on each machine represents the number of messages has
been sent and received by this machine. It is actually a counter used by the process (or
the machine emulator) to count events. Randomly initialize the logical clock of individual
processes and use Berkeley’s algorithm to synchronize these clocks to the average
clock. You can select any process as the time daemon to initiate the clock
synchronization. After the synchronization, each process prints out its logical clock to
check the result of synchronization.

# Compiling : 
Type the following in the src directory:

make compile
Then,

make clean

# Running :

For the server, type:  Vector-Clock-to-Timestamp-Messages
<port number> <processId> For example: ./Vector-Clock-to-Timestamp-Messages
 7001 1

To test the simulation, open 4 command line windows/prompts. For the first 3 command line prompts, run the servers by typing the following commands in each prompt respectively:

./Vector-Clock-to-Timestamp-Messages
 7002 2
./Vector-Clock-to-Timestamp-Messages
 7003 3
./Vector-Clock-to-Timestamp-Messages
 7004 4
This will activate the servers/processes on ports 7002, 7003, and 7004 respectively.

For the fourth commandline window/prompt, run the time synchronization process by typing the following:

./Vector-Clock-to-Timestamp-Messages
 7001 1
The process will send a request over a socket connection to each of the 3 servers running on ports 7002 to 7004, requesting for the logical clock values, they will respond and then the synchronizing process will calculate the average clock value and send the individual offset clock value relative to the calculated average to each of the servers.

The servers will then respond with their updated logical clcok values which will ALL be the SAME, this time around. You can view all their reponses from the same command prompt window; i.e. the command prompt of the synchronizing process. You can also view the individual output from each server in its respective command prompt window as well.
  
# Working Principle :
  
The second parameter on the command line for the program, the 'process ID' is for two purposes:

To easily identify each running process, while running.
To determine the role of the process, a process ID of 1 is a synchronizing process, any value other than 1 is simply a server whose clock will be synchronized.
  
# Issues: 
  
  The port numbers for each of the servers are fixed, in other words, they must be 7002, 7003, and 7004.
For the synchronizing/client process, the process ID has to have a value of 1: this is what determines that it is the synchronizing process. A process ID other than 1 is a server process.
A synchronizing process is the process that synchronizes the logical clock of all the other processes; the other processes are simply servers listening for a connection.
Once the synchronization/client process is done synchronizing the logical clocks of the listening servers, it closes on its own, but the other servers still remain running and can accept new connection requests.
After running the synchronization/client process the first time, you can run it again to check the returned logical clock values from all the servers, they will be the SAME.
Each process starts with a pseudo-randomly generated logical clock value; in other words, the logical clocks of the processes/servers are not hard-coded, they change it time they are run.
  
# Part 2
  
  Problem : Implement the vector clock for your distributed system. You can create two threads for
each process, one for sending messages to other nodes and one for listening to its
communication port. Communication among nodes can be done using RPC or using
sockets. Once a process sends a message, it should print its vector clock before and
after sending the message. Similarly, once a process receives a message, it should
print its vector clock before and after receiving the message. You can assume that the
number of processes (machines) is fixed (equal to or larger than 3) and processes will
not fail, join, or leave the distributed system.
# Running and Compiling :
  (i) To compile the above programs, change the directory of the Terminal or Command Prompt to the folder containing these files.

(ii) Then, enter 'javac Server.java', 'javac Client.java' and 'javac ServerThread' to compile these files. You can only run these files after compiling them.

(iii) Finally, to run these files correctly, first, run 'Server.class' by entering 'java Server' then run 'Client.class' by entering 'java Client'.

(iv) Do not run 'ServerThread.class' file. As it will be called by 'Server.class'.
  
# Issues :
  (i) For array passing, byte array can only process a small amount of data at a time. It fails when large data is passed to it.

(ii) This program is coded for fixed number of nodes. Coding variable number of nodes is also simple. It can just be done by adding while loops.
