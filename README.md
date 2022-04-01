# Vector-Clock-to-Timestamp-Messages
In this programming project, I developed develop an n-node distributed system that implements vector clock. The distributed system uses logical clock to timestamp messages sent/received between nodes. At first, each node should synchronize their logical clocks to the same initial value, based on which the ordering of events can be determined among the machines. used the Berkeley Algorithm to obtain an initial agreement on the logical clocks. You can use any programming language. To simplify the design and testing, the distributed system will be emulated using multiple processes on a single machine. Each process represents a machine and has a unique port number for communication.