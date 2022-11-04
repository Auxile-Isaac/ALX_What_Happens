what happens when you type https://www.google.com in your browser and press Enter?

	First you type  https://www.google.com and press enter, and the browser checks the cache for a DNS record to find the corresponding IP address of  https://www.google.com 

    • First, it checks the browser cache. The browser maintains a repository of DNS records for a fixed duration for websites you have previously visited. So, it is the first place to run a DNS query.
    • Second, the browser checks the OS cache. If it is not in the browser cache, the browser will make a system call to your underlying computer OS to fetch the record since the OS also maintains a cache of DNS records.
    • Third, it checks the router cache. If it’s not on your computer, the browser will communicate with the router that maintains its’ own cache of DNS records.
    • Fourth, it checks the ISP cache. If all steps fail, the browser will move on to the ISP. Your ISP maintains its’ own DNS server, which includes a cache of DNS records, which the browser would check with the last hope of finding your requested URL.

NB: Caches are essential for regulating network traffic and improving data transfer times. That’s the reason why there are so many caches maintained at so many levels.

NEXT…

If the requested URL is not in the cache, ISP’s DNS server initiates a DNS query to find the IP address of the server that hosts https://www.google.com .
	The purpose of a DNS query is to search multiple DNS 	servers on the internet until it finds the correct IP address 	for the website. This type of search is called a recursive 	search since the search will repeatedly continue from a 	DNS server to a DNS server until it either finds the IP 	address we need or returns an error response saying it was 	unable to find it.
NEXT…

Once the browser receives the correct IP address, it will build a connection with the server that matches the IP address to transfer information. Browsers use internet protocols to build such connections. There are several different internet protocols that can be used, but TCP is the most common protocol used for many types of HTTP requests.

	To transfer data packets between your computer(client) 	and the server, it is important to have a TCP connection 	established. This connection is established using a process 	called the . This is a three-step process where the client 	and the server exchange SYN(synchronize) and 	ACK(acknowledge) messages to establish a connection.

    1. The client machine sends a SYN packet to the server over the internet, asking if it is open for new connections.
    2. If the server has open ports that can accept and initiate new connections, it’ll respond with an Acknowledgment of the SYN packet using a SYN/ACK packet.
    3. The client will receive the SYN/ACK packet from the server and will acknowledge it by sending an ACK packet.
       Then a TCP connection is established for data transmission!

NEXT…

Once the TCP connection is established, it is time to start transferring data! The browser will send a GET request asking for https://www.google.com web page. If you’re entering credentials or submitting a form, this could be a POST request. This request will also contain additional information such as browser identification (User-Agent header), types of requests that it will accept (Accept header), and connection headers asking it to keep the TCP connection alive for additional requests. It will also pass information taken from cookies the browser has in store for this domain.

NEXT…
The server handles the request and sends back a response. The server contains a webserver (i.e., Apache, IIS) that receives the request from the browser and passes it to a request handler to read and generate a response. The request handler is a program (written in ASP.NET, PHP, Ruby, etc.) that reads the request, its’ headers, and cookies to check what is being requested and also update the information on the server if needed. Then it will assemble a response in a particular format (JSON, XML, HTML).

NEXT…
The server sends out an HTTP response. The server response contains the web page you requested as well as the status code, compression type (Content-Encoding), how to cache the page (Cache-Control), any cookies to set, privacy information, etc.

FINALLY…
The browser displays the HTML content (for HTML responses, which is the most common).

