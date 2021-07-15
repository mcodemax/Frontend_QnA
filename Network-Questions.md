## Traditionally, why has it been better to serve site assets from multiple domains?

It's because browsers usually have limits on the number of concurrent downloads from a domain at a moment. So, serving assets from multiple domains can increase the concurrent level.  -[Quizlet](https://quizlet.com/fr/175329230/web-developer-interview-questions-network-flash-cards/)

Most of large websites store their static content such as Images, JavaScrips & CSS files to a Content Delivery Network or CDN as deploying your content across multiple, geographically dispersed servers will make your pages load faster from the user's perspective. Additionally, it increases site performance by reducing the roundtrip time for resource requests.

As the CDN has a different domain name, it also provides **domain sharding** benefits. Web browsers are restricted to download several items at once, so the more you use resources hosted on external domains the faster a page loads. This applies to everything from images to javascripts. Hence, Requests for static resources should be parallelized and balanced across the hostnames. -[Quora](https://qr.ae/pGMOQC)

### Without a CDN
![without a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/without-a-cdn.webp?raw=true)

### With a CDN
![with a cdn](https://github.com/mcodemax/Frontend_QnA/blob/main/images/with-a-cdn.webp?raw=true)


