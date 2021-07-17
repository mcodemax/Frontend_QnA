## Traditionally, why has it been better to serve site assets from multiple domains?

It's because browsers usually have limits on the number of concurrent downloads from a domain at a moment. So, serving assets from multiple domains can increase the concurrent level.  -[Quizlet](https://quizlet.com/fr/175329230/web-developer-interview-questions-network-flash-cards/)

----------
Most of large websites store their static content such as Images, JavaScrips & CSS files to a Content Delivery Network or CDN as deploying your content across multiple, geographically dispersed servers will make your pages load faster from the user's perspective. Additionally, it increases site performance by reducing the roundtrip time for resource requests.

As the CDN has a different domain name, it also provides **domain sharding** benefits. Web browsers are restricted to download several items at once, so the more you use resources hosted on external domains the faster a page loads. This applies to everything from images to javascripts. Hence, Requests for static resources should be parallelized and balanced across the hostnames. -[Quora](https://qr.ae/pGMOQC)

### Without a CDN
![without a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/without-a-cdn.webp?raw=true)

### With a CDN
![with a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/with-a-cdn.webp?raw=true)

## Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.

When I enter a website's URL, in the transport layer, it will ask a local DNS what is the IP of the provided URL. We know the IP of the local DNS server by the DHCP protocol, when a node connects to internet and gets an IP address.

After that, a browser will try to establish a TCP connection with a server having the retrieved IP by **3-way handshake**. When it establish a TCP connection, the browser will form an HTTP request containing an HTTP header and body.

After the HTTP request is sent and the server responds with an HTTP response, the browser will parse the HTTP response header and body, and will render the website. If the document contains additional assets, the browser will create HTTP requests for the assets and send them like above -[Quizlet](https://quizlet.com/fr/175329230/web-developer-interview-questions-network-flash-cards/)

----------

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

## What are the differences between Long-Polling, Websockets and Server-Sent Events?



