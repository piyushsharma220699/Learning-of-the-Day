In distributed computing, leader election is the process of designating a single process as the organizer of some task distributed among several computers (nodes). 

Before the task has begun, all network nodes are either unaware which node will serve as the "leader" (or coordinator) of the task, or unable to communicate with the current coordinator. After a leader election algorithm has been run, however, each node throughout the network recognizes a particular, unique node as the task leader. 

The network nodes communicate among themselves in order to decide which of them will get into the "leader" state. For that, they need some method in order to break the symmetry among them. 

For example, if each node has unique and comparable identities, then the nodes can compare their identities, and decide that the node with the highest identity is the leader.

![[Leader-Election-NO-Recovery.jpg]]

Now, let's say our system gets a bunch of HTTP requests and we're handling it using a load balancer on more than one servers. Now if one of the server goes down, our task is to spin up a new server for that.

But who does that? Let's say we have an orchestrator for it. But then WHO MANAGES THE ORCHESTRATOR? Another orchestrator? This kinda becomes a recursion that has no end.

Thus, we need an AUTOMATED WAY TO RECOVER the system. We do this using Leader Election Algorithm.


### Leader-Follower Setup

Here, we have three things, API servers, Orchestrator Leader and Orchestrator Workers.
1. Orchestrator Workers monitor the API server and spins them up when one goes down. Workers ping the server continuously to check if they're alive or not.
2. Orchestrator Leader manages the Orchestrator Workers and and spins them up when one goes down. Leader ping the workers continuously to check if they're alive or not.
3. When Orchestrator Leader goes down, then all the orchestrator workers use an Leader Election Algorithm to elect one of them as the leader so as to recover the system to normal state.

![[Leader-Election-Automated-Recovery.jpg]]

There are some synchronous and other asynchronous algorithms for this. Example of Leader Election Algorithm :

1. Bully Election Algorithm : https://www.educative.io/answers/what-is-a-bully-election-algorithm
2. Paxos
3. RAFT
4. Apache Zookeeper : Used in HDFS