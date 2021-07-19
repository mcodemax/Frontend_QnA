## Traditionally, why has it been better to serve site assets from multiple domains?

It's because browsers usually have limits on the number of concurrent downloads from a domain at a moment. So, serving assets from multiple domains can increase the concurrent level.  -[Quizlet](https://quizlet.com/fr/175329230/web-developer-interview-questions-network-flash-cards/)

----------
Most of large websites store their static content such as Images, JavaScrips & CSS files to a Content Delivery Network or CDN as deploying your content across multiple, geographically dispersed servers will make your pages load faster from the user's perspective. Additionally, it increases site performance by reducing the roundtrip time for resource requests.

As the CDN has a different domain name, it also provides **domain sharding** benefits. Web browsers are restricted to download several items at once, so the more you use resources hosted on external domains the faster a page loads. This applies to everything from images to javascripts. Hence, Requests for static resources should be parallelized and balanced across the hostnames. -[Quora](https://qr.ae/pGMOQC)

### Without a CDN
![without a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/without-a-cdn.webp?raw=true)

### With a CDN
![with a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/with-a-cdn.webp?raw=true)

----------
## Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.

When I enter a website's URL, in the transport layer, it will ask a local DNS what is the IP of the provided URL. We know the IP of the local DNS server by the DHCP protocol, when a node connects to internet and gets an IP address.

After that, a browser will try to establish a TCP connection with a server having the retrieved IP by **3-way handshake**. When it establish a TCP connection, the browser will form an HTTP request containing an HTTP header and body.

After the HTTP request is sent and the server responds with an HTTP response, the browser will parse the HTTP response header and body, and will render the website. If the document contains additional assets, the browser will create HTTP requests for the assets and send them like above -[Quizlet](https://quizlet.com/fr/175329230/web-developer-interview-questions-network-flash-cards/)

-----

Let us suppose that you type the URL www.quora.com

Step 1 --> Get the ip address of the URL.

To Get the IP address for http://www.quora.com, the steps are
<ol type="a">
<li> System checks the browser cache. Browser caches the DNS data for some time.</li>
<li> If IP address[DNS data for http://www.quora.com] is not found in browser cahe, system will check the OS cache. [in windows gethostbyname system call is made]</li>
<li> If IP address[DNS data for http://www.quora.com] is not found in OS cache, then the request continues to DNS cache maintained by the router.</li>
<li> If DNS data for http://www.quora.com is not found then the search moves to next level where DNS cache of your Internet Service Provider.</li>
<li> If the DNS data is not found in ISP's DNS cache, then ISP's DNS server perform DNS query to search for the required DNS data.</li>
</ol>

Step 2>> Once browser gets the IP address it opens TCP connection and sends HTTP request to the web server.

Step 3>> The web server will handle the request [it happens in multiple steps] and send the HTTP response to the client/browser.

Step 4>> The browser parse the HTML docuemnt and render it.


This is basically summary of what happens when we type an URL and hit enter.

For more detail you can refer this link :-
http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/    -[Quora](https://quora.com/What-really-happens-when-you-navigate-to-a-URL)

----------

## What are the differences between Polling, Long-Polling, Websockets and Server-Sent Events?

### Polling vs Long Polling: 

The difference is this: long polling allows for some kind of **event-driven** notifying, so the server is able to actively send data to the client. Normal polling is a periodical checking for data to fetch, so to say. Wikipedia is quite detailed about that:

With long polling, the client requests information from the server in a way similar to a normal polling; however, if the server does not have any information available for the client, then instead of sending an empty response, the server holds the request and waits for information to become available (or for a suitable timeout event), after which a complete response is finally sent to the client.

Long polling reduces the amount of data that needs to be sent because the server only sends data when there really IS data, hence the client does not need to check at every interval x.

If you need a more performant (and imho more elegant) way of full duplex client/server communication, consider using the WebSocket protocol, it's great! [StackOverflow](https://stackoverflow.com/questions/18099798/polling-vs-long-polling)

----------
#### A flow for Long polling will look as follows
1. A client initiates an XHR/AJAX request, requesting some data from a server.
2. The server does not immediately respond with request information but waits until there is new information available.
3. When there is new information available, the server responds with new information.
4. The client receives the new information and immediately sends another request to the server restarting the process.

#### Some challenges in long polling
- Message ordering and delivery guarantees.
- Message ordering cannot be guaranteed if the same client opens multiple connections to the server.
- If the client was not able to receive the message then there will be possible message loss.
- Performance and scaling
- Device support and fallbacks [Medium](https://medium.com/system-design-blog/long-polling-vs-websockets-vs-server-sent-events-c43ba96df7c1)

### WebSockets

WebSocket is a computer communication protocol which provides full-duplex communication channels over a single TCP connection.
- It is different from HTTP but compatible with HTTP.
- Located at layer 7 in the OSI model and depends on TCP at layer 4.
- Works over port 80 and 443 ( in case of TLS encrypted) and supports HTTP proxies and intermediaries.
- To achieve compatibility, the WebSocket handshake uses Upgrade header to update the protocol to the WebSocket protocol.

The WebSocket protocol enables interaction between a client and a web server with lesser overheads, providing real-time data transfer from and to the server. WebSockets keeps the connection open, allowing messages to be passed back and forth between the client and the server. In this way, a two-way ongoing conversation can take place between the client and the server.

#### Pros and Cons of using websockets:

Pros:

- Full-duplex asynchronous messaging. In other words, both the client and the server can stream messages to each other independently, similarly to what happens with raw TCP. [To be totally correct, raw TCP deals with streams of bytes with no inherent concept of a message]
- WebSockets pass through most firewalls without any reconfiguration.
- Good security model (origin-based security model).
Cons:

- There are still several proxies and transparent proxies not supporting WebSockets.
- A WebSocket server requires different optimizations than traditional Web servers, so that a dedicated platform might be required.
The best approach is to use WebSockets but be ready to automatically fallback to HTTP Streaming and HTTP Long Polling when needed. [Quora](https://www.quora.com/What-are-the-pros-and-cons-of-using-WebSockets)

-----

The disadvantage with using web sockets is that it keeps the connection open on the server for the duration of the time the user is interacting with the page. This will increase the demand on the server, and means that you will always have to scale OUT rather than UP. (A port is hard limited to 64k active connections, and will seriously degrade after 10k or so.)

If you are creating an app that needs constant real-time updates (chat, interactive streaming media, live multiplayer games, etc) then there is no disadvantage to using web sockets, it is the best solution. But if you are creating an app that only needs to update periodically or based on user events, then web sockets is a less economical choice. [Quora](https://www.quora.com/What-are-the-disadvantages-of-WebSockets-and-associated-real-time-communication-frameworks-like-Socket-IO-against-AJAX-and-other-conventional-communication-technologies)

-----

#### Benefits or advantages of Websockets over HTTP
- It supports duplex communication.
- Using websockets, one can send and receive data immediately faster than HTTP. Moreover they are faster than AJAX.
- Cross origin communication (however this poses security risks).
- Cross platform compatibility (web, desktop, mobile)
- HTTP takes upto 2000 bytes of overhead where as websocket takes only 2 bytes.
- Replace long polling
- Websockets are data typed but AJAX calls can only send string datatypes.
#### Drawbacks or disadvantages of Websockets
- Web browser must be fully HTML5 compliant.
- Websockets has no success functions like AJAX.
- Intermediary/Edge caching is not possible with websockets unlike HTTP.
- To build even simple protocol of your own, one can not be able to use friendly HTTP statuses, body etc.
- If application does not require a lot of dynamic interaction, HTTP is much simpler to implement. [rfwireless-world](https://www.rfwireless-world.com/Terminology/Advantages-and-Disadvantages-of-Websockets.html)

### Server-Sent Events

Server-Sent Events are a one-way communication channel where events flow from server to client only. Server-Sent Events allows browser clients to receive a stream of events from a server over an HTTP connection without polling.

A client subscribes to a “stream” from a server and the server will send messages (“event-stream”) to the client until the server or the client closes the stream. It is up to the server to decide when and what to send the client, for instance as soon as data changes.

As SSE is based on HTTP, it is more compliant with existing IT infrastructure like (Load Balancer, Firewall, etc), unlike WebSockets which can be blocked by some firewall. Server-Sent events are not supported by all browsers.

#### A flow for a server sent events could be:

- Browser client creates a connection using an **EventSource API** with a server endpoint which is expected to return a stream of events over time. This essentially makes an HTTP request at given URL.
- The server receives a regular HTTP request from the client and opens the connection and keeps it open. The server can now send the event data as long as it wants or it can close the connection if there are no data.
- The client receives each event from the server and process it. If it receives a close signal from the server it can close the connection
- The client can also initiate the connection close request. [Medium](https://medium.com/system-design-blog/long-polling-vs-websockets-vs-server-sent-events-c43ba96df7c1)


----- 
EventSource [or Server-sent events] is a useful approach for handling things like social media status updates, news feeds, or delivering data into a client-side storage mechanism like IndexedDB or web storage. [Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/EventSource)

## Explain the following request and response headers:

- Diff. between Expires, Date, Age and If-Modified-...
- Do Not Track
- Cache-Control
- Transfer-Encoding
- ETag
- X-Frame-Options

### This is a summary of what these headers are:
  
- Expires - will be labeled stale after specified date.
- Date - The date and time that message was sent.
- Age - The age that object has lived in seconds.
- If-Modified-Since - will return 304 unchanged status code if content is unchanged.
- Transfer-encoding - In normal circumstance server will tell client the content length which server sent, but in some circumstance the content's length remains unknown, and server will send content in chunks. Specifying Transfer-encoding tells client server is sending in this way.
- ETag - an identifier which is used to identify version of a file/resource .
- X-Frame-Options - **Clickjacking** protection.
- Cache-Control - an attribute tells browser how. [Quora](https://www.quora.com/Could-anyone-explain-the-following-request-and-response-headers-read-question-details)

-----

- Do Not Track - Every time your computer sends or receives information over the Web, the request begins with some short pieces of information called headers. These headers include information like what browser you're using, what language your computer is set to, and other technical details. The Do Not Track signal is a machine-readable header indicating that you don't want to be tracked. Because this signal is a header, and not a cookie, users can clear their cookies at will without disrupting the functionality of the Do Not Track flag. [Electronic Frontier Foundation](https://www.eff.org/issues/do-not-track)

----------
## What are HTTP methods? List all HTTP methods that you know, and explain them.

HTTP methods are used to communicate with a server. There are five HTTP methods:
1. GET - used to retrieve resources from a server.
2. POST - used to send data to a server.
3. PUT - used to replace a resource on the server.
4. DELETE - used to delete a resource from the server.
5. PATCH - used to update a resource on the server.
6. HEAD - used to retrieve metadata from a server.
7. OPTIONS - used to retrieve information about the server.


----- The section below, except for the definition for "HEAD" is from [Assertible - Cody Reichert](https://assertible.com/blog/7-http-methods-every-web-developer-should-know-and-how-to-test-them) -----
### GET 

GET requests are the most common and widely used methods in APIs and websites. Simply put, the GET method is used to retreive data from a server at the specified resource. For example, say you have an API with a /users endpoint. Making a GET request to that endpoint should return a list of all available users.

Since a GET request is only requesting data and not modifying any resources, it's considered a safe and **idempotent** method.

### POST

In web services, POST requests are used to send data to the API server to create or update a resource. The data sent to the server is stored in the request body of the HTTP request.

It's worth noting that a POST request is non-idempotent. It mutates data on the backend server (by creating or updating a resource), as opposed to a GET request which does not change any data.

### PUT

Simlar to POST, PUT requests are used to send data to the API to update or create a resource. The difference is that PUT requests are idempotent. That is, calling the same PUT request multiple times will always produce the same result. In contrast, calling a POST request repeatedly make have side effects of creating the same resource multiple times.

Generally, when a PUT request creates a resource the server will respond with a 201 (Created), and if the request modifies existing resource the server will return a 200 (OK) or 204 (No Content).

### PATCH

A PATCH request is one of the lesser-known HTTP methods, but I'm including it this high in the list since it is similar to POST and PUT. The difference with PATCH is that you only apply partial modifications to the resource.

The difference between PATCH and PUT, is that a PATCH request is non-idempotent (like a POST request).

To expand on partial modification, say you're API has a /users/{{userid}} endpoint, and a user has a username. With a PATCH request, you may only need to send the updated username in the request body - as opposed to POST and PUT which require the full user entity.

### DELETE

The DELETE method is exactly as it sounds: delete the resource at the specified URL. This method is one of the more common in RESTful APIs so it's good to know how it works.

If a new user is created with a POST request to /users, and it can be retrieved with a GET request to /users/{{userid}}, then making a DELETE request to /users/{{userid}} will completely remove that user.

### HEAD

The HTTP HEAD method requests the headers that would be returned if the HEAD request's URL was instead requested with the HTTP GET method. For example, if a URL might produce a large download, a HEAD request could read its Content-Length header to check the filesize without actually downloading the file. [MOZILLA](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/HEAD)

### OPTIONS

Last but not least we have OPTIONS requests. OPTIONS requests are one of my favorites, though not as widely used as the other HTTP methods. In a nutshell, an OPTIONS request should return data describing what other methods and operations the server supports at the given URL.

OPTIONS requests are more loosely defined and used than the others, making them a good candidate to test for fatal API errors. If an API isn't expecting an OPTIONS request, it's good to put a test case in place that verifies failing behavior.

