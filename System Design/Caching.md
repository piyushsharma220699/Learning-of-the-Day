Caching is anything that helps you avoid an expensive Network I/O, Disk I/O or computation.

### Introduction

Caching is a technique used in computing to improve the performance of applications by temporarily storing frequently accessed data in a fast-access memory or storage location, so that it can be quickly retrieved when needed.

When an application needs to access data, it first checks the cache to see if the required data is already available. If the data is found in the cache, it can be quickly retrieved without the need to fetch it from a slower, more distant location, such as a hard disk or a remote server.

Caches that we typically use are :
- Redis
- Memcache

![[Pasted image 20230512021823.png]]

Whenever we add something to cache, it has an Expiration Time associated with it. In Redis, the default expiration time configured is INFINITE, which can be changed. 

#### Cache Invalidation

Cache invalidation is the process of removing or updating cached data to ensure that the data is up-to-date and accurate. When data is cached, it is stored in a cache for a certain period of time or until it is replaced by new data. However, if the original data changes before the cached data expires, the cached data becomes invalid and may result in inconsistencies or errors in the application.

### Benefits of Caching

- Improved Performance
- Reduced Server Load
- Reduced Bandwidth Usage
- Improved User Experience
- Reduce Latency, Improves Scalability, Enhances UX

### Disadvantages of Using Cache

- Stale Data Provision 
- Expensive
- Increased Memory Usage

### How to populate a Cache?

There are two ways to populate a cache:
1. Lazy Population
2. Eager Population

#### Lazy Population

Lazy population of cache, also known as lazy caching or lazy loading, is a technique used in caching where data is not preloaded into the cache but is instead loaded on demand, when it is requested by the application.

In a lazy cache, the cache is initially empty, and the application fetches data from the underlying storage (such as a database or a remote server) only when it is needed. When the data is fetched, it is stored in the cache for future access. This approach can be particularly useful for applications that deal with large volumes of data or where the data changes frequently, as it can help to reduce the amount of memory used by the cache.

![[Pasted image 20230512015205.png]]

**Example :**
A blogging platform that stores blog posts in a database and uses a cache to improve the performance of the site. 
--> With lazy population of cache, the blog platform would not pre-load any blog posts into the cache, but instead would fetch them from the database only when they are requested by a user. For example, when a user navigates to a particular blog post, the platform would check if the post is in the cache, and if it is not, it would fetch the post from the database and store it in the cache for future requests.

**Real Life Example (Amazon) :**
Amazon sells a large number of products. They have have a product catalog that is stored in a database, and it uses a cache to improve the performance of the site.
--> With lazy population of cache, the website would not pre-load all product data into the cache, but would instead fetch product data from the database on demand, as users browse the website. When a user visits a product page, the website would check if the product data is already in the cache. If the data is not in the cache, it would fetch the data from the database and store it in the cache for future requests.

### Eager Population

Eager population of cache, also known as eager caching or eager loading, is a technique used in caching where data is preloaded into the cache before it is requested by the application.

In an eager cache, data is loaded into the cache at startup or at some other pre-defined time, even if the data may not be needed by the application immediately. This can help to ensure that the data is readily available when it is needed, which can reduce access times and improve the overall performance of the application.

Now, Eager Population is also done at two points:

##### WHILE ADDING DATA TO THE DATABASE, ADD/UPDATE IT TO THE CACHE TOO :

--> Ex: Let's suppose you're handling an application like Cricbuzz, where you show the latest score to the users. Now, since everyone is interested about the latest score and the latest commentary, this should be cached. 
Also, now if you use lazy population, i.e. you don't update the cache yourself while you're updating your cache with the latest score and commentary, the users will see the stale data till that expires from the Cache and then one person will make a request to fetch it from DB and cache it again before they see the actual score (Poor User Experience).

##### PROACTIVELY ADD/UPDATE DATA TO THE CACHE :

--> Ex: Now, let's suppose in YouTube, you are shown the Recommended Videos everytime by the recommendation system of YouTube. Now, since you are most likely to watch the recommended videos, those need to be cached.
Everytime the recommendation engine changes it's recommendations, it updates the cache proactively.

--> Ex: When someone with 1000000 followers tweets, that is proactively cached since a lot of people will view/like/comment/share that tweet/post.

### How to Scale a Cache?

Since Cache is just a database, it's scaling techniques are similar to that of a Database i.e. Horizontal Scaling & Vertical Scaling.

![[Pasted image 20230512023733.png]]

### Places where one can Cache the Data :

1. **CPU cache:** A type of cache memory that is built directly into the CPU, used to store frequently accessed instructions and data. CPU cache is typically divided into several levels, with each level providing faster access but smaller capacity.
2. **Web cache:** A type of cache used by web servers and browsers to store frequently accessed web pages and resources, such as images and scripts. Web caches can be implemented at various levels, such as the browser, the network, or the server.
3. **Disk cache:** A type of cache used by operating systems to store frequently accessed data from a hard disk or other storage device in RAM, in order to reduce the time needed to access the data.
4. **DNS cache:** A type of cache used by DNS servers and clients to store recently resolved domain names and IP addresses, in order to reduce the time needed to resolve subsequent requests for the same domain.
5. **Browser cache:** A type of cache used by web browsers to store frequently accessed web pages, images, and other resources, in order to reduce the time needed to access the resources on subsequent visits to the same website.


Literally every piece/component of your infrastructure can cache something for you, but you shouldn't since invalidation is also extremely expensive then.

![[Pasted image 20230512014954.png]]

#### Client-Side Caching

- Here, the data is stored on the browser, mobile devices etc.
- One can cache the constant/static data. Eg: Images, HTML/CSS/JS files, Profile Information, Past orders.
- The Backend Request is not even made.
- Ex : Twitter uses client-side caching to cache user avatars, profile information, and other static assets on the user's device, so that they can be accessed more quickly when the user revisits the site. This helps to improve the performance of the site and reduce the number of requests made to the server.

#### CDN Caching

- A CDN (Content Delivery Network) is a network of geographically distributed servers that work together to provide fast and reliable delivery of web content, such as images, videos, and other static assets. CDNs work by caching content on their edge servers, which are located closer to the end-users, reducing the distance that data needs to travel and improving the overall performance of the website.
- Storing website content, such as images, videos, and other static assets, on the edge servers of a CDN. When a user requests content from a website that is using a CDN, the CDN's edge server that is closest to the user will respond to the request by serving the cached content from its local cache, instead of retrieving the content from the origin server where the content is stored.
- Reduces the time required to load resources and by reducing the load on the origin server. Also, load on the origin server gets reduced, allowing it to handle more requests and reducing the risk of downtime or performance issues.

#### Remote Caching

- General centralized caching which we use. 
- Ex: Redis Cache

#### Database Caching

- Ex: Instead of computing total_posts by user everytime, we store 'total_posts' as column and update it once a while (this saves an expensive DB computation).

SELECT COUNT(\*) FROM posts WHERE user_id = 123;

Here, everytime a post is published, we update the 'User' table and do total_posts = total_posts + 1; 