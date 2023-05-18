>>> These help in asynchronous processing.

A message queue is a communication mechanism used in computer systems to facilitate the exchange of messages between different components or processes. It provides an asynchronous way for components to send and receive messages without requiring them to be directly connected or synchronized in time.

In a message queue system, messages are stored in a queue until they are processed by the receiving component. The sending component puts messages into the queue, and the receiving component retrieves and processes them at its own pace. This decoupling of sender and receiver allows for greater flexibility and scalability in distributed systems.

![[Message-Queue-AWS.png]]

### What is a Message Queue (Example)?

Now, let's suppose we have a single shop, in which we get both online and offline orders. Whenever we receive the order, we are not served with the order immediately. We're given a token saying that our order is placed and will be served to us on our table. Till then we can do other tasks (eg: watching Netflix, talking to someone etc.)

![[Dominoes-Single-Store.jpg]]

However, now suppose there's a chain like Dominoes, in which we have a lot of outlets in a single place. Now, one thing which we can have is a separate queue for each store, which keeps the orders data in the RAM. 

But then, if a store goes down, all the orders will also be lost. Tho we could've still prepared the online orders by using a nearby store and saved some money. Thus we don't store this in RAM, we store the orders in a database.

![[Message-Queue-Dominoes.jpg]]

Now, these orders are stored in a DB and an orchestrator is used to check if all the servers are up and running or not. Whenever the orchestrator realizes that one server is down, it takes all the orders from the database that are having a "N" status in the DB and distribute them on the servers left there.

Now, since the servers that are up are already processing some of the orders, all their orders should be sent to them only even after a server fails and orchestrator is reassigning the orders. Thus we use CONSISTENT HASHING for this.

In short:

	* Servers are processing jobs in parallel.
	* A server can crash. The jobs running on the crashed server still needs to get processed.
	* A notifier constantly polls the status of each server and if a server crashes it takes ALL unfinished jobs (listed in some database) and distributes it to the rest of the servers. Because distribution uses a load balancer (with consistent hashing) duplicate processing will not occur as job_1 which might be processing on server_3 (alive) will land again on server_3, and so on.
	* This "notifier with load balancing" is a "Message Queue".

This, Orchestrator, Notifier and Load Balancer together becomes a Message Queue.

For more, check : https://www.youtube.com/watch?v=oUJbuFMyBDk

### Another Example

In case of YouTube, let's suppose the creator (T-Series) upload a video in 4k. But since this can't be consumed by every device, it is supposed to be converted into different resolutions: 144p, 720p, 1080p etc. Also, for every video, YouTube provides auto-generated captions too. Now after we upload a video, the format changing and caption generation happens in the background asynchronously using Message Queues.

![[Message-Queue-YouTube.jpg]]

#### Important Points :

- **The message broker can hold/retain the request for 'n' number of days**, which is configurable. You can set the TTL for requests, expired requests will be deleted.
- **Message Queues act as a Buffer**, eg: we're receiving requests at the rate of 100 req/minute but our service can handle only 60 req/minute, then we put the requests in the message queue so that they're processed slowly by our service.
- **Message Brokers can REQUEUE the message if not deleted by the CONSUMER**. Eg: Let's suppose the message is taken by the consumer from the queue, but while processing it dies. Now there are couple of ways to handle this stuff. One of them being:
	- **Use a Message Visibility Timeout** **:** When a message is delivered to a consumer, the broker usually sets a visibility timeout for that message. During this period, the message is considered "invisible" to other consumers, ensuring that only one consumer processes it at a time. If the consumer fails to acknowledge or delete the message within the visibility timeout, the message is automatically made visible again to other consumers, effectively requeuing it for processing.


### Message Queue Terminology



### Types of Message Queues

There are broadly two types of message queues:
1. Kafka
2. RabbitMQ
3. Amazon Simple Queue Service (SQS)
4. ActiveMQ

To know more: https://medium.com/event-driven-utopia/the-stuff-that-every-developer-should-know-about-message-queues-a9452ac9c9d

### Difference between Kafka and RabbitMQ
