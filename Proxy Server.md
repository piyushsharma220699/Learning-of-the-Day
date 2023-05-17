What is Proxy Server?

What are the different types of Proxy Server?

- Forward Proxy Server/Simple Proxy
	- Clients talk to proxy, proxy goes to internet, server and get the result. The client network is hidden to the server. Proxy sends its own ip address to the server than the client with the same request that client asked the proxy. CLIENT IS HIDDEN, NO SERVER CAN TALK DIRECTLY TO THE CLIENT. IT GIVES ANONYMYTY TO THE OUTER WORLD.
		- Grouping of Request. : All the requests grouped and sent in one and then returned.
		- Access Restricted Data : Eg noone should be able to access fb
		- Caching
THIS WORKS ON APPLICATION LEVEL, FOR EACH APPLICATION YOU NEED TO SETUP A DIFFERENT PROXY.

- Reverse Proxy Server
		- sECURITY SINCE ORIGINAL SERVER IS NOT EVEN KNOWN.
		- LOAD BALANCING
		- LATENCY REDUCED
eG: CDN


PROXY VS VPN

PROXY VS LOAD BALANCER
- Every Proxy is a load balancer but every load balancer is not a proxy. 

PROXY VS FIREWALL