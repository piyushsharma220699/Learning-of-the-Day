>>> Extremely essential in building horizontally scalable systems!

A load balancer is a device that acts as a reverse proxy and distributes network or application traffic across a number of servers. Load balancers are used to increase capacity (concurrent users) and reliability of applications. They improve the overall performance of applications by decreasing the burden on servers associated with managing and maintaining application and network sessions, as well as by performing application-specific tasks.

A load balancer either has a static IP or a static DNS name, allowing clients to talk to it.

LOAD BALANCER HELPS IN ABSTRACTING OUT THE DISTRIBUTEDNESS OF THE SYSTEM. USERS HAVE NO NEED TO KNOW THE NUMBER OF SERVERS USED IN THE SYSTEM.

![[Pasted image 20230517143038.png]]

Load Balancer is having a static IP or a static DNS name to which the end users fire their request. Using the Load Balancing Algorithm, it decides which Application server to route the request. Exact same request is routed to the app server and then the response when received gets delivered to the end user.

#### Timeline (Request-Response Flow)

1. Client makes a request to the Load Balancer.
2. Load Balancer, based on a load balancing algorithm, picks one server and MAKES THE EXACT SAME REQUEST to it.
3. Load balancer gets the response from the server.
4. Server sends the response back to the client.

### Benefits of Load Balancing

- Scalability
- Flexibility
- Efficiency
- Downtime Reduction
- Redundancy

### Load Balancing Algorithms

##### Round Robin (Default Algorithm used in almost every place)

![[Round-Robin-Algorithm.jpg]]

##### Weighted Round Robin

![[Weighted-Round-Robin-Algorithm.jpg]]

##### Least Connections

A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.

##### Hash 

For every request, a hash value is calculated which is then divided by the number of servers present in the system and then the remainder gives us the server to which the value should be redirected. Kinda like basic Hashing.


### Types of Load Balancers

Load balancers are generally grouped into two categories: Layer 4 and Layer 7. Layer 4 load balancers act upon data found in network and transport layer protocols (IP, TCP, FTP, UDP). Layer 7 load balancers distribute requests based upon data found in application layer protocols such as HTTP.

#### Layer 4

#### Layer 7

### Resources

- https://www.nginx.com/resources/glossary/load-balancing/
- https://aws.amazon.com/elasticloadbalancing/
- https://www.f5.com/glossary/load-balancer#:~:text=A%20load%20balancer%20is%20a,users)%20and%20reliability%20of%20applications.
